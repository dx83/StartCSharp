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



****
<br>
