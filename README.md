# unity-code-conventie

Team-swamp's Unity & C# code conventie. Everything is typed in the English languegue.

Always try to make your code less [coupled](https://en.wikipedia.org/wiki/Coupling_(computer_programming)) / dependant on other code, and try to adhere to [SRP (Single Responsability Princple)](https://en.wikipedia.org/wiki/Single-responsibility_principle) doing so will prevent scripts from breaking entire systems if something breaks. 
Also try to make your code [DRY (Dont Repeat Yourself)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself#:~:text=%22Don't%20repeat%20yourself%22,data%20normalization%20to%20avoid%20redundancy.)

- [Namespaces](#namespaces)
- [Classes](#classes)
- [Functions](#functions)
- [Variables](#variables)
- [Structs](#structs)
- [Enums](#enums)
- [If statement](#if-statements)
    - [Ternary operator](#ternary-operator)
- [Loops](#loops)
- [Scriptable object](#scriptable-object)

------
### Namespaces
The namespace name is written in PascalCasing.
Every class needs to be inside of a namespace.
```cs
namespace ExampleNamespace
{
    public class ExampleScript : MonoBehaviour
    {

    }
}
```
```cs
namespace ExampleNamespace.ScriptableObjects
{
    public class ExampleScriptableObject : ScriptableObject
    {

    }
}
```

------
### Classes
The Class name is written in PascalCasing.
If the function GetComponent is used to get a component from this gameObject you use RequireComponent above the class. I suggest using the 'sealed' and 'abstract' keywords to minmize confusion.
```cs
[RequireComponent(typeof(ExampleComponent))]
public sealed class ExampleScript : MonoBehaviour
{

}

public abstract class BaseExampleScript : MonoBehaviour
{

}

public class NonBaseExampleScript : BaseExampleScript
{

}
```

Class members should be grouped into sections:

- Constant Fields
- Static Fields
- Fields
- Constructors
- Properties
- Events / Delegates
- LifeCycle Methods (Awake, OnEnable, OnDisable, OnDestroy, IEnumerator)
- Public Methods
- Protected Methodes
- Private Methods
- Nested types

Within each of these groups order by access:
- public
- serializedFields
- internal
- protected
- private

------
### Functions
All functions and events perform some form of action, whether its getting info, calculating data, or causing something to explode. Therefore, all functions should **start with verbs**. They should be worded in the present tense whenever possible. They should also have some context as to what they are doing.

When writing a function that does not change the state of or modify any object and is purely for getting information, state, or computing a yes/no value, it should ask a question. This should also follow the verb rule.

This is extremely important as if a question is not asked, it may be assumed that the function performs an action and is returning whether that action succeeded.

The Function name is written in PascalCasing.
```cs
private void ExampleFunction()
{
    
}
```

**Access modifiers** are always written with functions.
```cs
void ExampleFunction()
{
    Debug.Log("Not allowed");
}

private void ExampleFunction()
{
    Debug.Log("I'm a private function.");
}

protected void ExampleFunction()
{
    Debug.Log("I'm a protected function.");
}

public void ExampleFunction()
{
    Debug.Log("I'm a public function.");
}
```

**Public & protected functions** require a summary including the parameters and returns.
```cs
/// <summary>
/// Function description.
/// </summary>
/// <param name="parameter">Parameter value to pass.</param>
/// <returns>What the function return.</returns>
public int ExampleFunction(string parameter)  
{
    Return 0;
}

/// <summary>
/// Function description.
/// </summary>
protected void ExampleFunction()  
{
    Debug.log("I am example!");
}
```

When there is more than 1 parameter, we add this rule for readability. This does defeat the rule below.
```cs
// Good
private void ExampleFunction(
    int firstNumber,
    int secondNumber,
    float numberWithComma,
    MonoBehaviour targetClass,
    bool isTrue,
    double funnyNumber)
{
    
}

// Bad
private void ExampleFunction(int a, int b, float c, MonoBehaviour targetClass, bool isTrue, double funnyNumber)
{
    
}
```

When there is only 1 line of code inside of an function you can use a lambda expresion.
```cs
public void ExampleFunction() => SecondExampleFunction();
```

Here is a function overfew.
```cs
/// <summary>
/// Function description.
/// </summary>
protected void ExampleFunction()  
{
    if(_exampleBoolean) ExampleFunction();
    else SeccondExampleFunction();

    var temporaryHealth = _exampleBoolean ? 1 : 69;
    _currentHealth = _exampleFloat;

    var listLength = _exampleList.Length;
    for (int i = 0; i < listLength; i++)
    {
         _exampleList[i].SetHealthColor(_blue);
    }
}
```

------
### Variables
When writing a function that does not change the state of or modify any object and is purely for getting information, state, or computing a yes/no value, it should ask a question. This should also follow the verb rule.

This is extremely important as if a question is not asked, it may be assumed that the function performs an action and is returning whether that action succeeded.

**Access modifiers** are always written with variables.
```cs
// Allowed
private int _variableExample0;
protected int variableExample1;
public int variableExample2;

// Not allowed
int _variableExample3;
```

**Private variable** names always start with an '_' (Even when serialized) after which it is written in camelCasing. If the variable is accisable in the **Unity Inspector** and it's an int or float it needs the Range attribute.
```cs
private Object _variableExample;

[SerializeField] private Object _secondVariableExample;

[SerializeField, Range(0, 10)] private int _thirdVariableExample;

[SerializeField, Range(0, 1)] private float _fourthVariableExample;
```

**Public variable** names are written in camelCasing. If not a simple int, float or bool, it needs to has the Tooltip attribute.
```cs
[Tooltip("Explaination of this varible.")] public Object variableExample;
```

**Readonly variable** names are written the same as public variables so in camelCasing.
```cs
public readonly Object variableExample;
```

**Constant variable** names are written in FULL_CAPITALS.
```cs
public const int EXAMPLE_CONSTANT_VALUE;
```

**Internal variable** names always start with 'i_' after which it is written in camelCasing.
```cs
internal int i_variableExample;
```

**Protected variable** names always start with 'p_' after which it is written in camelCasing.
```cs
protected int p_variableExample;
```

**Temporary variables** inside of an function always need to be written out and are written in camelCasing.
```cs
private void ExampleFunction()
{
    float temporaryFloat = 1f;
    int temporaryInt = 1;
    double temporaryDouble = 1.00;
}
```

**Temporary constants** inside of an function always need to be written out and are written in FULL_CAPITALS.
```cs
private void ExampleFunction()
{
    const float TEMPORARY_FLOAT = 1f;
    const int TEMPORARY_INT = 1;
    double TEMPORARY_DOUBLE = 1.00;
}
```

**Property** names are written in PascalCasing.
```cs
public int ExampleInteger
{
    get => _exampleInterger;
    set 
    {
        if(value < 0) _exampleInterger = 0;
    }
}
```

Arrays follow the same naming rules as above, but should be named as a plural noun.
```
// good
`Targets`, `Hats`, and `EnemyPlayers`

// bad
`TargetList`, `HatArray`, `EnemyPlayerArray`
```

------
### Structs
The struct name is written in PascalCasing and everything inside the struct follows the usual code conventions.
```cs
public struct ExampleStruct
{
    public double x;
    public double y;
}
```

------
### Enums
The enum name is written in PascalCasing while the constants are in FULL_CAPITALS.
```cs
enum ExampleEnum
{
    FIRST_CONSTANT,
    SECOND_CONSTANT
}
```

------
### If statements
When there is only 1 line of code after an if statement it comes right after it and same with the else.
```cs
if(_exampleBoolean) ExampleFunction();
else SeccondExampleFunction();

if(_exampleBoolean) ExampleFunction();
```

If either the if or the else in the statement contains multiple lines of code, the if and the else do not need brackets both.
```cs
if(_exampleBoolean) ExampleFunction();
else
{
    SeccondExampleFunction();
    ThirdExampleFunction();
}
```

When the condition is getting to long, make new lines for it.
```cs
// bad example
if(_exampleBoolean && 0 == 0 || true) ExampleFunction();

// good example
if(_exampleBoolean
    && 0 == 0
    || true) ExampleFunction();

// also good example
bool canBeCalled = _exampleBoolean && 0 == 0 || true;
if(canBeCallled) ExampleFunction();
```

##### ternary operator
I highly recommand ternary operators when dynamicly change 1 varible.
```cs
// bad example
if(_exampleBoolean) _exampleFloat = 1;
else _exampleFloat = 69;

// good example
_exampleFloat = _exampleBoolean ? 1 : 69;
```
Also a note, don't make them to big
```cs
// Not readable
currentIndex = direction ? (startIndex * 2 > (int)corridor.GetNodes().Lenght - 1) ? (int)corridor.GetNodes().Lenght - 1 : max(startIndex * 2 - 1, 0)) : (startIndex * 2 - 1 < 0 ? 0 : indexMinCap = max(startIndex * 2, nodeSize));

// Readable
currentIndex = direction
    ? (startIndex * 2 > (int)corridor.GetNodes().Lenght - 1)
        ? (int)corridor.GetNodes().Lenght - 1
        : max(startIndex * 2 - 1, 0)))
    : (startIndex * 2 - 1 < 0
        ? 0
        : indexMinCap = max(startIndex * 2, nodeSize));

// Best readable
int nodeSize = (int)corridor.GetNodes().Lenght - 1;
int indexMaxCap = max(startIndex * 2 - 1, 0);
int indexMinCap = max(startIndex * 2, nodeSize);
bool isBig = startIndex * 2 > (int)corridor.GetNodes().Lenght - 1;
bool isSmall = startIndex * 2 - 1 < 0;

currentIndex = direction
    ? (isBig ? nodeSize : indexMaxCap)
    : (isSmall ? 0 : indexMinCap)
```

------
### Loops
For better performance (even very small) we make the length it's own (local)varible.
```cs
int listLength = _exampleList.Length;
for (int i = 0; i < listLength; i++)
{

}
```

------
### Scriptable object
Scriptable objects holds data and/or settings, this needs to be reflected in the name. Do not forget the CreateAssetMenu attribute and put it in the correct namespace.
```cs
[CreateAssetMenu(fileName = "NewGunData", menuName = "Gun Data")]
public sealed class GunData : ScriptableObject
{
    private int _maxAmmoAmount;
    public int currentAmmoAmount;

    public void ResetAmmoAmount() => currentAmmoAmount = _maxAmmoAmount;
    public int MaxAmmoAmount() => _maxAmmoAmount;
}
```

Just in case, here is a bad way to make an scriptable object.
```cs
[CreateAssetMenu(fileName = "ScriptableObject / Song info")]
public sealed class SongInfo : ScriptableObject
{
    [field: SerializeField, Tooltip("This is the MP3 file that should play")] public AudioClip Song { get; private set; }
    [field: SerializeField, Tooltip("The person who made the song")] public string Artist { get; private set; }

    [Serializable] public struct LyricNode
    {
        [field: SerializeField, TextArea(5, 50)]  public string TextPart { get; private set; }
        [field: SerializeField, Tooltip("The delay till the next lyric node")] public float TimeStamp { get; private set; }
        [field: SerializeField, Range(0.05f, 1f)] public float Speed { get; private set; }
    }
    [field: SerializeField] public LyricNode[] Nodes { get; private set; }
}
```
