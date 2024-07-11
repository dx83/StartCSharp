### 열거형 (enumeration type)
> 값 형식의 하나로 byte, sbyte, short, ushort, int, uint, long, ulong 만을 상속받아 정의할 수 있는 제한된 사용자 정의 타입이다.
```csharp
[접근_제한자] enum 타입명
{
    // 숫자를 대표하는 식별자 이름 나열
}
```
- enum 타입은 숫자형 값에 사람이 인식하기 쉬운 문자열 이름을 부여한다.
- 상속 타입을 지정하지 않는 경우 기본적으로 System.Int32가 된다.
<br>

```csharp
enum Days
{
    Sunday, Monday, Tuseday, Wednesday, Thursday, Friday, Saturday
}

class Program
{
    static void Main(string[] args)
    {
        Days today = Days.Sunday;
        Console.WriteLine(today);   // sunday 출력
    }
}
```
- Sunday = 0, ~, Saturday = 6 으로 상속받은 System.Int32 타입에 해당하는 겂이 된다.
- 출력 시 숫자 0이 아닌 Sunday 라는 문자열이 나온 이유는 enum의 ToString 메서드를 재정의했기 때문이다.
<br>

▼ System.Int32를 부모로 두기 때문에 Days 타입은 각종 숫자형 타입과 형변환 가능
```csharp
Days today = Days.Sunday;

int n = (int)today;         // enum에서 int형으로 명시적 변환
short s = (short)today;     // enum에서 short형으로 명시적 변환

today = (Days)5;            // 숫자형에서 enum형으로 명시적 변환
Console.WriteLine(today);   // friday 출력
```
- 명시적 형변환을 해야 한다.
<br>

▼ enum의 시작 요소 값에 0이 아닌 다른 정수를 지정할 수 있다.
```csharp
enum Days
{
    Sunday = 5, Monday = 10, Tuseday, Wednesday, Thursday = 15, Friday, Saturday
}

enum Test : byte // 다른 타입 상속
{
}
```
- 그 이후의 요소에 대해서도 1씩 자동으로 증가하는 것이 아닌 임의로 값을 지정할 수 있다.
- Sunday = 5, Monday = 10, Tuseday = 11, Wednesday = 12, Thursday = 15, Friday = 16, Saturday = 17
- 값을 할당할 때 enum이 상속받은 부모의 숫자 타입 범위에 있는 값을 지정해야 한다.
<br>

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

Console.WriteLine(workingDays);

// 출력문
False
True
62    // 2 + 4 + 8 + 16 + 32
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
