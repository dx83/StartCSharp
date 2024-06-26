## 2. 형변환 (Type Conversion)
> 형변환 연산자 (cast operator) : ()

#### 암시적 형변환 (Implicit conversion) : 범위가 작은 데이터 타입에서 더 큰 범위의 타입으로 형변환하는 것
```csharp
byte b = 250;     // short보다 작은 데이터 타입
short s = b;      // 암시적 형변환

short s = 100;
byte b = s;       // 컴파일 에러
```
<br>

#### 명시적 형변환 (Explicit conversion)
- 큰 데이터 타입에서 작은 데이터 타입으로 형변환
- 개발자가 의도한 형변환
```csharp
ushort u = 65;
char c = u;            // 컴파일 에러
char c = (char)u;      // 명시적 형변환
Console.WriteLine(c);  // A 출력

int n = 40000;         // short보다 큰 데이터 타입
short s = (short)n;    // 명시적 형변환
Console.WriteLine(s);  // -25536 출력
```
****
<br>
