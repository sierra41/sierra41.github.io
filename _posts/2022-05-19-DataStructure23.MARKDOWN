---
title: "[자료구조] 4.2 단순 연결 리스트의 ADT와 구현 (3)" 
excerpt: "연결 리스트(Linked List) 2 - 단순 연결 리스트의 ADT와 구현 (3)"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
published: false
---
# 단순 연결 리스트의 ADT와 구현 (3)

<aside>
💡 "연결 리스트(Linked List) 2  -  단순 연결 리스트의 ADT와 구현 (3)
</aside>
<br>

## 더미 노드 기반 연결리스트 구현
### 초기화
- 구조체의 정의 : 초기화 함수를 위해 살펴봐야함
  
  ![초기화](/assets/images/posts/data23-1.png)
- 초기화 함수의 정의
  
  ![초기화](/assets/images/posts/data23-2.png)

### 삽입
- 데이터를 추가할 때 첫번째 노드와 그 이후 노드가 동일한 과정을 가짐
  => 더미 노드 기반 연결 리스트의 장점
- 첫번째 노드 삽입
  
  ![삽입](/assets/images/posts/data23-3.png)
- 두번째 노드 삽입

	![삽입](/assets/images/posts/data23-4.png)

### 참조
- 첫번 째 노드 : LFirst 통하여 참조
   
   ![참조](/assets/images/posts/data23-5.png)
- 두번째 이후 노드 : LNext 통하여 참조
   
   ![참조](/assets/images/posts/data23-6.png)


### 삭제
- cur : 삭제 후 재조정 필요
- before : LFirst 함수나 LNext의 호출 시 재설
정 됨 
  => 재조정 과정 불필요

   ![삭제](/assets/images/posts/data23-7.png)
- LRemove : 백업용으로 삭제 후 값 반환을 위해 rdata 변수 필요
  

## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127)  <br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
