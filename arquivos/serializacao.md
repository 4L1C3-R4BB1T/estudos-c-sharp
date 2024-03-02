🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 Serialização

* É o processo de conversão do estado de um objeto em um formato que possa ser armazenado e/ou transportado.

---

### 🔸 Desserialização

* É o processo recerso da serialização, que converte um fluxo de bytes (stream) em um objeto.

---

### 🔸 XML

```cs
public class Aluno
{
    public int Id { get; set; }
    public string Name { get; set; } = string.Empty;
    public string Email { get; set; } = string.Empty;
    public int Idade;

    public Aluno { }

    public Aluno(int id, string name, string email, int idade)
    {
        Id = id;
        Name = name;
        Email = email;
        Idade = idade;
    }
}

using System.Xml.Serialization;

Aluno aluno1 = new Aluno(101, "Maria", "maria@email.com", 17);

string path = @"path\arquivo.xml";

XmlSerializer serializer = new XmlSerializer(typeof(Aluno));

// serializar
using (StreamWriter writer = new XmlSerializer(path))
{
    serializer.Serialize(writer, aluno1);
}

// desserializar
using (StreamReader reader = new XmlSerializer(path))
{
    var aluno = (Aluno) serializer.Deserialize(reader);
}
```

---

### 🔸 JSON

```cs
public class Aluno
{
    public int Id { get; set; }
    public string Name { get; set; } = string.Empty;
    public string Email { get; set; } = string.Empty;
    public int Idade;

    public Aluno { }

    public Aluno(int id, string name, string email, int idade)
    {
        Id = id;
        Name = name;
        Email = email;
        Idade = idade;
    }
}

using System.Text.Json;

Aluno aluno1 = new Aluno(101, "Maria", "maria@email.com", 17);

string path = @"path\arquivo.json";

// serializar
using FileStream stream = new FileStream(path, FileMode.OpenOrCreate, FileAccess.ReadWrite)
{
    JsonSerializer.Serialize(stream, aluno1);
}

// desserializar
string jsonContent = File.ReadAllText(path);

var aluno = JsonSerializer.Deserialize<Aluno>(jsonContent);
```
