---
layout: single
title: "Android 개발공부 - 앱 출시 과정"
read_time: true

categories: 
 - Android
tags: 
 - Android
last_modified_at: '2021-03-28 23:55:00 +0800'
toc: true
toc_sticky: true
toc_label: 목차

---
# 애플리케이션 출시 기본작업
애플리케이션을 출시하려면 먼저 애플리케이션의 출시 버전을 구성, 빌드, 테스트해야 한다.   
**구성** :  최적화하는 기본적인 코드 정리 및 코드 수정 작업   
**빌드** :  디버그 빌드 프로세스 (JDK 및 Android SDK 도구 사용)   
**테스트** : 실제 환경 조건에서 애플리케이션이 정상적으로 작동하는지 확인하는 최종 검사   
⇒ **결과물** :  서명된 APK 파일 (해당 파일로 google play나 애플마켓을 통해 배포)   
    ![image](https://user-images.githubusercontent.com/66898243/112755824-6487ba00-901d-11eb-8e93-5d7195a27467.png)    
     
         
## 1. 자료 및 리소스 수집
애플리케이션 서명을 위한 암호화 키, 애플리케이션 아이콘, 최종 사용자 라이선스 계약   

    
 - **암호화 키**   
 Android 시스템에서 각 애플리케이션은 개발자가 비공개 키를 보유한 인증서를 사용하여 디지털 방식으로 서명해야한다.     
 애플리케이션 작성자를 식별하고 애플리케이션과 신뢰관계를 구축하는 수단으로 사용된다.    
 [애플리케이션 서명](https://developer.android.com/studio/publish/app-signing)     
    
 - **애플리케이션 아이콘**    
 사용자가 애플리케이션을 식별하는 이미지    
 아이콘 가이드라인을 준수하여 애플리케이션 아이콘을 만들어야한다.           
 [아이콘 가이드라인](https://developer.android.com/google-play/resources/icon-design-specifications?hl=ko)    
    
 - **최종 사용자 라이선스 계약**    
최종 사용자 라이선스 계약(EULA) :  개발자의 인력, 조직 및 지적 재산을 보호        
    
 - **기타 자료**    
홍보&마케팅 자료.  
ex) Google Play :  홍보 문구, 애플리케이션 스크린샷       
    
        
    
## 2.  **애플리케이션 구성**    
사용자의 Android 기기에서 설치&실행할 수 있는 출시용 패키지가 필요   
⇒ 디버그 APK 파일과 동일한 구성요소, 즉 컴파일된 소스 코드, 리소스, 매니페스트 파일   
⇒ 고유 인증서로 서명되어야 하며 zipalign 도구로 최적화되어야 한다       
   
 - **패키지 이름 선택**      
 애플리케이션이 버전업되고 수명이 지속되는 동안 적합하게 사용될 수 있는 이름을 선택한다   
 애플리케이션을 사용자에게 한번 배포한 후에는 변경 불가   
 패키지 이름은 매니페스트 파일에서 설정 가능   
    
 -  **로깅 및 디버깅 사용 중지**     
 출시할 애플리케이션을 빌드하기 전에 로깅을 비활성화하고 디버깅 옵션을 사용 중지해야 한다   
 로깅 : 소스 파일에서 Log 메서드 호출을 삭제하여 비활성화   
 디버깅 : 매니페스트 파일의 <application> 태그의 android:debuggable 속성을 삭제하거니 false 처리하여 중지    
 프로젝트 자체에서 만든 로그 파일이나 정적 테스트 파일들을 삭제   
 startMethodTracing() 및 stopMethodTracing() 메서드 호출과 같은 코드에 추가한 모든 Debug 추적 호출 삭제   
 ![image](https://user-images.githubusercontent.com/66898243/112756531-99e1d700-9020-11eb-898b-e053528341f1.png)     
    
 - **프로젝트 디렉토리 정리**    
 Android 프로젝트 디렉터리 구조를 준수.   
 이탈한 파일, 분리된 파일 정리.   
 **jni/** : Android NDK와 연결된 소스 파일(예: .c, .cpp, .h 및 .mk 파일)만 포함   
 **lib/** : 타사 라이브러리 파일이나 사전 빌드한 공유 및 정적 라이브러리가 포함된 비공개 라이브러리 파일(예: .so 파일)만 포함. 사용하지 않는 테스트 라이브러리는 삭제   
 **src/** : 애플리케이션의 소스 파일(.java 및 .aidl 파일)만 포함. .jar 파일은 포함되어서는 안된다   
 사용하지 않는 비공개&독점적 데이터 파일 삭제 (res/ 디렉토리의 오래된 드로어블 파일, 레이아웃 파일 및 값 파일)   
 **assets/, res/raw/** : 업데이트나 삭제가 필요한 원본 저작물 파일 및 정적 파일 여부 검토    
    
 - **매니페스트와 Gradle 빌드 설정 검토**    
 uses-permissio 요소   
 android:icon 및 android:label 속성   
 android:versionCode 및 android:versionName 속성      
    
 - **호환성**   
 여러 화면 지원 권장사항 준수 : 모든 화면 크기에 모양이 양호하도록   
 [화면 호환성](https://developer.android.com/guide/practices/screens_support#screen-independence)   
 애플리케이션 최적화 : 지원 버전에 맞는 앱 최적화   
 지원 라이브러리 사용 : 지원 버전에 맞는 api 사용    
 [지원 라이브러리](https://developer.android.com/topic/libraries/support-library)   
    
 - **URL 또는 경로 확인**   
 테스트 URL이나 경로가 아니라 서버와 서비스 프로덕션 URL과 경로를 사용하는지 확인   
        
    
            
## 3. **앱 빌드 및 서버 준비**
 - **앱 빌드 필요 요소**    
=> 서명이 완료되고 최적화 된 출시용 APK 파일    
안드로이드 스튜디오에 통합된 Gradle 빌드 시스템을 사용하면 쉽게 서명에 적합한 인증서와 비공개 키를 생성하고 최적화된 출시용 APK 파일을 빌드 할 수 있다.   
- **원격 서버 이용**     
서버가 프로덕션 용도로 구성되어야하며 서버의 보안이 보장되어야 한다. 특히 앱 내에서 결제를 구현하여 원격서버에서 서명 인증 단계를 실행하는 경우 특히 중요하다.    
   
 
       
## 4. **출시 테스트**
실제 기기 및 네트워크 환경에서 제대로 실행되는지 확인하는 절차.    
- 핸드셋 크기의 기기, 태블릿 크기의 기기 모두 테스트 할 것    
- UI 요소 크기가 다양한 화면에 맞는지 확인 할 것    
- 애플리케이션 성능과 배터리 효율이 허용 수준인지 확인 할 것   
 [출시 테스트 요소](https://developer.android.com/docs/quality-guidelines/core-app-quality)
     
    
         
       
## 참고 목록
[참고1 APK 확장API 파일](https://developer.android.com/google/play/expansion-files#Overview)    
[참고2 API 수준 요구사항](https://developer.android.com/distribute/best-practices/develop/target-sdk)    
[참고3 출시 준비](https://developer.android.com/studio/publish/preparing)    
[참고4 앱 게시](https://developer.android.com/studio/publish)   
[참고5 앱 테스트](https://developer.android.com/studio/test)    
