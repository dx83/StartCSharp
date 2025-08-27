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

    //public Book() : this(string.Empty) {}           // 매개변수가 1개인 생성자 호출

    public Book(string title) : this(title, 0) { }    // 매개변수가 2개인 생성자 호출

    // 매개변수가 3개인 생성자 호출
    public Book(string title, decimal isbn13) : this(title, isbn13, string.Empty) { }

    // 초기화 코드를 하나의 생성자에서 처리
    public Book(string title, decimal isbn13, string author)
    {
        this.title = title;
        this.isbn13 = isbn13;
        this.author = author;
    }

    public Book() : this(string.Empty, 0, string.Empty) { }    // 매개변수가 3개인 생성자 호출
}
```
- this를 사용해 또 다른 생성자를 호출하는 구문을 사용함으로써 초기화 관련 코드를 하나의 메서드 내에서 처리한다.
<br>

```
이외의 상황에서 this의 사용은 선택의 문제다.
```

****
<br>

### this와 인스턴스/정적 멤버의 관계
> this는 new로 할당된 객체를 가리키는 내부 식별자이므로 클래스 수준에서 정의되는 정적 멤버는 this 예약어를 사용할 수 없다.

```csharp
class Book
{
    string title;               // 인스턴스 필드
    static int count;           // 정적 필드

    public Book(string title)   // 인스턴스 생성자
    {
        this.title = title;     // this로 인스턴스 필드 식별 가능
        this.Open();            // this로 인스턴스 메서드 식별 가능
        Increment();
    }

    void Open()                 // 인스턴스 메서드
    {
        Console.WriteLine(this.title);  // 인스턴스 멤버 사용 가능
        Console.WriteLine(count);       // 정적 멤버 사용 가능
    }

    public void Close()
    {
        Console.WriteLine(this.title + " 책을 덮는다.");
    }

    static void Increment()     // 정적 메서드
    {
        count++;                // 정적 필드 사용 가능
                                // 정적 메서드에는 this가 없으므로 인스턴스 사용 불가능
    }

    public static void CountFix(int count)
    {
        Book.count = count;     // this.count가 아니라 형식 이름 사용
        Console.WriteLine(Book.count);
    }
}
```
<br>

▼ C#컴파일러는 메서드 호출 시 this를 인스턴스 메서드의 첫 번째 인자로 넘겨주는 식으로 구현한다.
```csharp
Book book = new Book("");
book.Close();

// C#컴파일러는 위의 코드를 빌드할 떄 자동으로 아래와 같이 변환한다.
Book book = new Book("");
book.Close(book);

class Book
{
    // ---- 생략 ----
    public void Close(Book this)
    {
        Console.WriteLine(this.title + "책을 덮는다.");
    }
}
```
<br>

```
모든 인스턴스 메서드는 인자를 무조건 1개 이상 더 받게 돼 있으므로
내부에서 인스턴스 멤버에 접근할 일이 없다면 정적 메서드로 명시하는 것이
성능상 유리할 수 있다.
```

****
<br>
