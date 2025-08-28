▼ 선택 정렬 알고리즘
```csharp
class SortObject    // 배열을 정렬할 수 있는 기능을 가진 타입 정의
{
    int[] numbers;

    public SortObject(int[] numbers) // 배열을 생성자의 인자로 받아서 보관
    {
        this.numbers = numbers;
    }

    // 전형적인 선택 정렬 알고리즘을 구현한 메서드
    public void Sort()  // numbers 배열의 요소를 크기순으로 정렬
    {
        int temp;

        for (int i = 0; i < numbers.Length; i++)
        {
            int lowPos = i;

            for (int j = i + 1; j < numbers.Length; j++)
            {
                // i 인덱스에 있는 값이 있어야할 자리를 찾는 방식
                if (numbers[j] < numbers[lowPos])
                {
                    lowPos = j;
                }
            }

            temp = numbers[lowPos];
            numbers[lowPos] = numbers[i];
            numbers[i] = temp;
        }
    }

    public void Display()   // numbers 요소를 화면에 출력
    {
        for (int i = 0; i < numbers.Length; i++)
            Console.Write(numbers[i] + "\t");
    }
}

static void Main(string[] args)
{
    int[] intArray = new int[] { 5, 2, 3, 1, 0, 4 };

    SortObject so = new SortObject(intArray);
    so.Sort();
    so.Display();  // 0  1  2  3  4  5
}
```
- Sort 메서드는 int형 배열을 오름차순(ascending)으로 정렬하고 있다.
- 여기서 `<`연산자를 `>`연산자로 변경하면 내림차순(descending)으로 정렬하게 된다.
    - `if (numbers[j] > numbers[lowPos])`
<br>

▼ 오름차순과 내림차순을 함께 구현
```csharp
// ---- 생략 ----
public delegate bool CompareDelegate(int arg1, int arg2);

public void Sort(CompareDelegate compareMethod)
{
    int temp;

    for (int i = 0; i < numbers.Length; i++)
    {
        int lowPos = i;

        for (int j = i + 1; j < numbers.Length; j++)
        {
            if (compareMethod(numbers[j], numbers[lowPos]))
            {
                lowPos = j;
            }
        }

        temp = numbers[lowPos];
        numbers[lowPos] = numbers[i];
        numbers[i] = temp;
    }
}
// ---- 생략 ----
```
- 비교하는 코드를 외부에서 선택하도록 델리게이트로 구현
```csharp
static void Main(string[] args)
{
    int[] intArray = new int[] { 5, 2, 3, 1, 0, 4 };

    SortObject so = new SortObject(intArray);
    so.Sort(AscendingCompare);  // 오름차순 정렬
    so.Display();    // 0  1  2  3  4  5

    Console.WriteLine();

    so.Sort(DescendingCompare); // 내림차순 정렬
    so.Display();    // 5  4  3  2  1  0
}

public static bool AscendingCompare(int arg1, int arg2)
{
    return (arg1 < arg2);
}

public static bool DescendingCompare(int arg1, int arg2)
{
    return (arg1 > arg2);
}
```


****
<br>
