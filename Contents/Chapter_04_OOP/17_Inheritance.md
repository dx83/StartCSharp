### 4) this 예약어
> 객체는 외부에서 자신을 식별할 수 있는 변수를 갖는다.    
> 클래스 내부에서 멤버에 접근할 때 this를 생략했다고 봐도 무방하다.
<br>

▼ this 용례 1
```csharp
class Book
{
    decimal isbn;

    public Book(decimal isbn)
    {
        this.isbn = isbn;   // this를 생략하면 메서드의 매개변수인 isbn 변수가 사용된다.
    }
}
```
- 메서드의 매개변수와 클래스에 정의된 필드의 이름이 같을 경우 this를 명시함으로써 멤버 변수를 사용할 수 있다.
<br>

▼ this 용례 2 : this 예약어를 사용해 생성자 내에서 다른 생성자를 호출
```csharp
class Book
{
    string title;
    decimal isbn13;
    string author;

    public Book(string title) : this(title, 0)
    {
    }

    public Book(string title, decimal isbn13) : this(title, isbn13, string.Empty)
    {
    }

    public Book(string title, decimal isbn13, string author)
    {
        this.title = title;
        this.isbn13 = isbn13;
        this.author = author;
    }

    public Book() : this(string.Empty, 0, string.Empty)
    {
    }
}
```
- this를 사용해 또 다른 생성자를 호출하는 구문을 사용함으로써 초기화 관련 코드를 하나의 메서드 내에서 처리한다.

****
<br>
