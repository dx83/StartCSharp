### 1) 형변환
> 암시적 형변환 (Implicit conversions)    
> 특수화 타입의 변수에서 일반화된 타입의 변수로 값이 대입되는 경우

```csharp
short a = 100;
int b = a;          // 암시적 형변환
```
<br>

> 명시적 형변환 (Explicit conversions)    
> 일반화 타입의 변수에서 특수화된 타입의 변수로 값이 대입되는 경우

```csharp
int c = 100;
short d = (short)c; // 명시적 형변환
```
<br>

▼ 이 규칙은 class로 정의된 타입의 부모/자식 관계에서도 동일하게 적용된다.

<img src="./Images/4_7.png" width="500"/>

```csharp
Notebook noteBook = new Notebook();

Computer pc1 = noteBook;    // 암시적 형변환 가능
pc1.Boot();
pc1.Shutdown();
```
- Notebook (특수화 타입) 인스턴스를 Computer (일반화 타입)의 변수로 대입하는 경우 암시적 형변환 가능
<br>

```csharp
Computer pc = new Computer();
Notebook nb = (Notebook)pc;  // 명시적 형변화, 컴파일은 가능
// 실행하면 오류 발생
```
- 반대로 부모 클래스 (일반화 타입)의 인스턴스를 자식 클래스 (특수화 타입)의 변수로 대입하는 것은 암시적 형변환이 불가능하다.
- 캐스팅 연산자를 사용해 명시적 형변환을 할 수 있지만 실행하면 오류가 발생한다.
<br>

▼ 컴파일 단계에서 명시적 형변환을 허용한 이유
```csharp
Notebook noteBook = new Notebook();
Computer pc1 = noteBook;            // 부모 타입으로 암시적 형변환

Notebook note2 = (Notebook)pc1;     // 다시 본래 타입으로 명시적 형변환
note2.CloseLid();
```
- 개발자의 의도가 있을 수 있다.
<br>

▼ 암시적 형변환 활용
```csharp
public class DeviceManager
{
    public void TurnOff(Computer device)
    {
        device.Shutdown();
    }
}

static void Main(string[] args)
{
    Computer[] machines =
    new Computer[] { new Notebook(), new Desktop(), new Netbook() };  // 암시적 형변환

    DeviceManager manager = new DeviceManager();

    foreach (Computer device in machines)
    {
        manager.TurnOff(device);
    }
}
```
- 암시적 형변환으로 각 자식 클래스의 인스턴스를 부모 객체의 배열에 담을 수 있다.

****
<br>
