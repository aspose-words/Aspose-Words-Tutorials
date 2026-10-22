---
category: general
date: 2026-03-25
description: Crie um callback de aviso para carregar o documento Word e detectar fontes
  ausentes. Aprenda como configurar as definições de fonte no Aspose.Words para .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: pt
og_description: Crie um callback de aviso para carregar documentos Word enquanto detecta
  fontes ausentes. Este guia mostra como configurar as definições de fonte no Aspose.Words.
og_title: Criar callback de aviso – Carregar documento Word e detectar fontes ausentes
tags:
- Aspose.Words
- C#
- Font handling
title: Criar callback de aviso para carregamento de documentos Word – Guia Completo
url: /pt/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar callback de aviso – Carregar documento Word e detectar fontes ausentes

Já precisou **criar um callback de aviso** ao carregar um documento Word e se perguntou por que algumas fontes simplesmente desaparecem? Você não está sozinho. Em muitas aplicações corporativas, fontes ausentes causam desastres de layout, e sem um callback adequado você pode nem perceber o problema.  

A boa notícia? Com Aspose.Words for .NET você pode **carregar documento Word**, **detectar fontes ausentes** e **configurar as definições de fonte** em poucas linhas de código bem organizadas. Neste tutorial vamos percorrer um exemplo completo e executável, explicar por que cada parte é importante e mostrar como verificar se o callback de aviso está fazendo seu trabalho.

> **O que você levará**  
> * Um programa C# completo que carrega um DOCX, relata quaisquer substituições de fonte e permite personalizar os caminhos de pesquisa de fontes.  
> * Compreensão das classes `FontSettings`, `LoadOptions` e `IWarningCallback`.  
> * Dicas para lidar com casos extremos como fontes incorporadas ou pastas de fontes do sistema.

---

## Pré‑requisitos

- .NET 6+ (ou .NET Framework 4.7.2+) com um compilador C#.  
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Um arquivo Word de exemplo (`input.docx`) que use ao menos uma fonte não instalada na máquina (por exemplo, *Calibri Light* em um contêiner Windows mínimo).  
- Familiaridade básica com aplicativos de console C#.

Nenhuma biblioteca adicional é necessária; tudo reside dentro do Aspose.Words.

---

## Etapa 1: Criar callback de aviso para detectar fontes ausentes

A peça **principal** desse quebra‑cabeça é uma classe que implementa `IWarningCallback`. Aspose.Words invocará esse callback sempre que encontrar uma situação que justifique um aviso – a substituição de fonte sendo a mais comum.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Por que isso importa** – Sem um callback você teria que vasculhar logs depois do fato. Ao tratar avisos em tempo real, pode decidir abortar o carregamento, substituir a fonte ausente por uma alternativa ou simplesmente registrar o problema para revisão posterior.

---

## Etapa 2: Configurar FontSettings para tratamento personalizado de fontes

Antes de realmente carregar o documento, talvez queiramos informar ao Aspose.Words onde procurar fontes que não estejam presentes no sistema. É aí que entra o `FontSettings`.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Por que isso importa** – Ao apontar o Aspose.Words para uma pasta que contenha as fontes ausentes, você costuma evitar a substituição completamente. Quando isso não for possível, um padrão sensato (como *Arial*) mantém o documento legível.

---

## Etapa 3: Carregar documento Word com o callback de aviso configurado

Agora juntamos tudo: criamos `LoadOptions`, inserimos nosso `FontSettings` e `FontWarningHandler` e, finalmente, carregamos o documento.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Por que isso importa** – `LoadOptions` é o único local onde você configura *como* um documento é lido. Ao fornecer tanto a configuração de fonte quanto o callback de aviso, garantimos que qualquer fonte ausente seja **procurada nos lugares corretos** **e** relatada imediatamente.

---

## Etapa 4: Verificar a saída – o que você deve ver?

Execute o programa em um console. Se `input.docx` usar uma fonte que não esteja instalada e também não esteja em `C:\SharedFonts`, você verá algo como:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Se todas as fontes estiverem disponíveis, a linha de aviso simplesmente nunca aparecerá. Esse ciclo de feedback imediato é inestimável em pipelines automatizados de processamento de documentos, onde trocas silenciosas de fonte podem quebrar diretrizes de identidade visual.

---

## Etapa 5: Armadilhas comuns e dicas de boas práticas

| Armadilha | Como evitá‑la |
|----------|---------------|
| **Esquecer de referenciar `Aspose.Words.Fonts`** | Certifique‑se de que há `using Aspose.Words.Fonts;` no topo; caso contrário o compilador reclamará de tipos ausentes. |
| **Caminho da pasta de fontes está errado** | Verifique o caminho e defina `recursive: true` se houver subpastas. Use `Path.GetFullPath` para depurar. |
| **Múltiplos callbacks de aviso** | Aspose.Words honra apenas o último `WarningCallback` atribuído. Mantenha um único handler que delegue se precisar de lógica mais complexa. |
| **Executando em um servidor sem UI** | Escritas no console são aceitáveis, mas para apps web talvez queira registrar em arquivo ou sistema de monitoramento ao invés de `Console.WriteLine`. |
| **Documentos grandes causam queda de desempenho** | Reutilize uma única instância de `FontSettings` em múltiplos carregamentos; criá‑la repetidamente pode ser custoso. |

**Dica de especialista:** Se precisar *coletar* avisos para análise posterior, armazene‑os em um `List<string>` dentro do handler ao invés de imprimir diretamente.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Você pode então inspecionar `handler.Messages` após o carregamento do documento.

---

## Etapa 6: Expandindo a solução – e se eu precisar incorporar uma fonte alternativa?

Às vezes você quer que a fonte ausente seja *incorporada* no PDF de saída para que visualizadores posteriores vejam a aparência exata. Após carregar o documento, você pode forçar a incorporação:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Este trecho demonstra como a mesma abordagem de **configurar definições de fonte** pode ser estendida além do simples carregamento.

---

## Exemplo completo executável

Abaixo está o programa completo que você pode copiar‑colar em um novo projeto de Console App. Ele inclui todas as peças discutidas acima.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Saída esperada** (quando uma fonte ausente está presente):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Se nenhuma substituição ocorrer, aparecerão apenas as mensagens de sucesso.

---

## Conclusão

Acabamos de **criar um callback de aviso** que detecta de forma confiável **fonts ausentes** ao **carregar um documento Word** com Aspose.Words, e mostramos como **configurar as definições de fonte** para controlar onde a biblioteca procura fontes e qual fallback usar. Ao conectar `FontSettings` e `LoadOptions`, você obtém total visibilidade sobre problemas relacionados a fontes — sem mais falhas silenciosas de layout.

Próximos passos? Experimente substituir o `FontWarningHandler` por um logger que grave em um banco de dados, ou teste **regras de substituição de fontes** para mapear fontes ausentes específicas a alternativas aprovadas pela marca. Você também pode explorar **carregamento dinâmico de fontes** a partir de armazenamento em nuvem se sua aplicação rodar em um ambiente conteinerizado.

Tem perguntas sobre um caso extremo específico — como lidar com recursos OpenType ou arquivos DOCX criptografados? Deixe um comentário abaixo, e feliz codificação!  

---

![Criar callback de aviso diagrama](https://example.com/images/create-warning-callback.png "Criar callback de aviso diagrama")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}