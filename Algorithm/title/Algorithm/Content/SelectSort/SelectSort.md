---
layout: simple
title: "Puzzle"
---

## 선택정렬
-  주어진 리스트 중에 최소값을 찾아서 맨 앞에 위치한 결과를 교체하는 방식으로 정렬하는 알고리즘입니다.

- 최초 정렬되지 않은 숫자배열
#### ![](Select1.PNG)

- 정렬되지 않은 배열 중 최솟값을 찾습니다.
- 현재 인덱스의 값과 최솟값이 있는 인덱스의 값을 서로 교환합니다.
#### ![](Select2.PNG)
#### ![](Select3.PNG)


```csharp
int[] sel = { 9, 6, 7, 3, 5 };
int size = sel.Length;
for (int i = 0; i < size - 1; i++)
{
    int min = sel[i];
    int position = i;
    for (int j = i; j < size; j++)
    {
        if (sel[j] < min)
        {
            min = sel[j];
            position = j;
        }
    }    int temp = sel[i];
    sel[i] = sel[position];
    sel[position] = temp;   
}
```

