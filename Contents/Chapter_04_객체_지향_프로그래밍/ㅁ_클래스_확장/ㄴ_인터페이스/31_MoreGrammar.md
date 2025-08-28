### 인터페이스 (interface)
> 추상 메서드만 0개 이상 담고 있는 추상 클래스로 봐도 무방하다.

```csharp
접근_제한자 interface 인터페이스_명
{
    메서드_선언;
}
```
- 인터페이스에는 메서드 선언을 0개 이상 포함할 수 있다.
- 관례적으로 인터페이스 이름에는 I 접두사를 붙인다.
<br>

▼ 다음 2 가지 표현은 몇가지 특징을 제외하고는 완전히 동일하다.
```csharp
abstract class DrawingObject
{
    public abstract void Draw();
    public abstract void Move(int offset);
}

interface IDrawingObject
{
    void Draw();
    void Move(int offset);
}
```
<br>

▼ 인터페이스는 클래스가 아니기 때문에 다중 상속이 허용된다.
```csharp
class Computer { }

// 메서드 시그니처만을 포함하고 있는 인터페이스
interface IMonitor
{
    void TurnOn();
}

interface IKeyboard { } // 비어 있는 인터페이스 정의 가능

// 클래스 상속과 함께 인터페이스로부터 다중 상속 가능
class Notebook : Computer, IMonitor, IKeyboard
{
    // 추상 메서드와 달리 override 예약어가 필요 없음
    public void TurnOn() { }
}
```
- 인터페이스의 메서드를 자식 클래스에서 구현할 때는 반드시 public 접근 제한자를 명시해야 한다.
<br>

▼ 인터페이스명을 직접 붙이는 경우 public 접근 제한자를 생략해도 된다.
```csharp
class Notebook : Computer, IMonitor, IKeyboard
{
    void IMonitor.TurnOn() { }
}
```
<br>

▼ 위 2 가지 메서드 구현 방삭은 호출하는 방법에 따른 차이점이 있다.
```csharp
Notebook notebook = new Notebook();
// public 접근 제한자를 사용한 경우
notebook.TurnOn();

// 인터페이스명을 명시한 경우
IMonitor mon = notebook as IMonitor;
mon.TurnOn();
```
- 인터페이스명을 명시한 경우 반드시 해당 인터페이스로 형변환해서 호출해야 한다.
<br>

▼ 프로퍼티
```csharp
interface IMonitor
{
    void TurnOn();
    int Inch { get; set; }  // 프로퍼티 get/set 포함
    int Width { get; }      // 하나만 포함하는 것도 가능
}

class Notebook : IMonitor
{
    public void TurnOn() { }

    int inch;
    public int Inch
    {
        get { return inch; }
        set { inch = value; }
    }

    int width;
    public int Width
    {
        get { return width; }
    }
}
```
- 인터페이스가 `메서드의 묶음`이고, C# 프로퍼티가 내부적으로 메서드로 구현되기 때문에 인터페이스에는 프로퍼티 역시 포함될 수 있다.

****
<br>
