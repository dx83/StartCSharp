### 클래스 간의 형변환

```csharp
public class Currency
{
    decimal money;
    public decimal Money { get { return money; } }

    public Currency(decimal money)
    {
        this.money = money;
    }
}

public class Won : Currency
{
    public Won(decimal money) : base(money) { }

    public override string ToString()
    {
        return Money + "Won";
    }
}

public class Dollar : Currency
{
    public Dollar(decimal money) : base(money) { }

    // explicit operator : 형변환 연산자를 사용해야 한다.
    public static explicit operator Won(Dollar dollar) // 명시적 형변환만 가능
    {
        return new Won(dollar.Money * 1000m);
    }

    public override string ToString()
    {
        return Money + "Dollor";
    }
}

public class Yen : Currency
{
    public Yen(decimal money) : base(money) { }

    // implicit operator : 암시적 형변환
    public static implicit operator Won(Yen yen)  // 명시적 형변환도 가능
    {
        return new Won(yen.Money * 9m);           // 1엔당 9원으로 가정
    }

    public override string ToString()
    {
        return Money + "Yen";
    }
}
// 출력문
Yen yen = new Yen(100);
Won won1 = yen;             // 암시적(implicit) 형변환 가능
Won won2 = (Won)yen;        // 명시적(explicit) 현변환 가능

Console.WriteLine(won1);    // 900Won

Dollar dollar = new Dollar(1);
Won won3 = dollar;          // 암시적(implicit) 형변환 불가능 (컴파일 에러)
Won won4 = (Won)dollar;     // 명시적(explicit) 형변환만 가능

Console.WriteLine(won4);    // 1000Won
```

****
<br>
