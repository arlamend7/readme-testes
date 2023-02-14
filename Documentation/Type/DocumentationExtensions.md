<h4 style='color: gray;margin:0; padding:0;'> [Briefcase.System, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null]</h4>

#### <small>namespace [Briefcase.System.Extensions](../Namespace/Briefcase.System.Extensions.md);</small>

#### <small>DocumentationExtensions</small>

<i>

```csharp
public static class DocumentationExtensions
{

	///<summary>
	///	Provides the documentation comments for a specific method
	///</summary>
	///<returns>The XML fragment describing the method</returns>
	public static XmlElement GetDocumentation(MethodInfo methodInfo); +2 overloads

	///<summary>
	///	Returns the Xml documenation summary comment for this member
	///</summary>
	public static String GetSummary(MemberInfo memberInfo); +1 overloads

	///<summary>
	///	Obtains the documentation file for the specified assembly
	///</summary>
	///<returns>The XML document</returns>
	public static XmlDocument XmlFromAssembly(Assembly assembly); 
}
```

</i>


---

#### GetDocumentation

<small><b>Return:</b> XmlElement</small>

<small>The XML fragment describing the method</small>

<small><b>Summary</b></small>

<small>Provides the documentation comments for a specific method
</small>

<i>

```csharp
public static class DocumentationExtensions
{

	///<summary>
	///	Provides the documentation comments for a specific method
	///</summary>
	///<returns>The XML fragment describing the method</returns>
	///<param name='methodInfo'>The MethodInfo (reflection data ) of the member to find documentation for</param>
	public static XmlElement GetDocumentation(MethodInfo methodInfo);

	///<summary>
	///	Provides the documentation comments for a specific member
	///</summary>
	///<returns>The XML fragment describing the member</returns>
	///<param name='memberInfo'>The MemberInfo (reflection data) or the member to find documentation for</param>
	public static XmlElement GetDocumentation(MemberInfo memberInfo);

	///<summary>
	///	Provides the documentation comments for a specific type
	///</summary>
	///<returns>The XML fragment that describes the type</returns>
	///<param name='type'>Type to find the documentation for</param>
	public static XmlElement GetDocumentation(Type type);
}
```

</i>

---

#### GetSummary

<small><b>Return:</b> String</small>

<small><b>Summary</b></small>

<small>Returns the Xml documenation summary comment for this member
</small>

<i>

```csharp
public static class DocumentationExtensions
{

	///<summary>
	///	Returns the Xml documenation summary comment for this member
	///</summary>
	///<param name='memberInfo'></param>
	public static String GetSummary(MemberInfo memberInfo);

	///<summary>
	///	Gets the summary portion of a type's documenation or returns an empty string if not available
	///</summary>
	///<param name='type'></param>
	public static String GetSummary(Type type);
}
```

</i>