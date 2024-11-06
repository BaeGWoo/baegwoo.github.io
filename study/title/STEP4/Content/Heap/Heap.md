---
layout: simple
title: "Heap"
---

## 특정한 규칙에 따라 데이터를 저장하는 이진 트리 기반의 자료 구조입니다.

- 주로 ***우선순위 큐(Priority Queue)***나 ***힙 정렬(Heap Sort) 알고리즘***에서 사용됩니다. 

###  힙의 종류
- Max Heap (최대 힙): 부모 노드의 값이 자식 노드의 값보다 항상 크거나 같은 특성을 가집니다. 즉, 루트 노드는 트리에서 가장 큰 값을 가집니다.

- Min Heap (최소 힙): 부모 노드의 값이 자식 노드의 값보다 항상 작거나 같은 특성을 가집니다. 즉, 루트 노드는 트리에서 가장 작은 값을 가집니다.

## Insert(T data)
- 데이터를 규칙에 맞게 삽입합니다.(최대 힙 기준)
 1. 가장 마지막에 데이터를 삽입합니다.
  #### ![](Insert(1).PNG)
 2. 부모와 비교하여 부모보다 삽입하는 데이터의 크기가 크다면, 부모와 현재 데이터를 ***Swap()*** 해줍니다.
  #### ![](Insert(2).PNG)
 3. 이같은 과정을 반복하여 더이상 부모와 바뀌지 않는 위치까지 교환해줍니다.
 -  간단한 실습을 위해 고정된 배열크기를 쓰는 Heap의 Insert를 구현해보았습니다.


```csharp
 public void Insert(int data)
        {
            if (size + 1 >= arraySize)
            {
                Console.WriteLine("OverFlow");
            }

            else
            {
                array[++size] = data;

                int child = size;
                int parent = size / 2;

                while (child != 1)
                {
                    if (array[parent] < array[child])
                    {
                        Swap(child, parent);
                        child = parent;
                        parent = child / 2;
                    }

                    else
                        break;
                }
            }
        }
```


## Remove(T data)
- 데이터를 규칙에 맞게 삭제합니다.(최대 힙 기준)
 1. 삭제하고자 하는 데이터의 위치를 찾습니다.
  #### ![](Remove(1).PNG)
 2. 삭제하고자 하는 데이터의 위치에 가장 끝의 데이터를 임시로 삽입하여 줍니다.
  #### ![](Remove(2).PNG)
 3. 위치로 부터 양 쪽의 데이터 중 만약 현재 데이터가 둘 중 하나의 데이터보다 작다면, 위치를 교환합니다.
 4. 만약 둘 모두가 현재 데이터보다 크다면 더 큰 쪽과 교환합니다.
  #### ![](Remove(3).PNG)
 5. 더 이상 자식 데이터와 바뀌지 않을때까지 교환해줍니다.
 ```csharp
  public int Remove()
        {
            if (size <= 0)
            {
                Console.WriteLine("UnderFlow");
                return -1;
            }

            int result = array[1];
            array[1] = array[size];
            array[size--] = 0;

            int cur = 1;
            while (cur * 2 <= size)
            {
                int next;
                //오른쪽 자식 데이터
                //없을 경우를 대비하여 삼항연산자를 사용해줍니다.
                if (cur * 2 + 1 <= size)
                    next = array[cur * 2] > array[cur * 2 + 1] ? cur * 2 : cur * 2 + 1;
                
                //왼쪽 자식 데이터
                else
                    next = cur * 2;


                if (array[next] > array[cur])
                    swap(ref array[cur], ref array[next]);

                cur = next;
            }


            return result;
        }
 ```




