<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Retrivers](../Namespace/Briefcase.System.Retrivers.md);</small>

#### <small>RetriverHelperInterface</small>

<i>

```csharp
public class RetriverHelperInterface : RetriverHelperBase, IEnumerable<ValueTuple<Type, IEnumerable<Type>>>, IEnumerable
{

	///<DeclaredOn>RetriverHelperBase</DeclaredOn>
	IEnumerable<Type> Types { get; set; }

	public RetriverHelperInterface(Type type); 

	public RetriverHelperInterface On(Assembly[] assemblies); +1 overloads

	public RetriverHelperInterface Where(Func<Type, Type, Boolean> condition); 

	public RetriverHelperInterface WhereImplementItAsOneOfInterface(); 

	public IEnumerator<ValueTuple<Type, IEnumerable<Type>>> GetEnumerator(); 

	///<DeclaredOn>RetriverHelperBase</DeclaredOn>
	public RetriverHelperInterface AsInterface(); 

	///<DeclaredOn>RetriverHelperBase</DeclaredOn>
	public RetriverHelper AsClass(); 
}
```

</i>


---

#### On

<small><b>Return:</b> RetriverHelperInterface</small>

<i>

```csharp
public class RetriverHelperInterface : RetriverHelperBase, IEnumerable<ValueTuple<Type, IEnumerable<Type>>>, IEnumerable
{

	public RetriverHelperInterface On(Assembly[] assemblies);

	public RetriverHelperInterface On(Type[] types);
}
```

</i>

#### <small>Related items</small>

[IEnumerable<ValueTuple<Type, IEnumerable<Type>>>](IEnumerable`1.md)
[IEnumerable](IEnumerable.md)
[RetriverHelperBase](RetriverHelperBase.md)