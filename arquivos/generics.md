🔙 [Voltar para o Início](https://github.com/4L1C3-R4BB1T/estudos-c-sharp "Voltar para o Início")

---

### 🔸 

```cs
NomeTipo<T>

public class ClasseGenerica<T> { }

public void MetodoGenerico<T>(T a) { }

// restrições (constraints)
NomeTipo<T> where T : <restrição>

public class ClasseGenerica<T> where T : struct { }

public void MetodoGenerico<T>(T a) where T : class { }
```
