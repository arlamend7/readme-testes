<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Reflections](../Namespace/Briefcase.System.Reflections.md);</small>

#### <small>PropertyGetter<T></small>

<i>

```csharp
public class PropertyGetter<T> : IEnumerable<PropertyInfo>, IEnumerable, IDisposable, IPropertyGetter<T>
{

	public PropertyGetter<T> For(Expression<Func<T, TProp>> expression); 

	public IEnumerator<PropertyInfo> GetEnumerator(); 

	public Void Dispose(); 
}
```

</i>


#### <small>Related items</small>

[IEnumerable<PropertyInfo>](IEnumerable`1.md)
[IEnumerable](IEnumerable.md)
[IDisposable](IDisposable.md)
[IPropertyGetter<T>](IPropertyGetter`1.md)