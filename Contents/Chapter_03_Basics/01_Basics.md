# C# 기초
## 1. 기본 자료형
> 자료형 (Data Type) : 프로그램에서 데이터를 담을 수 있는 일정한 형식    
> 기본 자료형 (Built-in Types) : C# 언어에서 자체적으로 제공하는 데이터 형식
```
저장 공간의 효율을 높이기 위해 상황에 맞는 자료형 사용
```
****
<br>

### 정수형 기본 타입
|자료형|닷넷 형식|범위|크기||
|---|---|---|---|---|
|sbyte|System.Sbyte|-128 ~ 127|부호 있는 8비트 정수|1 바이트|
|byte|System.Byte|0 ~ 255|부호 없는 8비트 정수|1 바이트|
|short|System.Int16|-32,768 ~ 32,767|부호 있는 16비트 정수|2 바이트|
|ushort|System.UInt16|0 ~ 65,535|부호 없는 16비트 정수|2 바이트|
|int|System.Int32|-2,147,483,648 ~ 2,147,483,647|부호 있는 32비트 정수|4 바이트|
|uint|System.UInt32|0 ~ 4,294,967,295|부호 없는 32비트 정수|4 바이트|
|long|System.Int64|-9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807|부호 있는 64비트 정수|8 바이트|
|ulong|System.UInt64|0 ~ 18,446,744,073,709,551,615|부호 없는 64비트 정수|8 바이트|

```
닷넷의 기본 타입 형식으로 바꿔 쓸 수 있지만 편의상 C#에서 제공되는 별칭을 사용한다.
```
****
<br>

### 실수형 기본 타입
|자료형|닷넷 형식|범위|크기|
|---|---|---|---|
|float|System.Single|±1.5e-45 ~ ±3.4e38|4 바이트|
|double|System.Double|±5.0e-324 ~ ±1.7e308|8 바이트|
|decimal|System.Decimal|±1.0 × 10<sup>-28</sup> ~ ±7.9 × 10<sup>28</sup>|16 바이트|

****
<br>

### 문자형 기본 타입
> 유니코드는 다국어 지원을 위한 문자 집합으로 전 세계의 모든 문자를 표현하기 위해 설계된 산업 표준이다.

|자료형|닷넷 형식|범위|설명|
|---|---|---|---|
|char|System.Char|U+0000 ~ U+FFFF|유니코드 16비트 문자|
|string|System.String|문자열|유니코드 문자열|
<br>

- char : "부호 없는 16비트 정수"인 System.UInt16 `ushort`과 표현할 수 있는 범위의 수가 동일
```csharp
char ch = 'A';  // 작은 따옴표 사용
ch = ch + 1;    // 사칙연산(+,-,*,/)을 하려는 경우 컴파일 오류
```
- 이스케이프 시퀀스 (escape sequence) : `\`(역슬래시, back-slaxh)로 시작하는 특수문자 표현, 키보드로 입력할 수 없는 문자를 표현
- 일부 편집기에서 `\` 문자는 한글 윈도우의 경우 `￦`(통화:원) 문자로 대체돼 표시되기도 한다.
```csharp
char ch1 = '\t';      // TAB 문자를 표현
char ch2 = '\n';      // 개행 (NEW LINE) 문자를 표현
char ch3 = '\'';      // 작은 따옴표, 큰 따옴표, 표현
char ch4 = '\u2024';  // 16진수의 유니코드 문자
//해당 문자 폰트가 없어서 '▶'이 출력되어야 하지만 '?'이 나온다.
char ch5= '\\';       // '\'를 출력하려면 2개의 역슬래시를 사용
```
<br>

- 문자열 : 문자가 둘 이상인 경우 string 타입에 대응된다.
```csharp
string text1 = "Hellow World";
string text2 = "\tHello\nWorld";   // 이스케이프 시퀀스 사용 가능
string text3 = "\"Hello World\"";  // 따옴표 표현
```
- `@` 문자를 문자열 앞에 붙이면 내부에 있는 `\`를 이스케이프 시퀀스가 아니라 순수 문자로 취급할 수 있다.
```csharp
string text4 = @"\tHello\nWorld";  // \tHello\nWorld 출력
```
- char 형과는 달리 string은 '+' 연산을 지원하며 이 연산자를 이용해 문자열을 연결할 수 있다.
```csharp
string text5 = "Hello";
Console.WriteLine(text5 + " " + "World");  // Hello World 출력
```
****
<br>

### 불린(boolean)형 기본타입
|자료형|닷넷 형식|범위|
|---|---|---|
|bool|System.Boolean|true, false|

```csharp
bool isNumeric = false;
Console.WriteLine(isNumeric);  // False 출력
```

****
<br>

