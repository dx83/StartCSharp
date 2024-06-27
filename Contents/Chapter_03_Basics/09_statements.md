## 5. 제어문
### 1) 선택문 (selection statements)
> if, switch
<br>

### 관계 연산자 (relational operator), 논리 연산자 (logical operator)
> 조건식의 나열은 부울 대수 (boolean algebra)의 기본 연산을 하는 것과 같다.

▼ 관계 연산자
|관계 연산자|평가 방식|예제|
|---|---|---|
|>|좌측 피연산자가 우측 피연산자보다 크면 참, 같거나 작으면 거짓|bool result = 10 > 20;  // 거짓|
|<|좌측 피연산자가 우측 피연산자보다 작으면 참, 같거나 크면 거짓|bool result = 10 < 20;  // 참|
|>=|좌측 피연산자가 우측 피연산자보다 크거나 같으면 참, 작으면 거짓|bool result = 10 >= 20;  // 거짓|
|<=|좌측 피연산자가 우측 피연산자보다 작거나 같으면 참, 크면 거짓|bool result = 10 <= 20;  // 참|
|==|좌측 피연산자와 우측 피연산자가 같으면 참, 다르면 거짓|bool result = 10 == 20;  // 거짓|
|!=|좌측 피연산자와 우측 피연산자가 다르면 참, 같으면 거짓|bool result = 10 != 20;  // 참|
<br>

▼ 논리곱 연산자 && (AND) `둘 다 참일때만 참`
|좌측 피연산자|우측 피연산자|AND 연산 결과|예제|
|:---:|:---:|:---:|---|
|true|true|true|bool result = true && true;|
|true|false|false|bool result = true && false;|
|false|true|false|bool result = false && true;|
|false|false|false|bool result = false && false;|
<br>

▼ 논리곱 연산자 || (OR) `둘 중 하나라도 참이면 참`
|좌측 피연산자|우측 피연산자|OR 연산 결과|예제|
|:---:|:---:|:---:|---|
|true|true|true|bool result = true \|\| true;|
|true|false|true|bool result = true \|\| false;|
|false|true|true|bool result = false \|\| true;|
|false|false|false|bool result = false \|\| false;|
<br>

▼ 논리곱 연산자 ^ (XOR) `둘 다 달라야 참`
|좌측 피연산자|우측 피연산자|XOR 연산 결과|예제|
|:---:|:---:|:---:|---|
|true|true|false|bool result = true ^ true;|
|true|false|true|bool result = true ^ false;|
|false|true|true|bool result = false ^ true;|
|false|false|false|bool result = false ^ false;|
<br>

▼ 부정 연산자 ! (NOT)
|우측 피연산자|NOT 연산 결과|예제|
|:---:|:---:|---|
|true|false|bool result = !true;|
|false|true|bool result = !false;|
<br>

▼ 단락 계산 (short-circuit), 단축 평가 (short-circuit evaluation)
> 프로그램의 실행 과정에서 뒤의 조건은 아예 실행조차 되지 않는 것을 두고 단락 계산 또는 단축 평가됐다고 한다.

```csharp
int n1 = 6;
int n2 = 10;
bool result = (n1 % 3 == 0 || n2 % 3 == 0);    // True 출력

int n1 = 10;
int n2 = 6;
bool result = (n1 % 3 == 0 && n2 % 3 == 0);    // False 출력
```
- 첫번째, 이미 (n1 % 3 == 0)의 표현식이 참이기 때문에 뒤의 (n2 % 3 == 0)의 결과값에 상관없이 전체 평가식이 참이 된다.
- 두번째, (n1 % 3 == 0)의 표현식이 거짓이므로 논리곱 연산의 성격상 뒤에 오는 식에 상관없이 전체 평가식이 거짓이 된다.
- 둘다, (n2 % 3 == 0) 코드는 실행되지 않는다.

```
단락 계산에 따른 부작용이 발생할 수 있음에 유의!
```

****
<br>
