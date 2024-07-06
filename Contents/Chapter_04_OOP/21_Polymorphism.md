## 4. 오버로드 (overload)
- 메서드 시그니처 (method signature) : 메서드의 `이름` `반환 타압` `매개변수의 수` `개별 매개변수 타입`
- 오버라이드 (override) : 시그니처가 완전히 동일한 메서드를 재정의하는 경우
> 오버로드    
> - 시그니처 중에서 `반환값`은 무시하고 `이름`이 같은 메서드가 `매개변수의 수`, `개별 매개변수 타입`만 다르게 재정의하는 경우

****
<br>

### 1) 메서드 오버로드 (method overload)
- 생성자 오버로드    
  - 생성자는 반환값이 없는 특수한 메서드로 `매개변수의 수`, `개별 매개변수 타입` 만 다른 여러 가기 생성자를 정의할 수 있다.
  - 사용법은 [생성자 파트](./04_Class.md) 참고
- 메서드 오버로드
- 연산자 오버로드
<br>

▼ 메서드 오버로드
```csharp
// 절댓값을 반환하는 클래스
class Mathematic
{
    public int AbsInt(int value)
    {
        return (value >= 0) ? value : -value;
    }

    public double AbsDouble(double value)
    {
        return (value >= 0) ? value : -value;
    }

    public decimal AbsDecimal(decimal value)
    {
        return (value >= 0) ? value : -value;
    }
}
// 메서드 오버로드
class Mathematics  // 메서드명 통일
{
    public int Abs(int value)
    {
        return (value >= 0) ? value : -value;
    }

    public double Abs(double value)
    {
        return (value >= 0) ? value : -value;
    }

    public decimal Abs(decimal value)
    {
        return (value >= 0) ? value : -value;
    }
}
// 출력문
Mathematics math = new Mathematics();
Console.WriteLine(math.Abs(-5));        // 5
Console.WriteLine(math.Abs(-10.052));   // 10.052
Console.WriteLine(math.Abs(20.01m));    // 20.01
```
- `ConsoleWriteLine`도 다양한 타입의 값을 받을 수  있게 정의된 메서드 오버로드의 예다.

****
<br>
