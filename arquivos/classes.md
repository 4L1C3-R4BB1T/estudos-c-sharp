🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

```cs
class Pessoa
{
    public string Nome;
    public int Idade;
    public string Sexo;

    public Pessoa(string nome) => Nome = nome;
    
    public Pessoa(string nome, int idade, string sexo): this(nome)
    {
        Idade = idade;
        Sexo = sexo;
    }

    public void Saudacao() => Console.WriteLine("Ola");
    
    public void Saudacao(string nome, string data) => 
        Console.WriteLine($"Ola {nome}, hoje é dia {data}.");

    public void ExibirData() => Console.WriteLine(DateTime.Now);

    public string ExibirDataNascimento() 
    {
        return DateTime.Now.AddYears(-Idade).ToShortDateString();
    }
}

Pessoa p = new Pessoa("João", 10, "M"); // Pessoa p = new();

p.Saudacao();
p.Saudacao("Livia", DateTime.Now.ToShortDateString());
p.ExibirData();
Console.WriteLine(p.ExibirDataNascimento());
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
```
