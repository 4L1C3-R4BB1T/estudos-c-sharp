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

---

```cs
Forma f = new Circulo(); // upcasting
Circulo c = (Circulo) new Forma(); // downcasting

Circulo c = f as Circulo; // downcasting

if (forma is Circulo) { ... } // verifica se o downcast é possível
```

---

### 🔸 Classe Abstrata

```cs
public abstract class MinhaClasse 
{ 
    public abstract tipo NomeMetodo();    
}

public abstract class Forma 
{
    public string Cor { get; set; }
    public double Area { get; set; }
    public double Perimetro { get; set; }

    // métodos abstratos 
    public abstract void CalcularArea();
    public abstract void CalcularPerimetro();

    public string Descricao()
    {
        return "Sou a classe abstrata Forma";
    }
}

public class Quadrado : Forma
{
    public double Lado { get; set; }

    public override void CalcularArea()
    {
        this.Area = Lado * Lado;
    }

    public override void CalcularPerimetro()
    {
        this.Perimetro = 4 * Lado;
    }
}
```

---

### 🔸 Interfaces

* Uma classe pode herdar múltiplas interfaces.

```cs
interface IControle
{
    void Desenhar();
    void Exibir() {...};
}

interface IGrafico
{
    void Pintar();
}

public class Demo : IControle, IGrafico
{
    public void Desenhar() { ... }
    public void Pintar() { ... }
}
```

---

### 🔸 Composição 

* Relacionamento do tipo **"Tem um"**. Representa uma relação **todo - parte**.

```cs
public class Casa
{
    private readonly Telhado _telhado;
    private readonly Alicerce _alicerce;

    public Casa() 
    {
        _telhado = new Telhado();
        _alicerce = new Alicerce();
    }
}

public class Telhado { }
public class Alicerce { }
```

---

### 🔸 Agregação 

* Relacionamento do tipo **"Tem um"**. Representa uma relação **todo - parte**.

* A **parte** e o **todo** são independentes.

* A **parte** pode existir sem o **todo**.

```cs
public class Professor 
{
    public string Nome { get; set; }
    public string Disciplina { get; set; }
}

public class Departamento 
{
    public string Nome { get; set; }
    public List<Professor> Professores { get; set; }

    public void IncluirProfessor(Professor professor)
    {
        Professores.Add(professor);
    }
}
```

---

### 🔸 Polimorfismo

* Sobrecarga ou Sobrescrita.
