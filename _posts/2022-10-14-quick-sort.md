---
layout: single
title: Algorithm. Quick Sort
categories: algorithm
---

## Quick Sort

퀵 정렬은 divide-conquer 방식의 정렬 방법입니다.  
divide-conquer 방식을 간단하게 이야기하면 배열을 어떠한 기준으로 나누고(divide), 나눈 것들을 각각 정복(정렬)하고(conquer), 그리고 정복된 것들을 다시 합치는 것입니다.(combine)  
하지만 퀵 정렬은 combine의 과정은 이미 정렬이 됐기 때문에 필요없습니다.

퀵 정렬의 과정입니다.
배열에서 하나의 요소를 선택합니다. 선택된 요소를 피봇(pivot)이라고 하고 피봇의 기준은 다양합니다.  
배열을 돌면서 피봇보다 작은 수는 피봇의 왼쪽에 큰 수는 피봇의 오른쪽에 위치하도록 합니다. 이 과정을 파티션(partition)이라고 하고 다양한 방법으로 가능합니다.  
그 결과 피봇은 정렬된 위치를 가지게 됩니다.  
이제 피봇 기준으로 나눠졌던 왼쪽과 오른쪽에 각각 피봇을 정하고 파티션을 진행합니다.  
위의 과정을 정렬될 때까지 반복하는 것이 퀵 정렬입니다.

보통 시간 복잡도를 구하게 되면 average case가 worst case와 유사하게 나오기 때문에 worst case를 사용합니다. 하지만 퀵 정렬은 특이하게도 worst case보다 average case의 경우가 더 많이 나오기 때문에 average case를 사용합니다.

### Pseudo code

```
Quicksort(A, left, right)
if left < right //배열 A의 원소가 2개 이상일 때
  then pivot <- Partition(A,left,right)
    Quicksort(A,left,pivot-1)
    Quicksort(A,pivot+1,right)
```

### Implementation Code(JS)

```javascript
let arr = [4, 6, 2, 5, 1, 3];

const swap = function (A, i, j) {
  const temp = A[i];
  A[i] = A[j];
  A[j] = temp;

  return A;
};

const partition = function (A, left, right) {
  const key = A[right];
  let i = left - 1;

  for (let j = left; j < right; j++) {
    if (A[j] <= key) {
      i = i + 1;
      swap(A, i, j);
    }
  }
  swap(A, i + 1, right);
  return i + 1;
};

const quickSort = function (A, left, right) {
  //배열 A의 원소가 1개 이하이면 배열 A 반환
  if (left >= right) return A;

  //배열 A의 원소가 2개 이상일 경우
  //pivot은 배열의 마지막 요소로 설정
  const pivot = partition(A, left, right);
  quickSort(A, left, pivot - 1);
  quickSort(A, pivot + 1, right);

  return A;
};

quickSort(arr, 0, arr.length - 1);

//출력 결과
//(6) [1, 2, 3, 4, 5, 6]
```

### 성능 비교(O notation)

**Best case**
피봇이 median(중앙값)일 경우  
$$ O(nlgn) $$
**Worst case**  
이미 정렬된 배열에서 피봇이 첫번째 요소나 마지막 요소일 경우  
$$ O(n^2) $$
**Average case**
$$ O(nlgn) $$

###### 참고 사이트

[코딩테스트, 기초, 퀵 정렬. quick sort. 퀵 소트](https://www.youtube.com/watch?v=H7CNZujkk0k)
