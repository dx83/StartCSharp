### 이벤트 (event)
- 다음 조건을 만족하는 정형화된 콜백 패턴을 구현할 때 event 예약어를 사용하면 코드를 줄일 수 있다.
  - 클래스에서 이벤트(콜백)를 제공한다.
  - 외부에서 자유롭게 해당 이벤트(콜백)를 구독하거나 해지하는 것이 가능하다.
  - 외부에서 구독/해지는 가능하지만 이벤트 발생은 오직 내부에서만 가능하다.
  - 이벤트(콜백)의 첫 번째 인자는 이벤트를 발생시킨 타입의 인스턴스다.
  - 이벤트(콜백)의 두 번째 인자로는 해당 이벤트에 속한 의미 있는 값이 제공된다.
<br>

▼ 델리게이트를 이용한 소수(prime number) 생성기
```csharp
class CallbackArg { }   // 콜백의 값을 담는 클래스의 최상위 부모 클래스 역할

class PrimeCallbackArg : CallbackArg    // 콜백 값을 담는 클래스 정의
{
    public int Prime;

    public PrimeCallbackArg(int prime)
    {
        this.Prime = prime;
    }
}

// 소수 생성기: 소수가 발생할 때마다 등록된 콜백 메서드를 호출
class PrimeGenerator
{
    // 콜백을 위한 델리게이트 타입 정의
    public delegate void PrimeDelegate(object sender, CallbackArg arg);

    // 콜백 메서드를 보관하는 델리게이트 인스턴스 필드
    PrimeDelegate callbacks;

    // 콜백 메서드를 추가
    public void AddDelegate(PrimeDelegate callback)
    {
        callbacks = Delegate.Combine(callbacks, callback) as PrimeDelegate;
    }

    // 콜백 메서드를 삭제
    public void RemoveDelegate(PrimeDelegate callback)
    {
        callback = Delegate.Remove(callbacks, callback) as PrimeDelegate;
    }

    // 주어진 수까지 루프를 돌면서 소수가 발견되면 콜백 메서드 호출
    public void Run(int limit)
    {
        for (int i = 2; i <= limit; i++)
        {
            if (IsPrime(i) == true && callbacks != null)
            {
                // 콜백을 발생시킨 측의 인스턴스와 발견된 소수를 콜백 메서드에 전달
                callbacks(this, new PrimeCallbackArg(i));
            }
        }
    }

    // 소수 판정 메서드: 이해 못해도 상관없음.
    private bool IsPrime(int candidate)
    {
        if ((candidate & 1) == 0)
        {
            return candidate == 2;
        }

        for (int i = 3; (i * i) <= candidate; i += 2)
        {
            if ((candidate % i) == 0) return false;
        }

        return candidate != 1;
    }
}
```
```csharp
// 콜백으로 등록될 메서드 1
static void PrintPrime(object sender, CallbackArg arg)
{
    Console.Write((arg as PrimeCallbackArg).Prime + ", ");
}

static int SUM;

// 콜백으로 등록될 메서드 2
static void SumPrime(object sender, CallbackArg arg)
{
    SUM += (arg as PrimeCallbackArg).Prime;
}

static void Main(string[] args)
{
    PrimeGenerator gen = new PrimeGenerator();

    // PrimeGenerator 클래스 내부의 PrimeDelegate 클래스를 이용하듯이...
    // PrimeGenerator.PrimeDelegate 사용

    // PrintPrime 콜백 메서드 추가
    PrimeGenerator.PrimeDelegate callprint = PrintPrime;
    gen.AddDelegate(callprint);

    // SumPrime 콜백 메서드 추가
    PrimeGenerator.PrimeDelegate callsum = SumPrime;
    gen.AddDelegate(callsum);

    // 1 ~ 10까지 소수를 구하고
    gen.Run(10);
    Console.WriteLine();
    Console.WriteLine(SUM);
    // SumPrime 콜백 메서드를 제거한 후 다시 1 ~15까지의 소수를 구하는 메서드 호출
    gen.RemoveDelegate(callsum);
    gen.Run(15);
}
// 출력 결과
2, 3, 5, 7,
17
2, 3, 5, 7, 11, 13,
```
- 소수가 발견될 때마다 콜백을 발생
- 외부에서 해당 콜백에 관심이 있다면 구독, 필요없어지면 해지할 수 있게 구현
<br>

▼ event를 사용 (System.EventArgs)
```csharp
class PrimeCallbackArg : EventArgs  // 콜백 값을 담는 클래스 정의
{
    public int Prime;

    public PrimeCallbackArg(int prime)
    {
        this.Prime = prime;
    }
}

// 소수 생성기: 소수가 발생할 때마다 등록된 콜백 메서드를 호출
class PrimeGenerator
{
    public event EventHandler PrimeGenerated;

    // 주어진 수까지 루프를 돌면서 소수가 발견되면 콜백 메서드 호출
    public void Run(int limit)
    {
        for (int i = 2; i <= limit; i++)
        {
            if (IsPrime(i) == true && PrimeGenerated != null)
            {
                // 콜백을 발생시킨 측의 인스턴스와 발견된 소수를 콜백 메서드에 전달
                PrimeGenerated(this, new PrimeCallbackArg(i));
            }
        }
    }

    // 소수 판정 메서드: 이해 못해도 상관없음.
    private bool IsPrime(int candidate)
    {
        if ((candidate & 1) == 0)
        {
            return candidate == 2;
        }

        for (int i = 3; (i * i) <= candidate; i += 2)
        {
            if ((candidate % i) == 0) return false;
        }

        return candidate != 1;
    }
}
```
```csharp
// 콜백으로 등록될 메서드 1
static void PrintPrime(object sender, EventArgs arg)
{
    Console.Write((arg as PrimeCallbackArg).Prime + ", ");
}

static int SUM;

// 콜백으로 등록될 메서드 2
static void SumPrime(object sender, EventArgs arg)
{
    SUM += (arg as PrimeCallbackArg).Prime;
}

static void Main(string[] args)
{
    PrimeGenerator gen = new PrimeGenerator();

    // 해당 메서드로 이벤트 구독
    gen.PrimeGenerated += PrintPrime;
    gen.PrimeGenerated += SumPrime;

    // 1 ~ 10까지 소수를 구하기
    gen.Run(10);
    Console.WriteLine();
    Console.WriteLine(SUM);
    // SumPrime 메서드의 이벤트 해지
    gen.PrimeGenerated -= SumPrime;
    gen.Run(15);
}
```
<br>

▼ event 구문
```csharp
class 클래스_명
{
    접근_제한자 event EventHandler 식별자;
}
```
- 클래스의 멤버로 이벤트를 정의한다.
- 이벤트는 외부에서 구독/해지가 가능하다.
- 내부에서 이벤트를 발생시키면 외부에서 다중으로 이벤트에 대한 콜백이 발생할 수 있다.

****
<br>
