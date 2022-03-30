---
title: "[자료구조] 3.2 배열을 이용한 리스트의 구현 (1)" 
excerpt: "3. 연결 리스트(Linked List) 1 - 배열을 이용한 리스트의 구현 (1)"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
# 배열을 이용한 리스트의 구현 (1)

<aside>
💡 "연결 리스트(Linked List) 1  - 배열을 이용한 리스트의 구현 (1)
</aside>
<br>

## 리스트
### 종류 : 구현방법을 기준으로
- 순차 리스트
  - 배열 기반 구현 
- 연결 리스트
  - 메모리의 동적 할당 기반 구현
  
### 특징 
- 리스트의 자료구조는 데이터를 나란히(일열로) 저장한다
- 데이터의 중복 저장이 가능하다
=> 위와 같은 특징이 리스트의 ADT 정의에 있어 중요

## 리스트 자료구조 ADT
- 리스트의 구현법, 동작 원리와는 관계없이 리스트 자료구조의 특징과 목적, 활용에 대한 것
- void ListInit(List *plist);
  - 리스트 초기화 역할 
   : 초기화 할 리스트의 주소 값을 인자로 전달
  - 리스트의 생성 후 가장 먼저 호출되는 함수 
- void LInsert(List * plist, LData data);
  - 데이터 저장 역할
   : 매개변수 data에 전달된 값을 리스트에 저장 
- 참고) LData는 리스트의 데이터 자료형에 제한이 없도록 typedef로 선언한 자료형명 
- int LFirst(List * plist, LData * pdata);
  - 데이터의 탐색 및 탐색 초기화
  1. 첫번 째 데이터를 pdata 메모리에 저장
  2. 데이터 참조를 위한 초기화
  3. 참조 성공 : TRUE(1), 실패  : FALSE(0) 반환
- int LNext(List * plist, LData * pdata);
  -  다음 데이터의 호출 -    참초(반환)의 목적으로
  -  참조된 데이터의 다음 데이터를 pdata 메모리에 저장  
  -  반복 호출 가능 - 순차적 참조
  -  참조를 새롭게 시작하려면 LFirst 함수를 먼저 호출한 다음 가능
  -   참조 성공 : TRUE(1), 실패  : FALSE(0) 반환
-  LData LRemove(List * plist);
   - 바로 이전에 참초(반환)되었던 데이터 삭제
   - LFirst 또는 LNext 함수의 마지막 반환 데이터 삭제
   - 삭제된 데이터는 반환
   - 마지막 반환 데이터는 삭제됨 - 반복 호출 불가
- int LCount(List * plist);
  - 현재 저장된 데이터 수 반환



## 참고

[윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127) 
[윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
