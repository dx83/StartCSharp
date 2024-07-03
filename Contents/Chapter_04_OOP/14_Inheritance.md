> 모든 클래스는 object를 상속받기 때문에 object가 가진 메서드를 제공하게 된다.    
> object의 대표적인 4가지 메서드

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
