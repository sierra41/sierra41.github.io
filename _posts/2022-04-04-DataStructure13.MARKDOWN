---
title: "[자료구조] 3.2 배열을 이용한 리스트의 구현 (2) " 
excerpt: "연결 리스트(Linked List) 1 - 배열을 이용한 리스트의 구현 (2)"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
published: false
---
# 배열을 이용한 리스트의 구현 (2)

<aside>
💡 "연결 리스트(Linked List) 1  - 배열을 이용한 리스트의 구현 (2)
</aside>
<br>

## 리스트 ADT - 예시를 통환 리스트 자료구조 확인
- ArrayList.h 리스트 자료구조의 헤더파일
- ArrayList.c 리스트 자료구조의 소스파일
- ListMain.c 리스트 관 main 함수가 담긴 소스파일
### 리스트 초기화 

```
int main(void) {
    List list; // 생성
    ListInit(&list); // 초기화
}
```

### 데이터 저장 

```
int main(void) {
    LInsert(&list, 11); 
    LInsert(&list, 22); 
    LInsert(&list, 33); 
    // 데이터 입력
}
```

- 데이터가 일 열로 저장
- 데이터의 입력 순서는 관계없음 
- 
### 데이터 참조 

```
int main(void) {
    if(LFirst(&list, &data))  {
        // 첫 번째 데이터 변수 - data에 저장
        printf("%d ", data);
        while(LNext(&list, &data)) { 
            // 두 번째 이후 데이터 변수 - data에 저장
            printf("%d ", data);
        }
    }
}
```

  1. LFirst 함수로 첫 번째 데이터 값 저장
     - LFirst 함수는 첫번 째 참조에서만 사용
  2. 저장된 데이터 참조(출력)
  3. LNext 함수로 다음 참조
   
### 데이터 삭제

```
int main(void) {
    if(LFirst(&list, &data)) {
        if(data == 22) {
            LRemove(&list); 
            // LFirst 함수로 참조한 데이터 삭제
        }    
        while(LNext(&list, &data)) {
            if(data == 22) {
                LRemove(&list); 
                // LNext 함수로 참조한 데이터 삭제
            }
        }
    }
}
```

- LRemove 함수는 연이은 호출이 불가
- LFirst함수와 LNext 함수를 통해 참조하여 삭제 가능

## 참고

- [윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127)  <br>
- [윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
