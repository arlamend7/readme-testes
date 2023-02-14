<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Delegates](../Namespace/Briefcase.System.Delegates.md);</small>

#### <small>TryConvert<T, TResult></small>

<i>

```csharp
public sealed class TryConvert<T, TResult> : MulticastDelegate, ICloneable, ISerializable
{

	///<DeclaredOn>Delegate</DeclaredOn>
	Object Target { get; }

	///<DeclaredOn>Delegate</DeclaredOn>
	MethodInfo Method { get; }

	public TryConvert`2(Object object, IntPtr method); 

	public Boolean Invoke(T value, out TResult result); 

	public IAsyncResult BeginInvoke(T value, out TResult result, AsyncCallback callback, Object object); 

	public Boolean EndInvoke(out TResult result, IAsyncResult __result); 

	///<DeclaredOn>MulticastDelegate</DeclaredOn>
	public Void GetObjectData(SerializationInfo info, StreamingContext context); 

	///<DeclaredOn>MulticastDelegate</DeclaredOn>
	public Boolean Equals(Object obj); 

	///<DeclaredOn>MulticastDelegate</DeclaredOn>
	public Delegate[] GetInvocationList(); 

	///<DeclaredOn>MulticastDelegate</DeclaredOn>
	public Int32 GetHashCode(); 

	///<DeclaredOn>Delegate</DeclaredOn>
	public Object Clone(); 

	///<DeclaredOn>Delegate</DeclaredOn>
	public Object DynamicInvoke(Object[] args); 
}
```

</i>


#### <small>Related items</small>

[ICloneable](ICloneable.md)
[ISerializable](ISerializable.md)
[MulticastDelegate](MulticastDelegate.md)