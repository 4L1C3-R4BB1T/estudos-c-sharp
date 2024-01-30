🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 LINQ - Language Integrated Query

* **Sintaxe de Consulta**

```cs
using System.Linq;
using System.Collections.Generic;

List<string> frutas = new List<string>() { "Banana", "Manga", "Laranja" };
var resultado = from f in frutas
                where f.Contains('r')
                select f;

```

* **Sintaxe de Método**

```cs
List<string> frutas = new List<string>() { "Banana", "Manga", "Laranja" };
var resultado = frutas.Where(f => f.Contains('r'));
```

---

```cs
int[] numeros = [1, 2, 3, 4];
var resultado = numeros.Where(n => n < 3);
var resultado = numeros.Where(n => n < 3 && != 4);
```

```cs
IEnumerable<string> nomes = FonteDados.GetAlunos().Select(n => n.Nome);
```

```cs
int[] numeros = {1, 1, 1, 2, 3, 3, 4};
var resultado = numeros.Distinct();
```

```cs
List<int> lista1 = new List<int>() {1, 2, 3, 4, 5, 6};
List<int> lista2 = new List<int>() {1, 3, 5, 8, 9, 10};
var resultado = lista1.Intersect(lista2).ToList();
```

```cs
List<int> lista1 = new List<int>() {1, 2, 3, 4, 5, 6};
List<int> lista2 = new List<int>() {1, 3, 5, 8, 9, 10};
var resultado = lista1.Union(lista2).ToList();
```

```cs
List<int> lista = new List<int>() {10, 2, 5, 1, 8};
var resultado = lista.OrderBy(n => n).ToList();
var resultado = lista.OrderByDescending(n => n).ToList();
```

```cs
int[] numeros = {1, 2, 3, 4, 5, 6};
var resultado = numeros.Reverse();
``` 

```cs
int[] numeros = {1, 2, 3, 4, 5, 6};
var resultado = numeros.Aggregate((n1, n2) => n1 * n2);
```

```cs
List<string> frutas = new List<string>() { "Banana", "Manga", "Laranja" };
var resultado = frutas.Count();
```

```cs
int[] numeros = {1, 2, 3, 4, 5, 6};
var resultado = numeros.Sum();
```

```cs
int[] numeros = {1, 2, 3, 4, 5, 6};
var resultado = numeros.Max(n => n);
var resultado = numeros.Min(n => n);
```
