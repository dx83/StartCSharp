### 2) 반복문 (iterations statement)
> for, foreach, while, do/while    
> 루프(loop)라고도 한다.
<br>

### 증감 연산자, 복합 대입 연산자
▼ 증감 연산자 (increment & decrement operator)
|증감 연산자|평가 방식|예제|
|---|---|---|
|++|피연산자의 값을 1 증가시킨다.|int n = 50;<br>n++;  // 결과값 51|
|--|피연산자의 값을 1 감소시킨다.|int n = 50;<br>n--;  // 결과값 49|
<br>

▼ 전위 (prefix) / 후위 (postfix) 표기법
```csharp
int n = 50;
Console.WriteLine(n++); // n을 평가하고 난 다음 1만큼 증가 => 50 출력
n = 50;
Console.WriteLine(++n); // n의 값을 1만큼 증가시키고 식을 평가 => 51 출력

int n = 50;
int result;
result = n++;   // result에 50을 대입한 후 값을 51로 증가, result의 값은 50
n = 50;
result = ++n;   // n의 값을 51로 증가시킨 후에 result에 값을 대입, result의 값은 51
n = 50;
result = n--;   // result에 50을 대입한 후에 값을 49로 감소, result의 값은 50
n = 50;
result = --n;   // n의 값을 49로 감소한 후에 result에 값을 대입, result의 값은 49
```
<br>

▼ 복합 대입 연산자 (compound assignment operator)
|연산자|평가 방식|예제|
|---|---|---|
|+=|우측 피연산자의 값을 죄측 피연산자 값에 더해 그 결과를 좌측 피연산자에 대입한다.|int n = 50;<br>n += 5;  // 결과값 55|
|-=|우측 피연산자의 값을 죄측 피연산자 값에서 빼고 그 결과를 좌측 피연산자에 대입한다.|int n = 50;<br>n -= 5;  // 결과값 45|
|*=|우측 피연산자의 값을 죄측 피연산자 값에 곱해 그 결과를 좌측 피연산자에 대입한다.|int n = 50;<br>n *= 5;  // 결과값 250|
|/=|우측 피연산자의 값을 죄측 피연산자 값을 나눠 그 결과를 좌측 피연산자에 대입한다.|int n = 50;<br>n /= 5;  // 결과값 10|
|%=|우측 피연산자의 값을 죄측 피연산자 값의 나머지 값을 구하고 그 결과를 좌측 피연산자에 대입한다.|int n = 50;<br>n %= 5;  // 결과값 0|


****
<br>
