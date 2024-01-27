🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 File 

```cs
using System.IO;

// string verbatim
string caminho = @"C:\MeusArquivos\arquivo.txt";

// criar arquivo
File.Create(caminho);

// escrever no arquivo
File.WriteAllText(caminho, "texto");

string texto = "asdasd";

// adicionar texto no arquivo
File.AppendAllText(caminho, texto);

// ler conteúdo do arquivo 
File.ReadAllText(caminho);

// última modificação do arquivo
File.GetLastWriteTime(caminho);

// último acesso ao arquivo
File.GetLastAccessTime(caminho);

// ler cada linha do arquivo
File.ReadAllLines(caminho);

// copiar arquivo
File.Copy(caminhoOrigem, caminhoCopia);

// mover arquivo
File.Move(caminhoOrigem, caminhoDestino);

// deletar arquivo
File.Delete(caminho);

// verificar se o arquivo existe
File.Exists(caminho);
```

---

### 🔸 FileInfo 

```cs
FileInfo fi = new FileInfo(caminho);

// nome do arquivo
fi.Name;

// diretório pai
fi.Directory;

// copiar arquivo
fi.CopyTo(caminhoCopia);

// mover arquivo
fi.MoveTo(caminhoDestino);
```

---

### 🔸 Directory

```cs
// verifica se o diretório existe
Directory.Exists(caminho);

// criar diretório
Directory.CreateDirectory(caminho);

// deletar diretório
Directory.Delete(caminho);

// retornar os subdiretórios
Directory.GetDirectories(caminho);
Directory.GetDirectories(caminho, filtro);

// retornar os arquivos
Directory.GetFiles(caminho);
Directory.GetFiles(caminho, filtro);

// mover diretório
Directory.Move(caminhoOrigem, caminhoDestino);
```

---

### 🔸 DirectoryInfo

```cs
DirectoryInfo di = new DirectoryInfo(caminho);

// nome do diretório
di.Name;

// criar diretório
di.Create();

// deletar diretório
di.Delete();

// retornar os subdiretórios
di.GetDirectories();

// retornar os arquivos
di.GetFiles();

// criar subdiretório
di.CreateSubdirectory();
```

---

### 🔸 Path

```cs
string caminho = "C:\\MeusArquivos\\arquivo.txt";
char dirSeparator = Path.DirectorySeparatorChar;
string[] diretorios = caminho.Split(dirSeparator);

Path.Combine(path1, path2);

Path.GetDirectoryName(path);
```

---

### 🔸 Streams

```cs
// FileStream
FileStream fs = new FileStream(caminho, FileMode.Open, FileAccess.Read, FileShare.Read);

// File 
FileStream fs = File.Open(caminho, FileMode.Open, FileAccess.Read, FileShare.Read);

// FileInfo
FileInfo fi = new FileInfo(caminho);
FileStream fs = fi.Open(FileMode.Open, FileAccess.Read, FileShareRead);
```

* Bloco **using** *(garante que os objetos sejam fechados automaticamente quando o bloco terminar de ser executado)*

```cs
using (FileStream fs = new FileStream(caminho, FileMode.Open))
{
    // operações de leitura e gravação no arquivo usando o objeto FileStream
}

using FileStream fs = new FileStream(caminho, FileMode.Open);
```
