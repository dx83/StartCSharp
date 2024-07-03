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



****
<br>
