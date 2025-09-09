### 리터럴에도 적용되는 타입
> 코드 내에서 사용되는 리터럴도 그에 해당하는 타입이 적용

▼ 수 : int형의 인스턴스이고 값이 고정된 변수로 사용
````
Console.WriteLine(5.ToString() + 6.ToString());  // 출력 : 56
````
▼ 문자열 : string 타입의 인스턴스로 취급
````
Console.WriteLine("test".ToUpper());  // 출력 : TEST
````
<br>

### 특성 (Attribute)
> 메타데이터에 주석에 해당하는 정보를 포함시키기 위한 것

▼ System.Attribute의 상속을 받는다.
````csharp
class DumbAttribute : Attribute { }  // 관례상 클래스명에 Attribute 접미사를 붙임

[DumbAttribute]
class Dummy1 { }

[Dumb]            // Attribute 접미사 생략 가능
class Dummy2 { }

[Dumb()]          // new Author(); 처럼 생성자를 표현한 구문 가능
class Dummy3 { }
````
<br>

▼ 매개변수를 받는 생성자를 정의했다면 특성을 사용할 때도 매개변수의 전달이 필요
````csharp
class AuthorAttribute : Attribute
{
    string name;

    public AuthorAttribute(string name)
    {
        this.name = name;
    }
}

[Author("Anders")]  // 매개변수 전달
class Author_ { }
````
<br>

▼ 선택적으로 public 변수에 값 지정 가능
````csharp
class VersionAttribute : Attribute
{
    string product;
    public VersionAttribute(string product)
    {
        this.product = product;
    }

    int _version;
    public int Version
    {
        get { return _version; }
        set { _version = value; }
    }
}

[Version("Unity", Version = 1)]  // public 변수에 값 지정
class Program
{
    static void Main(string[] args)
    {
    }
}
````
- 특성은 리플렉션 기술과 결합되면 응용 범위가 확장된다.
<br>
