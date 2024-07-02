### 3) 프로퍼티 (property)
> 접근자/설정자 메서드를 대체

```csharp
class 클래스_명
{
    접근_제한자 타입 프로퍼티_명
    {
        접근_제한자 get
        {
            // ...... 코드 ......
            return 프로퍼티의_타입과_일치하는_유형의_표현식;
        }
        접근_제한자 set
        {
            // value라는 문맥 키워드를 사용해 설정하려는 값을 표현
        }
    }
}
```
<br>

▼ 프로퍼티 사용
```csharp
class Circle
{
    double pi = 3.14;

    public double Pi
    {
        get { return pi; }
        set { pi = value;
    }
}

class Program
{
    public static void Main()
    {
        Circle circle = new Circle();
        circle.Pi = 3.14159;           // 쓰기
        double piValue = circle.Pi;    // 읽기
    }
}
```
- 프로퍼티 정의에서는 매개변수가 없으므로 set 블록 내부에서만 사용할 수 있는 `value` 예약어가 있다.

<img src="./Images/4_6.png" width="500"/>

****
<br>
