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

---

### 🔸 Tratamento de exceções

```cs
await LancaExceptionAsync();

static async Task LancaExceptionAsync()
{
    // try-catch dentro do método assíncrono
    try 
    {
        var primeiraTask = Task.Run(() => 
        {
            Task.Delay(1000);
            throw new IndexOutOfRangeException("Exception lançada");
        });
        // aguarda a execução e garante a captura da exceção
        await primeiraTask; 
    }
    catch (Exception e)
    {
        Console.WriteLine(e.Message);
    }
}
```

* **Múltiplas Exceções**

```cs
await LancaMultiplasExcecoesAsync();

static async Task LancaMultiplasExcecoesAsync()
{
    Task? tarefas = null;
    try
    {
        var primeiraTask = Task.Run(() =>
        {
            Task.Delay(1000);
            throw new IndexOutOfRangeException("Exceção 1");
        });
        var segundaTask = Task.Run(() =>
        {
            Task.Delay(1000);
            throw new InvalidOperationException("Exceção 2");
        });
        tarefas = Task.WhenAll(primeiraTask, segundaTask);
        await tarefas;
    }
    catch
    {
        AggregateException TodasExceptions = tarefas.Exception;
        foreach (var e in TodasExceptions.InnerExceptions)
        {
            Console.WriteLine(e.GetType().ToString());
        }
    }
}
```
