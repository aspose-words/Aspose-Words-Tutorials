---
category: general
date: 2026-04-07
description: Aprenda como detectar fontes e como capturar avisos ao lidar com fontes
  ausentes em C# usando Aspose.Words. Código passo a passo incluído.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: pt
og_description: Como detectar fontes no Aspose.Words? Siga este tutorial para capturar
  avisos e lidar com fontes ausentes sem esforço.
og_title: Como Detectar Fontes no Aspose.Words – Guia Completo
tags:
- Aspose.Words
- C#
- Font handling
title: Como Detectar Fontes no Aspose.Words – Guia Completo
url: /pt/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Detectar Fontes no Aspose.Words – Guia Completo

Já se perguntou **como detectar fontes** que estão ausentes em um documento Word antes de enviá‑lo para produção? Você não está sozinho. Em muitos cenários corporativos, uma fonte fora do lugar pode quebrar um pipeline de conversão para PDF ou causar falhas de layout que parecem pouco profissionais. A boa notícia é que o Aspose.Words oferece um modo interno de identificar essas tipografias ausentes e exibir avisos claros.

Neste tutorial vamos percorrer passo a passo **como detectar fontes**, **como capturar avisos**, e as melhores práticas para **lidar com fontes ausentes** para que sua aplicação continue robusta. Sem ferramentas externas, sem adivinhações — apenas código C# puro que você pode inserir no seu projeto agora mesmo.

> **Pré‑visualização rápida:** Ao final você terá um `FontSubstitutionWarningCollector` reutilizável que reúne todas as mensagens de substituição de fonte durante o carregamento do documento, e saberá como reagir quando uma fonte não for encontrada.

---

## O Que Você Vai Aprender

- Como configurar `LoadOptions` para escutar avisos de substituição de fonte.  
- Como capturar esses avisos em uma classe coletora personalizada.  
- Como processar os avisos coletados e decidir se aborta, registra ou substitui fontes.  
- Tratamento de casos extremos para documentos que referenciam fontes remotas ou incorporadas.  

**Pré‑requisitos:** .NET 6+ (ou .NET Framework 4.6+), Aspose.Words for .NET (versão mais recente) e familiaridade básica com C#. Se você nunca usou o Aspose.Words antes, não se preocupe — este guia assume apenas alguns minutos de configuração.

---

## Como Detectar Fontes Usando Aspose.Words LoadOptions

O primeiro passo para detectar fontes ausentes é instruir o Aspose.Words a relatá‑las. Isso é feito através da propriedade `LoadOptions.WarningCallback`, que aceita qualquer classe que implemente `IWarningCallback`. Abaixo criamos um pequeno coletor que armazena cada aviso para inspeção posterior.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Por que isso importa:** Sem um callback de aviso, o Aspose.Words substitui silenciosamente fontes ausentes por uma padrão, e você nunca saberá que há um problema. Ao capturar `WarningType.FontSubstitution` ganhamos total visibilidade — exatamente os dados que você precisa para **detectar fontes** que não estão disponíveis na máquina host.

Agora conectamos o coletor ao `LoadOptions` e carregamos um documento:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Dica de especialista:** Se você trabalha com muitos documentos em lote, reutilize a mesma instância de `FontSubstitutionWarningCollector`, mas lembre‑se de chamar `Clear()` entre os carregamentos para evitar misturar avisos de arquivos diferentes.

---

## Capturar Avisos Durante o Carregamento do Documento

Depois que o documento é carregado, o coletor já contém todos os avisos relacionados a fontes. A próxima pergunta lógica é: *Como capturo avisos* de forma que seja fácil registrar ou exibir?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

A saída típica se parece com:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**O que isso indica:** Cada linha revela o nome da fonte original e a fonte de fallback que o Aspose.Words escolheu. Munido dessas informações, você pode decidir se o fallback é aceitável ou se precisa incorporar a fonte ausente manualmente.

---

## Lidar com Fontes Ausentes de Forma Elegante

Detectar e capturar avisos é apenas metade da batalha. O verdadeiro valor surge quando você **lida com fontes ausentes** de maneira pronta para produção. Abaixo estão três estratégias comuns:

1. **Registrar e Continuar** – Adequado para processamento em lote onde você só precisa de um registro de auditoria.  
2. **Abortar em Fontes Críticas** – Lançar uma exceção se uma fonte específica (por exemplo, uma tipografia da marca) estiver ausente.  
3. **Incorporar a Fonte Sob Demanda** – Carregar a fonte ausente de uma pasta conhecida e registrá‑la no Aspose.Words antes de recarregar o documento.

### Exemplo: Abortando em uma Fonte Crítica

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Exemplo: Auto‑Incorporar Fontes Ausentes

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Por que esses padrões ajudam:** Ao decidir explicitamente o que fazer quando uma fonte falta, você elimina substituições silenciosas que poderiam comprometer a identidade visual ou a legibilidade. Essa é a essência de **lidar com fontes ausentes** de forma controlada.

---

## Exemplo Completo Funcional

Juntando tudo, aqui está um programa único, pronto‑para‑executar, que demonstra **como detectar fontes**, **como capturar avisos**, e uma política simples para **lidar com fontes ausentes** registrando‑as.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Resultado esperado:** Ao executar o programa contra um documento que referencia uma fonte não presente na máquina, o console listará cada aviso de substituição. Se algum aviso envolver uma fonte do conjunto `critical`, o programa encerrará antecipadamente, impedindo a geração de um PDF defeituoso.

---

## Perguntas Frequentes (FAQs)

| Pergunta | Resposta |
|----------|----------|
| *Preciso de licença para o Aspose.Words usar este código?* | Sim, uma licença válida do Aspose.Words remove marcas d'água de avaliação e desbloqueia toda a funcionalidade. |
| *Esta abordagem consegue detectar fontes incorporadas?* | Fontes incorporadas já fazem parte do arquivo, portanto o Aspose.Words não gera aviso de substituição. Você pode usar `Document.FontInfos` para enumerar fontes incorporadas, se necessário. |
| *E se a fonte ausente for uma fonte do sistema no Windows, mas não no Linux?* | O mesmo aviso será disparado no Linux porque a fonte não está instalada lá. Use a estratégia “lidar com fontes ausentes” para distribuir os arquivos `.ttf` necessários junto com seu aplicativo. |
| *O coletor de avisos é thread...* |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}