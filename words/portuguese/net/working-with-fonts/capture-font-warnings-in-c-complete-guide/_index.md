---
category: general
date: 2026-03-06
description: Capture avisos de fontes ao carregar um documento Word em C#. Aprenda
  a detectar fontes ausentes, verificar as fontes do documento e lidar com fontes
  ausentes de forma eficiente.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: pt
og_description: Capture avisos de fontes ao carregar um documento Word em C#. Este
  tutorial mostra como detectar fontes ausentes, verificar as fontes do documento
  e lidar com fontes ausentes.
og_title: Capturar Avisos de Fonte em C# – Guia Completo
tags:
- Aspose.Words
- C#
- Font Management
title: Capturar Avisos de Fonte em C# – Guia Completo
url: /pt/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturando Avisos de Fonte em C# – Guia Completo

Já precisou **capturar avisos de fonte** ao processar um documento Word? Capturar esses avisos é essencial para **detectar fontes ausentes** e garantir que o resultado final fique exatamente como você deseja.  

Neste tutorial vamos percorrer um exemplo prático, de ponta a ponta, que carrega um arquivo `.docx`, monitora o processo de carregamento e relata quaisquer substituições de fonte. Ao final, você saberá como **carregar documento Word** com segurança, **verificar fontes do documento** e **lidar com fontes ausentes** sem erros inesperados em tempo de execução.

## O que Você Vai Aprender

- Como anexar um coletor de avisos a um `Document` do Aspose.Words.  
- Quais tipos de aviso indicam uma fonte ausente ou substituída.  
- Formas de registrar ou reagir a esses avisos em uma aplicação de nível de produção.  
- Dicas para configurar fontes personalizadas caso precise **lidar com fontes ausentes** de forma elegante.

> **Pré‑requisito:** Você possui uma licença válida do Aspose.Words for .NET (ou está usando a avaliação gratuita) e um ambiente de desenvolvimento .NET (Visual Studio, Rider ou VS Code). Nenhuma outra biblioteca é necessária.

---

## Capturando Avisos de Fonte – Passo a Passo

A seguir está o código completo e executável. Cada seção está dividida em seu próprio passo para que você possa copiar‑colar, experimentar e expandir a lógica.

![Capturando avisos de fonte diagram](image.png "Diagrama mostrando a coleta de avisos"){: alt="diagrama de captura de avisos de fonte"}

### Passo 1: Carregar o Documento Word

Primeiro, precisamos **carregar documento word** que pode conter fontes não instaladas na máquina atual. O construtor `Document` faz o trabalho pesado, mas manteremos a chamada isolada para que você possa trocar por um stream ou um array de bytes mais tarde, se necessário.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Por que isso importa:** Carregar um documento sem um manipulador de avisos faz com que qualquer substituição de fonte seja ignorada silenciosamente. Definindo `WarningCallback` *antes* do carregamento garantimos que veremos cada aviso `FontSubstitution` que ocorrer.

### Passo 2: Anexar um Coletor de Avisos

A classe `WarningInfoCollector` é uma implementação interna de `IWarningCallback`. Ela simplesmente armazena cada aviso em uma lista que podemos inspecionar posteriormente.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Dica profissional:** Se precisar **lidar com fontes ausentes** de forma mais agressiva (por exemplo, abortar o carregamento ou substituir por um fallback específico), substitua o `Console.WriteLine` por lógica personalizada — lançar uma exceção, registrar em um arquivo ou até mesmo adicionar uma fonte personalizada.

### Passo 3: Verificar a Saída

Execute o programa em um console. Se o seu `input.docx` usar uma fonte que não está instalada, você verá linhas como:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Se nenhuma saída aparecer, o documento usou apenas fontes já disponíveis **ou** o Aspose.Words encontrou uma fonte correspondente em sua coleção interna de fallback. De qualquer forma, você **verificou fontes do documento** com sucesso.

---

## Detectar Fontes Ausentes sem Licença (Avaliação Gratuita)

Mesmo na avaliação de 30 dias, o mecanismo de avisos funciona exatamente da mesma forma. A única diferença é que a avaliação adiciona uma marca d'água ao output gerado, o que **não** afeta a coleta de avisos. Assim, você pode **detectar fontes ausentes** com segurança antes de decidir comprar uma licença completa.

---

## Lidar com Fontes Ausentes – Opções Avançadas

Às vezes você quer fornecer seus próprios arquivos de fonte (por exemplo, fontes da identidade corporativa) para que a substituição nunca ocorra. O Aspose.Words permite registrar pastas de fontes personalizadas:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Coloque o código acima **antes** de carregar o documento se quiser que o carregador considere essas fontes durante a fase inicial de análise. Essa é a maneira mais confiável de **lidar com fontes ausentes** sem depender das fontes padrão do sistema.

---

## Armadilhas Comuns & Como Evitá‑las

| Armadilha | Por que acontece | Solução |
|-----------|------------------|---------|
| **Coletor de avisos anexado após o carregamento** | O documento já foi analisado, portanto nenhum aviso é registrado. | Anexe `WarningCallback` **antes** de chamar `new Document(path)`. |
| **Apenas avisos genéricos aparecem** | Você filtrou pelo `WarningType` errado. | Use `WarningType.FontSubstitution` para focar em questões de fonte. |
| **Nenhuma saída apesar de fontes ausentes** | Aspose.Words encontrou um fallback interno (ex.: Arial). | Desative os fallbacks internos via `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Impacto de desempenho ao analisar documentos grandes** | Coletar todos os avisos pode ser custoso. | Limite a coleta a `FontSubstitution` somente, ou processe avisos em lotes. |

---

## Exemplo Completo Funcional (Pronto para Copiar‑Colar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Saída esperada no console** (supondo duas fontes ausentes):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Se o console permanecer silencioso exceto por “Document loaded successfully”, você **verificou fontes do documento** e não encontrou ausências.

---

## Conclusão

Mostramos como **capturar avisos de fonte** em C# usando Aspose.Words, um método confiável para **detectar fontes ausentes**, **carregar documento word** com segurança, **verificar fontes do documento** e **lidar com fontes ausentes** por meio de fontes personalizadas.  

Com esse padrão, você pode integrar a validação de fontes em qualquer pipeline de automação — seja gerando PDFs, convertendo para HTML ou simplesmente arquivando arquivos Word.

### O que vem a seguir?

- Explore a API **FontSettings.SubstitutionSettings** para definir suas próprias regras de fallback.  
- Combine a coleta de avisos com um framework de logging (Serilog, NLog) para monitoramento em produção.  
- Use a mesma abordagem para capturar outros tipos de aviso, como resolução de imagens ou recursos não suportados.

Tem mais dúvidas sobre manipulação de fontes ou Aspose.Words em geral? Deixe um comentário ou participe dos fóruns da comunidade Aspose. Boa codificação, e que seus documentos sempre renderizem com as fontes esperadas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}