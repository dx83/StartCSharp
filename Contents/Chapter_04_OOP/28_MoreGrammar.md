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



****
<br>
