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
▼ object의 기본 메서드 3 가지
```csharp
public class Object
{
    public virtual bool Equals(object obj);
    public virtual int GetHashCode();
    public virtual string ToString();
}
```
<br>

▼ ToString 재정의
```csharp
public class Point
{
    int x, y;

    public Point(int x, int y)
    {
        this.x = x;
        this.y = y;
    }

    public override string ToString()
    {
        return "X: " + x + "y: " + y;
    }
}

// 출력문
Point pt = new Point(5, 10);
Console.WriteLine(pt.ToString());    // X: 5, y: 10
```
- 로그를 남기거나 디버깅할 때 ToString에서 반환된 결과가 유용하게 쓰일 수 있다.
<br>

▼ Equals, GetHashCode 재정의
```csharp
class Book
{
    decimal isbn13;
    string title;
    string contents;

    public Book(decimal isbn13, string title, string contents)
    {
        this.isbn13 = isbn13;
        this.title = title;
        this.contents = contents;
    }

    public override bool Equals(object obj)
    {
        if (obj == null)
        {
            return false;
        }

        Book book = obj as Book;
        if (book == null)
        {
            return false;
        }

        return this.isbn13 == book.isbn13;
    }

    public override int GetHashCode()
    {
        return this.isbn13.GetHashCode();
    }
}
// 출력문
Book book1 = new Book(9788998139018, "리버스 엔지니어링 바이블", "......");
Book book2 = new Book(9788998139018, "리버스 엔지니어링 바이블", "......");
Book book3 = new Book(9788992939409, "파이썬 3.6 프로그래밍", "......");

Console.WriteLine("book1 == book2: " + book1.Equals(book2));    // True
Console.WriteLine("book1 == book3: " + book1.Equals(book3));    // False
```
- 책의 고유성이 포함된 `키(key` 속성은 ISBN 이므로 ISBN을 비교대상이 되도록 `Equals`를 재정의 한다.
- `GetHashCode`는 비교대상이 isbn13 필드 값이기 떄문에 isbn13의 해시 코드를 반환하는 것으로 재정의 한다.
<br>

```
특정 객체를 고유하게 식별할 수 있는 값을 `키(key)` 값이라고 한다.    
해당 객체의 키가 될 요소를 적절하게 찾는다면 Equals와 GetHashCode는 자연스럽게 만들 수 있다.
```

****
<br>
