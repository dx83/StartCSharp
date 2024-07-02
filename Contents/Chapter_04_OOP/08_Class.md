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
            Disk.FileSystem.File file = new Disk.FileSystem();
        }
    }
}
```
<br>

▼ using 예약어
```csharp

```

****
<br>
