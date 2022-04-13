---
title: "[자료구조] 3.2  배열을 이용한 리스트의 구현 (4) " 
excerpt: "연결 리스트(Linked List) 1 - 배열을 이용한 리스트의 구현 (4) "
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
#  배열을 이용한 리스트의 구현 (4)

<aside>
💡 "연결 리스트(Linked List) 1  -  배열을 이용한 리스트의 구현 (4)
</aside>
<br>

## 배열 기반 리스트 
### 배열 기반 리스트 초기화
- 실제 초기화 대상은 **구조체 변수의 멤버**
```
typedef struct __ArrayList {
	LData arr[LIST_LEN]; // 데이터 저장위치
	int numOfData; // 저장된 데이터 수
	int curPosition; // 마지막 참조 위치 정보
} ArrayList;

void ListInit(List * plist) {
// 구조체 변수가 선언되고 그 주솟값이 인자로 전달
	(plist->numOfData) = 0; 
	// plist 주소가 가리키는 구조체의 변수 numOfData 멤버를 초기화 
	(plist->curPosition) = -1; 
	// LFirst 함수와 LNext 함수에서 사용
	// -1은 아무런 위치도 참조하지 않았음을 의미
}
```

### 배열 기반 리스트 삽입
```
typedef struct __ArrayList {
	LData arr[LIST_LEN]; /
	int numOfData; // 초기화(0)
	int curPosition; // 초기화(-1)
} ArrayList;

void LInsert(List * plist, LData data) {
	if(plist->numOfData > LIST_LEN) {
		// 더 이상 저장할 공간이 없다면
		puts("저장이 불가능합니다.");
		return;
	}

	plist->arr[plist->numOfData] = data;  
	// 데이터 저장
	(plist->numOfData)++; 
	// 저장된 데이터의 수 증가(다음 인덱스)
}
```

### 배열 기반 리스트 조회

```
int LFirst(List * plist, LData * pdata) {
// 초기화 
// 첫 번째 데이터 참조	
	
	if(plist->numOfData == 0) {
		// 저장된 데이터가 하나도 없다면 : false
			return FALSE;
	}


	(plist->curPosition) = 0; 
	// 참조 위치 초기화
	// 첫 번째 데이터 참조

	*pdata = plist->arr[0]; 
	// pdata가 가리키는 공간에 데이터 저장
	return TRUE;
}

int LNext(List * plist, LData * pdata) {
// 그 다음 데이터 참조
	if(plist->curPosition >= (plist->numOfData)-1) {
	// 더 이상 참조할 데이터가 없다면 : false	
		return FALSE;
	}

	(plist->curPosition)++; 
	// 현재 위치 1 증가
	*pdata = plist->arr[plist->curPosition];  
	// 값의 반환은 매개변수를 통해
	// 함수의 반환은 성공여부를 반환하기 위해
	return TRUE;
}
```

### 배열 기반 리스트 삭제
- 배열의 데이터 삭제 : 특정 데이터를 삭제한 다음 한칸씩 자리를 옮겨 빈칸을 채워야함
- ![배열삭제](/assets/images/posts/data15.png)
```
LData LRemove(List * plist) {
	int rpos = plist->curPosition;  
	// 삭제할 데이터 인덱스 값 참조
	int num = plist->numOfData;
	int i;
	LData rdata = plist->arr[rpos]; 
	// 삭제할 데이터 임시 저장

	for(i=rpos; i<num-1; i++) {
	// 삭제를 위한 데이터의 이동을 진행
		plist->arr[i] = plist->arr[i+1];
	}

	(plist->numOfData)--; //데이터의 수 감소
	(plist->curPosition)--; // 참조위치를 하나 앞으로
	return rdata; 
	// 삭제 데이터 반환 : 삭제되는 데이터는 반환과정으로 돌려줘야함

}
```

## 참고

[윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127) 
[윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
