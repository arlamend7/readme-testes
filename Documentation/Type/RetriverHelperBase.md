<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Retrivers](../Namespace/Briefcase.System.Retrivers.md);</small>

#### <small>RetriverHelperBase</small>

<i>

```csharp
public class RetriverHelperBase
{

	IEnumerable<Type> Types { get; set; }

	public RetriverHelperBase(Type type); 

	public RetriverHelperInterface AsInterface(); 

	public RetriverHelper AsClass(); 
}
```

</i>
