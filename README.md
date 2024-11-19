# ApiMinimaC-
Desenvolvimento API Mínima com C# .NET

## Adicionar Swagger
Use o Swagger para garantir que você tenha uma API autodocumentada, na qual os documentos são alterados conforme você altera o código.

### Instale o pacote Swashbuckle:
dotnet add package Swashbuckle.AspNetCore --version 6.5.0

### Abra o projeto no Visual Studio Code:
code .

### No Visual Studio Code, no painel do explorer, abra PizzaStore.csproj. Você deverá ter uma entrada parecida com esta:
<PackageReference Include="Swashbuckle.AspNetCore" Version="6.5.0" />

Em seguida, configure seu projeto para usar o Swagger.
Abra Program.cs e adicione o código realçado. Salve as alterações:

using Microsoft.OpenApi.Models;

var builder = WebApplication.CreateBuilder(args);
    
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen(c =>
{
     c.SwaggerDoc("v1", new OpenApiInfo { Title = "PizzaStore API", Description = "Making the Pizzas you love", Version = "v1" });
});
    
var app = builder.Build();
    
if (app.Environment.IsDevelopment())
{
   app.UseSwagger();
   app.UseSwaggerUI(c =>
   {
      c.SwaggerEndpoint("/swagger/v1/swagger.json", "PizzaStore API V1");
   });
}
    
app.MapGet("/", () => "Hello World!");
    
app.Run();

### Navegue até o ponto de extremidade swagger do aplicativo, http://localhost:{PORT}/swagger.
