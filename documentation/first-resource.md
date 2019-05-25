# **First resource**

Creating your first resource, is very simple. 
All you need is a new **.NET Core 2.2 Class library** with a reference to our NuGet package, more information below.

## Step 0 - Prepare solution and project

The simplest way to prepare the project is by using the `dotnet` CLI. You can skip this step, if you use Visual Studio. 

We call our resource, in this example, "MyFirstResource".

```
$ dotnet new sln --name MyFirstResource
$ dotnet new classlib --name MyFirstResource --framework netcoreapp2.2
$ dotnet sln MyFirstResource.sln add MyFirstResource
```

## Step 1 - Install NuGet package

To get started, you need to reference the latest [AlternateLife.RageMP.Net NuGet package](https://www.nuget.org/packages/AlternateLife.RageMP.Net).

```
$ dotnet add MyFirstResource package AlternateLife.RageMP.Net
```

## Step 2 - Main class

The server is only able to find your resource, if you create a **single** class that implements our interface [IResource](~/api/AlternateLife.RageMP.Net.Scripting.IResource.yml). The class could look like this.

> [!NOTE]
> This class needs to have a parameterless-constructor, otherwise it is not startable.

```cs
using System.Threading.Tasks;
using AlternateLife.RageMP.Net.Scripting;

namespace MyFirstResource
{
    public class Main : IResource
    {
        public Main()
        {
            // Register events here or load everything, that needs to be loaded before the first player connects.
        }

        public async Task OnStartAsync()
        {
            // Load everything else like houses, cars or other things.
        }

        public async Task OnStopAsync()
        {
            // Save everything before the server will be stopped completely.
        }
    }
}
```

## Step 3 - Prepare resource

To finish your first resource, you need to copy your compiled `.dll` files to the server's resource folder. If you want to create a resource from the example above, the folder structure looks like this:

```text
├── ...
├── dotnet/
|   ├── resources/
|   |   └── firstresource/
|   |       └── MyFirstResource.dll
|   └── ..
├── ...
```

## Step 4 - Start server

The resource should be ready and startable. You can now edit the resource even more and implement your own logic.