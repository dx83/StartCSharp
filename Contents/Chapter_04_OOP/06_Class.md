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

****
<br>
