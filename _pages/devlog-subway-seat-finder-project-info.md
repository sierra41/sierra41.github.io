---
title: "지하철 빈자리 찾기 프로젝트 정보"
permalink: /devlog/subway-seat-finder-project-info/
layout: single
author_profile: true
last_modified_at: 2026-11-06
---

지하철 빈자리 찾기는 서울 지하철 이용자가 곧 비워질 좌석을 공유하고 같은 열차의 정보를 확인하는 Android 앱입니다.

## 프로젝트 개요

| 항목 | 내용 |
| --- | --- |
| 앱 ID | `subway-seat-finder` |
| 패키지 | `com.sicorp.subwayseatfinder` |
| 플랫폼 | Android 7.0 이상 |
| 소스 버전 | 1.0.21+36 |
| 프로덕션 | 1.0.21 (36) · 출시율 100% |
| 스토어 업데이트 / 게시 확인 | 2026-11-05 / 2026-11-06 |
| 스토어 표시 출시일 | 2026-06-25 |
| 수익화 | 무료 · AdMob 광고 |
| 저장소 | [sierra41/subway-seat-share](https://github.com/sierra41/subway-seat-share) |

## 주요 기능과 화면

Google 로그인 후 가까운 역과 실시간 열차를 확인하고, 열차·호차·좌석·내리는 역을 순서대로 선택해 공유합니다. 오늘의 빈자리에서 공유 내역과 좌석 위치를 확인하고 좋아요를 남길 수 있습니다. 부정확한 정보 확인 요청, 내 공유 기록, 계정 삭제, Google Play 인앱 업데이트를 제공합니다.

[앱 아이콘·홍보 이미지·휴대전화 및 태블릿 스크린샷 보기](/apps/subway-seat-finder/#앱-화면)

## 프로그램 구조

```text
Flutter Android 앱
  → Firebase Auth: Google 로그인과 ID 토큰
  → Cloudflare Worker: 인증 검증, 좌석 API, 요청 제한, 짧은 캐시
    → Cloudflare D1: 사용자·좌석·좋아요·신고와 누적 집계
    → 서울 공공데이터: 실시간 열차 정보
```

Firebase는 인증에 사용하며 좌석 데이터는 D1에서 관리합니다. 앱이 외부 지하철 API를 직접 호출하지 않고 Worker가 중계합니다. 위치 정보는 가까운 역 계산에 사용하며 정확한 위도·경도를 앱 서버에 저장하지 않습니다.

| 영역 | 역할 |
| --- | --- |
| `lib/src/auth/` | Firebase Google 로그인 |
| `lib/src/data/` | API 저장소와 공통 요청 관리자, 로컬 샘플 저장소 |
| `lib/src/models/` | 열차·좌석 모델 |
| `lib/src/ui/` | 열차·호차·좌석 탐색, 공개 기록, 내 정보 |
| `server-worker/` | 인증·좌석·관리자 API, D1 마이그레이션, 정리 작업 |
| `store-assets/play-console/` | 스토어 제출용 에셋 작업본 |

## 현재 운영 상태

2026년 11월 6일 Google Play 공개 상세에서 1.0.21을, Console에서 프로덕션 36 (1.0.21)과 출시율 100%를 확인했습니다. 스토어의 버전 업데이트 날짜는 11월 5일이며 Console의 최근 게시일은 11월 6일입니다.

1.0.21은 중복 조회와 새로고침을 개선하고 요청이 많을 때 대기시간을 안내합니다. Worker는 요청 제한과 짧은 조회 캐시를 사용합니다. 만료된 좌석·좋아요·신고 상세는 만료 후 30일이 지나면 순차 정리하고 회원별 누적 집계는 유지합니다. 관리자 전용 회원 조회 기능은 권한이 있는 계정에서만 접근합니다.

## 다음 확인 항목

- 실제 관리자 계정에서 회원 조회 화면 확인
- 로그인·공유·좋아요·신고·계정 삭제의 운영 회귀 확인
- Android 15 이상에서 화면 가장자리와 인셋 표시 확인

## 관련 링크

- [Google Play](https://play.google.com/store/apps/details?id=com.sicorp.subwayseatfinder)
- [앱 소개와 스토어 이미지](/apps/subway-seat-finder/)
- [개인정보처리방침](/policies/subway-seat-finder/)
- [계정 삭제 안내](/policies/subway-seat-finder-account-deletion/)
