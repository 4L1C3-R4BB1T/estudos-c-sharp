🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 Generics

```cs
NomeTipo<T>

public class ClasseGenerica<T> { }

public void MetodoGenerico<T>(T a) { }

// restrições (constraints)
NomeTipo<T> where T : <restrição>

public class ClasseGenerica<T> where T : struct { }

public void MetodoGenerico<T>(T a) where T : class { }
```

---

### 🔸 Equals e HashCode

```cs
public class Pessoa
{
    public Pessoa(int cpf, string nome)
    {
        CPF = cpf;
        Nome = nome;
    }

    public int CPF { get; set; }
    public string? Nome { get; set; }

    public override bool Equals(object? obj)
    {
        if (obj == null ) return false;

        if (obj is not Pessoa) return false;

        var other = (Pessoa) obj;

        return CPF.Equals(other.CPF);
    }

    public override int GetHashCode()
    {
        return CPF.GetHashCode();
    }
}
```