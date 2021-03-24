---

layout: single
title: "MVC, MVP, MVVM 디자인 패턴 비교"
read_time: true
last_modified_at: '2021-03-29 23:36:00 +0800'
categories:

- etc
tags:
- android
- mvc
- mvp
- mvvm
toc: true
toc_sticky: true
toc_label: 목차

---

## MVC, MVP, MVVM 디자인 패턴은 왜 필요한가?

프로그램의 크기가 점점 커짐에 따라 코드의 관리가 어렵고 유지보수와 개발효율이 떨어지게 되는데,    
이를 개선하기 위해 역할에 따라 코드를 분리시켜 서로 간의 의존성을 관리하는 프레임워크 패턴이 사용되게 됩니다.     
    
---   
    
### MVC 패턴 : Model + View + Controller    

**Model**     
db, network 등 프로그램에서 사용되는 데이터와 데이터를 처리하는 부분.     
View, Control에 종속적이지 않고 재사용이 가능함    
**View**    
사용자에게 보여지는 UI 부분. 웹페이지나 모바일어플의 화면.     
**Controller**    
사용자의 입력을 받고 처리하는 부분.      
Model과 View의 매개체    
<img src = "https://user-images.githubusercontent.com/66898243/112164023-e8623080-8c30-11eb-9ec3-28e69e8cdebd.png" width="500px">   
<img src = "https://user-images.githubusercontent.com/66898243/112809040-939d3a80-90b4-11eb-863d-c70cde0912a4.png" width="500px">   
<img src = "https://user-images.githubusercontent.com/66898243/112809626-263dd980-90b5-11eb-9e92-ec8641211b01.png" width="500px">     
<img src = "https://user-images.githubusercontent.com/66898243/112810296-d4e21a00-90b5-11eb-9942-6dd66608bc75.png" width="500px">         
    
1. Controller로 입력이 들어옴    
2. Controller가 Model을 데이터 업데이트하고    
3. Controller은 Model의 데이터 변화에 따라 나타낼 View를 선택    
4. View 갱신    
    
- 장점    
View와 Model을 분리 => Model의 비종속성으로 재사용 가능   
구현이 쉽고 단순함 => 개발기간이 짧아짐(특히 안드로이드에서 액티비티에 모든 동작을 넣으면 됨)   
유닛테스트에서 View는 테스트할 부분이 없으므로 Model만 하면 됨   
- 단점   
View와 Model 사이에 의존성이 있음 => View가 UI갱신을 위해 직/간접적으로 Model을 참조하므로 로직이 복잡하고 유지보수가 어렵다   
Controller가 안드로이드 API에 종속됨 => 유닛테스트가 어려워짐
    
---   
    
### MVP 패턴 : Model + View + Presenter   
**Model**   
db, network 등 프로그램에서 사용되는 데이터와 데이터를 처리하는 부분.   
View, Presenter 모두에게 의존적이지 않고 독립적으로 동작.   
**View**   
사용자에게 보여지는 UI 부분. 웹페이지나 모바일어플의 화면. 
안드로이드에서는 Activity, Fragment      
유저액션 및 라이프사이클 상태 변경을 Presenter에 전달하고   
Presenter에게서 Model이 처리한 데이터를 전달받음   => Presenter에 의존적
**Presenter**     
(Controller와 유사하게) Model과 View의 매개체    
View에 직접 연결되지는 않고 인터페이스로 상호작용  => 모듈화/유연성 증가 
View에게 Data(내용)만 전달 => 표현은 View가 담당   
<img src = "https://user-images.githubusercontent.com/66898243/112848205-c9591800-90e2-11eb-8b0d-0036844501dc.png" width="500px">   
<img src = "https://user-images.githubusercontent.com/66898243/112842612-b3e0ef80-90dc-11eb-8a7f-6e96d2f902d6.png" width="500px">   
    
1. View로 입력이 들어옴   
2. View에서 Presenter에게 데이터를 요청   
3. Presenter에서 Model에게 데이터를 요청   
4. Model은 Presenter에게 데이터를 응답   
5. Presenter는 View에게 데이터를 응답   
6. View는 응답받은 데이터를 이용하여 화면 출력   
   
- 장점   
Model과 View의 결합도가 낮음 => 유지보수 및 확장 편이    
유닛테스트 시 테스트 코드 작성 편하고 안전함   
- 단점     
앱이 커질수록 View와 Presenter의 의존성이 커짐   
시간이 지날수록 Presenter에 로직이 집중되며 분리가 힘들어짐   
- MVC와의 차이점   
Presenter는 View에 연결되지 않은 인터페이스 역할을 함.   
안드로이드의 Activity, Fragment가 View의 일부로 동작하며    
View가 유저 액션을 Presenter로 전달하고,    
(Presenter에서 받은 데이터로) View가 화면을 표시함.   
   
---   
    
### MVVM 패턴 : Model + View + ViewModel
**Model**   
db, network 등 프로그램에서 사용되는 데이터와 데이터를 처리하는 부분.   
ViewModel에서 데이터를 가져갈 수 있도록 데이터를 준비하고 이벤트를 보냄.   
**View**   
사용자에게 보여지는 UI 부분. 웹페이지나 모바일어플의 화면.   
안드로이드의 Activity나 Fragment   
ViewModel에서 상태 변화가 전달되면 화면을 갱신.   
**ViewModel**   
View를 나타내기 위한 Model.   
View와 연관된 로직이 처리되는 부분. View가 데이터 바인딩 할 수 있는 속성, 명령으로 구성    
View:ViewModel은 n:1의 관계. 여러개의 Fragment가 하나의 ViewModel을 가질 수 있다.
<img src = "https://user-images.githubusercontent.com/66898243/112846495-150ac200-90e1-11eb-9c32-cc1e7027a6d8.png" width="500px">  
<img src = "https://user-images.githubusercontent.com/66898243/112845267-a37e4400-90df-11eb-973d-d2bbbb86fd42.png" width="500px">   
   
  
1. View로 입력이 들어옴   
2. View에서 ViewModel로 명령 
3. ViewModel은 Model에 데이터 요청 
4. Model은 ViewModel에게 데이터 응답   
5. ViewModel은 받은 데이터를 가공(Presentation Logic)하여 저장.   
6.  View는 ViewModel와 데이터 바인딩되어 자동으로 업데이트   
     
- 장점   
하나의 프로젝트를 최대한 작은 기능 단위로 나눔 => 관리가 용이하고 테스트가 쉽다   
Model과 View사이에 의존성이 없고, View와 ViewModel 관계도 1:n이기 때문에 의존성이 없다    
=> 유닛 테스트가 더욱 쉬워지고, Model변경 시점에 관찰 변수 설정만 확인하면 된다  
Databinding 라이브러리 사용 => 의존성을 낮추고, 중복 코드 모듈화 가능   
- 단점   
View 변수, 표현식에 전부 바인딩이 될 수 있음 => 시간이 지남에 따라 Presentation Logic 증가   
ViewModel은 설계가 상대적으로 어려움   
   
   
   

## 참고
[디자인 패턴 MVC, MVP, MVVM](https://beomy.tistory.com/43)

[안드로이드 아키텍처 패턴](https://velog.io/@jojo_devstory/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%ED%8C%A8%ED%84%B4-MVVM%EC%9D%B4-%EB%AD%98%EA%B9%8C)

[디자인 패턴 04l](https://www.thekpop.net/2020/03/design-pattern-04-mvc-mvp-mvvm-3.html)
