---
layout: single
title: Algorithm. Radix Sort
categories: algorithm
---

## Radix Sort

 비교 정렬 알고리즘에는 O(n^2)이 걸리는 선택, 삽입, 버블 정렬이 있고, O(nlgn)이 걸리는 합병, 힙, 퀵 정렬 등이 있습니다. 앞에서 말한 정렬 알고리즘들은 n^2, nlgn보다 더 좋아질 수 없습니다. Counting sort는 O(n + k)가 걸립니다. 하지만 **만약 k가 n^2이 된다면**, Counting sort는 O(n^2)으로 사용하는 이유를 잃게됩니다. 이 때 가장 낮은 자리수(lsd, least significant digit)부터 가장 높은 자리수까지 자리수에 따라 Stable하게 정렬하는 방법인 **기수 정렬**이 답입니다.

### Pseudo Code

RadixSort(A,d)
  for i=1 to d
    StableSort(A) on digit i

### Implementation Code(JS)

```javascript
const getMax = function(array){
  let max = array[0];
  for(let i = 1; i < array.length; i++){
    if(array[i] > max) max = array[i];
  }
  return max;
}

const countingSort = function(A, B, d){
  // k=10
  let C = new Array(10);
  for(let i = 0; i < 10; i++){
    C[i] = 0;
  }
  for(let j = 0; j < A.length; j++){
    C[Math.floor(A[j] / d) % 10] += 1;
  }
  for(i = 1; i < 10; i++){
    C[i] += C[i-1];
  }
  for(j = A.length - 1; j >= 0; j--){
    B[C[Math.floor(A[j] / d) % 10] - 1] = A[j];
    C[Math.floor(A[j] / d) % 10] -= 1;
  }
    for(i=0; i<A.length;i++){
        A[i] = B[i];
    }
}

const radixSort = function(A){
  let max = getMax(A);
  let B = new Array(A.length);

  for(let d = 1; Math.floor(max / d) > 0; d *= 10){
    countingSort(A, B, d);
  }
}

let A = [170, 45, 75, 90, 802, 24, 2, 66];
radixSort(A);
//output: (8) [2, 24, 45, 66, 75, 90, 170, 802]
```

### 성능 비교(O notation)

O(d\*n + d\*k)

###### 참고 사이트
[Youtube - radix sort](https://www.youtube.com/watch?v=7heKwjqkY60&list=PLDV-cCQnUlIZXLSUeF2Fav3_7X7ku-F63&index=10)  
[GeekforGeeks - radix sort](https://www.geeksforgeeks.org/radix-sort/)  