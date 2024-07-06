### base를 이용한 메서드 재사용
> 부모와 중복되는 동작을 base로 호출하여 중복 코드가 생기지 않도록 한다.

```csharp
public class Computer
{
    virtual public void Boot()
    {
        Console.WriteLine("메인보드 켜기");
    }
}

public class Notebook : Computer
{
    public override void Boot()
    {
        base.Boot();
        Console.WriteLine("액정 화면 켜기");
    }
}
```
<br>

```
부모 클래스를 만들었던 개발자가 자식 클래스에서 base를 호출하거나 호출하지 못하게 강제할 방법이 없다.
따라서 상위 클래스의 도움말을 확인해야 하고, 상위 클래스 개발자라면 도움말을 기록해야 한다.
```

****
<br>

### objecct 기본 메서드 확장
▼ object의 기본 메서드 3 가지
```csharp
public class Object
{
    public virtual bool Equals(object obj);
    public virtual int GetHashCode();
    public virtual string ToString();
}
```
<br>

▼ ToString 재정의
```csharp
public class Point
{
    int x, y;

    public Point(int x, int y)
    {
        this.x = x;
        this.y = y;
    }

    public override string ToString()
    {
        return "X: " + x + "y: " + y;
    }
}

// 출력문
Point pt = new Point(5, 10);
Console.WriteLine(pt.ToString());    // X: 5, y: 10
```
- 로그를 남기거나 디버깅할 때 ToString에서 반환된 결과가 유용하게 쓰일 수 있다.
<br>

> 특정 객체를 고유하게 식별할 수 있는 값을 `키(key)` 값이라고 한다.



****
<br>
