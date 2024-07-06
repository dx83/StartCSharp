### 연산자 오버로드 (operator overload)
```csharp
int n1 = 5;
int n2 = 10;
int sum = n1 + n2;
Console.WriteLine(sum);         // 15

string txt1 = "123";
string txt2 = "456";
Console.WriteLine(txt1 + txt2); // 123456
```
- 정수형 타입과 문자열 타입에 대해 각각 + 연산을 수행하는데, 타입에 따라 + 연산자의 역할이 달라졌다.
<br>

```csharp
public class Kilogram
{
    double mass;

    public Kilogram(double value)
    {
        this.mass = value;
    }

    public Kilogram Add(Kilogram target)
    {
        return new Kilogram(this.mass + target.mass);
    }

    public override string ToString()
    {
        return mass + "kg";
    }
}
// 출력문
Kilogram kg1 = new Kilogram(5);
Kilogram kg2 = new Kilogram(10);

Kilogram kg3 = kg1.Add(kg2);

Console.WriteLine(kg3);     // 15kg
```
<br>

▼ 연산자 오버로드 정의
```csharp
public static 타입 operator 연산자 (타입1 변수명1, 타입2 변수명2)
{
    // [타입]을 반환하는 코드
}
```
- `public Kilogram Add(Kilogram target)` 부분 재정의
```csharp
public static Kilogram operator +(Kilogram op1, Kilogram op2)
{
    return new Kilogram(op1.mass + op2.mass);
}
// 출력문
Kilogram kg4 = kg1 + kg2;
Console.WriteLine(kg4);     // 15kg
```
<br>

```
C#에서는 연산자와 메서드 간의 구분이 없다.    
대부분의 연산자는 각 타입의 의미에 맞는 연산으로 새롭게 재정의할 수 있다.
```
<br>
▼ 연산자에 따른 오버로드 가능 여부

|C#연산자|오버로드 가능 여부|
|---|---|
|+, -, !, ~, ++, --, true, false|단항 연산자는 모두 오버로드 가능(+,-는 부호 연산자)|
|+, -, *, /, %, &, \|, ^, <<, >>|이형 연산자는 모두 오버로드 가능(+,-는 사칙 연산자)|
|==, !=, <, >, <=, >=|비교 연산자는 모두 오버로드할 수 있지만 반드시 쌍으로 재정의해야 한다.<br> == 연산자를 오버로드했다면 != 연산자도 해야 한다.|
|&&, \|\||논리 연산자는 오버로드할 수 없다.|
|[ ]|배열 인덱스 연산자 자체인 대괄호는 오버로드할 수 없지만 C#에서는 이를 대체하는 별도의 인덱서 구문을 지원한다.|
|(Type)x|형변환 연산자 자체인 괄호는 오버로드할 수 없지만 대신 explicit, implicit를 이용한 대체 정의가 가능하다.|
|+=, -=, *=, /=, %=, &=, \|=, ^=, <<=, >>=|복합 대입 연산자 자체는 오버로드할 수 없지만 대입이 아닌 +, -, *, / 등의 연산자를 오버로드하면 복합 대입 연산 구문이 지원된다.|
|기타 연산자|오버로드할 수 없다.|

****
<br>
