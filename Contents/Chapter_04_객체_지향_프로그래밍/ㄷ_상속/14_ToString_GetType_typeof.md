> 모든 클래스는 object를 상속받기 때문에 object가 가진 메서드를 제공하게 된다.    
> object의 대표적인 4가지 메서드
****
<br>

### ToString
> 해당 인스턴스가 속한 클래스의 전체 이름 (FQDN)을 반환한다.    
> - ToString 메서드는 자식 클래스에서 재정의를 할 수 있다.
> - C#에서 제공되는 기본 타입(short, int, ......)은 모두 ToString을 클래스의 전체 이름이 아닌 해당 타입이 담고 있는 값을 반환하도록 변경했다.
<br>

```csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            Program program = new Program();
            Console.WriteLine(program.ToString());  // ConsoleApp1.Program 출력

            int n = 500
            string txt = "Hello: ";
            Console.WriteLine(txt + n.ToString());  // Hello: 500 출력
        }
    }
}
```

****
<br>

### GetType
> class로 타입을 정의하면 내부적으로 해당 class 타입의 정보를 가지고 있는 System.Type의 인스턴스를 보유하게 되고, 그 인스턴스를 GetType 메서드를 통해 제공된다.
<br>

▼ Type 클래스의 프로퍼티 호출
```csharp
Computer computer = new Computer();
Type type = computer.GetType();

Console.WriteLine(type.FullName);   // ConsoleApp1.Program+Computer 출력
Console.WriteLine(type.IsClass);    // True 출력
Console.WriteLine(type.IsArray);    // False 출력
```
<br>

▼ GetType 메서드로 클래스에 대한 타입의 전체 이름 반환
```csharp
int n = 5;
string txt = "text";

Type intType = n.GetType();

Console.WriteLine(intType.FullName);          // System.Int32
Console.WriteLine(txt.GetType().FullName);    // System.String
```
<br>

▼ typeof 예약어 : 인자로 Type 그 자체를 받아서 인자의 표시된 타입을 반환합니다.
```csharp
Type type = typeof(double);
Console.WriteLine(type.FullName);            // System.Double
Console.WriteLine(typeof(short).FullName);   // System.Int16
```

****
<br>
