---
category: general
date: 2026-03-17
description: Como detectar fontes em C# usando Aspose.Words e um callback de aviso.
  Aprenda a usar o callback para capturar substituições de fontes ausentes ao carregar
  documentos.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: pt
og_description: Como detectar fontes em C# usando Aspose.Words. Este guia mostra como
  usar callbacks para capturar avisos de fontes ausentes ao carregar um documento.
og_title: Como Detectar Fontes em C# – Utilizar Callback com Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Como Detectar Fontes em C# – Use Callback com Aspose.Words
url: /pt/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

/products-backtop-button >}}

We must keep them unchanged.

Now produce final output with all translations.

Be careful to keep code block placeholders unchanged.

Also ensure not to translate URLs, file paths. In bullet lists, keep .NET etc.

Let's craft final.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Detectar Fontes em C# – Use Callback com Aspose.Words

Já precisou **como detectar fontes** em um documento Word programaticamente e se perguntou por que alguns caracteres parecem estranhos após a conversão? Você não está sozinho. Em muitos projetos do mundo real—geradores de faturas, exportadores de relatórios ou pipelines de processamento em lote—fonts ausentes causam falhas silenciosas de layout que são difíceis de depurar.  

A boa notícia? Aspose.Words oferece uma maneira limpa de expor esses problemas com um warning callback. Neste tutorial você verá **como usar callback** para capturar cada substituição de fonte que o Aspose realiza ao carregar um documento, e sairá com um exemplo pronto‑para‑executar que imprime um relatório claro de fontes ausentes.

Vamos cobrir:

* Os pré‑requisitos mínimos (um projeto .NET e o pacote NuGet Aspose.Words).  
* Como implementar `IWarningCallback` para escutar `WarningType.FontSubstitution`.  
* Como conectar o callback ao `LoadOptions` e carregar um documento.  
* Como é a saída, além de algumas dicas práticas para código de produção.

Ao final, você será capaz de **detectar fontes** automaticamente em qualquer arquivo DOCX, DOC ou RTF e agir sobre as informações de fontes ausentes—seja registrando, alertando o usuário ou substituindo por uma fonte fallback.

---

![How to detect fonts in a Word document using Aspose.Words warning callback](https://example.com/images/detect-fonts.png "how to detect fonts in a Word document")

## O que você precisará

* **.NET 6.0** ou superior (o exemplo também compila com .NET Framework 4.6+).  
* **Aspose.Words for .NET** – instale via NuGet: `Install-Package Aspose.Words`.  
* Um arquivo Word de exemplo que deliberadamente referencia uma fonte que você não tem instalada (por exemplo, `MissingFont.docx`).  

Nenhuma biblioteca adicional é necessária; tudo vive dentro do namespace Aspose.

---

## Como Detectar Fontes com um Warning Callback

### Etapa 1: Crie uma classe de warning‑callback

A classe de callback implementa `IWarningCallback`. Quando Aspose.Words encontra uma fonte que não consegue encontrar, ele gera um `WarningInfo` com `WarningType.FontSubstitution`. Nossa classe simplesmente grava uma linha amigável no console.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Por que isso importa:** Ao filtrar por `WarningType.FontSubstitution` evitamos avisos ruidosos (como recursos obsoletos) e mantemos o log focado no problema exato que você está tentando resolver—**detectar fontes** que não estão presentes na máquina.

---

### Etapa 2: Conecte o callback ao `LoadOptions`

`LoadOptions` permite personalizar como um documento é analisado. Atribuir nosso `FontWarningCollector` à propriedade `WarningCallback` indica ao Aspose que ele deve invocá‑lo sempre que uma fonte ausente for encontrada.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Dica:** Você também pode definir `LoadOptions.FontSettings` aqui se quiser fornecer uma fonte fallback programaticamente. Esse é um cenário avançado que mencionaremos mais adiante.

---

### Etapa 3: Carregue o documento e observe a saída

Agora carregamos o arquivo de fato. Assim que o Aspose analisa o documento, qualquer fonte que ele não localize dispara nosso callback.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Saída esperada no console** (supondo que o documento referencie *Comic Sans MS*, que não está instalado):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Se o documento contiver várias fontes ausentes, você verá uma linha por fonte—exatamente a informação de **como detectar fontes** que você precisa.

---

## Como Usar Callback para Cenários Mais Complexos

### Registrando em um arquivo em vez do console

Em produção você provavelmente quer um log persistente. Substitua `Console.WriteLine` por um `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Coletando avisos para análise posterior

Às vezes você precisa da lista de fontes ausentes após o documento ser carregado, talvez para exibir uma caixa de diálogo UI. Armazene os avisos em um `List<string>` e exponha‑os:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Fornecendo uma fonte fallback programaticamente

Se você tem uma fonte corporativa que deseja impor, pode adicioná‑la ao `FontSettings` antes de carregar:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Agora o Aspose substitui fontes ausentes por *Arial Unicode MS* enquanto ainda relata a substituição através do callback. Essa é uma forma inteligente de **como usar callback** tanto para detecção quanto para remediação automática.

---

## Armadilhas Comuns e Dicas Profissionais

| Armadilha | Por que acontece | Como evitar |
|----------|------------------|--------------|
| **Esquecer de referenciar `Aspose.Words.Warnings`** | A interface `IWarningCallback` está nesse namespace. | Adicione `using Aspose.Words.Warnings;` no topo do arquivo. |
| **Carregar um documento sem `LoadOptions`** | O carregador padrão substitui fontes silenciosamente sem notificação. | Sempre crie uma instância de `LoadOptions` e atribua seu callback. |
| **Executar em um servidor com permissões limitadas** | Gravar em um arquivo de log pode lançar `UnauthorizedAccessException`. | Use uma pasta gravável (por exemplo, o diretório de dados da aplicação) ou mantenha coleções em memória. |
| **Múltiplas threads compartilhando o mesmo collector** | `FontWarningCollector` não é thread‑safe por padrão. | Crie um collector separado por thread ou proteja a lista com um lock. |
| **Assumir que o callback dispara para fontes incorporadas** | Fontes incorporadas já estão presentes no documento; nenhum aviso é gerado. | Se precisar verificar a integridade de fontes incorporadas, inspecione `FontInfo` via `FontSettings`. |

---

## Exemplo Completo (Pronto para Copiar e Colar)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**O que você deve ver** (supondo que o arquivo referencie duas fontes ausentes):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Se o arquivo usar apenas fontes instaladas, o console simplesmente imprimirá:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Conclusão

Nós percorremos **como detectar fontes** em um documento Word ao conectar um callback de aviso personalizado ao Aspose.Words. A abordagem é leve, requer

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}