## out 예약어
- `out`으로 지정된 인자에 넘길 변수는 초기화되지 않아도 된다.
  - 초기화돼 있더라도 `out` 인자를 받는 메서드에서는 그 값을 사용할 수 없다.
- `out`으로 지정된 인자를 받는 메서드는 내부 구현에서 반드시 변수에 값을 넣어야 한다.
<br>

> 메서드는 단 1개의 반환값만 가질 수 있지만 out으로 지정된 매개변수를 사용함으로써 여러 개의 값을 반환할 수 있다.
<br>

▼ 나눗셈은 절대로 분자를 0으로 나눌 수 없다.
```csharp
struct DivideResult
{
    public bool Success;
    public int Result;
}

DivideResult Divide(int n1, int n2)
{
    DivideResult ret = new DivideResult();

    if (n2 == 0)    // 분모가 0이면 success 필드를 false로 설정
    {
        ret.Success = false;
        return ret;
    }

    ret.Success = true;
    ret.Result = n1 / n2;
    return ret;
}
// 출력문
DivideResult dv = Divide(15, 3);
Console.WriteLine(dv.Success ? dv.Result.ToString() : "나눗셈 실패"); // 5
```
- 위 코드를 out 예약어를 사용하여 개선
```csharp
bool Divide(int n1, int n2, out int result)
{
    if (n2 == 0)
    {
        result = 0;
        return false;
    }

    result = n1 / n2;
    return true;
}
// 출력문
int result;
Console.WriteLine(Divide(15, 3, out result) ? result.ToString() : "나눗셈 실패");  // 5
```
- `out`으로 지정된 result 변수는 메서드가 `return`하기 전에 반드시 초기화가 되어 있어야 한다.
- result = 0; 부분을 제거하면 컴파일 에러 발생
<br>

▼ System.Int32 타입에 정의된 TryParse 정적 메서드
```csharp
public static bool TryParse(string s, out int result);
```
- 변환이 성공했는지 여부를 true/false로 반환하고, 반환이 성공하면 `out`으로 지정된 result 변수에 값을 반환한다.

```csharp
int n;
if (int.TryParse("1234567", out n) == true) // System.Int32의 TryParse 호출
{
    Console.WriteLine(n);   // 1234567
}

double d;
if (double.TryParse("12E3", out d) == true) // double은 지수 표기법의 문자열도 지원
{
    Console.WriteLine(d);   // 12000
}

bool b;
if (bool.TryParse("true", out b) == true)   // bool 타입도 관련된 문자열 해석
{
    Console.WriteLine(b);   // true
}

short s;
if (short.TryParse("123456789", out s) == true) // short의 범위를 초과: false 반환
{
    Console.WriteLine(s);   // 실행되지 않음
}

if (short.TryParse("Not_a_number", out s) == true)   // 숫자가 아니므로 false 반환
{
    Console.WriteLine(s);   // false가 반환됐으므로 실행되지 않음
}
```
<br>

```
TryParse와 ToString은 문자열과 타입 간의 변환에 있어 쌍을 이룬다.
이 원리를 이용하면 타입의 값을 프로그램 외부에 저장하고 복원할 수 있다.
```

****
<br>
