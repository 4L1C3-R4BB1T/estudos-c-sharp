### Criar projeto

```bash
dotnet new console -o NomeDoProjeto

# criar uma solução 
dotnet new sln -o <nome_solução>

# criar um projeto dentro da solução (entrar na pasta da solução)
dotnet new <nome_template> -o <nome_projeto>

# incluir o projeto criado na solução existente (a partir da pasta da solução)
dotnet sln <nome_solução>.sln add <pasta_projeto>/<arquivo>.csproj
```

### Executar o código 

```bash
dotnet run 
```

### Escolher a versão do .NET SDK

```bash
# criar um arquivo global.json
dotnet new globaljson --sdk-version <versão> --force

# cria projeto especificando a versão instalada do .NET SDK
dotnet new console -o MeuApp -f .net5.0
dotnet new console -o MeuApp -f .net6.0

# cria projeto .NET 6/7 usando o método Main na classe Program
dotnet new console -o MeuApp --use-program-main
```

### Convenções

* **lastName**: parâmetros de métodos, variáveis dentro de métodos  
* **LastName**: namespaces, classe, properties, métodos  
* **_lastName**: atributos internos da classe  

