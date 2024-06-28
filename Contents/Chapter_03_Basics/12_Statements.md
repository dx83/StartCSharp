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
▼ foreach 문 문법
```csharp
for (표현식요소의자료형 변수명 in 표현식)
    구문;

for (표현식요소의자료형 변수명 in 표현식) 구문;
```
- 표현식에 올 수 있는 자료형 : 배열, 컬렉션
- 요소 수만큼 구문이 반복되며, 각 반복마다 해당 요소의 값을 `변수명`에 넣은 후 구문을 실행한다.
<br>

```csharp
int[] arr = new int[] { 1, 2, 3, 4, 5 };

foreach (int elem in arr)
{
    Console.WriteLine(elem);
}
```
- foreach 문은 in 다음에 오는 배열을 처음부터 끝까지 순회하면서 개별 요소를 `int elem`으로 선언된 변수에 넣어 반복문 구문 내에서 해당 변수를 사용할 수 있게 해준다.

****
<br>
