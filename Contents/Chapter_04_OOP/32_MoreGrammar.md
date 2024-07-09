### 상속으로서의 인터페이스
> 인터페이스의 가장 기본적인 역할은 상속이다.
> 구현 코드를 이어받는 것은 아니지만 메서드의 묶음에 대한 정의를 이어받는다.
```csharp
interface IDrawingObject
{
    void Draw();
}

class Line : IDrawingObject
{
    public void Draw() { Console.WriteLine("Line"); }
}

class Rectangle : IDrawingObject
{
    public void Draw() { Console.WriteLine("Rectangle"); }
}

static void Unit1()
{
    // 인터페이스 자체는 new로 인스턴스화할 수 없지만, 인터페이스 배열은 가능하다.
    IDrawingObject[] instances = new IDrawingObject[] { new Line(), new Rectangle() };

    foreach (IDrawingObject item in instances)
    {
        item.Draw();    // 인터페이스를 상속받은 객체의 Draw 메서드가 호출됨
    }

    // 자식 클래스로부터 암시적 형변환 가능
    IDrawingObject instance = new Line();
    instance.Draw();
}
// 출력 결과
Line
Rectangle
Line
```

****
<br>

### 인터페이스 자체로 의미 부여
> 비어 있는 인터페이스를 상속받는 것으로도 의미가 부여될 수 있다.
```csharp
// ToString을 재정의한 클래스에만 사용될 빈 인터페이스 정의
interface IObjectToString { }

class Object { }

class Person : IObjectToString  // ToString을 재정의했다는 의미로 인터페이스 상속
{
    string name;
    public Person(string name)
    {
        this.name = name;
    }

    public override string ToString()
    {
        return "Person: " + this.name;
    }
}

private static void DisplayObject(object obj)
{
    if (obj is IObjectToString) // 해당 인터페이스로 형변환이 가능 유무
    {
        Console.WriteLine(obj.ToString());
    }
}

static void Unit2()
{
    DisplayObject(new Object());
    DisplayObject(new Person("홍길동"));
}
// 출력 결과
Person: 홍길동
```
- 인터페이스로의 형변환 가능 유무를 활용

****
<br>
