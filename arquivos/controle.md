🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

```cs
int num = 3;
    
if (num == 1) 
{
    Console.WriteLine("1");
} 
else if (num == 2)
{
    Console.WriteLine("2");
}
else 
{
    Console.WriteLine("3");
}


switch (num) 
{
    case 1:
    case 2:
        Console.WriteLine("1 ou 2");
        break;
    case 3:
        Console.WriteLine("3");
        break;
}


while (num < 5)
{
    Console.WriteLine('a');
    num++;
}


do 
{
    Console.WriteLine('a');
    num++;
}
while (num < 5);


for (int i = 0; i < 3; i++)
{
    Console.WriteLine(i);
}
```