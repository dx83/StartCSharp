## 3. 상속 (Inheritance)
> 공통적인 특징을 정의 하는 부모 클래스와 부모의 기능을 물려받는 자식 클래스의 관계를 상속이라 한다.
- 부모 클래스 (parent class) : 기반 (base) 클래스, 슈퍼 (super) 클래스
  - 조상 (ancestor) 클래스 : 부모의 부모 클래스
- 자식 클래스 (child class) : 파생 (derived) 클래스, 서브 (sub) 클래스
  - 자손 (descendant) 클래스 : 자식의 자식 클래스
<br>

▼ 상속을 이용한 클래스 정의
```csharp
public class Computer
{
    bool powerOn;       // private
    public void Boot() { }
    public void Shutdown() { }
    public void Reset() { }
}

public class Notebook : Computer
{
    bool fingerScan;    // Notebook 타입에 필요한 고유 멤버만 추가
    public bool HasFingerScanDevice() { return fingerScan; }

    public void CloseLid()
    {
        Shutdown();     // Notebook에 추가된 메서드 내에서 부모의 메서드 호출
    }
}

public class Desktop : Computer
{
}

public class Netbook : Computer
{
}

static void Main(string[] args)
{
    Notebook noteBook = new Notebook();
    noteBook.Boot();    // Notebook 인스턴스에 대해 부모의 메서드 호출
}
```
- 콜론(:)을 이용해 부모 클래스의 기능을 상속받는다.
- 상속받은 클래스는 부모의 속성과 행위를 접근 제한자 규칙에 따라 외부에 제공한다.
- 자식 클래스일지라도 부모의 private 멤버에 접근할 수 없다.
<br>

▼ protected : 외부에서의 접근은 차단하면서도 자식에게는 허용
```csharp
public class Computer
{
    protected powerOn;
    // ---- 생략 ----
}

public class Notebook : Computer
{
    // ---- 생략 ----
    public void CloseLid()
    {
        if (powerOn == true)  // 접근 가능
        {
            Shutdown();
        }
    }
}
```
<br>

▼ sealed 예약어 : 상속 제한
```csharp
sealed class Pen
{
}

public class ElectricPen : Pen  // 컴파일 에러
{
}
```
<br>


▼ C#에서는 단일 상속 (single inheritance)만 지원한다.
```csharp
class Computer {}
class Monitor {}

class Notebook : Computer, Monitor  // 컴파일 에러
{
}
```
- C#은 `계층 상속`은 가능하지만 동시에 둘 이상의 부모 클래스로부터 다중 상속 (multiple inheritance)은 허용하지 않는다.

****
<br>
