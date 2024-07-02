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

