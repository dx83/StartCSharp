▼ enum을 값의 조합으로 사용
```csharp
enum Days
{
    Sunday = 1, Monday = 2, Tuseday = 4, Wednesday = 8,
    Thursday = 16, Friday = 32, Saturday = 64
}
```
- `|`(OR) 연산자를 사용해 정수형 값을 겹칠 수 있고, HasFlag 메서드를 사용해 특정 요소 값을 포함하고 있는지 판단할 수 있다.
```csharp
Days workingDays = Days.Monday | Days.Tuesday | Days.Wednesday | Days.Thursday | Days.Friday;

Console.WriteLine(workingDays.HasFlag(Days.Sunday));    // Sunday를 포함하고 있는가?

Days today = Days.Friday;
Console.WriteLine(workingDays.HasFlag(today));          // today를 포함하고 있는가?

Console.WriteLine(workingDays); // 2 + 4 + 8 + 16 + 32

// 출력문
False
True
62
```
- enum 타입의 인스턴스가 여러 개의 값을 포함하는 용도로 사용된다는 것을 알리기 위해 [Flags] 특성을 지정할 수 있다.
<br>

▼ [Flags] 특성은 enum 타입에만 사용될 수 있다.
```csharp
[Flags]
enum Days
{
    Sunday = 1, Monday = 2, Tuesday = 4, Wednesday = 8,
    Thursday = 16, Friday = 32, Saturday = 64
}
// 출력문
Console.WriteLine(workingDays); // Monday, Tuesday, Wednesday, Thursday, Friday
```
<br>

▼ enum은 코드의 가독성 및 오류를 줄이는 역할을 한다.
```csharp
int Calc(char opType, int operand1, int operand2)
{
    switch (opType)
    {
        case '+': return operand1 + operand2;
        case '-': return operand1 - operand2;
        case '*': return operand1 * operand2;
        case '/': return operand1 / operand2;
    }

    return 0;
}
// 출력문
Console.WriteLine(Calc('+', 5, 6));  // 11
```

```csharp
enum CalcType { Add, Minus, Multiply, Divide }

static int Calc(CalcType opType, int operand1, int operand2)
{
    switch (opType)
    {
        case CalcType.Add: return operand1 + operand2;
        case CalcType.Minus: return operand1 - operand2;
        case CalcType.Multiply: return operand1 * operand2;
        case CalcType.Divide: return operand1 / operand2;
    }

    return 0;
}
// 출력문
Console.WriteLine(Calc(CalcType.Add, 5, 6));  // 11
```
- CalcType enum 정의에서 지원되는 연산을 짐작할 수 있고, 오타 발생시 컴파일 오류를 발생시킨다.

****
<br>
