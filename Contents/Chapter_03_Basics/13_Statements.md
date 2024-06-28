### while 문
▼ while 문 문법
```csharp
while (조건식)
    구문;

while (조건식)  구문;
```
- 조건식을 평가하고 참이면 구문을 실행한다. 실행 순서는 `조건식` -> `구문` -> `조건식` -> `구문` ●●●●●● 으로 조건식이 거짓이 될 때까지 무한 반복된다.
<br>

```csharp
int sum = 0;
int n = 1;

while (n <= 1000)
{
    if (n % 2 == 0)
    {
        sum += n;
    }
    n++;
}
Console.WriteLine(sum); // 250500 출력
```
▼ 위 코드를 for 문으로 작성
```csharp
int sum = 0;
for (int n = 1; n <= 1000; n++)
{
    if (n % 2 == 0)
    {
        sum += n;
    }
}
Console.WriteLine(sum); // 250500 출력
```
****
<br>

### do/while 문
▼ do/while 문 문법
```csharp
do
    구문;
while (조건식);

do 구문; while (조건식);
```
- 먼저 구문을 실행하고 조건식을 평가한다. 실행 순서는 `구문` -> `조건식` -> `구문` -> `조건식` ●●●●●● 으로 조건식이 거짓이 될 때까지 무한 반복된다.
- while 문과는 다르게 do/while 문은 반복 실행돼야할 구문이 최소 한 번은 실행된다.
<br>

▼ 위 코드를 do/while 문으로 작성
```csharp
int sum = 0;
int n = 0;      // 초깃값이 0으로 변경됨
do
{
    if (n % 2 == 0) sum += n;
} while (++n <= 1000);
Console.WriteLine(sum); // 250500 출력
```
****
<br>
