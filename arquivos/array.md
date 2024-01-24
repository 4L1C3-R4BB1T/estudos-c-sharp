🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 Arrays

```cs
int[] numeros = new int[5] { 1, 2, 3, 4, 5 };

foreach (tipo elemento in coleção) { }

Array.Reverse(array);
Array.Sort(array);
Array.BinarySearch(array, obj);

NomeDoMetodo(params tipo[] nomeDaVariavel) { }
NomeDoMetodo(arg1, arg2, arg3, arg4 ...);

int[,] arr = new int[2,2] { { 0, 1 }, { 2, 3 } };
```

---

### 🔸 ArrayList

```cs
using System.Collections;

ArrayList arraylist = new ArrayList();
ArrayList arraylist = new ArrayList(5);

var lista = new ArrayList() { "A", 4.5, true };

arraylist.Add("a");
arraylist.Insert(index, value);
arraylist.AddRange(array);
arraylist.InsertRange(index, array);
arraylist.Remove(value);
arraylist.RemoveAt(index);
arraylist.RemoveRange(index, count);
arraylist.Contains(value);
arraylist.Sort();
arraylist.Clear();
```

---

### 🔸 List

```cs
using System.Collections.Generic;

List<T> list = new List<T>();

List<string> lista = new List<string>();

lista.Add("a");
lista.Insert(index, value);
lista.AddRange(array);
lista.InsertRange(index, array);
lista.Remove(value);
lista.RemoveAt(index);
lista.RemoveRange(index, count);
lista.Contains(value);
lista.Sort();
lista.Clear();

List<string> frutas = new() { "Uva", "Banana", "Laranja" };

// public T? Find(Predicate<T> match);

frutas.Find(f => f.Contains('n'));
frutas.FindLast(f => f.Contains('n'));
frutas.FindIndex(f => f.Contains('n'));
frutas.FindLastIndex(f => f.Contains('n'));
frutas.FindAll(f => f.Contains('n'));
```

---

### 🔸 List e ArrayList

* **Boxing**: É a conversão de um *Value Type* para um *Reference Type*.

```cs
int num = 23;
Object obj = num; // Boxing 
```

* **Unboxing**: É quando um *Reference Type (object)* volta a ser um *Value Type*. 

```cs
int num = 23;
Object obj = num; // Boxing 
int i = (int) obj; // Unboxing
```

---

### 🔸 IEnumerable<T>

```cs
var lista2 = lista1.Where(x => x.function()).ToList();

var lista2 = lista1.FirstOrDefault();
```
