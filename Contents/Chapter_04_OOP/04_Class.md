### 3) 생성자 (constructor)
> 생성자는 이름이 `클래스명`과 동일하며 `반환타입`을 명시하지 않는다    
> 는 점을 제외하고 메서드를 정의하는 방법을 따른다.
- 생성자를 줄여서 ctor 이라고 부른다.

```csharp
class 클래스_명
{
    접근_제한자 클래스_명(타입 매개변수명, ......)
    {
    }
}
```
- new 로 객체를 생성하는 시점에 생성자가 실행된다.
- 따라서 생성자는 객체를 생성하는 시점에 실행돼야 할 코드를 담을 수 있다.
<br>

```
생성자를 명시적으로 정의하지 않았다면 C# 컴파일러는 빈 생성자를 클래스에 집어넣고 컴파일한다.
```
- new를 실행하면 언제나 해당 객체의 생성자가 함께 실행된다.

****
<br>

```csharp
class Program
{
    static void Main(string[] args)
    {
        Person person = new Person("영희");
        person.WriteName();  // 출력 => Name: 영희
    }
}

class Person
{
    string _name;
    int _age;

    public Person()  // 가본 생성자 (default constructor)
    {
    }

    public Person(string name)  // 매개변수를 갖는 생성자
    {
        _name = name;
    }

    public Person(string name, int age)  // 각 생성자를 상황에 따라 골라 사용
    {
        _name = name;
        _age = age;
    }

    public void WriteName()
    {
        Console.WriteLine("Name: " + _name);
        Console.WriteLine("Age: " + _age);
    }
}
```
- 매개변수가 하나도 없는 생성자를 `기본 생성자`라고 한다.
- 일반적으로 매개변수를 갖는 생성자를 통해 외부로부터 객체를 초기화하는 값을 입력받는다.
- 생성자를 여러개 정의하는 것도 가능하다.

****
<br>

### 4) 종료자 (finalizer)
> 종료자는 이름이 ~(틸드: tilde)를 접두사로 쓰는 `클래스명`과 동일하며 어떤 인자나 반환값도 갖지 않는다.
- 종료자가 실행되는 시점은 예측할 수 없다.
- 종료자를 줄여서 dtor 이라고 부른다.

```csharp
class 클래스_명
{
    ~클래스_명()
    {
        // ......[자원 해제를 위한 코드]......
    }
}
```
```csharp
class Book
{
    public Book()   // 생성자
    {
    }

    ~Book()         // 종료자
    {
    }
}
```
<br>

- C#에는 객체를 의도적으로 제거하는 기능이 없다.
- CLR에서는 가비지 수집기 (Garbage Collector, GC)라는 개념을 도입해서 해결하고 있다.

> 모든 참조형 변수를 생성할 때 GC는 요청된 변수의 타입이 요구하는 메모리를 "관리 힙"이라는 곳에 할당한다.    
> 프로그램이 실행되고 있는 중에 GC는 스스로 적절하다고 판단되는 시점이 오면 관리 힙을 청소하는 작업을 한다.    
> 이떄 어떤 객체가 더는 사용되고 있지 않다면 객체의 데이터를 해제해 버린다.
- C#의 참조형 변수가 가리키는 객체는 GC가 호출돼야 종료자가 호출된다.
- GC가 불확실한 시점에 메모리 정리를 한다.

```
닷넷이 괸라하지 않는 시스템 지원을 얻은 경우에만 종료자를 정의해야 한다.
```

****
<br>
