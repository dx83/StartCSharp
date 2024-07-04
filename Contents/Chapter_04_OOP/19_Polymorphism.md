## 4. 다형성 (Polymorphism)
****
<br> 

### 1) 메서드 오버라이드 (method override)
> 
- 가상 메서드 (virtual method)
    - virtual 예약어 : 부모 클래스의 메서드에 적용
    - override 예약어 : 자식 클래스의 메서드에 적용

```csharp
class Mammal
{
    public void Move()
    {
        Console.WriteLine("이동한다.");
    }
}

class Lion : Mammal
{
    public void Move()
    {
        Console.WriteLine("네 발로 움직인다.");
    }
}

class Whale : Mammal
{
    public void Move()
    {
        Console.WriteLine("수영한다.");
    }

}

class Human : Mammal
{
    public void Move()
    {
        Console.WriteLine("두 발로 움직인다.");
    }
}

static void Main(string[] args)
{
    Mammal mm = new Mammal();
    mm.Move();     // 이동한다.

    Lion lion = new Lion();
    lion.Move();    // 네 발로 움직인다.

    Whale whale = new Whale();
    whale.Move();   // 수영한다.

    Human human = new Human();
    human.Move();   // 두 발로 움직인다.

    Mammal m1 = lion;   // 부모 타입으로 형변환
    m1.Move();      // 이동한다. => 원하는 동작이 아님
}
```
- m1.Move() : mm에 Lion 인스턴스가 이동했기 때문에 Lion 클래스의 Move가 호촐되는 것이 의도된 동작이다.

▼ virtual, override 예약어 사용
```csharp
class Mammal
{
    virtual public void Move()
    {
        Console.WriteLine("이동한다.");
    }
}

class Lion : Mammal
{
    override public void Move()
    {
        Console.WriteLine("네 발로 움직인다.");
    }
}

class Whale : Mammal
{
    override public void Move()
    {
        Console.WriteLine("수영한다.");
    }

}

class Human : Mammal
{
    override public void Move()
    {
        Console.WriteLine("두 발로 움직인다.");
    }
}

static void Main(string[] args)
{
    // ---- 생략 ----
    Mammal m1 = lion;   // 부모 타입으로 형변환
    m1.Move();      // 네 발로 움직인다.

    Mammal m2 = human;
    m2.Move();      // 두 발로 움직인다.
}
```
<br>

▼ new 예약어 : 단순히 자식 클래스에서 동일한 이름의 메서드가 필요한 경우
```csharp
class Mammal
{
    new public void Move()
    {
        Console.WriteLine("이동한다.");
    }
}

class Lion : Mammal
{
    new public void Move()
    {
        Console.WriteLine("네 발로 움직인다.");
    }
}

class Whale : Mammal
{
    new public void Move()
    {
        Console.WriteLine("수영한다.");
    }

}

class Human : Mammal
{
    new public void Move()
    {
        Console.WriteLine("두 발로 움직인다.");
    }
}
```
<br>

```
부모와 자식 클래스에서 동일한 이름의 메서드를 사용하려면 2가지 중 하나를 선택해야 한다.
1 virtual/override : 메서드 오버라이드
2 new : 자식 클래스에서 단순히 동일한 이름의 메서드가 필요한 경우
```
****
<br>
