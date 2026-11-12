---
title: "고양이 방울방울"
permalink: /apps/cat-cozy-drop/
layout: single
author_profile: true
app_id: cat-cozy-drop
document_type: app
nav_order: 2
last_modified_at: 2026-11-12
toc: true
toc_sticky: true
toc_label: 목차
---

고양이방울방울은 Flutter와 Flame 엔진으로 만든 Android용 물리 기반 머지 퍼즐 게임입니다.
같은 단계의 고양이를 떨어뜨리고 합쳐 더 큰 고양이를 만들며, 최종 단계인 `달잠냥`을 목표로 플레이합니다.

앱은 회원가입, 로그인, 결제, 위치 정보 수집 기능을 제공하지 않으며, 게임 플레이에 필요한 최소한의 로컬 데이터만 사용합니다.

[Google Play에서 설치](https://play.google.com/store/apps/details?id=com.sicorp.catbubbles)

## 현재 출시 상태

- 현재 프로덕션: **1.0.11 (Version Code 17)**
- 실제 게시: **2026년 11월 11일 오전 10시 44분(KST)**
- 출시 범위: **178개 국가·지역, 출시율 100%**
- [1.0.11 프로덕션 업데이트 기록](/records/cat-cozy-drop-1-0-11-production-release/)

## 주요 기능

- 고양이 드롭 퍼즐 gameplay
- 같은 단계 고양이 충돌 시 상위 고양이로 병합
- 물리 엔진 기반 위치, 충돌, 낙하 처리
- 현재 점수 / 최고 점수 표시
- 다음 고양이 미리보기
- 콤보 표시
- 게임 오버 화면
- 달잠냥 생성 감지
- 달잠냥 생성 횟수 기반 컬렉션 진행도
- 컬렉션 진행도 로컬 저장
- 달잠냥 생성 시 반짝이 연출
- 컬렉션 완성 시 클리어 안내
- AdMob 배너 / 전면 광고 연동
- 시작·복귀 시 최소 지원 버전 확인 및 필요한 경우 Google Play 업데이트 안내
- Google Play 배포용 AAB 빌드 지원

## 게임 동작 방식

1. 플레이어가 화면을 터치하거나 드래그해 고양이를 떨어뜨릴 위치를 정합니다.
2. 고양이는 서랍 안으로 떨어지고 물리 엔진에 따라 굴러가거나 충돌합니다.
3. 같은 단계의 고양이 두 마리가 닿으면 다음 단계 고양이로 합쳐집니다.
4. 병합할수록 점수가 증가하며, 연속 병합 시 콤보가 적용됩니다.
5. 최종 단계인 달잠냥을 만들면 컬렉션 진행도가 1칸 채워집니다.
6. 컬렉션은 여러 판에 걸쳐 누적 저장됩니다.
7. 서랍이 꽉 차면 게임 오버가 됩니다.
8. 게임 오버 후 다시 시작할 수 있습니다.

## 고양이 단계

게임에는 총 9단계의 고양이 티어가 있습니다.

- 콩냥
- 양말냥
- 치즈냥
- 턱시도냥
- 삼색냥
- 식빵냥
- 쿠션냥
- 집사냥
- 달잠냥

달잠냥은 최종 단계이며, 달잠냥끼리는 더 이상 합쳐지지 않습니다.

## 서비스 정보

- 앱 이름: 고양이 방울방울
- 플랫폼: Android
- 지원 언어: 한국어·영어
- 로그인·계정 생성: 없음
- 광고: 게임 오버 배너, 게임 오버 2회마다 준비된 전면 광고 표시
- 결제: 없음
- 가격: 무료
- 문의: sicorp.apps@gmail.com
- 패키지명: `com.sicorp.catbubbles`
- 장르: 캐주얼 물리 퍼즐 / 머지 드롭 게임
- 배포 대상: Google Play
- 저장소명: `cat-cozy-drop`

## 데이터 처리 안내

고양이 방울방울은 최고 점수와 게임 설정 등 일부 정보를 사용자의 기기 내부에 저장할 수 있습니다.

앱은 광고 표시를 위해 Google AdMob을 사용하며, AdMob을 통해 광고 ID, 기기 정보, 앱 사용 정보, 광고 상호작용 정보 등이 처리될 수 있습니다.

업데이트 확인 시 GitHub Pages의 공개 HTTPS 정책을 조회하고, 설치 버전 비교는 기기에서 수행합니다. 마지막 유효 정책은 기기에 저장하며 첫 오프라인 실행은 허용합니다. 최고 점수·게임 진행·광고 ID를 정책 요청에 별도로 넣어 보내지 않습니다. 접속 과정에서 호스팅 제공자가 처리할 수 있는 IP·요청 정보는 개인정보처리방침에서 안내합니다.

별도의 자체 서버·회원 데이터베이스는 운영하지 않습니다. 앱의 네트워크 접근은 광고 및 업데이트 정책 조회에 사용됩니다.

## 사용 기술

- Flutter
- Dart
- Flame
- Forge2D / flame_forge2d
- shared_preferences
- google_mobile_ads
- Android Gradle / Google Play App Bundle

## 프로젝트 구조

```text
lib/
  main.dart
  src/
    cat_cozy_drop_app.dart
    ads/
      ad_mob_ids.dart
      game_ads_controller.dart
    updates/
      update_gate.dart
      update_policy.dart
      update_policy_fetch_io.dart
    game/
      cat_cozy_drop_game.dart
      cat_piece.dart
      cat_tier.dart
      game_asset_paths.dart
      game_page.dart
      game_snapshot.dart
      room_components.dart

assets/
  game/
    room_background.png
    cats/
      cat_0.png
      cat_1.png
      ...
      cat_8.png
  brand/
    app-icon-source.png
    app-icon-round-source.png

android/
  app/
    src/main/
      AndroidManifest.xml

play-store-assets/
  app icons
  feature graphic
  phone/tablet screenshots

tooling/
  GeneratePlayStoreAssets.java

../tooling/
  build_flutter_aab.sh
```

## 정책

- [개인정보처리방침](/policies/cat-cozy-drop/)
