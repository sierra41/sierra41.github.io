---
title: "고양이 방울방울 프로젝트 정보"
permalink: /devlog/cat-cozy-drop-project-info/
layout: single
author_profile: true
---

# 고양이방울방울

고양이방울방울은 Flutter와 Flame 엔진으로 만든 Android용 물리 기반 머지 퍼즐 게임입니다.  
같은 단계의 고양이를 떨어뜨리고 합쳐 더 큰 고양이를 만들며, 최종 단계인 `달잠냥`을 목표로 플레이합니다.

## 프로젝트 개요

- 앱 이름: 고양이방울방울
- 패키지명: `com.sicorp.catbubbles`
- 플랫폼: Android
- 장르: 캐주얼 물리 퍼즐 / 머지 드롭 게임
- 배포 대상: Google Play
- 저장소명: `cat-cozy-drop`

## 사용 기술

- Flutter
- Dart
- Flame
- Forge2D / flame_forge2d
- shared_preferences
- google_mobile_ads
- Android Gradle / Google Play App Bundle

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

## 프로젝트 구조

```text
lib/
  main.dart
  src/
    cat_cozy_drop_app.dart
    ads/
      ad_mob_ids.dart
      game_ads_controller.dart
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
