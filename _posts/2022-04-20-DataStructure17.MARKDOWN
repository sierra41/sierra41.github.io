---
title: "[자료구조] 3.2  배열을 이용한 리스트의 구현 (6) " 
excerpt: "연결 리스트(Linked List) 1 - 배열을 이용한 리스트의 구현 (6) "
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
#  배열을 이용한 리스트의 구현 (6)

<aside>
💡 "연결 리스트(Linked List) 1  -  배열을 이용한 리스트의 구현 (6)
</aside>
<br>

## 리스트
### 구조체 변수 저장 - 예제 (PointListMain.c)로 확인하기
#### 초기화 및 저장
```
int main(void) {
 List list;
 Point compPos;
 Point * ppos;
 ListInit(&list);


// 데이터 4개 저장 --------------------------
 ppos = (Point*)malloc(sizeof(Point));
 // Point 구조체의 ppos 변수에 malloc에 주소값을 저장
 SetPointPos(ppos, 2, 1);
 LInsert(&list, ppos);
 // ppos(malloc 주소값)를 리스트 저장
 // => 동적 할당됨

 ppos = (Point*)malloc(sizeof(Point));
 SetPointPos(ppos, 2, 2);
 LInsert(&list, ppos);

}
```

#### 참조 및 조회
```
int main(void) {

// 데이터 출력 --------------------------
 printf("현재 데이터의 수: %d \n", LCount(&list));

 if(LFirst(&list, &ppos)) {
	ShowPointPos(ppos);

	while(LNext(&list, &ppos)) {
		ShowPointPos(ppos);
	}

 }
 printf("\n");

}
```

#### 삭제
```
int main(void) {
	
// xpos가 2인 데이터 삭제 --------------------
 compPos.xpos=2;
 compPos.ypos=0;

 if(LFirst(&list, &ppos)) {
	if(PointComp(ppos, &compPos)==1) {
	//동적 할당 구조체 멤버변수 == compPos.xpos
		ppos=LRemove(&list);
		// 구초제 변수 삭제
		free(ppos);
		// LRemove 함수가 반환한 주소값으로 동적할당 메모리 해제
	}

	while(LNext(&list, &ppos)) {
		if(PointComp(ppos, &compPos)==1) {
			ppos=LRemove(&list);
			free(ppos);
		}	
	}
 }

}
```


## 참고

[윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127) 
[윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
