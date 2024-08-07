▼ Person 타입을 Age 필드 순으로 정렬
```csharp
class Person
{
    public int Age;
    public string Name;

    public Person(int age, string name)
    {
        this.Age = age;
        this.Name = name;
    }

    public override string ToString()
    {
        return Name + ": " + Age;
    }
}

class SortPerson
{
    Person[] men;
    
    public SortPerson(Person[] men)
    {
        this.men = men;
    }

    public void Sort()
    {
        Person temp;

        for (int i = 0; i < men.Length; i++)
        {
            int lowPos = i;

            for (int j = i + 1; j < men.Length; j++)
            {
                if (men[j].Age < men[lowPos].Age)
                {
                    lowPos = j;
                }
            }

            temp = men[lowPos];
            men[lowPos] = men[i];
            men[i] = temp;
        }
    }

    public void Display()
    {
        for (int i = 0; i < men.Length; i++)
        {
            Console.WriteLine(men[i] + ",");
        }
    }
}
```
- Name 필드 순으로, 더 나아가 Person 타입에 Address, Telephone 등의 속이 추가되고 정렬을 요구한다면...
<br>

▼ 모든 복잡성을 델리게이트를 사용해 해결
```csharp
// ---- 생략 ----
delegate bool CompareDelegate(Person grg1, Person arg2);

class SortPerson
{
// ---- 생략 ----
    public void Sort(CompareDelegate compareMethod) // 비교를 위한 델리게이트 인자
    {
        Person temp;

        for (int i = 0; i < men.Length; i++)
        {
            int lowPos = i;

            for (int j = i + 1; j < men.Length; j++)
            {
                if (compareMethod(men[j], men[lowPos]))
                {
                    lowPos = j;
                }
            }

            temp = men[lowPos];
            men[lowPos] = men[i];
            men[i] = temp;
        }
    }
// ---- 생략 ----
}
```
```csharp
static bool AscSortByName(Person arg1, Person arg2)
{
    // string 객체의 CompareTo 메서드는 문자열 비교를 수행
    // 문자열 사전 정렬 순으로 비교해서 크면 1, 같으면 0, 작으면 -1을 반환
    // 따라서 0보다 작은 값을 반환한 경우를 true로 하면 오름차순 정렬
    return arg1.Name.CompareTo(arg2.Name) < 0;
}

static void Main(string[] args)
{
    Person[] personArray = new Person[]
    {
        new Person(51, "Anders"),
        new Person(37, "Scott"),
        new Person(45, "Petter"),
        new Person(62, "Mads"),
    };

    SortPerson so = new SortPerson(personArray);
    so.Sort(AscSortByName);
    so.Display();
}
```
- 필요한 정렬을 메서드로 만들어 계속 추가할 수 있다.

****
<br>
