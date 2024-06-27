### if 문
▼ if 문 문법
```csharp
if (조건식)
    구문;

if (조건식) 구문;
```
- 조건식이 참인 경우, 구문에 해당하는 코드를 실행한다.
<br>

> 블록 (block) : 시작과 끝에 중괄호 (brace)를 사용, 여러개 구문을 실행해야 하는 경우 필수    
> else 예약어 : 조건식의 결과가 참인 경우뿐 아니라 거짓인 경우에도 실행할 수 있는 구문
```csharp
int value = 5;
if (value <= 255)
{
    Console.WriteLine("byte 변환 가능");
    byte b = (byte)value;
}
else if (value <= 65535)
{
    Console.WriteLine("ushort 변환 가능");
    ushort u = (ushort)value;
}
else
{
    Console.WriteLine("int 타입");
}
```
<br>

▼ 삼항 연산자 (ternary operator) 또는 조건 연산자
```
(조건식) ? 표현식 1 : 표현식 2;
```
- 조건식이 참인 경우 표현식 1을 평가해서 반환하고, 거짓인 경우 표현식 2를 평가해서 반환한다.
<br>

```csharp
int value = 5;
string result;
if (value % 2 == 0)
{
    result = "짝수";
}
else
{
    result = "홀수";
}
Console.WriteLine(result);  // 홀수 출력
```
▼ 위 코드를 삼항 연산자를 이용해 표현
```csharp
int value = 5;
string result = (value % 2 == 0) ? "짝수" : "홀수"; // "홀수" 대입
```

****
<br>

### switch 문
▼ switch 문 문법
```csharp
switch (인스턴스)
{
    case 상수식1:
        구문;
        break;

    ----- [임의의 case 문 반복] -----

    case 상수식n:
        구문;
        break;

    default:
        구문;
        break;
}
```


****
<br>
