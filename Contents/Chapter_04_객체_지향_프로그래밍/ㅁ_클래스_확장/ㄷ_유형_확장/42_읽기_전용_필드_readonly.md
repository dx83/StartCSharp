### 2) 멤버 유형 확장
> 클래스에서 기본적으로 제공되는 멤버 유형은 필드와 메서드다.
- 프로퍼티는 메서드의 변형, 델리게이트는 중첩 클래스의 변형이라고 할 수 있다.
****
<br>

### 읽기 전용 필드 (readonly field)
> readonly 예약어 : 클래스 내부에서도 읽기만 가능한 필드 정의
<br>

```csharp
public class Scheduler
{
    readonly int second = 1;    // 읽기 전용 필드 정의 및 값을 대입
    readonly string name;       // 읽기 전용 필드 정의

    public Scheduler()
    {
        this.name = "일정관리";  // 읽기 전용 필드는 생성자에서도 대입 가능
    }

    public void Run()
    {
        this.second = 5;        // 컴파일 에러, 일반 메서드에서 값을 대입할 수 없다.
    }
}
```
- 읽기 전용 필드는 변수를 정의할 때와 생성자 내부를 제외하고는 그 값을 바꾸는 시도를 할 수 없다.
<br>

> 가변 객체 (mutable object) : 객체의 상태가 변할 수 있는 객체    
> 불변 객체 (immutable object) : 객체의 상태가 한번 지정되면 다시 바뀔 수 없는 객체

▼ 불변 타입
```csharp
public class Point
{
    int x, y;

    public int X { get { return x; } }
    public int Y { get { return y; } }

    public Point(int x, int y)
    {
        this.x = x;
        this.y = y;
    }
}
// 출력문
Point pt1 = new Point(5, 10);
Point pt2 = new Point(pt1.X + 1, pt1.Y + 1);

Console.WriteLine(pt1.X + ", " + pt1.Y);    // 5, 10
Console.WriteLine(pt2.X + ", " + pt2.Y);    // 6, 11
```
- 기본 pt1 값에서 X, Y 방향으로 1씩 증가한 상태를 얻고 싶은데, 내부 값을 변경할 수 없으므로 새롭게 별도의 Point 객체를 만들어야 한다.
- 즉, 불변이므로 객체의 내부 값을 변경할 수 없는 것이다.
<br>

▼ 불변 타입을 만들 때 readonly 예약어가 도움될 수 있다.
```csharp
public class Point
{
    public readonly int X;
    public readonly int Y;

    public Point(int x, int y)
    {
        this.X = x;
        this.Y = y;
    }
}
```
- Point 클래스가 외부적으로는 불변이라고 약속될 수 있지만 내부적으로 불변 상태가 보장되고 있는 것이 아니기 때문이다.
- 유지보수 중 나올 실수를 미연에 방지하기 위해 readonly 에약어를 X, Y 필드에 적용할 수 있다.

****
<br>
