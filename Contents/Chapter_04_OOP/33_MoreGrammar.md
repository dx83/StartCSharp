### 인터페이스를 이용한 콜백 구현
> 인터페이스에 포함된 메서드는 상속된 클래스에서 반드시 구현한다는 보장이 있다.
<br>

▼ 콜백 구현
```csharp
interface ISource
{
    // 콜백용으로 사용될 메서드를 인터페이스로 분리한다.
    int GetResult();
}

class Source : ISource
{
    public int GetResult() { return 10; }

    public void Test()
    {
        Target target = new Target();
        target.Do(this);
    }
}

class Target
{
    // Source 타입이 아닌 ISource 인터페이스를 받는다.
    public void Do(ISource obj)
    {
        Console.WriteLine(obj.GetResult()); // 콜백 메서드 호출
    }
}
```
- 인터페이스를 이용한 콜백 : 하나의 타입에서 여러 가지 메서드를 담을 수 있다.
- 델리게이트를 이용한 콜백 : 한 번의 호출로 다중으로 등록된 콜백 메서드를 호출할 수 있다.
<br>

▼ IComparer 인터페이스를 이용한 Array.Sort 사용
```csharp
using System;
using System.Collections;  // IComparer가 정의된 네임스페이스 사용

// IComparer를 상속받는 타입 정의
class IntegerCompare : IComparer
{
    // IComparer 인터페이스의 Compare 메서드를 구현
    // 이 메서드는 Array.Sort 메서드 내에서 콜백으로 호출됨
    public int Compare(object x, object y)
    {
        int xValue = (int)x;
        int yValue = (int)y;

        if (xValue > yValue) return -1; // 내림차순 정렬이 되도록 -1을 반환
        else if (xValue == yValue) return 0;

        return 1;
    }
}

class Program
{
    static void Unit1()
    {
        int[] intArray = new int[] { 1, 2, 3, 4, 5 };

        // 메서드 원형 public static void Sort(Array array, IComparer comparer)
        // IComparer를 상속받은 IntegerCompare 인스턴스 전달
        Array.Sort(intArray, new IntegerCompare());
        foreach (int item in intArray)
        {
            Console.Write(item + "\t");  // 5  4  3  2  1
        }
    }
}
```
- IComparer를 구현한 인스턴스를 인자로 넘기면 Array.Sort는 요소의 값을 비교하기 위해 IComparer.Compare 메서드에 2개의 값을 전달한다.
- Compare 메서드는 Array.Sort 메서드가 한번 호출될 때 내부에서는 요소의 수에 비례해 여러번에 걸쳐 호출된다.

****
<br>
