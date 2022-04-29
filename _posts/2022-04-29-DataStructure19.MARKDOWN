---
title: "[자료구조] 4.1 연결 리스트의 개념적인 이해 (1)" 
excerpt: "연결 리스트(Linked List) 2 - 연결 리스트의 개념적인 이해 (1)"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
# 연결 리스트의 개념적인 이해 (1)

<aside>
💡 "연결 리스트(Linked List) 2  - 연결 리스트의 개념적인 이해 (1)
</aside>
<br>

## 연결 리스트
### 연결리스트 개념
![연결리스트](/assets/images/posts/data19-1.png)
-  방향성을 가지고 메모리를 동적 할당받아 연결시킴
-  배열과 같이 미리 사용할 길이가 정해진 리스트가 아닌 필요할 때 마다 메모리를 할당받아 사용
-  새로운 데이터의 입력으로 메모리가 추가 할당되어도 Head/Tail로 연결하여 사용
#### malloc 함수
- 함수 : void * malloc(size_t * Size);
  (데이터타입 *) malloc(sizeof(데이터타입) * 할당크기);
- 헤더 : stdlib.h
- 포인터 값만 가지고 어떤 형의 타입으로도 변환이 가능한(void *) 변수를 리턴. 개발자가 void부분에 필요한 자료형 캐스팅함
- 리턴값 : 성공 - 할당 메모리 첫번째 주소, 실패 - null
- 데이터의 크기에 따라 필요한 메모리를 동적으로 할당
- 할당된 메모리는 free 함수로 메모리 해제를 시켜줘야함
#### free 함수
- 함수 : void free(void * ptr);
  (데이터타입 *) malloc(sizeof(데이터타입) * 할당크기);
- 헤더 : stdlib.h
- 리턴 값 없음
- malloc 함수에서 메모리를 할당 > 힙 메모리에 공간 생성 > 사용 종료 후 메모리를 해제 필요(free의 역할)
- 메모리 누수 방지


```
typedef struct _node {
	int data; 
    // 데이터 공간
	struct _node * next; // 연결 도구. 
    // _node가 구조체 변수(데이터를 담고 연결)가 되고 next는 _node를 추적하는 구조체 포인터 변수
} Node;
```
![연결리스트2](/assets/images/posts/data19-2.png)


## 참고

[윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127) 
[윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
