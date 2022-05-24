---
title: "[자료구조] 4.3 연결 리스트의 정렬 삽입의 구현" 
excerpt: "연결 리스트(Linked List) 2 - 연결 리스트의 정렬 삽입의 구현"
 
categories:  
 - 자료구조
tags: 
 - 자료구조

toc: true
toc_sticky: true
toc_label: 목차
---
# 연결 리스트의 정렬 삽입의 구현

<aside>
💡 "연결 리스트(Linked List) 2  -  연결 리스트의 정렬 삽입의 구현
</aside>
<br>

## 정렬 리스트
### 정렬 기준 설정
- 단순 연결 리스트의 정렬 관련 요소
  - **`SetSortRule`**  
    - 정렬의 기준이 되는 함수를 등록하는 함수
    
    ```
    void SetSortRule(List * plist, int (*comp)(LData d1, LData d2)) {
        plist->comp = comp;
    }
    ```

  - **`LinkedList의  comp`**
    - `SetSortRule`  에서 전달된 정렬 기준을 comp 에서 저장
  
    ```
    typedef struct _linkedList {
    Node * head;
    Node * cur;
    Node * before;
    int numOfData;
    int (*comp)(LData d1, LData d2);
    } LinkedList;
    ```
  - **`SInsert`**
    - `comp` 에 저장된 정렬 기준을 근거로 데이터를 정렬하여 저장하는 함수
    ```
    void LInsert(List * plist, LData data) {
        if(plist->comp == NULL) {
            FInsert(plist, data);
        } else {
            SInsert(plist, data);
        }
    }
    ``` 
 

  
  =>   `SetSortRule` 함수의 호출 > 정렬의 기준이 `comp`에 등록 > `SInsert` 로 `comp` 를 근거로 데이터 정렬

### SInsert 함수
  ![SInsert](/assets/images/posts/data24-1.png)

  ```
  void SInsert(List * plist, LData data) {
      Node * newNode = (Node*)malloc(sizeof(Node));
      Node * pred = plist->head;
      newNode->data = data;

      while(pred->next != NULL && plist->comp(data, pred->next->data) != 0) {
      // 새 노드가 삽입될 위치를 찾는 while
      
      // 조건 1) pred->next != NULL
      // pred가 가리키는 노드가 마지막 노드인지 확인

      // 조건2) plist->comp(data, pred->next->data) != 0
      // 새로 삽입되는 데이터와 pred 다음 노드 데이터 사이의 비교를 위한 함수호출
      // comp 반환값 = 0 : 첫 번째 인자의 data가 앞 순서로 정렬되어야 하는 경우(head로 방향으로)
      // comp 반환값 = 1 : 두 번째 인자의 pred->next->data가 앞 순서로 정렬되어야 하는 경우(head로 방향으로)
      
          pred = pred->next;
          // 다음 노드로 이동
      }
      newNode->next = pred->next;
      pred->next = newNode;
      (plist->numOfData)++;
  }
  ``` 


### 정렬 함수의 정의
- 비교할 두개의 인자를 전달받아야 한다
- 첫 번째 인자가 우선순위가 높으면 0, 두 번째 인자가 우선순위가 높으면 1을 반환한다
- 정렬 관련된 함수는 DLinkedListSortMain.c 에 포함시켜야 한다
```
int WhoIsPrecede(int d1, int d2) {
// 오른차순 정렬

  if(d1 < d2) {
     return 0; 
    // d1이 정렬 순서상 앞선다
  } else {
    return 1; 
    // d2가 정렬 순서상 앞서거나 같다
  }
}
```  




## 참고

[윤성우의 열혈 자료구조](https://book.naver.com/bookdb/book_detail.nhn?bid=6809127) 
[윤성우의 열혈 자료구조 강의](http://www.orentec.co.kr/teachlist/DA_ST_1/teach_sub1.php)
