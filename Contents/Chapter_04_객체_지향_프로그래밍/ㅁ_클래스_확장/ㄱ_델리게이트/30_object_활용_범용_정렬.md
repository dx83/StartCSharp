▼ 델리게이트와 object를 이용한 범용 정렬 코드
```csharp
class Person
{
// ---- 생략 ----
}

delegate bool CompareDelegate(object grg1, object arg2);    // object 인자 2개

class SortObject
{
    object[] things;
    
    public SortObject(object[] things)  // object 배열
    {
        this.things = things;
    }

    public void Sort(CompareDelegate compareMethod)
    {
        object temp;

        for (int i = 0; i < things.Length; i++)
        {
            int lowPos = i;

            for (int j = i + 1; j < things.Length; j++)
            {
                if (compareMethod(things[j], things[lowPos]))
                {
                    lowPos = j;
                }
            }

            temp = things[lowPos];
            things[lowPos] = things[i];
            things[i] = temp;
        }
    }
}
```
```csharp
static bool AscSortByName(object arg1, object arg2)
{
    Person person1 = arg1 as Person;    // 대상 타입으로 형변환
    Person person2 = arg2 as Person;

    return person1.Name.CompareTo(person2.Name) < 0;
}

static bool AscSortByAge(object arg1, object arg2)
{
    Person person1 = arg1 as Person;
    Person person2 = arg2 as Person;

    return person1.Age < person2.Age;
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

    SortObject so = new SortObject(personArray);
    so.Sort(AscSortByName);

    Person[] p = personArray;
    for (int i = 0; i < p.Length; i++)
    {
        Console.WriteLine(p[i].Name + ": " + p[i].Age);
    }

    Console.WriteLine();

    so.Sort(AscSortByAge);
    for (int i = 0; i < p.Length; i++)
    {
        Console.WriteLine(p[i].Name + ": " + p[i].Age);
    }
}
// 출력 결과
Anders: 51
Mads: 62
Petter: 45
Scott: 37

Scott: 37
Petter: 45
Anders: 51
Mads: 62
```
- object를 사용해 Sort 메서드를 타입에 종속적이지 않게 만들었다.
- 모든 타입에 대해 SortObject 클래스를 이용해 정렬을 수행할 수 있다.

```
델리게이트만 전달하는 것으로 코드 재사용 능력을 극대화한 것이다.
```
****
<br>
