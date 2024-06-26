## 값을 할당하지 않은 참조 형식
> 초기화되지 않은 모든 참조형 변수는 null 값을 가진다.

```csharp
string text1;         // 숫자 0 을 담고 있음, 출력문(Console.Write) 작성시 컴파일 에러
string text2 = null;  // 숫자 0 을 담고 있음, 출력시 아무값도 출력하지 않음
```
- 숫자 0 : 가리킬 수 있는 힙 주소가 없다.
- 참조형 변수에 숫자 0을 대입할 수 없으므로 null 예약어를 사용
<br>

```csharp
string name = "C#";
name = null;
```
- 참조형 변수가 더는 사용되지 않음을 명시하기 위해 null을 할당
<br>

```csharp
int n1 = 5;
int n2 = n1;
string txt1 = "C#";
string txt2 = txt1;
```
▼ n1과 n2가 같은 값이고, txt1과 txt2 역시 같은 값을 출력하지만 값 형식과 참조 형식은 메모리의 표현 방식이 서로 다르다.

<img src="./Images/3_6.png" width="700"/>

- 값 형식은 스택의 각각 다른 위치에 동일한 값이 복사돼 개별 값을 가리킨다.
- 참조 형셕은 힙 메모리에 하나의 값만 위치한 상태에서 스택의 변수 값이 같은 힙 주소 값을 가지고 있다.

****
<br>

## 기본값 (default value)
> 닷넷은 자료형에 대한 메모리를 할당하면 해당 영역을 무조건 0으로 초기화¹한다.

▼ 각 타입의 기본값
```csharp
bool result;  // bool형 false
int n;        // 숫자형 0
string text;  // 참조 형식 null
// 출력문(Console.Write) 작성시 모두 컴파일 에러
```

*¹C#9.0의 신규 문법에 이러한 초기화를 생략하는 방법을 제공*
****
<br>
