### 델리게이트 (delegate)
> 메서드를 가리킬 수 있는 타입

```csharp
접근제한자 delegate 대상_메서드의_반환타입 식별자(...... 대상_메서드의_매개변수_목록 ......)
```
- 대상이 될 메서드의 반환 타입 및 매개변수 목록과 일치하는 델리게이트 타입을 정의한다.
- 참고로 C/C++ 에서는 델리게이트를 함수 포인터라고 한다.
<br>

▼ delegate 정의 방법    
<img src="./Images/4_11.png" width="700"/>
<br>

```csharp
namespace ConsoleApp1
{
    class Program
    {
        delegate int FuncDelegate(object arg);  // 델리게이트 타입 정의

        static void Main(string[] args)
        {
            Disk disk = new Disk();
            // 델리게이트 타입의 인스턴스 생성
            FuncDelegate cleanFunc = new FuncDelegate(disk.Clean);
        }

        public class Disk
        {
            public int Clean(object arg)
            {
                Console.WriteLine("작업 실행");
                return 0;
            }
        }
    }
}
```
<br>

▼ new 없이 대입 가능    
```csharp
FuncDelegate cleanFunc = new FuncDelegate(disk.Clean);
FuncDelegate workFunc = disk.Clean;  // 위와 동일 코드
```
<br>

▼ 메서드 호출    
```csharp
Disk disk = new Disk();
FuncDelegate cleanFunc = disk.Clean;

disk.Clean(null);   // Clean 메서드를 직접 호출
cleanFunc(null);    // 델리게이트 인스턴스를 통해 Clean 메서드를 호울
```
<br>

▼ 델리게이트 활용
```csharp
using System;

public class Mathematics
{
    delegate int CalcDelegate(int x, int y);

    static int Add(int x, int y) { return x + y; }
    static int Subtract(int x, int y) { return x - y; }
    static int Multiply(int x, int y) { return x * y; }
    static int Divide(int x, int y) { return x / y; }

    CalcDelegate[] methods;

    public Mathematics()
    {
        // static 메서드를 가리키는 델리게이트 배열 초기화
        methods = new CalcDelegate[]
        {
            Add, Subtract, Multiply, Divide,
        };
    }

    // methods 배열에 담긴 델리게이트를 opCode 인자에 따라 호출
    public void Calculate(char opCode, int operand1, int operand2)
    {
        switch (opCode)
        {
            case '+':
                Console.WriteLine("+: " + methods[0](operand1, operand2));
                break;
            case '-':
                Console.WriteLine("-: " + methods[1](operand1, operand2));
                break;
            case '*':
                Console.WriteLine("*: " + methods[2](operand1, operand2));
                break;
            case '/':
                Console.WriteLine("+: " + methods[3](operand1, operand2));
                break;
        }
    }
}

namespace ConsoleApp1
{
    class Program
    {
        // 3개의 매개변수를 받고 void를 반환하는 델리게이트 정의
        // 매개변수의 타입이 중요할 뿐 매개변수의 이름은 임의로 정할 수 있음
        delegate void WorkDelegate(char arg1, int arg2, int arg3);

        static void Main(string[] args)
        {
            Mathematics math = new Mathematics();
            WorkDelegate work = math.Calculate;

            work('+', 10, 5);    // 15 출력
            work('-', 10, 5);    // 5 출력
            work('*', 10, 5);    // 50 출력
            work('/', 10, 5);    // 2 출력
        }
    }
}
```
<br>

- 델리게이트는 타입이다.
    - 메서드의 반환값으로 델리게이트를 사용
    - 메서드의 인자로 델리게이트를 전달
    - 클래스의 멤버로 델리게이트를 정의
<br>

- 델리게이트는 메서드다.
    - 메서드의 반환값으로 메서드를 사용
    - 메서드의 인자로 메서드를 전달
    - 클래스의 멤버로 메서드를 정의

****
<br>
