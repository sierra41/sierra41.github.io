---
layout: single
title: "Dependabot alerts 해결"
read_time: true

categories: 
 - Jekyll
tags: 
 - Ruby
 - Jekyll
 - Dependabot alerts
last_modified_at: '2021-03-26 17:30:00 +0800'
toc: true
toc_sticky: true
toc_label: 목차

---
## Dependabot alerts   
![image](https://user-images.githubusercontent.com/66898243/112602505-1e80f980-8e57-11eb-8ed5-a2e33428e800.png)     
git blog repository에 떠 있던 Dependabot alerts 해결하기    


### alerts 내용 
 > ![image](https://user-images.githubusercontent.com/66898243/112602481-17f28200-8e57-11eb-86d7-33ccaf7c9a13.png)    
 > ![image](https://user-images.githubusercontent.com/66898243/112603132-e928db80-8e57-11eb-8959-f4b37437f1a7.png)      
 gitblog 생성시 사용했던 Ruby의 gem을 업데이트 해주라는 알림이 떴다
 
 
 
### alerts 해결


 1. bundle update로 전체적인 gem 버전 업데이트
 > ![image](https://user-images.githubusercontent.com/66898243/112721035-1c956400-8f45-11eb-8e2c-8c9668c3466d.png)   
 > ![image](https://user-images.githubusercontent.com/66898243/112604443-7c164580-8e59-11eb-8131-18f082be1f48.png)     
 kramdown은 정상적으로 update 됐는데 (원래 뒤에 was v.이전버전 안내가 나오는데 그때 캡쳐를 못했다)    
 > ![image](https://user-images.githubusercontent.com/66898243/112721019-ff609580-8f44-11eb-9be4-36a7baed599b.png)       
 rack은 업데이트가 되지 않는다    
 
 
 
 2. rack만 따로 install 한 다음 이전버전 rack을 uninstall
 > ![image](https://user-images.githubusercontent.com/66898243/112605317-84bb4b80-8e5a-11eb-92cb-2c5ef19959a2.png)    
 만약 그래도 alerts가 계속 떠있다면
 
 
 
 3. Gemfile.lock 수정    
 > Gemfile.lock 파일(설치된 젬들의 버전을 기억해 두는 파일)에서 rack 버전을 수정
 
 
 
 
 
## 참고 목록
- https://kbs4674.tistory.com/20
- https://talk.jekyllrb.com/t/dependabot-vulnerability-in-gem-rack-2-1-4/5387
- https://stackoverflow.com/questions/31775991/you-have-already-activated-rack-1-6-0-but-your-gemfile-requires-rack-1-6-4
