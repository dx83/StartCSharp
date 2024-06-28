### for 문
▼ for 문 문법
```csharp
for (초기화; 조건식; 반복식)
    구문;

for (초기화; 조건식; 반복식) 구문;
```
- for 문에 진입할 때 `초기화` 코드가 실행되고, 이후 `조건식` -> `구문` -> `반복식`을 번갈아 가며 조건식의 평가 결과가 bool 타입으로 false가 될 때까지 실행을 반복한다.
<br>

```csharp
for (int n = 1; n <= 9; n++)    // 10이 되면 for 문 벗어남
{
    Console.WriteLine(n);
}

int n = 1;
for (; n <= 9; n++)             // 초기화 구문 생략
{
    Console.WriteLine(n);
}

int n = 1;
for (; ; n++)                   // 초기화, 조건식 구문 생략
{
    if (n > 9) break;           // break 사용 가능
    Console.WriteLine(n);
}

int n = 1;
for (;;)            // 초기화, 조건식, 반복식 구문 모두 생략
{
    if (n > 9) break;
    Console.WriteLine(n);
    n++;
}
```
- 초기화, 조건식, 반복식을 생략할 수 있지만, 세미콜론은 반드시 있어야 한다.
<br>

▼ 중첩 루프 (nested loop) : for 루프 안에 또 다시 for 루프가 있는 경
```csharp
// 구구단
for (int x = 2; x < 10; x++)
    for (int y = 1; y < 10; y++)
        Console.WriteLine(x + " * " + y + " = " + (x * y));
```
****
<br>

### foreach 문



****
<br>
