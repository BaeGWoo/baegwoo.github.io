---
layout: simple
title: "Vector"
---

## Vector

- Vector는 동적 배열(dynamic array)을 의미하는 자료 구조입니다.
- 크기가 가변적이고, 연속적인 메모리 블록에 데이터를 저장합니다.
- 벡터는 배열과 유사하지만, 크기를 동적으로 조정할 수 있다는 점에서 차별화됩니다.
- List<요소타입>()의 형태로 사용합니다.

---

### Vector의 삽입과 삭제

- 벡터의 끝에서 삽입과 삭제는 O(1) 시간 복잡도로 매우 빠르게 이루어집니다.
- 벡터의 중간에서 삽입이나 삭제를 할 경우, 나머지 요소들을 이동시켜야 하기 때문에 O(n) 시간 복잡도를 가집니다.

#### Add(data)

```csharp
  public void Add(T data)
  {
      if (arr == null)
      {
          Resize(1);
      }

      else
      {
          if (size == capacity)
          {
              Resize(capacity * 2);
          }
      }
      arr[size] = data;
      size++;
  }
```

- 벡터는 초기 용량을 설정할 수 있으며, 데이터가 추가됨에 따라 용량이 부족할 때마다 자동으로 확장됩니다.
- 확장 시 일반적으로 현재 용량의 두 배로 크기를 늘립니다.

```csharp
 public void Reserve(int newSize)
 {
     if (newSize > capacity)
     {
         Resize(newSize);
     }
 }


  public void Resize(int newSize)
 {
     T[] temp = new T[newSize];
     for (int i = 0; i < size; i++)
     {
         temp[i] = arr[i];
     }
     arr = temp;
     temp = null;
     capacity = newSize;
 }
```

### Vector 목적위치 삭제구현

```csharp
private T error;
public void RemoveAt(int index)
{
    if (index < size)
    {
        for (int i = index; i < size - 1; i++)
        {
            arr[i] = arr[i + 1];
        }

        arr[size - 1] = error;
        size--;
    }

    else
    {
        Console.WriteLine("index is out of Range");
    }
}
```
