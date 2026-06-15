---
title: "YouTube List Maker 프로젝트 정보"
categories:
  - DevLog
tags:
  - YouTube List Maker
  - Flutter
  - Node.js
  - Cloud Run
  - YouTube API
toc: true
toc_sticky: true
toc_label: 목차
---

## 프로젝트 구조

YouTube List Maker: Flutter 앱과 Node.js API 서버로 구성된 Android 앱.

- `youtube-list-maker-app`
    - Flutter Android 앱
    - 사용자 입력, 결과 표시, 링크 열기 담당
- `youtube-list-maker-api`
    - Node.js Express API
    - YouTube 검색, 필터링, 링크 생성 담당
- Google Cloud Run
    - API 서버 배포
- Google Play Console
    - Android 앱 배포
- GitHub Pages
    - 개인정보처리방침 페이지 제공

## 사용한 주요 기술

| 구분 | 기술 |
| --- | --- |
| 앱 | Flutter, Dart |
| Android 배포 | Android App Bundle `.aab`, Play Console |
| API 서버 | Node.js, Express |
| HTTP 요청 | Axios |
| 배포 | Docker, Google Cloud Run |
| 외부 API | YouTube Data API v3 |
| 문서/정책 | GitHub Pages |
| 인증/배포 설정 | Android Keystore, Play App Signing |

## 현재 앱 동작 방식

### 1. 사용자 입력

사용자가 앱에서 다음 정보를 입력한다.

- 가수 이름
- 곡 개수(기본 10개, 최대 30개)



### 2. Flutter 앱에서 API 요청

Flutter 앱은 Cloud Run에 배포된 API 서버로 요청을 보낸다.

### 3. API 서버에서 가수 확인

API는 먼저 입력된 가수가 미리 등록된 Known Artist 목록에 있는지 확인한다.

Known Artist 예시:

- 아이유
- BTS
- 뉴진스
- 화사
- BLACKPINK
- IVE
- aespa
- LE SSERAFIM
- SEVENTEEN
- 임영웅
- 송가인

### 4. 미리 등록된 영상 우선 사용

등록된 가수라면 미리 저장된 공식 음원/뮤직비디오 ID를 우선 사용한다.

이 방식의 장점:

- YouTube API quota 절약
- 응답 속도 개선
- 검색 품질 안정화
- 공식 음원 위주 결과 제공

### 5. 부족하면 YouTube API 검색 사용

Known Artist 목록에 없거나 결과가 부족하면 YouTube Data API를 사용한다.

이때 다음 기준으로 필터링한다.

- Shorts 제외
- 120초 미만 영상 제외
- 가사 영상 제외
- 커버 영상 제외
- 팬 영상 제외
- 리액션 영상 제외
- 티저 / 트레일러 제외
- Official Audio 우선
- Topic 채널 우선
- 공식 MV 우선
- 공식 채널 영상 우선

### 6. 중복 제거

같은 곡이 여러 형태로 나오는 경우를 필터링한다.

예:

- Official Audio
- Official MV
- Performance Video
- Topic 영상
- Lyrics 영상

API는 제목을 정규화해서 같은 곡으로 판단되는 결과를 중복 제거한다.

### 7. 임시 재생목록 링크 생성

최종 영상 ID 목록으로 YouTube 임시 재생목록 링크를 만든다.

저장형 재생목록이 아니라, 사용자가 바로 열 수 있는 링크 방식으로 제공한다.

### 8. YouTube / YouTube Music 링크 제공

- YouTube에서 열기
- YouTube Music에서 열기

YouTube Music 링크는 단순 `watch_videos` 방식이 아니라, YouTube 임시 목록을 실제 `watch?v=...&list=...` 형태로 변환한 뒤 Music 도메인으로 바꿔서 제공한다.

### 9. Flutter 앱에서 결과 표시

앱은 다음을 보여준다.

- 곡 목록
- 썸네일
- 제목
- 영상 ID
- YouTube에서 열기 버튼
- YouTube Music에서 열기 버튼
- 링크 복사 버튼

## 현재 핵심 기능

- Google 로그인 없음
- YouTube 계정 권한 요청 없음
- 저장형 YouTube 재생목록 생성 없음
- YouTube / YouTube Music 임시 재생목록 링크 생성
- 기본 10곡
- 최대 30곡
- Shorts 제외
- 120초 미만 영상 제외
- 중복 곡 제거
- 공식 음원 / Topic / 공식 MV 우선
- 서버 메모리 캐시
- Known Artist 사전 등록
- Cloud Run 저비용 배포

## 비용 절감 구조

Cloud Run 설정:

| 항목 | 설정 |
| --- | --- |
| min instances | 0 |
| max instances | 1 |
| memory | 256Mi |
| cpu | 1 |
| concurrency | 10 |
| CPU throttling | enabled |
| timeout | 120초 |

비용 절감 방법:

- 저장형 재생목록 생성 제거
- Google 로그인 제거
- YouTube API 호출 최소화
- Known Artist 목록 우선 사용
- 서버 메모리 캐시 사용
- Cloud Run 최소 인스턴스 0 유지
- 최대 인스턴스 1로 제한
