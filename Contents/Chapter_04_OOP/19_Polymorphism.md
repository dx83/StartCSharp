## 4. 다형성 (Polymorphism)
****
<br> 

### 1) 메서드 오버라이드 (method override)
> 
- virtual 예약어
- override 예약어

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
    Mammal one = new Mammal();
    one.Move();     // 이동한다.

    Lion lion = new Lion();
    lion.Move();    // 네 발로 움직인다.

    Whale whale = new Whale();
    whale.Move();   // 수영한다.

    Human human = new Human();
    human.Move();   // 두 발로 움직인다.

    Mammal mm = lion;   // 부모 타입으로 형변환
    mm.Move();      // 이동한다.
}
```
- mm.Move() : mm에 Lion 인스턴스가 이동했기 때문에 Lion 클래스의 Move가 호촐되는 것이 의도된 동작이 이다.
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
    Mammal mm = lion;   // 부모 타입으로 형변환
    mm.Move();      // 네 발로 움직인다.
}
```

****
<br>
