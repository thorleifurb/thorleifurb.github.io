# Create **thorough** Open API Definition with XML Comments in ASP .NET Core 5

I have the following requirement in project that I am working on.
* Provide REST services against a data source. (ASP.NET Core)
* Document the services **thoroughly**. (OpenAPI)

In addition I need to set customable fields in OpenAPI description.

## Tools

I use Visual Studio 2019 to implement these REST Services. 
For OpenAPI documentation I use middleware, At least 2 options are popular.
* Swashbuckle See https://github.com/domaindrivendev/Swashbuckle.AspNetCore
* NSwag. See https://github.com/RicoSuter/NSwag.
Both options provide the ability to generate OpenAPI from XML comments in code.

## Steps
Following are the steps taken in order to create **thorough** OpenAPI specification of a REST service.

### Create project
Create Asp.Net Project as defined in the following tutorial from Microsoft.
https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-5.0&tabs=visual-studio

### Install Documentation middleware (Swashbuckle or NSwag)
You need to deside which midleware to use in OpenAPI documentation.

#### Add Swashbuckle to project
There is good description of how to do that in Microsoft documentation.
https://docs.microsoft.com/en-us/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-5.0&tabs=visual-studio

In the Project sample the default is to use Swashbuckle.AspNetCore, so the NuGet package is already added to the project.

#### Add NSwag to project
There is good description of how to do that in Microsoft documentation.
https://docs.microsoft.com/en-us/aspnet/core/tutorials/getting-started-with-nswag?view=aspnetcore-5.0&tabs=visual-studio 

I used NuGet package manager to install  NSwag.AspNetCore to the project.
Since the SwashBuckle and NSWag do not coexist, you need to remove SwashBuckle when you add NSwag.

### Add OpenAPI documentation to REST service

Since the changes on code is slightly different, depending on usage of SwashBuckle or NSwag, we look at each option.

## OpenAPI with Swashbuckle

Following are the steps to enable OpenAPI generation with Swashbuckle.
There is detailed description in https://docs.microsoft.com/en-us/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-5.0&tabs=visual-studio.
In the project sample the default is to use Swashbuckle.AspNetCore, so the NuGet package was already added to the project.

### Add Document Generation from XML comments to project

Change projects csproj file and add following to property groups.

```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
	<GenerateDocumentationFile>true</GenerateDocumentationFile>
	<NoWarn>$(NoWarn);1591</NoWarn>
  </PropertyGroup>
```

Note that when GenerateDocumentationFile is set as true, there is greated warning for all undocumented public types and members.
To suppress warnings project-wide, define a semicolon-delimited list of warning codes to ignore in the project file. 
Appending the warning codes to $(NoWarn); applies the C# default values too. Warnings can also be ignored for specific members.
See chapter XML comments in https://docs.microsoft.com/en-us/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-5.0&tabs=visual-studio.

### Use Swashbuckle OpenAPI Comments
I change service ConfigureServices in startup.cs to Include XML Context by adding the following code
<pre>
<code class="lang-csharp" highlight-lines="2">
    function main() {
        __config_bash
        __config_xdg_dirs
    }
</code>
</pre>

```csharp
	// Set the comments path for the Swagger JSON and UI.
	var xmlFile = $"{Assembly.GetExecutingAssembly().GetName().Name}.xml";
	var xmlPath = Path.Combine(AppContext.BaseDirectory, xmlFile);
	c.IncludeXmlComments(xmlPath);
```

The full service is then the following code.

```csharp
	// This method gets called by the runtime. Use this method to add services to the container.
	public void ConfigureServices(IServiceCollection services)
	{
		services.AddControllers();
		services.AddSwaggerGen(c =>
		{
			c.SwaggerDoc("v1", new OpenApiInfo { Title = "SampleAPI", Version = "v1" });
```
			<div style="margin:0; background-color:powderblue;">
```csharp
			// Set the comments path for the Swagger JSON and UI.
			var xmlFile = $"{Assembly.GetExecutingAssembly().GetName().Name}.xml";
			var xmlPath = Path.Combine(AppContext.BaseDirectory, xmlFile);
			c.IncludeXmlComments(xmlPath);
```
			</div style="margin:0; background-color:powderblue;">
```csharp
		});
	}
```



## OpenAPI with NSwag

## OpenAPI middleware for .NET Core. (NSwag)

### Difference

1. Swahbucle does not show example on Class.
