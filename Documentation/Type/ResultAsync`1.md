<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Asyncronuos](../Namespace/Briefcase.System.Asyncronuos.md);</small>

#### <small>ResultAsync<T></small>

<i>

```csharp
public class ResultAsync<T> : IResultAsyncCreator<T>, IResultAsync<T>, IEnumerable<T>, IEnumerable, IDisposable
{

	IEnumerable<T> Values { get; }

	IEnumerable<T> ManuallyAddedValues { get; }

	List<Func<T>> Funcs { get; set; }

	List<T> ExecutedValues { get; set; }

	Int32 ExecutedLength { get; }

	Int32 NotExecutedLength { get; }

	Int32 ManuallyValuesAdded { get; }

	public static IResultAsyncCreator<T> Create(); 

	public IResultAsyncCreator<T> AddRange(IEnumerable<Func<T>> func); 

	public IResultAsyncCreator<T> Add(Func<T> func); +1 overloads

	public IResultAsyncCreator<T> Append(Func<T> func); +1 overloads

	public Void Dispose(); 
}
```

</i>


---

#### Add

<small><b>Return:</b> IResultAsyncCreator\<T></small>

<i>

```csharp
public class ResultAsync<T> : IResultAsyncCreator<T>, IResultAsync<T>, IEnumerable<T>, IEnumerable, IDisposable
{

	public IResultAsyncCreator<T> Add(Func<T> func);

	public IResultAsyncCreator<T> Add(T consolidateValue);
}
```

</i>

---

#### Append

<small><b>Return:</b> IResultAsyncCreator\<T></small>

<i>

```csharp
public class ResultAsync<T> : IResultAsyncCreator<T>, IResultAsync<T>, IEnumerable<T>, IEnumerable, IDisposable
{

	public IResultAsyncCreator<T> Append(Func<T> func);

	public IResultAsyncCreator<T> Append(T consolidateValue);
}
```

</i>

#### <small>Related items</small>

[IResultAsyncCreator<T>](IResultAsyncCreator`1.md)
[IResultAsync<T>](IResultAsync`1.md)
[IEnumerable<T>](IEnumerable`1.md)
[IEnumerable](IEnumerable.md)
[IDisposable](IDisposable.md)