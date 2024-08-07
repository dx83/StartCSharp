### 구조체 (struct)
> 값 형식의 class 같은 사용자 정의 형식
- 인스턴스 생성을 new로 해도 되고, 안해도 된다.
- 기본 생성자는 명시적으로 정의할 수 없다.
- 매개변수를 갖는 생성자를 정의해도 마치 기본 생성자가 있는 것처럼 C# 컴파일러에 의해 자동으로 지원된다.    
(클래스의 경우에는 포함되지 않는다.)
- 매개변수를 받는 생성자의 경우 반드시 해당 코드 내에서 구조체의 모든 필드에 값을 할당해야 한다.
<br>

▼ struct 예약어
```csharp
using System;

namespace Chapter04
{
    struct Vector
    {
        public int X;
        public int Y;

        public Vector(int x, int y) // 매개변수를 가진 생성자 정의
        {
            this.X = x; // 구조체가 가진 모든 필드를 초기화
            this.Y = y;
        }

        // System.Object의 ToString 재정의
        public override string ToString()
        {
            return "X: " + X + ", Y: " + Y;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Vector v1 = new Vector();       // new를 사용해 인스턴스 생성 가능
            Vector v2;                      // new가 없어도 인스턴스 생성 가능
            Vector v3 = new Vector(5, 10);  // 명시적으로 생성자 지정 가능

            Console.WriteLine(v3);          // X: 5, Y: 10 출력
        }
    }
}
```
<br>

▼ new : 변수의 모든 값을 0으로 할당
```csharp
Vector v1 = new Vector();

Vector v2;
v2.X = 0;
v2.Y = 0;

Vector v3 = new Vector(0, 0);
```
- 모두 같은 표현
```csharp
int n1 = new int();

int n2;
n2 = 0;

int n3 = 0;
```
- 기본형도 모두 같은 표현
<br>

▼ C# 컴파일러는 개발자가 직접 코드 상에서 값을 할당하지 않는 변수를 사용하는 것을 `오류`라고 판단한다.
```csharp
int n;    // n은 0의 값을 갖고 있지만 개발자가 할당한 것은 아니다.
Console.WriteLine(n);   // 컴파일 에러 발생
```

****
<br>
