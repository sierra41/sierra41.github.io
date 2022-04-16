---
title: "[자료구조] 3.2  배열을 이용한 리스트의 구현 (5) " 
excerpt: "연결 리스트(Linked List) 1 - 배열을 이용한 리스트의 구현 (5) "
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
#  배열을 이용한 리스트의 구현 (5)

<aside>
💡 "연결 리스트(Linked List) 1  -  배열을 이용한 리스트의 구현 (5)
</aside>
<br>

## 리스트
### 구조체 변수 저장
  - Point 구조체 변수 헤더파일 선언 
  	: 자료형 저장 대상 변경하기

	```
	typedef struct _point {
	int xpos;
	int ypos;
	} Point;

	void SetPointPos(Point *ppos, int xpos, int ypos) {
	// Point 변수의 xpos, ypos 값 설정

		ppos->xpos = xpos;
		ppos->ypos = ypos;
	}

	void ShowPointPos(Point *ppos) {
	// Point 변수의 xpos, ypos 정보 출력

		printf("[%d, %d]\n", ppos->xpos, ppos->ypos);
	}

	int PointComp(Point *pos1, Point *pos2) {
	// 두 Point 변수의 비교

		if(pos1->xpos == pos2->xpos && pos1->ypos == pos2->ypos) {
			return 0;
		} else if(pos1->xpos == pos2->xpos) {
			return 1;
		} else if(pos1->ypos == pos2->ypos) {
			return 2;
		} else {
			return -1;
		}
	}
	```
	
	- ArrayList.h 변경 사항
      - typedef int LData; (typedef 선언변경)
  		=> typedef Point * LData;
      - 실제로 저장하는 것은 Point 구조체 변수의 주소 값
    - #include "Point.h" 
 		 => ArrayList.h 헤더파일 추가 선언
 	 <BR>
	- 실행 파일 구성
      - Point.h, Point.c 	: 구조체 	Point를 위한 파일
      - ArrayList.h, ArrayList.c 	: 배열 기반 리스트
      - PointListMain.c 	: 구조체 	Point의 변수 저장


## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127)  <br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php) <br>
