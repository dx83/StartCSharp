# 4장 C# 객체지향 문법
> Object-Oriented Programming    
> C#은 객체지향 프로그래밍 언어 (OOP Language) 이다.
<br>

<img src="./Images/4_2.png" width="500"/>

## 1. 클래스
> 기본 타입 외에 개발자가 원하는 모든 객체의 타입을 새롭게 정의해서 사용    
> C#에서 타입 정의를 위해서 `class` 예약어 제공
<br>

````csharp
class 클래스_명
{
    // 속성 정의;
    // 행위 정의;
}
````
- 클래스명은 식별자이기 때문에 사용자가 임의로 정의하는 것이 가능
<br>

▼ 클래스로 정의된 타입은 모두 "참조형"으로 분류

<img src="./Images/4_3.png" width="600"/>

- 정의된 타입을 사용하려면 new 연산자로 메모리 할당을 해야 한다.

****
<br>

### 1) 필드 (field)
> 클래스 내 정의된 속성

- 필드에 값을 대입
    - 객체.필드명 = 필드의_타입과_일치하는_표현식;
- 필드로부터 값을 가져옴
    - 필드의_타입과_일치하는_변수 = 객체.필드명;

````
필드는 객채에 속한 변수이고, 멤버 변수(member variable)라고도 한다.
````

****
<br>

```csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            // new 연산자로 메모리 할당
            Book gulliver = new Book();

            gulliver.Author = "Jonathan Swift";
            gulliver.ISBN13 = 9788983920775m;
            gulliver.Title = "걸리버 여행기";
            gulliver.Contents = "...";
            gulliver.PageCount = 384;

            string author = gulliver.Author;
            decimal isbn13 = gulliver.ISBN13;
            string title = gulliver.Title;
            string contents = gulliver.Contents;
            int pageCount = gulliver.PageCount;
        }
    }

    class Book
    {
        // 속성 정의
        string Title;
        decimal ISBN13;
        string Contents;
        string Author;
        int PageCount;
    }
}
```
- `class Program` : C# 프로그램은 모든 것이 타입으로 정의돼 있다는 특징이 있다.

****
<br>
