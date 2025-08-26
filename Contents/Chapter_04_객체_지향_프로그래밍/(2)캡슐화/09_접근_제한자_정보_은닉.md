## 2. 캡슐화 (Encapsulation)
> 객체의 외부에서 알아야 할 필요가 없는 내부 멤버를 숨기는 것을 캡슐화라고 한다.    
> 클래스는 객체의 역할을 추상화한다.
****
<br>

### 1) 접근 제한자 (access modifier)
▼ 접근 제한자 유형
|접근 제한자|설명|
|---|---|
|private|내부에서만 접근을 허용한다.|
|protected|내부에서의 접근과 함께 파생 클래스에서만 접근을 허용한다.|
|public|내부 및 파생 클래스에서의 접근뿐만 아니라 외부에서도 접근을 허용한다.|
|internal|동일한 어셈블리 내에서는 public에 준한 접근을 허용한다. 다른 어셈블리에서는 접근할 수 없다.|
|internal protected<br>protected internal|동일 어셈블리 내에서 정의된 클래스이거나 다른 어셈블리라면 파생 클래스인 경우에 한해 접근을 허용한다.|

- 적용 대상 : 클래스, 구조체, 인터페이스
- 일반 클래스 정의는 public, internal만 사용 가능
- 클래스 내부에 정의되는 또 다른 클래스 (중첩 클래스)에는 5가지 접근 제한자 모두 사용 가능
<br>

- class 정의에서 접근 제한자를 생략한 경우 기본적으로 internal로 설정
- class 내부의 멤버에 대해서는 private으로 설정
<br>

```
객체지향 프로그램밍의 관점에서 접근 제한자는 정보 은닉에 중요한 역할을 한다.
```

****
<br>

### 2) 정보 은닉 (information hiding)
> 클래스에서 멤버 변수를 외부에서 직접 접근할 수 없게 만드는 것이 정보 은닉이다.

▼ 접근자 메서드 (getter), 설정자 메서드 (setter)
```csharp
class Circle
{
    double pi = 3.14;

    public double GetPi()            // 접근자 메서드
    {
        return pi;
    }

    public void SetPi(double value)  // 설정자 메서드
    {
        pi = value;
    }
}

class Program
{
    public static void Main()
    {
        Circle circle = new Circle();
        circle.SetPi(3.14159);              // 쓰기
        double piValue = circle.GetPi();    // 읽기
    }
}
```
- 설정자 메서드를 제거한면 읽기만 가능 (read-only)하도록 만들 수 있다.
<br>

▼ 멤버 변수를 public이 아닌 접근자/설정자 메서드를 사용하는 이유
```
향후 코드에 대한 유지보수 용이    
접근자/설정자 메서드에 진단 목적의 코드를 넣어서 디버거(debugger)를 할 수 있다.
```

****
<br>
