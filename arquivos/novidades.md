🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 Aliases com diretivas using para tipos adicionais

```cs
using Ponto3D = (int, int, int);
Ponto3D ponto3D = (1, 2, 3);
Console.WriteLine($"{ponto3D.Item1}, {ponto3D.Item2}, {ponto3D.Item3}");
```

---

### 🔸 Inicializando arrays

```cs
int[] numeros = [1, 2, 3, 4];

List<int> lista1 = [1, 2, 3];
List<int> lista2 = [4, 5, 6];
List<int> listaCombinada = [.. lista1, .. lista2];
```

---

### 🔸 Construtores primários

```cs
public class Aluno(string nome, string sobrenome, int nota)
{
    public string Nome { get; set; } = nome;
    public string Sobrenome { get; set; } = sobrenome;
    public int Nota { get; set; } = nota;

    public string NomeCompleto => $"{Nome} {Sobrenome}";
}
```

---

### 🔸 Required members

```cs
public class Pessoa
{
    public required string Nome { get; set; }
    public required int Idade { get; set; }

    [SetsRequiredMembers]
    public Pessoa(string nome, int idade)
    {
        Nome = nome;
        Idade = idade;
    }
}
```

---

### 🔸 Extended nameof scope

```cs
[MeuAtributo(nameof(meuParametro))]
public void MeuMetodoComParametros(string meuParametro) { }
```
