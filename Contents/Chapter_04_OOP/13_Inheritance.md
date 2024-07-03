### as, is 연산자
> as 연산자    
> - 형변환이 가능하면 지정된 타입의 인스턴스 값을 반환하고, 가능하지 않으면 null을 반환한다.    
> - 참조형 변수에 대해서만 적용할 수 있고 참조형 타입으로의 체크만 가능하다.

```csharp
Computer pc = new Computer();
Notebook noteBook = pc as Notebook;

if (noteBook != null)       // 아래의 코드는 실행되지 않는다.
{
    noteBook.CloseLid();
}
```
<br>

> is 연산자    
> - 형변환의 가능성 여부를 불린형의 결괏값(true/false)으로 반환한다.    
> - 참조 형식뿐 아니라 값 형식에도 사용할 수 있다.

```csharp
int n = 5;
if (n is string)    // false
{
    Console.WriteLine("변수 n은 string 타입");
}

string txt = "text";
if (txt is int)    // false
{
    Console.WriteLine("변수 txt는 int 타입");
}
```
- C# 컴파일러는 값 형식과 참조 형식을 구분할 수 있기 때문에 위 예제 코드에서 컴파일 오류는 아니나 경고는 발생시킨다.
****
<br>

### 2) 모든 타입의 조상 : System.Object
> 



****
<br>
