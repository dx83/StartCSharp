### 5) 상수 (constant)
> 변수가 값이 바뀌는 식별자라면 값이 절대 바뀌지 않는 상수가 있다.
- 상수 식별자에는 값이 한 번 대입되면 그 이후로 다른 값을 대입할 수 없다.

```csharp
const bool result = false;
const int n = 5;
const string text = "Hello";

result = true;  // 컴파일 에러, const 상수 값은 바꿀 수 없다.
```
<br>

```csharp
int n = Math.Max(0, 5);          // 프로그램을 실행할 때 n의 값이 결정 => n = 5

const int maxN = Math.Max(0, 5); // Math.Max 메서드가 실행된 이후에야 값이 결정되고,
                                 // 컴파일 시점에는 컴파일러가 해당 값을 알 수 없으므로
                                 // 컴파일 에러 발생

const int n = 5 * 100 / 2;       // 이러한 단순 수식은 컴파일러가 값을 계산할 수 있다.
// n은 상수라고 하고 "5 * 100 / 2" 는 상수식 (constant expression)이라고 구분할 수 있다.
```
- 상수식 : 언제나 캄파일할 때 값이 결정되는 수식

****
<br>

### 6) 연산자, 문장 부호
▼ 주석 부분이 모두 연산자 또는 문장 부호
```csharp
using System;                              // ;
namespace ConsoleApp1
{                                          // {
    class Program
    {                                      // {
        static void Main(string[] args)    // ( [ ] )
        {                                  // {
            string text = "Hello World";   // = ;
            Console.WriteLine(text);       // ( ) ;
        }                                  // }
    }                                      // }
}                                          // }
```
- `;` : 세미콜론, 한 구문의 끝을 컴파일러에게 알리는 문자 부호
- `=` : 대입 연산자 (assignment operator)
- `+,-*,/` : 산술 연산자 (arithmetic operator)
<br>

▼ `%` 나머지 연산자
```csharp
int n = 5;
int divider = 3;
int mod = n % divider;
Console.WriteLine(mod); // 2 출력
```
- 나머지 연산자를 이용하면 나눗셈 연산의 나머지 값을 알 수 있다.

****
<br>
