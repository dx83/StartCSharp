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







****
<br>
