## 3. 기본 문법 요소
### 1) 예약어, 키워드
> 예약어 (reserved word) 또는 키워드(keyword)는 C# 언어에서 문법을 표현하기 위해 미리 예약된 단어를 의
- 현재까지 배운것 중에서 예약어
  - sbyte, byte, short, ushort, int, uint, long, ulong
  - float, double, decimal
  - char, string
  - bool
****
<br>

### 2) 식별자 (identifier)
> 개발자가 프로그래밍을 하면서 임의로 선택해서 이름 지을 수 있는 단어

▼ 주석 부분의 단어가 모두 식별자
```csharp
using System;

namespace ConsoleApp1                    // ConsoleApp1
{
    class Program                        // Program
    {
        static void Main(string[] args)  // Main, args
        {
            string text = "Hello World"; // text
            Console.WriteLine(text);
        }
    }
}
```
****
<br>
