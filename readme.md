<h3 style='color: gray;margin:0; padding:0;'> [Briefcase.Handlers, Version=0.1.2.0, Culture=neutral, PublicKeyToken=null]</h3>

#### Configuration

If you want to separete the code and configuration you can create classes with configuration and import it on code.
<i>

```csharp
public class Person
{
    public int Id { get; set; }
    public int Age { get; set; }
    public string Name { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string CompleteName { get; set; }
}
public class PersonInsertRequest
{
    public string CompleteName { get; set; }
    public string Birthdate { get; set; }
}

public class PersonHandlerConfiguration : EditHandlerCustomConfigutation<Person>
{
    public override void ConfigureRules(IEditHandlerConfigurationBuilder<Person> builder)
    {
        builder
       .ForProperty(x => x.Id, builder => builder.Ignore())
       .ForProperty(x => x.FirstName, builder =>
       {
           return builder
                   .FormatAfterChanged(prop => prop.ToLower())
                   .ThrowErrorIfValueIs("caleb", "O nome não pode ser Caleb")
                   .ThrowErrorIfValueIs("arlan", "O nome não pode ser arlan")
                   .ThrowErrorIfValue(prop => prop.EndsWith("zinho"), prop => $"o nome {prop} finaliza com zinho, isto não é permitido!")
                   .Conclude;
       })
       .ForProperty(x => x.Age, builder =>
       {
           return builder
                       .IgnoreIfValueIs(0)
                       .Conclude;
       });
    }
}
public class PersonMapperHandlerConfiguration : IEditHandlerMapperConfigurarion<Person, PersonInsertRequest>
{
    public void ConfigureMapper(IMapperConfigurationBuilder<Person, PersonInsertRequest> builder)
    {
        builder
            .ForProperty(person => person.Age, propertyMapper =>
            {
                return propertyMapper
                            .MapFrom(request => request.Birthdate)
                            .IgnoreDefaultValue()
                            .ConvertUsing(Convert, "data não é valida para conversão")
                            .ConvertUsing(GetAgeByBirthdate, "a data é maior que hoje");
            })
            .ForProperty(person => person.FirstName, propertyMapper =>
            {
                return propertyMapper
                            .MapFrom(request => request.CompleteName)
                            .ConvertUsing(x => x.Split(" ").First());
            });

        builder.ForProperty(person => person.LastName, propertyMapper =>
        {
            return propertyMapper
                        .MapFrom(request => request.CompleteName)
                        .IgnoreDefaultValue()
                        .ConvertUsing(x => x.Split(" ").Last());
        });

        builder.ForProperty(person => person.CompleteName, propertyMapper =>
        {
            return propertyMapper
                        .MapFrom(request => request.CompleteName)
                        .IgnoreDefaultValue()
                        .UseSameValue;
        });
    }

    public DateTime Convert(string dataString)
    {
        return DateTime.Parse(dataString);
    }

    public int GetAgeByBirthdate(DateTime data)
    {
        return (int)Math.Floor((DateTime.Now - data).TotalDays / 365);
    }
}

void Main()
{
    var configurationBuilder = new PersonHandlerConfiguration()
                                .Builder();

    configurationBuilder.SetMapper(new PersonMapperHandlerConfiguration());

    IEditHandler<Person> personHandler = new EditHandler<Person>(configurationBuilder.Build());
}
```

</i>


or you can make everything together, so use the method CreateUsing of IEditHandler<T>
<i>

