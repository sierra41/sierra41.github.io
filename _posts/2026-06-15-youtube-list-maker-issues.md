---
title: "YouTube List Maker 이슈 해결"
categories:
  - DevLog
tags:
  - YouTube List Maker
  - Cloud Run
  - YouTube API
  - YouTube Music
  - Node.js
toc: true
toc_sticky: true
toc_label: 목차
---

## 1. Cloud Run 비용 문제

### 문제

Google Cloud 무료 체험판 종료 후 서버를 배포 요금에 대한 문제

### 해결

Cloud Run을 가능한 한 저비용 제한하여 설정하고 배포하였으며, 특정 금액 초과시 알림을 설정함

적용한 설정:

- min instances: 0
- max instances: 1
- memory: 256Mi
- cpu: 1
- concurrency: 10
- CPU throttling enabled
- timeout: 120초

---

## 2. YouTube API quota 부족

### 문제

초기 구조는 사용자가 로그인을 하고 사용자의의 YouTube 계정에 실제 재생목록을 생성하는 방식으로 진행되었으나 quota 소모가 매우 컸음.

문제점:

- 사용자 수가 늘면 quota가 빠르게 소진됨
- 10곡 기준으로 중복제거 등의 프로세스를 진행하면 5번 이하의 호출로도 모든 quota가 소진됨
- 비공개 테스트만 해도 여러 명이 반복 사용하면 quota 부족 발생
- 상용 앱으로 운영하기 어려움

### 해결

저장형 재생목록 생성을 제거하고 영상 ID 기반의 임시 재생목록 링크를 생성하는 방식으로 변경.

변경 전:

```text
Google 로그인
YouTube 권한 요청
사용자 계정에 재생목록 직접 생성
```

변경 후:

```text
로그인 없음
YouTube 권한 요청 없음
임시 재생목록 링크 생성
```

---

## 3. YouTube Music 링크가 제대로 열리지 않는 문제

### 문제

YouTube 링크는 정상적으로 열렸지만, YouTube Music 링크가 목록처럼 열리지 않음.

기존 방식:

```text
https://music.youtube.com/watch_videos?video_ids=...
```

이 방식은 YouTube Music에서 정상적인 임시 재생목록으로 동작하지 않음

### 해결

서버에서 먼저 YouTube 임시 재생목록 링크를 실제 링크로 변환.

변경 후 방식:

```text
https://music.youtube.com/watch?v=첫번째영상ID&list=임시목록ID
```

또한 실패 시 첫 번째 곡으로라도 열리도록 fallback URL을 추가.

---

## 4. 검색 결과 중복 문제

### 문제

검색 결과에 같은 곡이 여러 번 나오는 이슈 발생.

예:

- Official MV
- Official Audio
- Topic 영상
- Performance Video
- Lyrics Video
- Cover 영상

### 해결

곡 제목 정규화 로직을 추가.

처리 내용:

- HTML entity decode
- 괄호/대괄호 제거
- Official / MV / Audio 같은 노이즈 단어 제거
- 아티스트 이름 제거
- 공백 정리
- 같은 곡으로 보이는 항목 중복 제거

---

## 5. 검색 결과 품질 문제

### 문제

원하는 것은 음악 재생목록인데, 공식 채널과 영상을 우선으로 필터링하다보니 검색 결과에는 영상 콘텐츠 위주로 설정되어 공식 mv가 없는 음원들이 배제되는 경우가 발생.

예:

- 커버 영상
- 리액션 영상
- 팬캠
- 티저
- 트레일러
- 가사 영상
- Shorts

### 해결

필터링 기준을 추가했다.

제외 대상:

- Shorts
- lyrics / 가사
- karaoke
- cover
- fan
- instrumental
- reaction
- fancam
- teaser
- trailer
- behind
- dance practice

우선 대상:

- Official Audio
- Topic 채널
- Official Music Video
- Official MV
- 공식 채널
- VEVO

---

## 6. Shorts와 짧은 영상 문제

### 문제

검색 결과에 Shorts나 짧은 클립이 섞임.

### 해결

영상 길이 필터를 추가.

현재 기준:

```text
120초 미만 영상 제외
```

YouTube videos API에서 duration 정보를 가져와 필터링한다.

---

## 7. API 응답 속도 문제

### 문제

재생목록 생성 버튼을 누른 뒤 결과가 나오기까지 시간이 최대 8초이상 걸림.

원인:

- YouTube 검색 API 호출
- 영상 상세 조회 API 호출
- duration 확인
- 필터링
- 중복 제거

### 해결

Known Artist 목록과 메모리 캐시를 추가.

개선 효과:

- 등록된 가수는 API 호출 없이 빠르게 응답 가능
- 반복 검색은 캐시에서 바로 응답
- quota 절약
- 체감 속도 개선

---

## 8. 서버 메모리 캐시 도입

### 문제

같은 검색어를 반복해서 요청해도 매번 YouTube API를 호출하여 속도저하 및 quota 낭비.

### 해결

메모리 캐시를 추가. (서버비용 최소화 한도에서 추가)

캐시 기준:

| 유형 | 보관 기간 |
| --- | --- |
| 인기 검색어 | 7일 |
| 일반 검색어 | 1일 |
| 실패 / 결과 없음 | 1시간 |

캐시 키:

```text
artist + limit
```

---

## 9. Known Artist 목록 도입

### 문제

YouTube API 검색만으로는 quota 소모가 크고 결과 품질도 불안정.

### 해결

유명 가수의 공식 음원/뮤직비디오 ID를 미리 등록하여 데이터 확보. 등록된 가수는 YouTube API 검색 없이 결과를 제공 가능.

장점:

- 빠름
- quota 절약
- 결과 품질 안정
- 공식 음원 위주 구성 가능

단점:

- 최신곡의 반영이 불가하여 주기적으로 추가적인 수동 업데이트 필요
