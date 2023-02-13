<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.HealthCheck, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.HealthCheck](../Namespace/Briefcase.HealthCheck.md);</small>

#### <small>HealthExecutionBase</small>

<i>

```csharp
public abstract class HealthExecutionBase
{

	public static IHealthResult ExecuteTaskHealthly(Func<Task<Object>> task, out Object result, out Exception exception); +1 overloads
}
```

</i>


---

#### ExecuteTaskHealthly

<small><b>Return:</b> IHealthResult</small>

<i>

```csharp
public abstract class HealthExecutionBase
{

	public static IHealthResult ExecuteTaskHealthly(Func<Task> task, out Exception exception);

	public static IHealthResult ExecuteTaskHealthly(Func<Task<Object>> task, out Object result, out Exception exception);
}
```

</i>