<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Builders](../Namespace/Briefcase.System.Builders.md);</small>

#### <small>BuilderOf<T></small>

<i>

```csharp
public abstract class BuilderOf<T> : IBuilderOf<T>, IDisposable
{

	T Value { get; set; }

	public BuilderOf`1(BuilderOf<T> builder); 

	public T Build(); 

	public Void Dispose(); 
}
```

</i>


#### <small>Related items</small>

[IBuilderOf<T>](IBuilderOf`1.md)
[IDisposable](IDisposable.md)