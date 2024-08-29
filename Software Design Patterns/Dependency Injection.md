A dependency is an object that another object depends on. For example the following `MyDependency` class with a `WriteMessage` method that other classes depend on:

```cs
public class MyDependency
{
    public void WriteMessage(string message)
    {
        Console.WriteLine($"MyDependency.WriteMessage called. Message: {message}");
    }
}
```

A class can create an instance of the `MyDependency` class to make use of its `WriteMessage` method. In the following example, the `MyDependency` class is a dependency of the `IndexModel` class:

```cs
public class IndexModel : PageModel
{
    private readonly MyDependency _dependency = new MyDependency();

    public void OnGet()
    {
        _dependency.WriteMessage("IndexModel.OnGet");
    }
}
```

The class creates and directly depends on the `MyDependency` class. Code dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:

1. To replace `MyDependency` with a different implementation, the `IndexModel` class must be modified.
2. If `MyDependency` has dependencies, they must also be configured by the `IndexModel` class. In a large project with multiple classes depending on `MyDependency`, the configuration code becomes scattered across the app.
3. This implementation is difficult to unit test.

Dependency injection addresses these problems through:

1. The use of an interface or base class to abstract the dependency implementation.
2. Registration of the dependency in a service container. ASP.NET Core provides a built-in service container, `IServiceProvider`. Services are typically registered in the app's `Program.cs` file.
3. Injection of a service into the constructor of the class where it's used. The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.

The sample app registers the `IMyDependency` service with the concrete type `MyDependency`. The `AddScoped` method registers the service with a scoped lifetime, the lifetime of a single request.

```cs
using DependencyInjectionSample.Interfaces;
using DependencyInjectionSample.Services;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddRazorPages();

builder.Services.AddScoped<IMyDependency, MyDependency>();

var app = builder.Build();
```