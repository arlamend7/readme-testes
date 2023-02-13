<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.HealthCheck, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.HealthCheck](..\Namespace\Briefcase.HealthCheck.md);</small>

#### <small>HealthExecution</small>

<i>

```csharp
public class HealthExecution : HealthExecutionBase
{

	///<summary>
	///	Com certeza voce vai usar
	///</summary>
	///<returns>é uma lista</returns>
	public static List<IHealthResult> ExecuteHealthly(ValueTuple<String, Func<Task<Object>>>[] healthTests); +1 overloads

	public static IHealthResult ExecuteHealthly(String methodName, Func<Task<T>> Process); +11 overloads
}
```

</i>


---

#### ExecuteHealthly

<small><b>Return:</b> List\<IHealthResult></small>

<small>é uma lista</small>

<small><b>Summary</b></small>

<small>Com certeza voce vai usar
</small>

<i>

```csharp
public class HealthExecution : HealthExecutionBase
{

	///<summary>
	///	Com certeza voce vai usar
	///</summary>
	///<returns>é uma lista</returns>
	public static List<IHealthResult> ExecuteHealthly(ValueTuple<String, Func<Task<Object>>>[] healthTests);

	public static List<IHealthResult> ExecuteHealthly(ValueTuple<String, Func<Task>>[] healthTests);
}
```

</i>

---

#### ExecuteHealthly

<small><b>Return:</b> IHealthResult</small>

<i>

```csharp
public class HealthExecution : HealthExecutionBase
{

	public static IHealthResult ExecuteHealthly(Func<Task<T>> Process);

	public static IHealthResult ExecuteHealthly(Func<Task> Process);

	public static IHealthResult ExecuteHealthly(Func<T> Process);

	public static IHealthResult ExecuteHealthly(Task<T> Process);

	public static IHealthResult ExecuteHealthly(Action Process);

	public static IHealthResult ExecuteHealthly(Task Process);

	public static IHealthResult ExecuteHealthly(String methodName, Func<Task<T>> Process);

	public static IHealthResult ExecuteHealthly(String methodName, Func<Task> Process);

	public static IHealthResult ExecuteHealthly(String methodName, Func<T> Process);

	public static IHealthResult ExecuteHealthly(String methodName, Task<T> Process);

	public static IHealthResult ExecuteHealthly(String methodName, Action Process);

	public static IHealthResult ExecuteHealthly(String methodName, Task Process);
}
```

</i>

#### <small>Related items</small>

[HealthExecutionBase](HealthExecutionBase.md)