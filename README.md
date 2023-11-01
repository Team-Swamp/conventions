# Code conventions

### **Namespaces**

The namespace name is written in UpperCamelCase.
Every class needs to be inside of a namespace.
```cs
namespace ExampleNamespace
{
    public class ExampleScript : MonoBehaviour
    {

    }
}
```

------

### **Classes**

The Class name is written in UpperCamelCase.
If the function GetComponent is used to get a component from this gameObject you use RequireComponent above the class.
```cs
[RequireComponent(typeof(ExampleComponent))]
public class ExampleScript : MonoBehaviour
{

}
```

------

### **Functions**

The Function name is written in UpperCamelCase.
```cs
private void ExampleFunction()
{
    
}
```

**Public functions** require a summary including the parameters and returns.
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
```

When there is only 1 line of code inside of an function you can use a lambda expresion.
```cs
public void ExampleFunction() => SecondExampleFunction();
```

------

### **Variables**

**Private variable** names always start with an '_' (Even when serialized) after which it is written in lowerCamelCase.
```cs
private Object _variableExample;

[SerializeField]
private Object _secondVariableExample;
```

**Public variable** names are written in lowerCamelCase.
```cs
public Object variableExample;
```

**Readonly variable** names are written the same as public variables so in lowerCamelCase.
```cs
public readonly Object variableExample;
```

**Constant variable** names are written in FULL_CAPITALS.
```cs
public const int EXAMPLE_CONSTANT_VALUE;
```

**Internal variable** names always start with 'i_' after which it is written in lowerCamelCase.
```cs
internal int i_variableExample;
```

**Protected variable** names always start with 'p_' after which it is written in lowerCamelCase.
```cs
protected int p_variableExample;
```

**Temporary variables** inside of an function always need to be written out and are written in lowerCamelCase.
```cs
private void ExampleFunction()
{
    float temporaryFloat = 1f;
    int temporaryInt = 1; 
}
```

**Temporary constants** inside of an function always need to be written out and are written in FULL_CAPITALS.
```cs
private void ExampleFunction()
{
    const float TEMPORARY_FLOAT = 1f;
    const int TEMPORARY_INT = 1; 
}
```

**Propertie** names are written in UpperCamelCase.
```cs
public int ExampleInteger
{
    get => _exampleInterger;
    set 
    {
        if(value < 0)
            _exampleInterger = 0;
    }
}
```

------

### **If statements**

When there is only 1 line of code after an if statement it needs to be tabbed under the if statement and does not need brackets and same with the else.
```cs
if(_exampleBoolean)
    ExampleFunction();
else
    SeccondExampleFunction();

if(_exampleBoolean)
    ExampleFunction();
```

If either the if or the else in the statement contains multiple lines of code both the if and the else need brackets.
```cs
if(_exampleBoolean)
{
    ExampleFunction();
}
else
{
    SeccondExampleFunction();
    ThirdExampleFunction();
}
```

------

### **Structs**

The struct name is written in UpperCamelCase and everything inside the struct follows the usual code conventions.
```cs
public struct ExampleStruct
{
    public double x;
    public double y;
}
```

------

### **Enums**

The enum name is written in UpperCamelCase while the constants are in FULL_CAPITALS.
```cs
enum ExampleEnum
{
    FIRST_CONSTANT,
    SECOND_CONSTANT
}
```
