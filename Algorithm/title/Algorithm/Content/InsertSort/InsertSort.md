---
layout: simple
title: "삽입 정렬"
---

## 삽입 정렬
- 데이터를 하나씩 확인하면서 이미 정렬된 부분과 비교하여 자신의 위치를 찾아 삽입하는 방식으로 정렬하는 알고리즘입니다.

- 최초 정렬되지 않은 숫자배열
#### ![](Insert1.PNG)

- 0번째 인덱스는 이미 정렬되어있다고 가정합니다.
- 이후 회차부터는 해당 인덱스가 들어가야할 위치로 삽입합니다.
#### ![](Insert2.PNG)
#### ![](Insert3.PNG)



```csharp
int[] insertArr = new int[] { 8, 5, 6, 2, 4 };
int keyValue;
for (int i = 1; i < insertArr.Length; i++)
{
    keyValue = insertArr[i];
    for (int j = i; j > 0; j--)
    {
        if (keyValue < insertArr[j - 1])
        {
            insertArr[j] = insertArr[j - 1];
            if (j - 1 == 0)
            {
                insertArr[j - 1] = keyValue;
            }
        }
        else
        {
            insertArr[j] = keyValue;
            break;
        }
    }
}
```
