### 중복 코드 제거
> 함수는 코드를 재사용하기 쉽게 해준다.

- 중복된 코드는 향후 유지보수를 어렵게 만드므로 메서드를 사용하면 이런 문제를 개선할 수 있다.
- 관리해야 할 코드가 한 곳에 모여고, 이를 재사용할 수 있다면 좀 더 간결하게 프로그램을 만들 수 있다.

```
코드가 2번 이상 중복된다면 무조건 메서드로 분리하자.
```
****
<br>

### 코드 추상화
> 메서드는 특정 목적을 수행하는 일련의 코드를 모아서 입력 인자와 출력 인자를 정의해 추상화할 수 있다.

- 함수는 `입력 인자`와 `출력 인자`의 용도만 알면 내부에 어떤 식으로 코드가 작성돼 있는냐와 상관없이 사용할 수 있다.

|함수 이름|입력 인자 타입|출력 인자 타입|설명|
|---|---|---|---|
|abs|int|int|입력된 값의 절댓값을 반환한다.|
|max|int<br>int|int|2개의 입력 인자 중 큰 값을 변환한다.|

- 위와 같은 정보만으로 abs와 max 함수를 올바르게 사용할 수 있다.

```csharp
int absoluteValue = abs(-5);            // 반환값 5
int maxValue = max(absoluteValue, 10);  // 반환값은 10
```
****
<br>

```
타입(class)  = 속성 (field) + 행위 (method)
```
- 클래스는 데이터를 속성으로, 코드를 메서드로 추상화한 개념이다.

```
메서드는 객체에 속한 함수이며, 멤버 메서드 (member method)라고도 불린다.
```

****
<br>
