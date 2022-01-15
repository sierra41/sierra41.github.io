---
layout: single
title: "Android 개발공부 - Android 4대 컴포넌트(Component)"
read_time: true

categories: 
 - Android
tags: 
 - Android
last_modified_at: '2021-04-02 20:55:00 +0800'
toc: true
toc_sticky: true
toc_label: 목차

---
## Android 4대 컴포넌트(Component)    
안드로이드의 특징 중 하나는 컴포넌트(Component) 기반으로 개발된다는 것이다.   
여기서 컴포넌트는 앱의 구성 단위로 안드로이드 어플리케이션을 생성할 수 있도록 제공되는 구성요소이다.   
![image](https://user-images.githubusercontent.com/66898243/113412456-4b9f5000-93f3-11eb-9776-0d21240e8aaf.png)   
- 각 컴포넌트는 하나의 독립적인 형태로 존재한다   
- 각 컴포넌트는 고유의 기능을 수행한다   
- 각 컴포넌트는 인텐트(intent)를 통해 서로 상호작용이 가능하다   
   
## 컴포넌트의 종류   
   
### 1. 액티비티 (Activity)   
![image](https://user-images.githubusercontent.com/66898243/113414204-65db2d00-93f7-11eb-8000-1691b33c8088.png)   
- 액티비티는 화면 UI 담당하는 컴포넌트로, android.app.Activity 클래스를 상속받아 생성한다.   
- Manifest.xml에서 activity태그로 액티비티에 대한 설정을 변경하거나 다른 액티비티를 추가할 수 있으며    
  Activity Stack에서 ActivityManager로 인해 관리 된다.   
- 액티비티는 사용자가 앱과 상호작용하는 단일 화면을 의미한다. 즉, 앱과 사용자와의 상호작용을 담당하는데 
  액티비티는 화면에 표시하는 역할만 수행하고 화면에 표시될 내용은 뷰(View)가 수행한다
- 안드로이드 어플리케이션은 반드시 하나 이상의 액티비티를 가지고 있다   
- 인텐트(intent)를 통해 다른 어플리케이션의 액티비티를 호출할 수 있다   
- 2개 이상의 엑티비티를 동시에 Display 할 수 는 없지만    
  액티비티 내의 프래그먼트(Fragment)를 추가하여 화면을 분할시킬 수는 있다   
- 액티비티가 기본적으로 가지고 있는 생명주기를 상태에 맞추어 재정의하여 원하는 기능을 구현할 수 있다.   
- 액티비티 생명주기 : void onCreate(Bundle savedInstanceState), void onStart(), void onResume(), void onDestroy() 등   
![image](https://user-images.githubusercontent.com/66898243/113414998-39c0ab80-93f9-11eb-9203-56d393d44ff9.png)   
   
### 2. 서비스(Service)      
![image](https://user-images.githubusercontent.com/66898243/113414517-24974d00-93f8-11eb-848b-42f17b98d786.png)    
- UI 없이 백그라운드에서 실행되는 컴포넌트로 Android.app.Service 클래스를 상속받아 생성한다    
- 새로운 서비스를 시작할 때는 Manifest.xml에서 새 서비스 정보를 추가하여 사용한다   
- 사용자와 직접적으로 상호작용하는 구성요서는 아니며, 백그라운드에서 음악을 듣거나 파일을 다운로드하는 등 액티비티에서 처리하기 힘든 작업을 처리한다   
- 장기간 실행된 상태를 유지하기 위해서 서비스가 비정상적으로 종료되어도 자동으로 재실행되며, 애플리케이션이 종료되어도 이미 시작이 된 서비스는 백그라운드에서 동작한다.   
- 서비스는 액티비티와 같이 메인 스레드(UI스레드)에서 동작하기 때문에 서비스 내에서 별도의 스레드를 생성하여 작업을 처리해야한다.   
- 메인 액티비티에서 startService()를 이용하여 서비스를 실행시킬 수 있다.      
![image](https://user-images.githubusercontent.com/66898243/113417974-83ac9000-93ff-11eb-8cc3-153b668b44f7.png)      
- 네트워크(Network)와 연동하여 네트워크를 통해서 데이터를 가져올 수 있다.   
- 서비스 생명주기 :  생성 -  void onCreate(), 시작  - void onStart(Intent intent), 제거 - void onDestroy()   
![image](https://user-images.githubusercontent.com/66898243/113417982-87401700-93ff-11eb-85b7-f3fd8f6d02df.png)   
   
### 3. 콘텐츠 프로바이더(ContentProvider)   
- 어플리케이션 사이에 데이터 공유를 관리하는 컴포넌트로 android.content.ContentProvider 클래스를 상속받아 생성한다.   
- 파일입출력, SQLifeDB, Web 등에 저장된 데이터들이 콘텐츠 프로바이더를 통해 표준화된 인터페이스로 공유될 수있다.   
- 생명주기를 가지고 있지 않으며   
- 데이터베이스의 CRUD(Create, Read, Update, Delete) 칙을 준수하며 데이터의 Read, Write 권한이 있어야 접근이 가능하다.   
- 작은 데이터는 인텐트로 공유가 가능하지만 비디오, 사진, 음악 파일 등 용량이 큰 데이터는 콘텐츠 프로바이더가 적합하다.   
    
### 4. 브로드캐스트 리시버(BroadcastReceiver)   
![image](https://user-images.githubusercontent.com/66898243/113417997-8effbb80-93ff-11eb-99cd-07a99dbaaf75.png)   
- 안드로이드 OS에서 발생하는 이벤트와 정보를 수신만 하는 컴포넌트로    
  android.content.BroadcastReceiver 클래스를 상속받아 생성한다   
- 사용자 디바이스의 배터리 부족, 부팅시 앱 초기화, 네트워크 연결 끊김, 문자수신 등 정보를 받아 반응한다.   
- 대부분 UI를 가지지 않으며 이벤트 발생 시 상태바 알림 표시를 통해 정보를 방송(BroadCast)한다.   
- 한 하나의 콜백 메소드 : void onReceive(Context, Intent) - 메시지가 리시버로 도착하면 자동 실행되어 인텐트객체와 연결된 객체로 전달   
   
### - 인텐트 (Intent) : 컴포넌트 사이의 통신수단   
- 액티비티, 서비스, 브로드캐스트 리시버는 인텐트로 활성화되며, 주요 기능은 컴포넌트 실행이다.   
- android.content.Intent 클래스를 상속받아 생성된다.   
- 같은 어플리케이션 내에서 다른 액티비티로 화면을 전환하거나 다른 어플리케이션의 컴포넌트를 활성화할 수 있다.   
- 컴포넌트A가 컴포넌트B를 호출할 때 B의 이름, B의 속성들이 표시하며 컴포넌트B에서 컴포넌트A로 결과를 전달될 때도 사용된다.   
   
      
         
## 참고   
[[Android] 안드로이드 기초 - 안드로이드 4대 컴포넌트 : 액티비티, 서비스, 콘텐츠 프로바이더, 브로드캐스트 리시버](https://4z7l.github.io/2020/07/08/android-4-component.html)   
[[Android] 안드로이드 4대 컴포넌트(구성요소)란 무엇인가?](https://coding-factory.tistory.com/205)   
[안드로이드 (Android) 4대 컴포넌트(구성요소)](https://velog.io/@jojo_devstory/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-Android-4%EB%8C%80-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8)   
