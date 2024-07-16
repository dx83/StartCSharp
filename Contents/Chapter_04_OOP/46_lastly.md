## 4장 정리
> 클래스
> - 현실 세계의 객체를 프로그래밍 세계에 표현한다는 객체지향 개념을 토대로
> 그것을 프로그래밍 언어 차원에서 지원하기 위해 만든 일반적인 개념
<br>
 
|||
|---|---|
|예약어|● using, namespace<br>● class, interface, struct, enum<br>● private, protected, public, internal<br>● return<br>● this, base<br>● typeof<br>● delegate, event<br>● virtual, override<br>● as, is<br>● sealed, abstract<br>● operator, implicit, explicit<br>● static, const, readonly<br>● ref, out|
|문맥 예약어|get, set, value|
- 일반 예약어는 C#으로 작성한 모든 영역의 코드에서 식별자로 사용할 수 없다.
- 문맥 예약어는 특정한 상황을 제외하고는 식별자로 쓰는 것이 가능하다.
- `get` `set` `value` 예약어는 오직 프로퍼티 구문에서만 예약어로 처리된다.
  - 그 외의 코드에서는 여전히 식별자로 사용할 수 있다.
<br>

▼ get, set, value 식별자로 사용
```csharp
int set = 5;
int get = 6;
int value = set + get;
```
<br>

```
문맥 예약어는 하위 버전의 소스코드를 문제 없이 컴파일할 수 있게 한다.
```

****
<br>
