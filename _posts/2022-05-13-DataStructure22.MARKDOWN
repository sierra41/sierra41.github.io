---
title: "[자료구조] 4.2 단순 연결 리스트의 ADT와 구현 (2)" 
excerpt: "연결 리스트(Linked List) 2 - 단순 연결 리스트의 ADT와 구현 (2)"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
# 단순 연결 리스트의 ADT와 구현 (2)

<aside>
💡 "연결 리스트(Linked List) 2  -  단순 연결 리스트의 ADT와 구현 (2)
</aside>
<br>

## 연결리스트의 ADT 
### 더미 노드 기반 연결리스트

  1. 머리에 새 노드를 추가할 때 더미 노드 없는 경우
     - 첫번째 노드와 두번째 이후 노드의 추가/삭제 과정이 달라짐
     - 방식이 다르면 복잡해짐
  
  2. 머리에 새 노드를 추가할 때 더미 노드 있는 경우
     - 노드의 순서와 관계없이 노드 추가/삭제 과정이 일정함
     - data를 저장하지 않는 dummy node 활용
- DLinkedRead.c 에서 dummy node 추가 가능
  
### 정렬 기능이 추가된 연결리스트 
#### 구조체
- 구조체의 표현을 통하여 연결리스트 관리
  - 구조체로 연결리스트에 피요한 변수를 묶는 것은 좋지 않음.
- 구조체 표현
  
   ![구조체](/assets/images/posts/data22-2.png)


#### 헤더파일
- 앞부분
  
   ![헤더](/assets/images/posts/data22-3.png)
- 뒷부분
  
   ![헤더](/assets/images/posts/data22-4.png)


## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127)  <br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
