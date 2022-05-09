# Development notes for .Net

### Managing Secrets

https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-6.0&tabs=linux

### Enable secret storage

In the project folder  type `dotnet user-secrets init` and press ENTER.
#### List all projects secret

In the project folder  type `dotnet user-secrets list` and press ENTER.


#### Add an secret to the project


In the project folder type `dotnet user-secrets set "ConnectionStrings:SqlServer" "Server=(local);Database=myDb;User=sa;Password=1234;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=Yes"` and press ENTER.

#### Remove an specific secret

In the project folder  type `dotnet user-secrets remove "ConnectionStrings:SqlServer"` and press ENTER


#### Remove all secrets from project

In the project folder  type `dotnet user-secrets clear` and press ENTER

