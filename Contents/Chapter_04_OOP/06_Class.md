### 정적 메서드 (static method)
- 일반 메서드에 static 예약어를 사용해 정의
- new로 객체를 생성하는 것과 무관하게 [클래스이름].[정적메서드]형태로 호출

```csharp
class Person
{
    private static int CountOfInstance; // private 정적 필드
    public string _name;

    public Person(string name)
    {
        CountOfInstance++;
        _name = name;
    }

    public static void OutputCount()    // public 정적 메서드
    {
        Console.WriteLine(CountOfInstance); // 정적 메서드에서 정적 필드 접근
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person.OutputCount();   // 클래스 이름으로 정적 메서드 호출
                                // 0 출력
        Person person1 = new Person("홍길동");
        Person person2 = new Person("홍길순");

        Person.OutputCount();   // 2 출력
    }
}
```
- `Console.WriteLine`은 Console 클래스에 정의된 WriteLine 정적 메서드를 가리킨다.
```
정적 메서드 안에서는 인스턴스 멤버에 접근할 수 없다.
```

****
<br>

### Main 메서드
> 진입점 (entry point) : 프로그램에서 CPU에 의해 가장 처음 실행되는 명령어
- C#에서 최초로 실행될 메서드 규정
    - 메서드 이름은 반드시 Main    
    - 정적 메서드
    - Main 메서드가 정의된 클래스의 이름은 제한 없음<br>   2개 이상의 클래스에서 Main 메서드를 정의하고 있다면 C# 컴파일러에게 클래스를 지정해야 함
    - Main 메서드의 반환값은 void 또는 int만 허용됨
    - Main 메서드의 매개변수는 없거나 string 배열만 허용됨
```
이 규칙을 만족하는 메서드를 정의하면 C# 컴파일러는 자동으로 그 메서드를 시작점으로 선택해 EXE 파일을 생성한다.
```
<br>

▼ 반환값은 대개 EXE 프로그램의 실행 결과에 대한 오류 여부를 판단하는 데 사용된다.
```csharp
class Program
{
    static int Main(string[] args)
    {
        return 0;
    }
}
```
```
C:\temp> ConsoleApp1.exe

C:\temp> echo %ERRORLEVEL%
0
```
- Main 메서드에서 0 이외의 다른 값을 반환하면 `%ERRORLEVEL%` 값 역시 그에 따라 바뀐다.
- 일반적으로 프로그램이 정상적으로 실행돼 종료하면 0을 반환하고, 오류가 발생한 경우에는 오류의 종류에 따라 숫자 값을 정해서 반환한다.
<br>

▼ Main 메서드의 인자로 허용되는 string 배열
```csharp
class Program
{
    static void Main(string[] args)
    {
        if (args.Length < 2)
        {
            return;
        }

        Console.WriteLine(args[0]);
        Console.WriteLine(args[1]);
    }
}
```
```
c:\temp> ConsoleApp1.exe Hello World
Hello
World
```

****
<br>
