## 5. C#의 클래스 확장
****
<br> 

### 1) 타입 유형 확장
****
<br> 

### 중첩 클래스 (nested class)
> 클래스 내부에 또 다른 클래스를 정의하는 것

```csharp
class HardDisk          // internal
{
    class Platter { }   // private
    class Head { }      // private

    Platter[] platter;
    Head head;
}

class Software          // internal
{
    void Excute()
    {
        HardDisk hd = new HardDisk();   // internal

        // 보호 수준 때문에 컴파일 에러
        HardDisk.Platter pt = new HardDisk.Platter();
    }
}
```

****
<br> 

### 추상 클래스 (abstract class)
> 부모 클래스의 인스턴스를 생성하지 못하게 하면서 특정 메서드에 대해 자식들이 반드시 재정의하도록 강제한다.
- 추상 클래스 (abstract class)
  - 추상 메서드를 가질 수 있다.
  - new를 사용해 인스턴스를 만들 수 없다.
<br>

- 추상 메서드 (abstract method)
  - 추상 클래스 안에서만 선언할 수 있다.
  - 코드 없는 가상 메서드
  - 반드시 자식 클래스에서 재정의해야 하므로 `private`로 지정할 수 없다.
<br>

```csharp
class Point
{
    int x, y;

    public Point(int x, int y)
    {
        this.x = x;
        this.y = y;
    }

    public override string ToString()
    {
        return "X: " + x + ", Y: " + y;
    }
}

abstract class DrawingObject        // 추상클래스
{
    public abstract void Draw();    // 추상 메서드

    // 일반 메서드도 정의 가능
    public void Move() { Console.WriteLine("Move"); }
}

class Line : DrawingObject  // 추상 클래스를 상속
{
    Point pt1, pt2;
    public Line(Point pt1, Point pt2)
    {
        this.pt1 = pt1;
        this.pt2 = pt2;
    }

    // 추상 클래스의 추상 메서드를 반드시 정의해야 함
    public override void Draw()
    {
        Console.WriteLine("Line " + pt1.ToString() + " ~ " + pt2.ToString());
    }
}

// 출력문
DrawingObject Line = new Line(new Point(10, 10), new Point(20, 20));
// 다형성에 따라 Line.Draw가 호출됨
Line.Draw();    // Line X: 10, Y: 10 ~ X: 20, Y: 20 출력
```

****
<br> 
