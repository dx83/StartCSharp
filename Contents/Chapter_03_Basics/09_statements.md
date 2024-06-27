## 5. 제어문
### 1) 선택문 (selection statements)
> if, switch
<br>

### 관계 연산자, 논리 연산자
|관계 연산자|평가 방식|예제|
|---|---|---|
|>|좌측 피연산자가 우측 피연산자보다 크면 참, 같거나 작으면 거짓|bool result = 10 > 20;  // 거짓|
|<|좌측 피연산자가 우측 피연산자보다 작으면 참, 같거나 크면 거짓|bool result = 10 < 20;  // 참|
|>=|좌측 피연산자가 우측 피연산자보다 크거나 같으면 참, 작으면 거짓|bool result = 10 >= 20;  // 거짓|
|<=|좌측 피연산자가 우측 피연산자보다 작거나 같으면 참, 크면 거짓|bool result = 10 <= 20;  // 참|
|==|좌측 피연산자와 우측 피연산자가 같으면 참, 다르면 거짓|bool result = 10 == 20;  // 거짓|
|!=|좌측 피연산자와 우측 피연산자가 다르면 참, 같으면 거짓|bool result = 10 != 20;  // 참|

****
<br>

### 2) 식별자 (identifier)
> 개발자가 프로그래밍을 하면서 임의로 선택해서 이름 지을 수 있는 단어

<br>
▼ 주석 부분의 단어가 모두 식별자

```csharp
using System;

namespace ConsoleApp1                           // ConsoleApp1
{
    class Program                               // Program
    {
        public static void Test(string[] args)  // Test, args
        {
            string text = "Hello World";        // text
            Console.WriteLine(text);
        }
    }
}
```
<br>

- 식별자 규칙
  - 식별자의 시작 문자는 숫자로 시작할 수 없고, 반드시 문자여야 한다.
  - 특숫 문자 중에서 유일하게 _(밑줄, underscore) 문자만을 시작 문자로 사용할 수 있다.
  - 유니코드 범위의 문자가 허용되기 때문에 '한글' 식별자도 가능은 하다. (권장되지 않는다!!)
  - 예약어를 식별자로 사용할 수 없다.
  
  ```csharp
  string @bool = "true";        // 단, '@' 문자를 접두사로 붙여 사용 가능
  string _bool = "TRUE";        // '_' 도 가능
  ```
  
  - 흔한 경우는 아니지만 이스케이프 시퀀스로도 식별자를 사용할 수 있다.

  ```csharp
  string \u0062ool = "true";    // @bool와 동일해서 같이 정의한 경우 컴파일 에러
  string @bool = "true"         // \u0062ool 와 동일해서 같이 정의한 경우 컴파일 에러
  Console.WriteLine(\u0062ool); // true 출력
  ```

****
<br>

### 3) 리터럴 (literal)
> 소스코드에 포함된 값

▼ 주석 부분의 값이 모두 리터럴

```csharp
string text = "Hello World";  // Hello World
int n = 5;                    // 5
char ch = 'N';                // N
bool result = true;           // true
```

****
<br>
