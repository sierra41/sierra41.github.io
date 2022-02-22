---
title: "[자료구조] 1.2 알고리즘의 성능분석 방법 (2)" 
excerpt: "자료구조와 알고리즘의 이해 - 알고리즘의 성능분석 방법 (2)"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
# 알고리즘의 성능분석 방법 (2)

<aside>
💡 자료구조와 알고리즘의 이해 - 알고리즘의 성능분석 방법 (2)
</aside>
<br>

## 시간복잡도와 순차 탐색 알고리즘
```
int LSearch(int ar[], int len, int target) {
	int i;
	for(i = 0; i < len; i++) {
		if(ar[i] == target) {
			return i;
		}
	}	
}
```


### 최악의 경우 (worst case)
> 최악의 경우 시간복잡도
> T(n) =n
> 데이터 수 n => 연산 수 n

- 탐색 대상을 배열의 끝에서 찾는 경우
- 탐색 대상이 저장되지 않은 경우
- 최악의 경우가 성능 평가 알고리즘의 기준이 됨

### 최상의 경우(best case)
- 탐색 대상을 배열의 가장 앞에서 찾는 경우
- 성능 평가 알고리즘과 관련이 적다

### 평균의(일반적) 경우
> 평균적 경우 시간복잡도
> 
> 탐색 대상이 저장되지 않은 경우 50% : 연산 수 n  
> 
> 탐색 대상이 존재하는 경우 50% : 연산 수 n/2
> 
T(n) = n \times \frac{1}{2}  + \frac{n}{2} \times  \frac{1}{2} = \frac{3}{4}n

![평균적경우](/assets/images/posts/data03.png)

- 최악과 최상이 아닌 나머지 경우
- 상황에 따라 달라지며 평균적인 경우의 증명이 어렵다
- 성능 평가 알고리즘에 도움이 되지만 객관적 평가가 어렵다


## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127) <br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
