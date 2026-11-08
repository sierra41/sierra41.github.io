---
title: "[자료구조] 3.2  배열을 이용한 리스트의 구현 (3) " 
excerpt: "연결 리스트(Linked List) 1 - 배열을 이용한 리스트의 구현 (3) "
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
published: false
---
#  배열을 이용한 리스트의 구현 (3)

<aside>
💡 "연결 리스트(Linked List) 1  -  배열을 이용한 리스트의 구현 (3)
</aside>
<br>

## 배열 기반 리스트 
### 배열 기반 리스트의 헤더파일
- ArrayList.h 
  - 리스트 자료구조의 헤더파일

	```
	#ifndef __ARRAY_LIST_H__ 
	#define __ARRAY_LIST_H__
	// ifndef : 파일이 나뉠 때 같은 헤더파일을 각각 파일에서 
	//          중복으로 선언되는 것을 방지하는 매크로

	#define TRUE	1
	#define FALSE	0
	```

	```
	// ArrayList --------------------- 정의

	#define LIST_LEN 100

	typedef int LData; 
	// typedef : 사용자 정의 자료형. 
	// 긴 자료형을 편하게 별칭 가능하고 데이터의 자료형이 변경될 때 일괄로 처리 가능 
	// 이식성을 높여 줌
	// typedef 기존의형명 새로운 형명 형태로 사용

	typedef struct __ArrayList {
	// 배열기반 리스트를 정의한 구조체

		LData arr[LIST_LEN]; // 리스트의 저장소인 배열
		int numOfData;       // 저장된 데이터의 수
		int curPosition;     // 데이터를 참조하는 위치를 기록

	} 

	ArrayList; // 배열 기반 리스트를 의미하는 구조체
	```

	```
	// ArrayList --------------------- 연산

	typedef ArrayList List; 
	// 리스트의 변경의 편의성을 위해 typedef 선언

	void ListInit(List * plist); // 초기화
	void LInsert(List * plist, LData data); // 데이터 저장

	int LFirst(List * plist, LData * pdata); // 첫번째 참조
	int LNext(List * plist, LData * pdata); // 이후 참조

	LData LRemove(List * plist); // 참조 데이터 삭제
	int LCount(List * plist); // 저장 데이터 수

	#endif
	```


## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127)  <br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
