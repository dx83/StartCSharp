### 인덱서 (indexer)
> 인덱서를 이용하면 클래스의 인스턴스 변수에 배열처럼 접근하는 방식의 대괄호 연산자를 사용할 수 있다.    
> 프로퍼티를 정의하는 구문과 유사하나 다음과 같은 다른점이 있다.
> - 프로퍼티명이 `this` 예약어로 대체된다.
> - 인덱스로 별도의 타입을 지정할 수 있다.

```csharp
class 클래스_명
{
    접근_제한자 반환타입 this[인덱스타입 인덱스식별자]
    {
        접근_제한자 get
        {
            // ------ [코드] ------
            return 반환타입과_일치하는_유형의_표현식;
        }
        접근_제한자 set
        {
            // 인덱스식별자로 구분되는 값에 value를 대입
        }
    }
}
```
<br>

▼ Int32 정수형 데이터의 특정 자릿수를 인덱서를 사용해 문자(char) 데이터로 다루는 예제
```csharp
class IntegerText
{
    char[] txtNumber;

    public IntegerText(int number)
    {
        // Int32 타입을 System.String으로 변환, 다시 String에서 char 배열로 변환
        this.txtNumber = number.ToString().ToCharArray();
    }

    // 인덱서를 사용해 숫자의 자릿수에 따른 문자를 반환하거나 치환
    public char this[int index]
    {
        get
        {
            // 1의 자릿수는 숫자에서 가장 마지막 단어를 뜻하므로 역으로 인덱스를 다시 계산
            // 가장 낮은 자릿수에 있는 값이 [0] 인덱스에 담긴다는 뜻
            return txtNumber[txtNumber.Length - index - 1];
        }
        set
        {
            // 특정 자릿수를 숫자에 해당하는 문자로 치환 가능
            txtNumber[txtNumber.Length - index - 1] = value;
        }
    }

    public override string ToString()
    {
        return new string(txtNumber);
    }

    public int ToInt32()
    {
        return Int32.Parse(ToString());
    }
}

static void Main(string[] args)
{
    IntegerText aInt = new IntegerText(123456);

    int step = 1;
    int max = aInt.ToString().Length;
    for (int i = 0; i < max; i++)
    {
        Console.WriteLine(step + "의 자릿수: " + aInt[i]);
        step += i == 0 ? 9 : 10;
    }

    aInt[3] = '5';

    Console.WriteLine(aInt.ToInt32());
}
// 출력 결과
1의 자릿수: 6
10의 자릿수: 5
20의 자릿수: 4
30의 자릿수: 3
40의 자릿수: 2
50의 자릿수: 1
125456
```
<br>

****
<br>
