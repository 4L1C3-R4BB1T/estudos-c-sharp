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

### Convenções

* lastName: parâmetros de métodos, variáveis dentro de métodos  
* LastName: namespaces, classe, properties, métodos  
* _lastName: atributos internos da classe  

