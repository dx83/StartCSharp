### 상수 (constant)
> 변하지 않는 값인 리터럴을 식별자로 재사용할 수 있게 만들어준다.
<br>

```csharp
int x = 5;
int y = 10;

Console.WriteLine("x 변수의 값: " + x);
Console.WriteLine("y 변수의 값: " + y);
```
- "변수의 값: "이라는 문자열이 중복되고 있다.
- 해당 문자열의 변경 사항이 있는 경우 사용된 모든 코드를 찾아서 수정해야 한다.
```csharp
const string TEXT = "변수의 값: ";

static void Main(string[] args)
{
    int x = 5;
    int y = 10;

    Console.WriteLine("x" + TEXT + x);
    Console.WriteLine("y" + TEXT + y);
}
```
- 이런 경우 상수를 사용하여 유지보수에 도움이 된다.
<br>

```csharp
class 클래스_명
{
    접근_제한자 const 상수타입 식별자 = 값;
}
```
- 상수는 readonly 변수와 유사하지만 몇 가지 차이가 있다.
    - 상수는 static 예약어가 허용되지 않는다. (의미상으론 이미 static에 해당)
    - `기본 자료형` 형식에 대해서만 상수 정의가 허용된다.
    - 반드시 상수 정의와 함께 값을 대입해야 한다. 생성자에서 접근할 수 없다.
    - 상수는 컴파일할 때 해당 소스코드에 값이 직접 치환되는 방식으로 구현된다.
<br>

▼ 기본 자료형의 숫자 형식은 표현할 수 있는 범위에 대한 상한값과 하한값을 MaxValue, MinValue라는 상수로 제공된다.
```csharp
Console.WriteLine("sbyte \t: " + sbyte.MinValue + " ~ " + sbyte.MaxValue);
Console.WriteLine("byte \t: " + byte.MinValue + " ~ " + byte.MaxValue);
Console.WriteLine("short \t: " + short.MinValue + " ~ " + short.MaxValue);
Console.WriteLine("ushort \t: " + ushort.MinValue + " ~ " + ushort.MaxValue);
Console.WriteLine("char \t: " + (int)char.MinValue + " ~ " + (int)char.MaxValue);
Console.WriteLine("int \t: " + int.MinValue + " ~ " + int.MaxValue);
Console.WriteLine("uint \t: " + uint.MinValue + " ~ " + uint.MaxValue);
Console.WriteLine("long \t: " + long.MinValue + " ~ " + long.MaxValue);
Console.WriteLine("ulong \t: " + ulong.MinValue + " ~ " + ulong.MaxValue);
Console.WriteLine("float \t: " + float.MinValue + " ~ " + float.MaxValue);
Console.WriteLine("double \t: " + double.MinValue + " ~ " + double.MaxValue);
Console.WriteLine("decimal : " + decimal.MinValue + " ~ " + decimal.MaxValue);
// 출력문
sbyte   : -128 ~ 127
byte    : 0 ~ 255
short   : -32768 ~ 32767
ushort  : 0 ~ 65535
char    : 0 ~ 65535
int     : -2147483648 ~ 2147483647
uint    : 0 ~ 4294967295
long    : -9223372036854775808 ~ 9223372036854775807
ulong   : 0 ~ 18446744073709551615
float   : -3.402823E+38 ~ 3.402823E+38
double  : -1.79769313486232E+308 ~ 1.79769313486232E+308
decimal : -79228162514264337593543950335 ~ 79228162514264337593543950335
```
<br>

▼ 숫자형 상수는 연관된 것들끼리 모아서 enum 타입으로 정리할 수 있다.
```csharp
// 개별적인 상수로 표현
const int Sunday = 0;
const int Monday = 1;
const int Tuesday = 2;
const int Wednesday = 3;
const int Thursday = 4;
const int Friday = 5;
const int Saturday = 6;

// 상수를 enum 타입으로 묶어서 표현
enum Days
{
    Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday
}
```
- Days 타입은 숫자형 상수의 묶음을 표현한 것과 같다.

****
<br>
