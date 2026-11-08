---
title: "[자료구조] 2.1 함수의 재귀적 호출의 이해" 
excerpt: "재귀 - 함수의 재귀적 호출의 이해"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
published: false
---
# 함수의 재귀적 호출의 이해 

<aside>
💡 재귀 - 함수의 재귀적 호출의 이해 
</aside>
<br>

## 재귀의 기본 개념
- 재귀 함수는 탈출 조건이 필수적
- 탈출 조건이 명시되지 않은 함수는 무한 반복(loop) 됨

## 재귀의 디자인 사례 

> 0! = 1! = 1
>
> 2! = (1) × 2 = 1! x 2 = 2
>
> 3! = (1 × 2) x 3 = 2! x 3 = 6
>
> 4! = (1 × 2 × 3) × 4 = 3! x 4 = 24
> 
> 5! = (1 × 2 × 3 × 4) × 5 = 4! x 5 = 120
> 
> 6! = (1 × 2 × 3 × 4 × 5) x 6 = 5! x 6 = 720

![재귀](/assets/images/posts/data08.png)

## 재귀 구현

```
int Factorial(int n) {
    	if (n == 0) {
        		return 1;
	} else {
		return n * Factorial(n - 1);
	}
}
 
```

## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127) <br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
