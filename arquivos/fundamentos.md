🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 Tipos de Dados

```cs
int valor1 = 123;
const int valor2 = 123;

byte n1 = 255;
sbyte n2 = -127;
int n3 = -129134;
uint n4 = 129134;
long n5 = -12389134;

double n6 = 1.234;
float n7 = 1.234f; 
decimal n8 = 1.234m;

bool ativo = true;
bool inativo = false;

char c = 'a';

string nome = "Curso C#";

object nota = 10;
object valor = 8.55m;
object nome1 = "Maria";
object ativa = true;

// reflection
dynamic nota = 10;
dynamic valor = 8.55m;
dynamic nome1 = "Maria";
dynamic ativa = true;
```

---

### 🔸 DateTime

```cs
DateTime dataAtual = DateTime.Now;
DateTime dataHoje = new DateTime(2024, 01, 22); // aaaa, mm, dd
DateTime dataHoraHoje = new DateTime(2024, 01, 22, 16, 37, 24); // aaaa, mm, dd, hh, mm, ss

Console.WriteLine(dataAtual.Year);
Console.WriteLine(dataAtual.Month);
Console.WriteLine(dataAtual.Day);
Console.WriteLine(dataAtual.Hour);
Console.WriteLine(dataAtual.Minute);
Console.WriteLine(dataAtual.Second);
Console.WriteLine(dataAtual.Millisecond);

Console.WriteLine(dataAtual.AddDays(30));
Console.WriteLine(dataAtual.AddMonths(1));
Console.WriteLine(dataAtual.AddHours(2));
Console.WriteLine(dataAtual.AddYears(5));

Console.WriteLine(dataAtual.DayOfWeek);
Console.WriteLine(dataAtual.DayOfYear);

Console.WriteLine(dataAtual.ToLongDateString());
Console.WriteLine(dataAtual.ToShortDateString());

Console.WriteLine(dataAtual.ToLongTimeString());
Console.WriteLine(dataAtual.ToShortTimeString());
```

---

### 🔸 Nullable Types

* Um **Nullable Type** é um tipo de valor que pode receber um valor null.

```cs
Nullable<T> <nome> = null;

Nullable<int> i = null;
int? i = null;
```

* Use o operador **??** para atribuir um tipo anulável a um tipo não anulável.

```cs
int? a = null;
int b = a ?? 0; // se a != null, retorna a, senão retorna 0

int? c = 100;
if (c.HasValue) 
{
    Console.WriteLine("Possui valor");
}
```

---

### 🔸 Formatação da saída de dados

```cs
string nome = "João";
int idade = 10;

// Interpolação
Console.WriteLine($"{nome} tem {idade} anos");

// placeholder
Console.WriteLine("{0} tem {1} anos", nome, idade);
```

---

### 🔸 Casting

```cs
double d = 12.456;
int i = (int) d;

string s = d.ToString();
```

---

### 🔸 Entrada de Dados

```cs
Console.ReadLine(); // lê apenas uma linha
Console.Read(); // lê apenas um caracter
Console.ReaadKey(); // lê apenas um caracter e espera o usuário pressionar uma tecla
```
