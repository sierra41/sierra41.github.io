---
title: "[자료구조] 1.2 알고리즘의 성능분석 방법 (6)" 
excerpt: "자료구조와 알고리즘의 이해 - 알고리즘의 성능분석 방법 (6)"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
# 알고리즘의 성능분석 방법 (6)

<aside>
💡 자료구조와 알고리즘의 이해 -  알고리즘의 성능분석 방법 (6)
</aside>
<br>

## 순차 탐색 알고리즘과 이진 탐색 알고리즘 비교

### 순차 탐색 알고리즘
- 최악의 경우 시간 복잡도  : T(n) = n
- 순차 탐색 알고리즘의 빅-오표기법 : O(n)

### 이진 탐색 알고리즘
- 최악의 경우 시간 복잡도  : T(n) = log_{2}n + 1
- 이진 탐색 알고리즘의 빅-오표기법 : O(log n)

### n의 값에 따른 순차 탐색과 이진 탐색의 연산 횟수
![표](/assets/images/posts/data07.png)

### 비교
- 빅오표기법으로 시간복잡도를 봤을 때 이진 탐색 알고리즘 O(log n) 가 순차 탐색 알고리즘 O(n) 보다 효율적이다.
- 이진 탐색 알고리즘의 성능이 우수하지만 이진 탐색 알고리즘의 경우 정렬된 데이터에서만 사용이 가능하다



## 참고

[윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127) <br>
[윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
