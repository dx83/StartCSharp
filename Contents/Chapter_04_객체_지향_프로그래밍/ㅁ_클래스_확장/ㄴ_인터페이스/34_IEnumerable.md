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
// 출력 결과
1  2  3  4  5
```
<br>

▼ foreach 제어문의 `in` 다음에 오는 객체는 IEnumerable 인터페이스를 구현한 인스턴스여야 한다.
```csharp
// 위의 예제 foreach 문 사용
foreach (int elem in intArray)
{
    Console.Write(elem + "\t");
}
// string 타입도 IEnumerable 인터페이스를 구현했다.
string name = "Korea";
foreach (char ch in name)
{
    Console.Write(ch + "\t");    // K    o    r    e    a
}
```
<br>

▼ IEnumerable 인터페이스 구현해보기
```csharp
class Hardware { }

class USB
{
    string name;
    public USB(string name) { this.name = name; }
    public override string ToString()
    {
        return name;
    }
}

class Notebook : Hardware, IEnumerable
{
    USB[] usbList = new USB[] { new USB("USB1"), new USB("USB2") };

    // IEnumerator를 구현한 열거자 인스턴스 반환
    public IEnumerator GetEnumerator()
    {
        return new USBEnumerator(usbList);
    }

    // 중첩 클래스로 정의된 열거자 타입
    public class USBEnumerator : IEnumerator
    {
        int pos = -1;
        int length = 0;
        object[] list;

        public USBEnumerator(USB[] usb)
        {
            list = usb;
            length = usb.Length;
        }

        public object Current   // 현재 요소를 반환하도록 약속된 접근자 메서드
        {
            get { return list[pos]; }
        }

        public bool MoveNext()  // 다음 순서의 요소를 지정하도록 약속된 메서드
        {
            if (pos >= length -1)
            {
                return false;
            }

            pos++;
            return true;
        }

        public void Reset()     // 처음부터 열거하고 싶을 때 호출하면 되는 메서드
        {
            pos = -1;
        }
    }
}

// 출력문
Notebook notebook = new Notebook();
foreach (USB usb in notebook)
{
    Console.WriteLine(usb);
}
// 출력 결과
USB1
USB2
```

****
<br>
