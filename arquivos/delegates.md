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