```csharp
public class Person
{
    public int Id { get; set; }
    public int Age { get; set; }
    public string Name { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string CompleteName { get; set; }
}

public class PersonInsertRequest
{
    public string CompleteName { get; set; }
    public string Birthdate { get; set; }
}

void Main()
{
    IEditHandler<Person> editHandler
        = IEditHandler<Person>.CreateUsing(builder =>
        {
            builder
              .ForProperty(x => x.Id, builder => builder.Ignore())
              .ForProperty(x => x.FirstName, builder =>
              {
                  return builder
                          .FormatAfterChanged(prop => prop.ToLower())
                          .ThrowErrorIfValueIs("caleb", "O nome não pode ser Caleb")
                          .ThrowErrorIfValueIs("arlan", "O nome não pode ser arlan")
                          .ThrowErrorIfValue(prop => prop.EndsWith("zinho"), prop => $"o nome {prop} finaliza com zinho, isto não é permitido!")
                          .Conclude;
              })
              .ForProperty(x => x.Age, builder =>
              {
                  return builder
                              .IgnoreIfValueIs(0)
                              .Conclude;
              })
              .CreateMapper<PersonInsertRequest>(builder =>
              {
                  builder
                       .ForProperty(person => person.Age, propertyMapper =>
                       {
                           return propertyMapper
                                       .MapFrom(request => request.Birthdate)
                                       .IgnoreDefaultValue()
                                       .ConvertUsing<DateTime>(DateTime.TryParse, "data não é valida para conversão")
                                       .ConvertUsing(data => (int)Math.Floor((DateTime.Now - data).TotalDays / 365), "a data é maior que hoje");
                       })
                       .ForProperty(person => person.FirstName, propertyMapper =>
                       {
                           return propertyMapper
                                       .MapFrom(request => request.CompleteName)
                                       .ConvertUsing(x => x.Split(" ").First());
                       });

                      builder.ForProperty(person => person.LastName, propertyMapper =>
                      {
                          return propertyMapper
                                      .MapFrom(request => request.CompleteName)
                                      .IgnoreDefaultValue()
                                      .ConvertUsing(x => x.Split(" ").Last());
                      });

                      builder.ForProperty(person => person.CompleteName, propertyMapper =>
                      {
                          return propertyMapper
                                      .MapFrom(request => request.CompleteName)
                                      .IgnoreDefaultValue()
                                      .UseSameValue;
                      });
              });
        });
}

```

</i>


#### How to use


<i>

```csharp
IEditHandler<Person> personHandler = null; // use your configuration
//or
IEditHandler handlers = null;// use your configuration

var insertRequest = new PersonInsertRequest()
{
    CompleteName = "Arlan dos Santo Franklin Mendes",
    Birthdate = "000"
};

var person = new Person()
{
    FirstName = "Caleb",
    Age = 29
};

using IEditHandlerOperation<Person> operation = personHandler.Edit(person);

operation.EditBy(insertRequest);

operation.OrderBy(getter =>
{
    getter.For(x => x.Age);
    getter.For(x => x.FirstName);
    getter.For(x => x.LastName);
});

var error = operation.FirstOrDefault(x => x.IsError);

if (error != null && error is IHandledMessaged messaged)
{
    throw new Exception(messaged.Message);
}

var ageChange = operation.GetChangeFor(x => x.Age);

if(ageChange != null)
{
    Console.WriteLine($"The property age was changed from {ageChange.LastValue} to {ageChange.Value}");
}

foreach (var handles in operation.ForProperty(x => x.Age))
{
    // all operations for age;
}

person = operation.GetResultEntityFor("Age", "FirstName", "CompleteName");
person = operation.GetResultEntity(getter =>
{
    getter.For(x => x.Age);
    getter.For(x => x.FirstName);
    getter.For(x => x.LastName);
});

person = operation.ResultEntity;

```

</i>


#### Assembly information


#### Namespace [Briefcase.Handlers](Namespace/Briefcase.Handlers.md);

##### Classes

<small>[EditHandler<T>](Documentation/Type/EditHandler`1.md)</small>

#### Namespace [Briefcase.Handlers.Operations.Base.Interfaces](Namespace/Briefcase.Handlers.Operations.Base.Interfaces.md);

##### Interfaces

<small>[IEditResultChanges<T>](Documentation/Type/IEditResultChanges`1.md)</small>

<small>[IEditResultOrdenableChanges<T>](Documentation/Type/IEditResultOrdenableChanges`1.md)</small>

<small>[IEditResultTimeLiner<T>](Documentation/Type/IEditResultTimeLiner`1.md)</small>

#### Namespace [Briefcase.Handlers.Interfaces](Namespace/Briefcase.Handlers.Interfaces.md);

##### Interfaces

<small>[IEditHandler](Documentation/Type/IEditHandler.md)</small>

<small>[IEditHandler<T>](Documentation/Type/IEditHandler`1.md)</small>

<small>[IEditHandlerOperation<T>](Documentation/Type/IEditHandlerOperation`1.md)</small>

#### Namespace [Briefcase.Handlers.Handleds.Interfaces](Namespace/Briefcase.Handlers.Handleds.Interfaces.md);

##### Interfaces

<small>[IHandled](Documentation/Type/IHandled.md)</small>

<small>[IHandledChange](Documentation/Type/IHandledChange.md)</small>

<small>[IHandledMessaged](Documentation/Type/IHandledMessaged.md)</small>

<small>[IMapperHandled](Documentation/Type/IMapperHandled.md)</small>

#### Namespace [Briefcase.Handlers.Handleds.Extensions](Namespace/Briefcase.Handlers.Handleds.Extensions.md);

