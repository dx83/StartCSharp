### 6) 네임스페이스 (namespace)
> 이름 공간    
> - 이름이 중복되어 정의된 것을 구분하려는 목적    
> - 일반적으로 수많은 클래스를 분류하는 방법으로 사용
<br>

▼ 이름 중복 정의
```csharp
namespace MilkyWay
{
    class Earth
    {
    }
}

namespace Andromeda
{
    class Earth
    {
    }
}
```
<br>

▼ 클래스 분류
```csharp
namespace Communication
{
    class Http
    {
    }

    class Ftp
    {
    }
}

namespace Disk.FileSystem
{
    class File
    {
    }

    namespace Files
    {
    }
}
```
- 네임스페이스 안에 또 다른 네임스페이스 사용 가능
<br>

▼ [네임스페이스].[클래스] 형식으로 사용
```csharp
namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            Communication.Http http = new Communication.Http();
            Disk.FileSystem.File file = new Disk.FileSystem.File();
        }
    }
}
```
<br>

▼ using 예약어
```csharp
using Communication;
using Disk.FileSystem;

// ---- 생략 ----- "▼ 클래스 분류" 참고

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            Http http = new Http();
            File file = new File();
        }
    }
}
```
- using 문은 반드시 파일의 첫 부분에 있어야 한다.
- 어떤 코드도 using 문 앞에 와서는 안된다.
<br>

▼ System
```csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World");
        }
    }
}
```
- `System.Console.WriteLine` : Console 클래스가 System 네임스페이스 내부에 정의

****
<br>
