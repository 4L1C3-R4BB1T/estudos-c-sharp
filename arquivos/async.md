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

---

### 🔸 Cancelamento de tarefas

* **Task.Run()** - enfileira o trabalho especificado para execução no **ThreadPool** e retorna uma tarefa (Task) ou identificador **Task\<T>** para esse trabalho.

```cs
private static Task<int> OperacaoLongaDuracao(int valor, CancellationToken cancellationToken = default)
{
    Task<int> task = null;
    task = Task.Run(() => 
    {
        int resultado = 0;
        for (int i = 0; i < valor; i++)
        {
            if (cancellationToken.IsCancellationRequested)
            {
                throw new TaskCanceledException(task);
            }
            Thread.Sleep(10);
            resultado += i; 
        }
        return resultado;
    });
    return task;
}
```

```cs
public static async Task ExecutaCancelamentoComTimeout(int tempo)
{
    using (var cancellationTokenSource = new CancellationTokenSource(tempo))
    {
        try
        {
            var resultado = await OperacaoLongaDuracaoCancelavel(100, cancellationTokenSource.Token);
            Console.WriteLine(resultado);
        }
        catch (TaskCanceledException)
        {
            throw;
        }
    }
}
```

```cs
public static async Task ExecutaCancelamentoComTimeout(int tempo)
{
    using (var cancellationTokenSource = new CancellationTokenSource())
    {
        cancellationTokenSource.CancelAfter(tempo);
        try
        {
            var resultado = await OperacaoLongaDuracaoCancelavel(100, cancellationTokenSource.Token);
            Console.WriteLine(resultado);
        }
        catch (TaskCanceledException)
        {
            throw;
        }
    }
}
```

```cs
cancellationTokenSource.Cancel();
```
