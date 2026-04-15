

```csharp
string sourcepath = @"C:\Users\scfaria\Desktop\Projeto c#\loremipsum 4.txt";
string linhaImpar = @"C:\Users\scfaria\Desktop\Projeto c#\Impares.txt";
string linhaPar = @"C:\Users\scfaria\Desktop\Projeto c#\Pares.txt"; ;

try
{
    if (!File.Exists(sourcepath))
    {
        Console.WriteLine("Arquivo não encontrado");
        return;
    }
    string[] lines = File.ReadAllLines(sourcepath);

    List<string> impares = new List<string>();
    List<string> pares = new List<string>();

    for (int i = 0; i < lines.Length; i++)
    {
        if (string.IsNullOrWhiteSpace(lines[i]))
        { continue; }
        if ((i + 1) % 2 == 0)
        {
            pares.Add(lines[i]);
        }
        else
        {
            impares.Add(lines[i]);
        }
    }
    File.WriteAllLines(linhaImpar, impares);
    File.WriteAllLines(linhaPar, pares);
}
catch (IOException e)
{
    Console.WriteLine("Erro ao processar o arquivo:");
    Console.WriteLine(e.Message);
}
```