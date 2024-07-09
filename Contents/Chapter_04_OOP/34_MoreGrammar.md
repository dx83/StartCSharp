### IEnumerable 인터페이스
> 인터페이스에 정의된 유일한 메서드인 GetEnumerator는 `열거자(enumerator)`라고 하는 객체를 반환하도록 약속돼 있다.
```csharp
// 닷넷 프레임워크에 정의돼 있는 IEnumerable 인터페이스
public interface IEnumerable
{
    IEnumerator GetEnumerator();
}
// 닷넷 프레임워크에 정의돼 있는 IEnumerator 인터페이스
public interface IEnumerator
{
    object Current { get; } // 현재 요소를 반환하도록 약속된 get 프로퍼티
    bool MoveNext();        // 다음 순서의 요소로 넘어가도록 약속된 메서드
    void Reset();           // 열거 순서를 처음으로 되돌릴 때 호출하면 되는 메서드
}
```
<br>

▼ IEnumerable 인터페이스를 구현한 System.Array
```csharp
int[] intArray = new int[] { 1, 2, 3, 4, 5 };

IEnumerator enumerator = intArray.GetEnumerator();

// 더 이상 열거할 수 없을 때 false를 반환
while (enumerator.MoveNext())
{
    Console.Write(enumerator.Current + "\t");
}
// 출력문
1  2  3  4  5

// foreach 문을 사용하면 편리
foreach (int elem in intArray)
{
    Console.Write(elem + "\t");
}
```





****
<br>
