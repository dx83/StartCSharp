### 5) base 예약어
> "부모 클래스"를 명시적으로 가리키는데 사용    
> this와 마찬가지로 부모 클래스의 멤버를 사용할 때 base 키워드를 생략했다고 봐도 무방하다.
<br>

▼ base 명시
```csharp
public class Notebook : Computer
{
    bool fingerScan;
    public bool HasFingerScanDevice() { return fingerScan; }

    public void CloseLid()
    {
        base.Shutdown();    // 부모 클래스의 메서드임을 base 예약어로 명시
    }
}
```
<br>

▼ base 예약어를 이용한 생성자 호출
```csharp
class Book
{
    decimal isbn13;

    public Book(decimal isbn13)
    {
        this.isbn13 = isbn13;
    }
}

class EBook : Book
{
    // 부모의 생성자 초기화
    public EBook() : base(0) { }

    // 또는 이렇게  값을 연계하는 것도 가능하다.
    public EBook(decimal isbn) : base(isbn)
    {
    }
}
```
- public EBook() {}
  - 이렇게만 하면 컴파일 오류가 발생한다.
  - 자식 클래스를 생성할 때 부모 클래스의 생성자도 함께 호출된다.
  - 이때 부모의 private 멤버에 접근할 수 없으므로 초기화가 불가능하다.

****
<br>
