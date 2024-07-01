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
