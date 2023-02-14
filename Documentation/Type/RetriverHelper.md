<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Retrivers](../Namespace/Briefcase.System.Retrivers.md);</small>

#### <small>RetriverHelper</small>

<i>

```csharp
public class RetriverHelper : RetriverHelperBase, IEnumerable<Type>, IEnumerable
{

	///<DeclaredOn>RetriverHelperBase</DeclaredOn>
	IEnumerable<Type> Types { get; set; }

	public RetriverHelper(Type type); 

	///<summary>
	///	Um teste por ai
	///</summary>
	///<returns> um retorno qualquer </returns>
	public RetriverHelper On(Type[] types); +1 overloads

	public static RetriverHelperBase Get(); +1 overloads

	public RetriverHelper WhereIsAssignedFromIt(); 

	public RetriverHelper WhereIsAssignedToIt(); 

	public IEnumerator<Type> GetEnumerator(); 

	///<DeclaredOn>RetriverHelperBase</DeclaredOn>
	public RetriverHelperInterface AsInterface(); 

	///<DeclaredOn>RetriverHelperBase</DeclaredOn>
	public RetriverHelper AsClass(); 
}
```

</i>


---

#### On

<small><b>Return:</b> RetriverHelper</small>

<small> um retorno qualquer </small>

<small><b>Summary</b></small>

<small>Um teste por ai
</small>

<i>

```csharp
public class RetriverHelper : RetriverHelperBase, IEnumerable<Type>, IEnumerable
{

	public RetriverHelper On(Assembly[] assemblies);

	///<summary>
	///	Um teste por ai
	///</summary>
	///<returns> um retorno qualquer </returns>
	///<param name='types'> tipagens</param>
	public RetriverHelper On(Type[] types);
}
```

</i>

---

#### Get

<small><b>Return:</b> RetriverHelperBase</small>

<i>

```csharp
public class RetriverHelper : RetriverHelperBase, IEnumerable<Type>, IEnumerable
{

	public static RetriverHelperBase Get();

	public static RetriverHelperBase Get(Type type);
}
```

</i>

#### <small>Related items</small>

[IEnumerable<Type>](IEnumerable`1.md)
[IEnumerable](IEnumerable.md)
[RetriverHelperBase](RetriverHelperBase.md)