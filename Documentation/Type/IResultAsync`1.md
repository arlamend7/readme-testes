<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Asyncronuos.Interfaces](../Namespace/Briefcase.System.Asyncronuos.Interfaces.md);</small>

#### <small>IResultAsync<T></small>

<i>

```csharp
public interface IResultAsync<T> : IEnumerable<T>, IEnumerable, IDisposable
{

	Int32 ExecutedLength { get; }

	Int32 NotExecutedLength { get; }

	Int32 ManuallyValuesAdded { get; }
}
```

</i>


#### <small>Related items</small>

[IEnumerable<T>](IEnumerable`1.md)
[IEnumerable](IEnumerable.md)
[IDisposable](IDisposable.md)