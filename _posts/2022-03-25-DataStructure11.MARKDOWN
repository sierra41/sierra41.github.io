---
title: "[자료구조] 3.1 추상 자료형: Abstract Data Type " 
excerpt: "연결 리스트(Linked List) 1 - 추상 자료형: Abstract Data Type"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
# 추상 자료형: Abstract Data Type

<aside>
💡 "연결 리스트(Linked List) 1  - 추상 자료형: Abstract Data Type
</aside>
<br>

## 추상 자료형(ADT)

### 추상 자료형의 개념
- 추상 = 기능 
- 기능의 명세
- 전체적인 완성과정이 아닌 개별적이고 순수한 기능의 나열
- 예시
	- 지갑의 추상자료형 
		- 카드의 삽입
		- 카드의 추출(카드를 빼냄)
		- 동전의 삽입
		- 동전의 추출(동전을 빼냄)
		- 지폐의 삽입
		- 지폐의 추출(지폐를 빼냄)
<br>
- 컴퓨터공학적으로 자료형의 정의는
	1. Wallet이라는 자료형이 있음
	2. Wallet이라는 자료형에는 함수가 정의 되어있음
	3. Wallet이라는 자료형이 연산이 결정됨
	- 1, 2, 3 이 모두 이루어져야 결과적으로 Wallet이라는 자료형이 정의되는 것

```
int TakeOutMoney(Wallet * pw, int coinNum, int billNum); 
void PutMoney(Wallet * pw, int coinNum, int billNum); 
```

### ADT 정의와 자료구조의 학습
1. 리스트 자료구조의 ADT를 정의한다.
2. ADT를 근거로 리스트 자료구조를 활용하는 main 함수를 정의한다.
3. ADT를 근거로 리스트를 구현한다.

### 올바른 ADT 정의
- 자료구조의 내부 구현을 몰라도 자료구조의 활용이 가능하도록 정의한다
- main 함수로부부터 자료구조를 구성할 함수를 이해 가능하도록 정의한다


## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127) <br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
