---
title: "[자료구조] 1.2 알고리즘의 성능분석 방법 (1)"
excerpt: "자료구조와 알고리즘의 이해 - 알고리즘의 성능분석 방법(1)"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
# 알고리즘의 성능분석 방법 (1)

<aside>
💡 자료구조와 알고리즘의 이해 - 알고리즘의 성능분석 방법 (1)
</aside>
<br>

## 기본 배경지식 : 지수와 로그

![지수식로그식](/assets/images/posts/data02-1.png)
**x축** : 데이터의 수<br>
**y축** : 연산의 횟수

## 시간복잡도와 공간복잡도

- 알고리즘의 수행시간을 분석하는 방식<br>
- 시간복잡도(time complexity)는 알고리즘 수행 시간이 얼마나 걸리는지<br>
- 공간복잡도(space complexity)는  메모리 공간이 얼마나 사용되는지

### 중요성
- **시간복잡도 \> 공간복잡도** <br>
- 시간복잡도가 데이터 수에 대한 연산의 횟수를 판단하기 더 쉽다.

## 시간복잡도
### 평가 방법

- **중심이 되는 연산**을 기준으로 횟수를 세어서 평가<br>
- **함수 T(n)** : 데이터 수에 대한 연산의 횟수 

### 수행시간 비교

- 데이터 수가 적으면 수행 속도에 큰 의미가 없다.<br>
- 데이터 수의 변화에 따른 수행 속도의 변화 정도로 비교한다<br>
  
![지수식로그식](/assets/images/posts/data02-2.png)

## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127)<br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
