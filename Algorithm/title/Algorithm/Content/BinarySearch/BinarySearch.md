---
layout: simple
title: "이진탐색"
---

## 이진탐색
- 정렬된 배열에서 특정 값을 효율적으로 찾기 위한 재귀를 이용하는 알고리즘입니다.
 1. 배열이 정렬되어있어야합니다.
 2. 기준점을 기준으로 찾아야 할 범위를 줄여가며 탐색합니다.
 3. 
  - 찾고자 하는 값이 중간값보다 크면, 배열의 오른쪽 절반을 대상으로 검색을 계속합니다.
  - 찾고자 하는 값이 중간값보다 작으면, 배열의 왼쪽 절반을 대상으로 검색을 계속합니다.
 4. 배열에서 해당 값을 찾을 때까지 이 과정을 반복합니다.
 5. 찾을 수 없다면, 값은 배열에 존재하지 않음을 의미합니다.



```csharp
int[] arr = new int[] { 5, 6, 8, 11, 22, 33, 44, 50, 51, 79 };
int pivot = 0, left = 0, right = arr.Length - 1;
int target = 44;
while (left < right)
{
    pivot = (left + right) / 2;
    if (pivot == left)
    {
        if (arr[pivot] != target)
        {
            Console.WriteLine("해당하는 값이 존재하지 않습니다.");
            break;
        }
    }    if (target < arr[pivot])
    {
        right = pivot - 1;
    }    else if (target > arr[pivot])
    {
        left = pivot + 1;
    }    else
    {
        Console.WriteLine("해당하는 값(" + target + ")은 " + pivot + "에 위치합니다.");
        break;
    }
}
Console.WriteLine(BinarySearch(target, 0, arr.Length - 1, arr));

```
