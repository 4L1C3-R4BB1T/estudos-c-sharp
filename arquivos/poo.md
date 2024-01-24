🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

```cs
// sealed - inibe que uma classe possa ser herdada por outra

sealed class MinhaClasse { }

public class Pessoa
{
    public string Nome { get; set; }
    public string Email { get; set; }
    
    public Pessoa(string nome, string email)
    {   
        Nome = nome;
        Email = email;
    }
    
    // método que será sobrescrito ou herdado
    public virtual void ExibirClasse()
    {
        Console.WriteLine("Pessoa");
    }
}

// herança
public class Funcionario : Pessoa
{
    public string Empresa { get; set; }
    public decimal Salario { get; set; }
    
    // usando o construtor da classe herdada
    public Funcionario(string nome, string email, string empresa) : base(nome, email) 
    {
        Empresa = empresa;
    }
    
    // sobrescrita
    public override void ExibirClasse()
    {
        Console.WriteLine("Funcionario");
    }
    
    // sobrescrita
    public override string ToString()
    {
      return $"{base.Nome} - {base.Email} - {Empresa}";
    }
}

Funcionario f = new Funcionario("João", "joao@email.com", "Ifes");
    
Console.WriteLine(f);
f.ExibirClasse();
```

---

### 🔸 Herança Múltipla

* Ocorre quando temos uma classe base e uma classe derivada que implementa uma ou mais interfaces.

```cs
class Forma
{
    public void SetLado(int s)
    {
        lado = s;
    }
    protected int lado;
}

interface ICusto
{
    int GetCusto(int area);
}

class Quadrado : Forma, ICusto
{
    public int GetArea()
    {
        return lado * lado;
    }
    public int GetCusto(int area)
    {
        return area * 10;
    }
}
```