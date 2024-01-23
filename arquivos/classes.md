🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

```cs
class Pessoa
{
    public static int IdadeMinima;

    public string Nome;
    public int Idade;
    public string Sexo;

    public Pessoa(string nome) => Nome = nome;
    
    public Pessoa(string nome, int idade, string sexo): this(nome)
    {
        Idade = idade;
        Sexo = sexo;
    }

    static Pessoa() 
    {
        Console.WriteLine("Construtor estático");
        IdadeMinima = 18;
    }

    public void Saudacao() => Console.WriteLine("Ola");
    
    public static void Saudacao(string nome, string data) => 
        Console.WriteLine($"Ola {nome}, hoje é dia {data}.");

    public void ExibirData() => Console.WriteLine(DateTime.Now);

    public string ExibirDataNascimento() 
    {
        return DateTime.Now.AddYears(-Idade).ToShortDateString();
    }
}

Pessoa p = new Pessoa("João", 10, "M"); // Pessoa p = new();

p.Saudacao();
p.ExibirData();
Console.WriteLine(p.ExibirDataNascimento());

Pessoa.Saudacao("Livia", DateTime.Now.ToShortDateString());

Console.WriteLine(Pessoa.IdadeMinima);
```

---

### 🔸 Parâmetros entre Classes

```cs
public class Aluno
{
    public string Nome;
    public int Idade;
    public string Aprovado;

    public Aluno(string nome, int idade, string aprovado) {
        Nome = nome;
        Idade = idade;
        Aprovado = aprovado;
    }
}

public class Curso 
{
    public void Resultado(Aluno a)
    {
        Console.Write($"O aluno {a.Nome}, com {a.Idade} anos foi ");
        Console.WriteLine(a.Aprovado == "S" ? "aprovado." : "reprovado.");
    }
}

Aluno a = new Aluno("Maria", 22, "S");
Curso c = new Curso();
c.Resultado(a);
```

---

### 🔸 Passagem de argumentos por referência

```cs
funcao(ref x);

funcao(out x); // transfere dados para fora do método

public class Circulo
{
    public double CalculaAreaPerimetro(double raio, out double area)
    {
        area = Math.PI * Math.Pow(raio, 2);
        double perimetro = 2 * Math.PI *  raio;
        return perimetro;
    }
}

Circulo c = new Circulo();

double circunferencia = c.CalculaAreaPerimetro(5, out double area);
Console.WriteLine("Perimetro: " + circunferencia);
Console.WriteLine("Área: " + area);
```

---

### 🔸 Argumentos nomeados

```cs
public class Email
{
    public void Enviar(string destino, string titulo, string assunto)
    {
        Console.WriteLine($"{destino}, {titulo}: {assunto}");
    }
}

Email e = new Email();
e.Enviar(destino: "teste@email.com", assunto: "Reunião Orçamento", titulo: "Urgente");
```

---

### 🔸 Parâmetros opcionais

```cs
public class Email
{
    public void Enviar(string destino, string titulo = "Reunião", string assunto = "Avaliação")
    {
        Console.WriteLine($"{destino}, {titulo}: {assunto}");
    }
}

Email e = new Email();
e.Enviar(destino: "teste@email.com");
e.Enviar(destino: "teste@email.com", titulo: "Orçamento");
```

---

### 🔸 Campos estáticos

```cs
public class A
{
    public int x;
    public static int y;
}

A a1 = new A();
a1.x = 10;

A a2 = new A();
a2.x = 20;

A.y = 30;

Console.WriteLine($"a1.x = {a1.x} a2.x = {a2.x} A.y = {A.y}");
```

---

### 🔸 Propriedades

```cs
public class Pessoa
{
    private string nome; // campo
    public string Nome { 
        get { return nome.ToUpper(); }
        set { nome = value; } 
    } // propriedade 
}

Pessoa p = new Pessoa();
p.Nome = "Pedro";    
Console.WriteLine(p.Nome);
```

---

### 🔸 Structs

```cs
public struct Pessoa
{
    public string? Nome { get; set; }
    public int Idade { get; set; }

    public Pessoa(string? nome, int idade)
    {
        Nome = nome;
        Idade = idade;
    }
}
```
