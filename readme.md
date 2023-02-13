<h3 style='color: gray;margin:0; padding:0;'> [Briefcase.HealthCheck, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h3>

#### Description

Library to verify the health of any execution.  it will return the result, ElapsedTime, and if its success or not, and if not will return the errorMessage of it.

#### Examples

To verify the health of any single funtion, use the exempla below:
<i>

```csharp
IHealthResult item = HealthExecution
   .ExecuteHealthly(() => Sum(1,2,3));

item = HealthExecution.ExecuteHealthly(ReturnText);

//retorna true e false 
Console.WriteLine(item.Success);
//retorna to tempo de execução
Console.WriteLine(item.ElapsedTime);

if (item is IHealthNamedResult resultNamed)
{
    // retorna o nome do metodo
    Console.WriteLine(resultNamed.MethodName);
}
if (item is IHealthResultError resultError)
{
    // retorna a mensagem de erro
    Console.WriteLine(resultError.ErrorMessage);
}
if (item is IHealthResultResponse resultResponse)
{
    // retorna o resultado como Object
    Console.WriteLine(resultResponse.Result);
}

int Sum(params int[] values)
{
    return values.Sum();
}

string ReturnText()
{
    return "value";
}
```

</i>


If you want to use it for multiple results at same time, you can use one of overloads with multiple params:
<i>

```csharp
List<IHealthResult> resultado = HealthExecution
   .ExecuteHealthly(
               (nameof(Sum), () => Task.FromResult<object>(Sum())),
               (nameof(ReturnText), () => Task.FromResult<object>(ReturnText()))
           );

foreach (var item in resultado)
{
    //retorna true e false 
    Console.WriteLine(item.Success);
    //retorna to tempo de execução
    Console.WriteLine(item.ElapsedTime);

    if (item is IHealthNamedResult resultNamed)
    {
        // retorna o nome do metodo
        Console.WriteLine(resultNamed.MethodName);
    }

    if (item is IHealthResultError resultError)
    {
        // retorna a mensagem de erro
        Console.WriteLine(resultError.ErrorMessage);
    }
    if (item is IHealthResultResponse resultResponse)
    {
        // retorna o resultado como Object
        Console.WriteLine(resultResponse.Result);
    }
}

int Sum(params int[] values)
{
    return values.Sum();
}

string ReturnText()
{
    return "value";
}
```

</i>


#### Assembly information


#### Namespace [Briefcase.HealthCheck](Namespace/Briefcase.HealthCheck.md);

##### Classes

<small>[HealthExecution](Documentation/Type/HealthExecution.md)</small>

<small>[HealthExecutionBase](Documentation/Type/HealthExecutionBase.md)</small>

#### Namespace [Briefcase.HealthCheck.Entities.Interfaces](Namespace/Briefcase.HealthCheck.Entities.Interfaces.md);

##### Interfaces

<small>[IHealthNamedResult](Documentation/Type/IHealthNamedResult.md)</small>

<small>[IHealthResult](Documentation/Type/IHealthResult.md)</small>

<small>[IHealthResultError](Documentation/Type/IHealthResultError.md)</small>

<small>[IHealthResultResponse](Documentation/Type/IHealthResultResponse.md)</small>