<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Asyncronuos.Interfaces](../Namespace/Briefcase.System.Asyncronuos.Interfaces.md);</small>

#### <small>IResultAsyncCreator<T></small>

<i>

```csharp
public interface IResultAsyncCreator<T> : IResultAsync<T>, IEnumerable<T>, IEnumerable, IDisposable
{

	public IResultAsyncCreator<T> Add(T consolidateValue); +1 overloads

	public IResultAsyncCreator<T> Append(T consolidateValue); +1 overloads

	public IResultAsyncCreator<T> AddRange(IEnumerable<Func<T>> func); 
}
```

</i>


---

#### Add

<small><b>Return:</b> IResultAsyncCreator\<T></small>

<i>

```csharp
public interface IResultAsyncCreator<T> : IResultAsync<T>, IEnumerable<T>, IEnumerable, IDisposable
{

	public IResultAsyncCreator<T> Add(T consolidateValue);

	public IResultAsyncCreator<T> Add(Func<T> func);
}
```

</i>

---

#### Append

<small><b>Return:</b> IResultAsyncCreator\<T></small>

<i>

```csharp
public interface IResultAsyncCreator<T> : IResultAsync<T>, IEnumerable<T>, IEnumerable, IDisposable
{

	public IResultAsyncCreator<T> Append(T consolidateValue);

	public IResultAsyncCreator<T> Append(Func<T> func);
}
```

</i>

#### <small>Related items</small>

[IResultAsync<T>](IResultAsync`1.md)
[IEnumerable<T>](IEnumerable`1.md)
[IEnumerable](IEnumerable.md)
[IDisposable](IDisposable.md)