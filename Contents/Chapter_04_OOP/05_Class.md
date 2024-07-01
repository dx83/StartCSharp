### 5) 정적 멤버, 인스턴스 멤버
> 인스턴스 (instance)
> - 어떤 타입을 실체화한 객체
> - new 연산자를 거쳐서 메모리에 할당된 객체
- 객체와 관련된 멤버를 인스턴스 멤버 (instance member)라고 한다.
- 지금까지 설명한 필드, 메서드, 생성자는 모두 여기에 속한다.

```csharp
class Program
{
    static void Main(string[] args)
    {
        Person person = new Person("홍길동");  // new를 통해 인스턴스 생성자에 접근
        Person.OutputYourName();              // new로 생성된 객체의 인스턴스 메서드를 호출
        Console.WriteLine(person._name);      // new로 생성된 객체의 인스턴스 필드에 접근
    }
}
```
<br>

> 개별 인스턴스 수준이 아닌 해당 인스턴스의 타입 전체에 결쳐 전역적으로 적용되는 필드, 메서드, 생성자가 필요할 수 있는데, 이러한 멤버를 정적 맵버 (static member)라고 한다.

****
<br>



****
<br>
