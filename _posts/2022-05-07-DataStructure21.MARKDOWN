---
title: "[자료구조] 4.2 단순 연결 리스트의 ADT와 구현 (1)" 
excerpt: "연결 리스트(Linked List) 2 - 단순 연결 리스트의 ADT와 구현 (1)"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
# 단순 연결 리스트의 ADT와 구현 (1)

<aside>
💡 "연결 리스트(Linked List) 2  -  단순 연결 리스트의 ADT와 구현 (1)
</aside>
<br>

## 연결리스트의 ADT - 기능정렬 추가된 연결리스트
- 이전과 동일한 함수
![자료구조의 분류](/assets/images/posts/data21-1.png)
- 새로운 함수
![자료구조의 분류](/assets/images/posts/data21-2.png)
-   SetSortRule 
    -   정렬의 기준을 설정하기 위한 함수
 
### 새 노드의 추가 위치
#### 머리에 추가하는 경우
- 장점 : 포인터 변수 tail이 불필요
- 단점 : 저장 순서를 유지하지 못함
  
#### 꼬리에 추가하는 경우
- 장점 : 저장 순서가 유지됨
- 단점 : 포인터 변수 tail이 필요
  
#### 중간에 추가하는 경우
- 단점 : head 와 tail 모두 필요

### SetSortRule 함수
| void SetSortRule ( List * plist, int (*comp)(LData d1, LData d2) );
- 반환형이 int
    **int** (*comp)(LData d1, LData d2) 
- LData형 인자를 2개 전달받음
    int (*comp)(**LData d1, LData d2**) 
- 함수 주소값 전달
    **int** (***comp**)(LData d1, LData d2)    
```
int WhoIsPrecede(LData d1, LData d2) {
 if(d1 < d2) {
 // d1이 앞순서인 경우
    return 0; 
 } else {
 // d2이 앞순서거나 같은 경우   
    return 1;
 } 
}
```
=> 정렬의 기준은 오름차순/내림차순과 같이 결정된 약속(정의)를 근거로 함수가 정의되어야함

## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127)  <br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
