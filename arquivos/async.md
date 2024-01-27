🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 Task e Task\<T> 

```cs
using System.Threading.Tasks;

public async Task MeuMetodoAsync()
{
    await Task.Delay(1000);
    Console.WriteLine("Concluído");
}

await MeuMetodoAsync();
```

```cs
using System.Threading.Tasks;

public async Task<int> MeuMetodoAsync()
{
    await Task.Delay(1000);
    Console.WriteLine("Concluído");
    return 1;
}

var resultado = await MeuMetodoAsync();
```

---

### 🔸 ValueTask e ValueTask\<T> 

```cs
using System.Threading.Tasks;

public async ValueTask MetodoSemRetornoAsync()
{
    Console.WriteLine("Método que não retorna valor");
    await Task.Delay(2000);
}
```

```cs
using System.Threading.Tasks;

public async ValueTask<int> MetodoRetornaValorAsync(int valor)
{
    Console.WriteLine("Método que retorna valor");
    await Task.Delay(2000);
    return valor * 2;
}
```
