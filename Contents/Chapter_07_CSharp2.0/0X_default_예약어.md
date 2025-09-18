### default 예약어
> 타입에 상관 없이 초기값을 얻고 싶을 때 default 예약어를 사용한다.
<br>

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
