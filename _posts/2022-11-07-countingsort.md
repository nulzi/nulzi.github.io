---
layout: single
title: Algorithm. Counting Sort
categories: algorithm
---

## Counting Sort

계수 정렬은 특정한 범위에서 키를 바탕으로 하는 정렬입니다. 키 값으로 구분되는 원소의 개수를 세는(counting) 방법으로 비교 없이 정렬할 수 있습니다. 

### 과정

- A: 정렬하고자 하는 배열
- B: 정렬된 요소 배열
- C: 카운팅 및 누적 인덱스 배열
- k: 배열의 원소의 범위 ex) 0~5

1. k 크기의 배열 C를 만든다.
2. A를 돌며 C에 카운팅을 한다.
3. 카운팅이 끝나면 값들을 누적해 C에 저장한다.
4. A를 마지막 요소부터 첫 요소까지 돌며 C에 누적된 값을 인덱스로 B에 정렬한다.

### Pseudo Code

CountingSort(A,B,k)
  for i=0 to k
    C[i] = 0
  for j = 1 to length[A]
    C[A[j]] = C[A[j]] + 1
  for i = 1 to k
    C[i] = C[i] + C[i-1]
  for j = length[A] downto 1
    B[C[A[j]]] = A[j], C[A[j]] = C[A[j]] - 1

### Implementation Code(JS)

```javascript
const CountingSort = function(A,B,k){
  let C = [];
  for(let i=0; i<=k;i++){
    C[i] = 0;
  }
  for(let j=0; j<A.length;j++){
    C[A[j]] += 1;
  }
  for(let i=1; i<=k; i++){
    C[i] += C[i-1];
  }
  for(let j=A.length-1; j>=0;j--){
    B[C[A[j]]-1] = A[j];
    C[A[j]] -= 1;
  }
}

let A = [3,0,5,1,1];
let B = [0,0,0,0,0];
CountingSort(A,B,5);

// sort (5) [3, 0, 5, 1, 1]
// sorted (5) [0, 1, 1, 3, 5]
```

### 성능 비교(O notation)

O(n + k)

###### 참고 사이트
[Youtube - counting sort](https://www.youtube.com/watch?v=Urmb0FpW6Hk&list=PLDV-cCQnUlIZXLSUeF2Fav3_7X7ku-F63&index=9)  
[GeeksforGeeks - counting sort](https://www.geeksforgeeks.org/counting-sort/)  