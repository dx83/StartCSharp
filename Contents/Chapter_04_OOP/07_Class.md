### 정적 생성자 (static constructor)
> 기본 생성자에 static 예약어 사용    
> 클래스에 단 한 개만 존재할 수 있고, 주로 정적 멤버를 초기화하는 기능    
> 형식 이니셜라이저 (type initializer) 라고도 한다.
- 정적 생성자를 줄여서 cctor 라고 부른다.

```csharp
class 클래스_명
{
    static 클래스_명()
    {
        // 단 한번, 가장 최초로 실행될 초기화 코드
    }
}
```
- 단 한 개만 정의할 수 있고 매개변수를 포함할 수 없다.
<br>


```csharp
class Person
{
    public static Person President;        // = new Person("대통령") 초기화 코드를
                                           // 정적 생성자로 이전
    public string _name;

    private Person(string name)
    {
        _name = name;
    }

    static Person()                        // 정적 생성자
    {
        President = new Person("대통령");  // 정적 필드 초기화
    }
}
```
- 정적 필드에 초기화 코드도 포함돼 있고, 동시에 정적 생성자도 정의해 뒀다면 C# 컴파일러는 사용자가 정의한 정적 생성자의 코드와 초기화 코드를 자동으로 병합해서 정의한다.
- 이 규칙은 인스턴스 필드와 기본 생성자 간에도 동일하게 적용된다.

```
정적 생성자는 클래스의 어떤 멤버든 최초로 접근하는 시점에 단 한 번만 실행.    
정적 멤버를 처음 호출할 경우 또는 인스턴스 생성자를 통해 객체가 만들어지는 시점이 되면 우선적으로 실행된다.
```
<br>

▼ 실행 예제
```csharp
class Person
{
    public string _name;

    public Person(string name)
    {
        _name = name;
        Console.WriteLine("ctor 실행");
    }

    static Person()
    {
        Console.WriteLine("cctor 실행");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person1 = new Person("");
        Console.WriteLine("----------");
        Person person2 = new Person("");
    }
}
// 출력 결과
cctor 실행
ctor 실행
----------
ctor 실행
```

****
<br>
