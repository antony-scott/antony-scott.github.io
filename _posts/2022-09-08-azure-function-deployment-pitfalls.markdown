---
layout: post
title:  "Azure Function Deployment Pitfalls"
date:   2022-09-08 12:56 +0100
categories: Azure
---
# Azure Function Deployment Pitfalls

![](https://upload.wikimedia.org/wikipedia/en/0/06/Pitfall%21_Coverart.png)

---

## Argh! It works on my machine, but when I deploy to Azure there are no functions listed

### Problem:
This is because the folder layout of the zip file isn't quite right and by default includes the project name and target framework.

For example - `\landingPageApp\netcoreapp3.1\bin`

### Solution:
Add the below to your `.csproj` file

```xml
  <PropertyGroup>
    <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
  </PropertyGroup>
```

---

## It just says `Function host is not running`

### Problem:
This is caused by the functionapp being unable to startup.

### Solution (1):
Instead of using something like this in your startup code ...

```csharp
    var basePath = "WEBSITE_INSTANCE_ID".EnvironmentVariable().IsNullOrEmpty()
        ? Environment.CurrentDirectory
        : "/home/site/wwwroot";
```

... make use of `IOptions<ExecutionContextOptions>` like so ...

```csharp
    var rootFolder = builder
        .Services
        .BuildServiceProvider()
        .GetService<IOptions<ExecutionContextOptions>>()
        .Value
        .AppDirectory;
```

Obviously, you could probably do this in a cleaner way by using DI to simply take a dependency on `IOptions<ExecutionContextOptions>` and get the `.Value.AppDirectory` property, for example ...

```csharp
    public MyConfigService(IOptions<ExecutionContextOptions> executionContextOptions)
    {
        var config = AppConfigHelper.GetConfig(executionContextOptions.Value.AppDirectory);
        ...
    }
```
