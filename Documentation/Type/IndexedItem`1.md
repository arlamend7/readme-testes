<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Models](../Namespace/Briefcase.System.Models.md);</small>

#### <small>IndexedItem<T></small>

<i>

```csharp
public sealed IndexedItem<T> : ValueType
{

	T Value { get; }

	Int32 Index { get; }

	public IndexedItem`1(T value, Int32 index); 

	///<DeclaredOn>ValueType</DeclaredOn>
	public Boolean Equals(Object obj); 

	///<DeclaredOn>ValueType</DeclaredOn>
	public Int32 GetHashCode(); 

	///<DeclaredOn>ValueType</DeclaredOn>
	public String ToString(); 
}
```

</i>


#### <small>Related items</small>

[ValueType](ValueType.md)