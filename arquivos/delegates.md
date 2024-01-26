🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 Delegates

* Um **delegate** é um tipo que *representa referências a  métodos* com um **lista de parâmetros** e um **tipo de retorno** específicos. 

* Ao instanciar um **delegate**, podemos *associar a sua instância a qualquer método* com uma **assinatura compatível e tipo de retorno**, e, podemos invocar o método por meio da *instância delegada*.

* Os **delegates** são usados para implementar *eventos, métodos de retorno de chamada e para passar métodos como argumentos para outros métodos*.

```cs
[modificador de acesso] delegate [tipo de retorno][nomedo delegate]([parâmetros])

public delegate void MeuDelegate(string mensagem);

// atribuir o método de destino 
MeuDelegate del1 = new MeuDelegate(MeuMetodo);
del1.Invoke("Minha mensagem");

// ou
MeuDelegate del2 = MeuMetodo;
del2("Minha mensagem");

// ou define uma expressão lambda
MeuDelegate del3 = (msg) => Console.WriteLine(msg); 
del3("Minha mensagem");

// método de destino
static void MeuMetodo(string msg) { }
```

---

### 🔸 Multicast Delegate

* **SingleCast Delegate**: delegate que referencia e invoca um único método.

* **MultiCastDelegate**: delegate que referencia e invoca mais de um método.

```cs
MeuDelegate delMult = new MeuDelegate(Metodo1);
delMult += Metodo2; // -= remove um método do delegate
delMult("Olá, multicast delegate!");

static void Metodo1(string mensagem) { }

static void Metodo2(string mensagem) { }

public delegate void MeuDelegate(string mensagem);
```

---

### 🔸 Métodos Anônimos

```cs
Imprimir imprimir = delegate (int valor)
{
    Console.WriteLine($"Método anônimo. Valor: {valor}");
};

imprimir(100);

public delegate void Imprimir(int valor);
```

---

### 🔸 Expressão Lambda

```cs
(parâmetros de entrada) => {expressão ou bloco de instrução};
```

---

### 🔸 Delegates: Predicate, Action e Func

```cs
public delegate bool Predicate<in T>(T obj);

public delegate void Action<in T>(T obj);

public delegate TResult Func<in T1, in T2, ..., out TResult>(T1 arg, T2 arg, ...);  
```

---

### 🔸 Eventos

* Publisher / Subscriber.

```cs
public delegate void PedidoEventHandler();

public class Pedido
{
    public event PedidoEventHandler OnCriarPedido;

    public void CriarPedido()
    {
        Console.WriteLine("Pedido criado !!!");

        if (OnCriarPedido != null)
        {
            OnCriarPedido();
        }
    }
}

public class Email 
{
    public static void Enviar()
    {
        Console.WriteLine("Enviando um email");
    }
}

public class SMS
{
    public static void Enviar()
    {
        Console.WriteLine("Enviando um SMS");
    }
}

Console.WriteLine("Usando o evento OnCriarPedido");

var pedido = new Pedido();

pedido.OnCriarPedido += Email.Enviar;
pedido.OnCriarPedido += SMS.Enviar;

pedido.CriarPedido();
```

---

### 🔸 EventHandler

```cs
public class Pedido
{
    public event EventHandler OnCriarPedido;

    public void CriarPedido()
    {
        Console.WriteLine("Pedido criado !!!");

        if (OnCriarPedido != null)
        {
            OnCriarPedido(this, EventArgs.Empty);
        }
    }
}

public class Email 
{
    public static void Enviar(object sender, EventArgs e)
    {
        Console.WriteLine("Enviando um email");
    }
}

public class SMS
{
    public static void Enviar(object sender, EventArgs e)
    {
        Console.WriteLine("Enviando um SMS");
    }
}

Console.WriteLine("Usando o evento OnCriarPedido");

var pedido = new Pedido();

pedido.OnCriarPedido += Email.Enviar;
pedido.OnCriarPedido += SMS.Enviar;

pedido.CriarPedido();
```

---

### 🔸 EventHandler<TEventArgs>

```cs
public class PedidoEventArgs : EventArgs
{
    public string Email { get; set; }
    public string Telefone { get; set; }
}

public class Pedido
{
    public event EventHandler<PedidoEventArgs> OnCriarPedido;

    public void CriarPedido(string email, string fone)
    {
        Console.WriteLine("Pedido criado !!!");

        if (OnCriarPedido != null)
        {
            OnCriarPedido(this, new PedidoEventArgs{ Email = email, Telefone = fone });
        }
    }
}

public class Email 
{
    public static void Enviar(object sender, PedidoEventArgs e)
    {
        Console.WriteLine($"Enviando um email para : {e.Email}");
    }
}

public class SMS
{
    public static void Enviar(object sender, PedidoEventArgs e)
    {
        Console.WriteLine($"Enviando um SMS para : {e.Telefone}");
    }
}

Console.WriteLine("Usando o evento OnCriarPedido");

var pedido = new Pedido();

pedido.OnCriarPedido += Email.Enviar;
pedido.OnCriarPedido += SMS.Enviar;

pedido.CriarPedido("email@email.com", "(11) 11111-1111");
```

---

### 🔸 Métodos de extensão

```cs
public static class StringExtensions
{
    public static string InverteString(this string str)
    {
        char[] charArray = str.ToCharArray();
        Array.Reverse(charArray);
        return new string(charArray);
    }
}

using <namespace_da_classe_StringExtensions>;

string nome = "teste";
string stringInvertida = nome.InverteString();
Console.WriteLine(stringInvertida);
```