##### Classes

<small>[HandledStopStageEnumExtensions](Documentation/Type/HandledStopStageEnumExtensions.md)</small>

##### Extensions

HandledStopStageEnum.IsIgnored();

HandledStopStageEnum.IsError();

#### Namespace [Briefcase.Handlers.Handleds.Enums](Namespace/Briefcase.Handlers.Handleds.Enums.md);

##### Classes

<small>[HandledStopStageEnum](Documentation/Type/HandledStopStageEnum.md)</small>

#### Namespace [Briefcase.Handlers.Handleds.Creators.Interfaces](Namespace/Briefcase.Handlers.Handleds.Creators.Interfaces.md);

##### Interfaces

<small>[IHandledCreator](Documentation/Type/IHandledCreator.md)</small>

#### Namespace [Briefcase.Handlers.Customizes](Namespace/Briefcase.Handlers.Customizes.md);

##### Classes

<small>[EditHandlerCustomConfigutation<T>](Documentation/Type/EditHandlerCustomConfigutation`1.md)</small>

#### Namespace [Briefcase.Handlers.Customizes.Interfaces](Namespace/Briefcase.Handlers.Customizes.Interfaces.md);

##### Interfaces

<small>[IEditHandlerCustomConfigutation](Documentation/Type/IEditHandlerCustomConfigutation.md)</small>

<small>[IEditHandlerCustomConfigutation<T>](Documentation/Type/IEditHandlerCustomConfigutation`1.md)</small>

<small>[IEditHandlerMapperConfigurarion<T, TMapper>](Documentation/Type/IEditHandlerMapperConfigurarion`2.md)</small>

#### Namespace [Briefcase.Handlers.Configurations](Namespace/Briefcase.Handlers.Configurations.md);

##### Classes

<small>[EditHandlerConfiguration](Documentation/Type/EditHandlerConfiguration.md)</small>

<small>[EditHandlerConfiguration<T>](Documentation/Type/EditHandlerConfiguration`1.md)</small>

<small>[MapperConfiguration](Documentation/Type/MapperConfiguration.md)</small>

<small>[PropertyConfiguration](Documentation/Type/PropertyConfiguration.md)</small>

<small>[PropertyMapperConfiguration](Documentation/Type/PropertyMapperConfiguration.md)</small>

<small>[ThrowErrorIf](Documentation/Type/ThrowErrorIf.md)</small>

<small>[TryConvertMessage](Documentation/Type/TryConvertMessage.md)</small>

<small>[IgnoreifMessage](Documentation/Type/IgnoreifMessage.md)</small>

#### Namespace [Briefcase.Handlers.Builder.Interfaces](Namespace/Briefcase.Handlers.Builder.Interfaces.md);

##### Interfaces

<small>[IEditHandlerConfigurationBuilder](Documentation/Type/IEditHandlerConfigurationBuilder.md)</small>

<small>[IEditHandlerConfigurationBuilder<T>](Documentation/Type/IEditHandlerConfigurationBuilder`1.md)</small>

<small>[IMapperConfigurationBuilder](Documentation/Type/IMapperConfigurationBuilder.md)</small>

<small>[IMapperConfigurationBuilder<T, TRequest>](Documentation/Type/IMapperConfigurationBuilder`2.md)</small>

<small>[IPropertyConfigBuilder<T, TProp>](Documentation/Type/IPropertyConfigBuilder`2.md)</small>

<small>[IPropertyConfigInfoBuilder<T, TProp>](Documentation/Type/IPropertyConfigInfoBuilder`2.md)</small>

<small>[IPropertyConfigNoPropertyBuilder<T, TProp>](Documentation/Type/IPropertyConfigNoPropertyBuilder`2.md)</small>

<small>[IPropertyMapperBuilder<TProp>](Documentation/Type/IPropertyMapperBuilder`1.md)</small>

<small>[IPropertyMapperBuilder<T, TRequest, TProp>](Documentation/Type/IPropertyMapperBuilder`3.md)</small>

<small>[IPropertyMapperConvertBuilder<T, TProp, TRequest, TRequestProp>](Documentation/Type/IPropertyMapperConvertBuilder`4.md)</small>

<small>[IPropertyMapperConvertBuilderConverted<TRequest, TRequestProp, TProp>](Documentation/Type/IPropertyMapperConvertBuilderConverted`3.md)</small>

#### Namespace [Briefcase.Handlers.Base](Namespace/Briefcase.Handlers.Base.md);

##### Classes

<small>[EditHandlerBase](Documentation/Type/EditHandlerBase.md)</small>