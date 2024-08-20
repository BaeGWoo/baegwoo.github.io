---
layout: simple
title: "함수"
---

## 하나의 특별한 목적의 작업을 수행하기 위해 독립적으로 설계된 코드의 집합입니다.

- 함수의 경우 자료형과 반환하는 값의 형태가 일치하지 않으면 원하는 값을 얻을 수 없습니다.
- **오버헤드**
  - 프로그램의 실행흐름 도중에 동떨어진 위치의 코드를 실행시켜야 할 때 , 추가적으로 시간,메모리,자원이 사용되는 현상입니다.

### "매개변수"

- 함수의 정의에서 전달받은 인수를 함수 내부로 전달하기 위해 사용하는 변수입니다.
- 매개변수는 함수 내부에서만 연산이 이루어지며, 함수가 종료되면 메모리에서 사라지는 특징을 가지고 있습니다.

```csharp
static void Recovery(int health)
{
    Console.WriteLine("health의 값 : " + health);
}

int hp=100;
Recovery(100);
```

#### **params**

- 메서드에 가변 개수의 인수를 전달할 수 있도록 해줍니다.
- 메서드가 불특정 다수의 인수를 받을 수 있게 하며, 메서드를 호출할 때 인수의 개수나 배열을 신경 쓰지 않고 편리하게 사용할 수 있습니다.

```csharp
static void PrintNumbers(params int[] numbers)
  {
      foreach (int number in numbers)
      {
          Console.WriteLine(number);
      }
  }

  static void Main()
  {
      PrintNumbers(1, 2, 3, 4, 5); // 여러 인수를 전달
      PrintNumbers(new int[] { 6, 7, 8 }); // 배열을 전달
  }
```

### "인수"

- 함수가 호출될 때 매개 변수에 실제로 전달되는 값입니다.

#### 1. ref 키워드

- **참조로 전달**
  - 값을 직접 전달하는 대신, 변수의 메모리 주소를 전달하여, 그 메모리 위치의 값을 함수 내에서 읽고 변경할 수 있게 합니다.
  - 함수가 호출된 곳의 변수와 동일한 변수를 가리키기 때문에 함수 내에서 변수의 값이 변경되면 호출된 곳에서도 그 변경 사항이 반영됩니다.

```csharp
static void Swap(ref int x, ref int y)
{
    int temp = x;
    x = y;
    y = temp;
}
```

#### 2. out 키워드

- 함수 내부에서 반드시 값을 할당해야 합니다.
- 함수가 여러 개의 값을 반환할 수 있습니다.

```csharp
static void GetValues(out int x, out int y)
{
    x = 10;
    y = 20;
}

static void Main()
{
    GetValues(out int a, out int b);
    Console.WriteLine($"a: {a}, b: {b}"); // 출력: a: 10, b: 20
}
```

#### 3. in 키워드

- 함수가 매개변수로 전달된 값을 읽기만 하고 수정하지 않도록 보장합니다.

### "재귀 함수"

- 어떤 함수에서 자신을 다시 호출하여 작업을 수행하는 함수입니다.
- 재귀 함수는 함수를 계속 호출하기 때문에 스택 영역에 메모리가 계속 쌓이게 되므로 `스택 오버플로우`가 일어나게 됩니다.
- 재귀 함수의 경우 특정한 시점에서 함수를 반환해야 하며, 재귀적으로 호출한 함수는 스택 프레임에 의해 마지막에 호출된
- 함수부터 차례대로 스택 영역에서 해제됩니다.

```csharp
 static void Start(int count)
 {
     if (count <= 0)
     {
         return;
     }
     else
         Start(count - 1);
     Console.WriteLine("Start" + count);
 }
```

### "박싱과 언박싱"

#### **박싱**

- 값 형식을 참조 형식으로 변환하는 과정을 의미합니다.

#### **언박싱**

- 참조형식을 값 형식으로 변환하는 과정입니다.

```csharp
//박싱
int attack = 10;
object box=attack;
Console.WriteLine("box의 값 : "+box);

//언박싱
int result = (int)box;
object[] dataList = new object[3];

Console.WriteLine("result의 값 : "+result);

dataList[0] = 10;//Attack
dataList[1] = "Marine";//Name
dataList[2] = 55.5f;//Health
Information(dataList);


static void Information(object[] item)
{
    foreach (object element in item)
    {
        Console.WriteLine("element : " + element);
    }
}
```

#### `foreach 문`

- 배열의 각 요소를 순회하며 반복하는 구조입니다.
- 인덱스나 범위의 관리 없이 각 요소를 직접적으로 접근할 수 있는 장점이 있습니다.
