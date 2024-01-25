🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

```cs
try
{
    // código que pode gerar erro
}
catch (TypeException e)
{
    // captura a exceção gerada
}
catch (TypeException e)
{
    // captura a exceção gerada
}
...
finally
{
    // executado sempre
}


throw new Exception("Lançando uma exceção");
```

---

### 🔸 Exception Filters

```cs
try
{
    // código passível de erro
}
catch (Exception e) when (Filtro/Critério/Condição)
{
    // ação
}


try 
{
    int i = 10 / "a";
}
catch (Exception e) when (e.Message.Contains("format"))
{
    Console.WriteLine(e.Message);
}
```

---

```cs
using System.Net.Http;

try 
{
    string arquivo = "poesia.txt";
    string url = "https://macoratti.net/dados";

    HttpClient client = new HttpClient();
    HttpResponseMessage response = client.GetAsync(url + "/" + arquivo).Result;

    if (response.IsSuccessStatusCode)
    {
        Console.WriteLine("Sucesso\nCódigo de Status: " + response.StatusCode);
    }
    else
    {
        throw new HttpRequestException("Erro: " + (int) response.StatusCode);
    }
}
catch (HttpRequestException e) when (e.Message.Contains("404"))
{
    Console.WriteLine("Página não encontrada");
}
catch (HttpRequestException e) when (e.Message.Contains("401"))
{
    Console.WriteLine("Acesso não autorizado");
}
catch (HttpRequestException e) when (e.Message.Contains("400"))
{
    Console.WriteLine("Requisição inválida");
}
catch (HttpRequestException e) when (e.Message.Contains("500"))
{
    Console.WriteLine("Erro interno do servidor");
}
catch (Exception e) 
{
    Console.WriteLine("Erro: " + e.Message);
}
finally
{
    Console.WriteLine("Processamento concluído");
}
```

---

### 🔸 Exceções Personalizadas

```cs
public class MinhaExcecaoException : Exception
{
    public MinhaExcecaoException() { }

    public MinhaExcecaoException(string message) : base(message) { }

    public MinhaExcecaoException(string message, Exception inner) : base(message, inner) { }
}

throw new MinhaExcecaoException("Minha exceção personalizada");
```
