### default 예약어
> 타입에 상관 없이 초기값을 얻고 싶을 때 default 예약어를 사용한다.
<br>

▼ default(Type)
````csharp
static void Main(string[] args)
{
    printInitValue(123);    // 출력 결과 : 0
    printInitValue("abc");  // 출력 결과 : 
    printInitValue(true);   // 출력 결과 : false

}
        
static void printInitValue<T>(T item)
{
    Console.WriteLine(default(T));
}
````
<br>

### default 리터럴
> C# 7.1부터 타입 추론이 가능해져서 리터럴 형식으로 사용 가능
<br>

````csharp
int intValue = default;              // default(int)
BigInteger bigIntValue = default;    // default(BigInteger)

Console.WriteLine(intValue);
Console.WriteLine(bigIntValue);

string txt = default;                // default(string)
Console.WriteLine(txt ?? "(null)");  // 출력 결과 : (null)
````
- Console.WriteLine(default(T));<br>bool 과 char 의 메서드 또는 속성 간 호출이 모호하여 (T) 명시가 필요
<br>

▼ 제네릭 인자에도 사용 가능
````csharp
class GenericTest<T>
{
    public T GetDefaultValue()
    {
        return default;              // default(T)
    }
}

static void Main(string[] args)
{
    Generic<int> t = new GenericTest<int>();
    Console.WriteLine(t.GetDefaultValue());    // 출력 결과 : 0
}
````
<br>
