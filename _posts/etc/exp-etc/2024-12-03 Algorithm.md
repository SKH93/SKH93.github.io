---
layout: post
bigtitle: "[Algortihm] Sorting"
subtitle: "01. Sorting"
categories:
    - etc
    - exp-etc
# tags:
#   - python
#   - programming language
#   - basic
comments: true
# related_posts:
#    -
#    - 
published: true
---

이번 포스트에서는 알고리즘에 대해 다루겠습니다.
기본 언어는 Python3입니다.


## 알고리즘이란?

문제를 해결하기 위한 절차나 방법

## 시간 복잡도, 공간복잡도란?

알고리즘을 평가하는 척도
알고리즘을 효율성으로 평가 -> 시간, 메모리 자원 소모
시간의 경우 시간 복잡도로 평가
메모리의 경우 공간 복잡도로 평가

**시간 복잡도(Time Complexity)**
보통 Big-O 표기법으로 나타냄
예를 들어, 자료의 수가 n일 때 시간복잡도가 O(n)이면 n에 비례한 시간이라고 표현

아래로 갈수록 시간 복잡도 증가
- O(1) : 상수
- O(logn) : 로그
- O(n) : 선형
- O(nlogn) : 선형로그
- O(n^x) : 다차
- O(c^n) : 지수
- O(n!) : 팩토리얼

*공간 복잡도(Space Complextiy)*
- 주로 Big-O 표기법으로 나타냄
- 보통 시간 복잡도가 증가하면 같이 증가하는 경향이 보임
- 하드웨어(Hardware) 환경이 극도로 한정시 중요
- 알고리즘 자체보다는 알고리즘 구현에서 발생

## Sorting

- 정렬 알고리즘
    - 자료를 정렬하는 알고리즘

- 종류
    - 시간 복잡도 순
    - O(n^2)
        - 버블 정렬(Bubble Sort)
        - 선택 정렬(Selection Sort)
        - 삽입 정렬(Insertion Sort)
    - O(nlogn)
        - 병합 정렬/합병 정렬(Merge Sort)
        - 힙 정렬(Heap Sort)
        - 퀵 정렬(Quick Sort)
        - 트리 정렬(Tree Sort)
    
    그 밖에 하이브리드 정렬, 기수 정렬 ...등 종류가 다양함

1. 버블 정렬
1번째,2번째 비교, 2번째,3번째 비교 ... 하면서 정렬하는 알고리즘 
1부터 n까지의 수를 최대 n(n-1)/2번 정렬
모든 수를 돌기 때문에 최악의 성능, 이미 정렬된 자료에서만 최선의 성능

```python
#버블 정렬(Bubble Sort) 예시 코드
arr = [5, 2, 7, 6, 3, 1, 4]
for front_index in range(0, len(arr) - 1):
    for index in range(0, len(arr) - 1 - front_index):
        if arr[index] > arr[index + 1]:
            arr[index], arr[index + 1] = arr[index + 1], arr[index]
```

2. 선택 정렬
1번째, 2번째, 3번째 .. 부터 전체와 모두 비교하고 정렬을 반복하는 알고리즘
인간이 사용하는 방식과 유사
1부터 n까지의 수를 정렬된 상태에 상관없이 일관성있게 n(n-1)/2번 정렬
버블 정렬보다 2배 빠름

```python
arr = [5, 2, 7, 6, 3, 1, 4]
for i in range(len(arr) - 1):
        min_idx = i
        for j in range(i + 1, len(arr)):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
```

3. 삽입 정렬
하나를 선택해서 뽑고 그 수를 비교해가면서 가장 적합한 자리에 집어넣어 반복하는 알고리즘
인간이 무의식적 사용하는 대표적인 알고리즘
배열이 작을 경우 상당히 효율적, 작은 수가 뒤쪽에 많을 때는 효율 최악

```python
arr = [5, 2, 7, 6, 3, 1, 4]
for end in range(1, len(arr)):
        for i in range(end, 0, -1):
            if arr[i - 1] > arr[i]:
                arr[i - 1], arr[i] = arr[i], arr[i - 1]
```

4. 병합정렬/합병정렬
분할 정복 알고리즘 중 하나
데이터 상태에 영향을 받지 않음
먼저 데이터를 가장 작은 단위까지 분할한 후 이를 정렬하여 이어붙임을 반복

```python
arr = [5, 2, 7, 6, 3, 1, 4]    
if len(arr) < 2:
    return arr

mid = len(arr) // 2
low_arr = merge_sort(arr[:mid])
high_arr = merge_sort(arr[mid:])

merged_arr = []
l = h = 0
while l < len(low_arr) and h < len(high_arr):
    if low_arr[l] < high_arr[h]:
        merged_arr.append(low_arr[l])
        l += 1
    else:
        merged_arr.append(high_arr[h])
        h += 1
merged_arr += low_arr[l:]
merged_arr += high_arr[h:]
```

5. 힙 정렬
힙트리 구조에 먼저 삽입하고 이를 비교하며 반복하면서 정렬하는 알고리즘

```python
arr = [5, 2, 7, 6, 3, 1, 4]  

for arr_len in range(len(arr), 1, -1):
    last_parent = len(arr) // 2 - 1
    for current in range(last_parent, -1, -1):
        while current <= last_parent:
            child = current * 2 + 1
            sibling = child + 1
            if sibling < len(arr) and arr[child] < arr[sibling]:
                child = sibling
            if arr[current] < arr[child]:
                arr[current], arr[child] = arr[child], arr[current]
                current = child
            else:
                break
    arr[arr_len - 1], arr[0] = arr[0], arr[arr_len - 1]
```