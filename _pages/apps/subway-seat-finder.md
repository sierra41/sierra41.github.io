---
title: "지하철 빈자리 찾기"
permalink: /apps/subway-seat-finder/
layout: single
author_profile: true
last_modified_at: 2026-11-06
excerpt: "서울 지하철에서 곧 비워질 좌석을 공유하고 확인하는 Android 앱"
header:
  teaser: /assets/images/apps/subway-seat-finder/icon.png
gallery_phone:
  - url: /assets/images/apps/subway-seat-finder/01-train-selection.webp
    image_path: /assets/images/apps/subway-seat-finder/01-train-selection.webp
    alt: "가까운 역과 실시간 열차 선택"
    title: "가까운 역과 실시간 열차 선택"
  - url: /assets/images/apps/subway-seat-finder/02-car-selection.webp
    image_path: /assets/images/apps/subway-seat-finder/02-car-selection.webp
    alt: "탑승한 호차 선택"
    title: "탑승한 호차 선택"
  - url: /assets/images/apps/subway-seat-finder/03-seat-selection.webp
    image_path: /assets/images/apps/subway-seat-finder/03-seat-selection.webp
    alt: "좌석 위치 선택"
    title: "좌석 위치 선택"
  - url: /assets/images/apps/subway-seat-finder/04-seat-status.webp
    image_path: /assets/images/apps/subway-seat-finder/04-seat-status.webp
    alt: "공유된 좌석 상태 확인"
    title: "공유된 좌석 상태 확인"
  - url: /assets/images/apps/subway-seat-finder/05-exit-station.webp
    image_path: /assets/images/apps/subway-seat-finder/05-exit-station.webp
    alt: "내리는 역 선택과 공유"
    title: "내리는 역 선택과 공유"
  - url: /assets/images/apps/subway-seat-finder/06-today-seats.webp
    image_path: /assets/images/apps/subway-seat-finder/06-today-seats.webp
    alt: "오늘의 빈자리 목록"
    title: "오늘의 빈자리 목록"
gallery_tablet:
  - url: /assets/images/apps/subway-seat-finder/07-tablet-car-selection.webp
    image_path: /assets/images/apps/subway-seat-finder/07-tablet-car-selection.webp
    alt: "태블릿 호차 선택"
    title: "태블릿 호차 선택"
  - url: /assets/images/apps/subway-seat-finder/08-tablet-train-selection.webp
    image_path: /assets/images/apps/subway-seat-finder/08-tablet-train-selection.webp
    alt: "태블릿 열차 선택"
    title: "태블릿 열차 선택"
app_id: subway-seat-finder
document_type: app
nav_order: 3
---

<img src="{{ '/assets/images/apps/subway-seat-finder/icon.png' | relative_url }}" alt="지하철 빈자리 찾기 앱 아이콘" width="112" height="112">

지하철 빈자리 찾기는 지하철 이용자가 곧 비워질 좌석 정보를 쉽게 공유하고 확인할 수 있는 앱입니다.

가까운 역의 실시간 지하철 도착 정보를 확인하고, 내가 탄 열차와 호차, 좌석 위치, 내릴 역을 그림 방식으로 선택할 수 있습니다.

다른 이용자는 같은 열차의 좌석 정보를 보고 곧 비워질 자리를 더 쉽게 찾을 수 있습니다.

[Google Play에서 설치하기](https://play.google.com/store/apps/details?id=com.sicorp.subwayseatfinder){: .btn .btn--primary}

![지하철 빈자리 찾기 스토어 홍보 이미지]({{ '/assets/images/apps/subway-seat-finder/feature-graphic.png' | relative_url }})

## 주요 기능

- 가까운 지하철역 기준 열차 선택
- 실시간 지하철 도착 정보 확인
- 열차, 호차, 좌석 위치를 그림으로 선택
- 내릴 역 선택
- 곧 비워질 좌석 정보 공유
- 부정확한 정보 확인 요청
- 오늘의 빈자리 목록과 좌석 위치 확인, 좋아요
- 내 공유 기록 확인과 계정 삭제

좌석 정보는 이용자 공유를 바탕으로 하므로 실제 상황과 다를 수 있습니다. 현재는 서울 지하철 중심으로 제공하며, 이동할 때에는 주변 승객과 안전을 먼저 살펴 주세요.

## 앱 화면

현재 Google Play에 게시된 휴대전화 스크린샷입니다. 열차 → 호차 → 좌석 → 내리는 역 순서로 공유하고, 오늘의 빈자리에서 다른 이용자의 공유를 확인할 수 있습니다. 이미지를 누르면 크게 볼 수 있습니다.

{% include gallery id="gallery_phone" layout="third" %}

### 태블릿 화면

{% include gallery id="gallery_tablet" layout="half" %}

이미지는 2026년 11월 6일 현재 게시된 스토어 등록정보를 기준으로 하며, 등록정보의 최근 이미지 업데이트는 2026년 10월 21일입니다.

## 최근 업데이트 · 1.0.21

- 새로고침과 중복 요청 처리를 개선했습니다.
- 요청이 많을 때 재시도 대기시간을 안내합니다.
- 좌석 공유·좋아요·신고 상세는 만료 후 30일이 지나면 순차 정리하며 누적 활동 수치는 유지합니다.

## 데이터 안내

지하철 빈자리 찾기는 가까운 지하철역을 찾기 위해 기기의 위치 권한을 요청할 수 있습니다.

위치 정보는 가까운 역 계산에 사용되며, 정확한 위도/경도는 앱 서버에 저장하지 않습니다.

본 앱은 서울특별시 공공데이터를 활용합니다.

## 서비스 정보

- 앱 이름: 지하철 빈자리 찾기
- 플랫폼: Android 7.0 이상
- 가격: 무료 · 광고 포함
- 앱 카테고리: 지도/내비게이션
- 현재 버전: 1.0.21 (Version Code 36)
- 스토어 업데이트 날짜: 2026년 11월 5일
- 프로덕션 게시 확인: 2026년 11월 6일 · 출시율 100%
- 스토어 표시 출시일: 2026년 6월 25일
- 개발자: sicorp.apps
- 문의: sicorp.apps@gmail.com

## 관련 문서

- [프로젝트 정보](/devlog/subway-seat-finder-project-info/)
- [계정 삭제 안내](/policies/subway-seat-finder-account-deletion/)
- [개인정보처리방침](/policies/subway-seat-finder/)
