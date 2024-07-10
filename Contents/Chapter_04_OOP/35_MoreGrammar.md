### 느슨한 결합 (loose coupling)
> 클래스 간에 구현 타입의 정보 없이 인터페이스 등의 방법을 이용해 상호 간에 맺은 계약만으로 동작하는 것을 의미한다.
<br>

▼ 강력한 결합 (tight coupling)
```csharp
class Computer
{
    public void TurnOn()
    {
        Console.WriteLine("Computer: TurnOn");
    }
}

class Monitor
{
    public void TurnOn()
    {
        Console.WriteLine("Monitor: TurnOn");
    }
}

class Switch
{
    public void PowerOn(Computer machine)   // Computer 타입을 직접 사용한다.
    {
        machine.TurnOn();
    }
}
```
- Computer와 Switch 타입은 강력한 결합 관계를 맺고 있다.
- Switch에 Monitor를 연결하려면
  - Computer에서 Monitor로 코드를 바꿔야 할까?
  - Monitor를 매개변수로 받는 중복 메서드를 하나 더 만들어야 할까?
<br>

▼ 강력한 결합의 보완책으로 나온 인터페이스를 사용한 느슨한 결합
```csharp
interface IPower
{
    void TurnOn();
}

class Computer : IPower
{
    public void TurnOn()
    {
        Console.WriteLine("Computer: TurnOn");
    }
}

class Monitor : IPower
{
    public void TurnOn()
    {
        Console.WriteLine("Monitor: TurnOn");
    }
}

class Switch
{
    public void PowerOn(IPower machine) // 특정 타입 -> 인터페이스
    {
        machine.TurnOn();
    }
}

// 출력문
Switch sw = new Switch();
sw.PowerOn(new Computer());
sw.PowerOn(new Monitor());

// 출력 결과
Computer: TurnOn
Monitor: TurnOn
```
- 새로운 타입을 정의하더라도 IPower 인터페이스를 상속받았다면 내부 코드를 변경할 필요가 없다.

```
구현 클래스를 Concrete 타입이라고 한다. (인터페이스나 추상 클래스 아닌 모든 클래스가 이에 해당) 
```
****
<br>
