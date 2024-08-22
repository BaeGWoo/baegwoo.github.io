---
layout: simple
title: "String"
---

## String

- 문자(characters)의 순서 있는 시퀀스로, 텍스트 데이터를 표현하고 조작하는 데 사용되는 자료형입니다.
- 문자열은 프로그래밍 언어에서 가장 기본적이고 중요한 데이터 타입 중 하나로 단어, 문장, 심지어 전체 문서를 저장할 수 있습니다.
- 문자열은 배열처럼 각 문자가 특정 위치(인덱스)에 의해 접근 가능합니다.
- 첫 번째 문자는 인덱스 **0**에 위치합니다.

#### ![](plus.PNG)

- 음수 인덱스를 사용하면 문자열의 끝에서부터 접근할 수 있습니다.

#### ![](minus.PNG)

---

### 문자열 연산

- 문자열은 `+` 연산자를 사용해 두 문자열을 연결(concatenation)하거나, `*` 연산자를 사용해 문자열을 반복할 수 있습니다.
- Concat()구현

```csharp
 public void ConCat(char[] content)
 {
     int newSize = content.Length + size;
     char[] newArr = new char[newSize + 1];
     for (int i = 0; i < size; i++)
     {
         newArr[i] = arr[i];
     }

     for (int i = 0; i < content.Length; i++)
     {
         newArr[i + size] = content[i];
     }
     arr = newArr;
     size = newSize;
 }
```

### IndexOf(char target)

- 문자열에 해당 문자가 있는 최초위치를 반환하는 함수를 구현해보았습니다.

```csharp
 public int IndexOf(char target)
 {
     int result = -1;
     for (int i = 0; i < size; i++)
     {
         if (arr[i] == target)
         {
             result = i;
             break;
         }
     }
     return result;
 }
```

### Contains(char[] target)

- 문자열에 특정 문자열이 포함되어있는지 확인하는 함수를 구현해보았습니다.

```csharp
  public bool Contain(char[] target)
  {
      int index = 0;
      char cur = ' ';
      for (int i = 0; i < size; i++)
      {

          if (arr[i] == target[index])
              index++;

          else index = 0;

      }

      if (index == target.Length)
          return true;
      return false;
  }

```

### 파일 입출력

- File : 파일에 대한 생성, 복사, 이동 및 열기를 위한 클래스
- FileInfo : 파일에 대한 생성, 복사, 이동 및 열기에 대한 속성
- FileStream : 파일에 대한 스트림을 제공하여 동기 및 비동기 읽기/쓰기를 지원

```csharp
//data.txt파일을 불러옵니다.
FileStream fileStream = File.Create("data.txt");
fileStream.Close();
```

- StreamReader : 문자열에서 읽어오는 TextReader 구현
- StreamWriter : TextWriter를 구현하여 특정 인코딩을 스트림에 문자로 저장

```csharp
//data.txt파일에 원하는 정보를 입력합니다.
StreamWriter streamWriter = new StreamWriter("data.txt");
streamWriter.WriteLine("HP : 100");
streamWriter.WriteLine("Level : 13");
streamWriter.WriteLine("Name : Warrior");
streamWriter.Close();
```

#### 특정 파일에 저장된 내용을 읽어와서 콘솔창에 입력하기

```csharp
//매개변수인 name에 원하는 파일명을 입력합니다.
 static public void Print(string name)
 {
     StreamReader streamReader = new StreamReader(name);

     while (streamReader.Peek() >= 0)
     {
         Console.WriteLine(streamReader.ReadLine());
     }
     streamReader.Close();
 }
```
