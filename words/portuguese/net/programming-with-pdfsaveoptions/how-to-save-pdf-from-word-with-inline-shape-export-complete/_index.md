---
category: general
date: 2026-06-02
description: Como salvar PDF a partir de um DOCX usando Aspose.Words, exportar formas
  como tags span inline e converter Word para PDF em apenas alguns passos.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: pt
og_description: Como salvar PDF a partir de um documento Word usando Aspose.Words,
  exportando formas flutuantes como tags span inline para um resultado de conversão
  Word para PDF limpo.
og_title: Como salvar PDF a partir do Word – Tutorial de exportação de forma inline
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Como salvar PDF do Word com exportação de forma embutida – Guia completo
url: /pt/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como salvar PDF a partir do Word com exportação de forma inline – Guia completo

Já se perguntou **como salvar PDF** a partir de um arquivo Word mantendo cada forma flutuante bem encaixada no fluxo? Você não está sozinho. Em muitas aplicações corporativas precisamos *converter Word para PDF* sem acabar com imagens fora de lugar ou objetos de desenho soltos. A boa notícia? Aspose.Words torna isso indolor, e você pode até instruir a biblioteca a **exportar formas como tags `<span>` inline** para que o PDF fique exatamente como o DOCX original.

Neste tutorial percorreremos todo o processo — carregando um DOCX, ajustando o `PdfSaveOptions` e, finalmente, salvando um PDF limpo. Ao final você saberá **como salvar PDF**, **salvar docx como pdf**, e até **como exportar formas** usando *tags span inline*.

## O que você precisará

- **Aspose.Words for .NET** (última versão, 24.x no momento da escrita).  
- **.NET 6.0** ou superior – o código também funciona no .NET Framework 4.7.2, mas o .NET 6 é o ponto ideal.  
- Um documento Word simples que contenha ao menos uma forma flutuante (imagem, caixa de texto ou desenho).  
- Qualquer IDE que você prefira (Visual Studio, Rider, VS Code + extensão C#).  

É isso — sem pacotes NuGet extras, sem interop COM complicado. Pronto? Vamos mergulhar.

## Etapa 1: Configurar o Projeto e Adicionar Aspose.Words

Primeiro, crie um aplicativo console (ou integre o código ao seu serviço existente).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Dica profissional:** Se você estiver usando o Visual Studio, pode adicionar o pacote via a interface do NuGet Package Manager — basta procurar por *Aspose.Words*.

## Etapa 2: Carregar o Documento Fonte

Agora que a biblioteca está referenciada, podemos carregar o DOCX. Esta é a primeira ação concreta da parte **como salvar pdf** — obter a fonte na memória.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Por que isso importa:** Carregar o arquivo valida que o caminho está correto e que o Aspose pode analisar a estrutura do Word. Se o arquivo contém formas flutuantes, elas farão parte da árvore de nós do objeto `Document`.

## Etapa 3: Configurar as Opções de Salvamento PDF – Exportar Formas como Tags Inline

Aqui está o cerne de **como exportar formas**. Por padrão, Aspose.Words renderiza formas flutuantes como objetos separados no PDF, o que pode deslocar o layout. Definir `ExportFloatingShapesAsInlineTag` como `true` instrui o motor a envolver cada forma em um elemento `<span>` inline, preservando o fluxo.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**Por que habilitar essa flag?** Imagine um contrato com uma caixa de assinatura que flutua sobre o texto. Quando você converte para PDF sem essa configuração, a caixa pode aparecer em outra página. Tags `<span>` inline mantêm a forma ancorada ao parágrafo ao redor, produzindo uma réplica visual fiel.

## Etapa 4: Salvar o Documento como PDF

Finalmente, chamamos `doc.Save` com as opções que acabamos de criar. Este é o momento em que você realmente **salva docx como pdf**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Execute o programa (`dotnet run`) e verifique o `output.pdf`. Você deverá ver suas formas flutuantes renderizadas inline, exatamente como apareceram no Word.

## Etapa 5: Verificar o Resultado – Checklist Rápido

1. **Todo o texto está presente** – sem parágrafos ausentes.  
2. **Formas flutuantes aparecem onde deveriam** – agora fazem parte do fluxo de texto.  
3. **O tamanho do PDF é razoável** – exportar como tags inline geralmente reduz o inchaço do arquivo comparado a fluxos de imagens separados.  

Se algo parecer errado, verifique novamente se o DOCX fonte realmente usa formas *flutuantes* (clique com o botão direito → Layout → “Em linha com o texto” vs “Quadrado/Por trás do texto”). Alterar uma forma para “Em linha” antes da conversão também funciona, mas a opção de tag inline lhe dá controle sem editar o arquivo original.

## Casos de Borda & Perguntas Frequentes

### E se meu documento contiver **SmartArt** ou **Gráficos**?

SmartArt e gráficos são tratados como objetos de desenho. A flag `ExportFloatingShapesAsInlineTag` ainda os envolverá em tags `<span>`, mas gráficos complexos podem perder parte da fidelidade. Nesses casos, considere exportar o gráfico como imagem primeiro (`Chart.ToImage()`) e então inseri‑lo inline.

### Posso **preservar hyperlinks** e **marcadores**?

Absolutamente. Esses elementos não são afetados pela configuração `ExportFloatingShapesAsInlineTag`. Aspose.Words retém todas as informações de hyperlink e marcador automaticamente.

### Como eu **altero a compressão do PDF** ou **incorporo fontes**?

`PdfSaveOptions` oferece muitas propriedades adicionais:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

## Exemplo Completo Funcional (Pronto para Copiar‑Colar)

Abaixo está o programa completo que você pode copiar para `Program.cs`. Substitua `YOUR_DIRECTORY` por um caminho de pasta real.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Saída esperada no console:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Abra `output.pdf` — você verá o layout original, com cada forma flutuante posicionada confortavelmente dentro do fluxo de texto.

## Conclusão

Cobrimos **como salvar PDF** a partir de um documento Word garantindo que as formas flutuantes se tornem tags `<span>` inline. Carregando o DOCX, configurando `PdfSaveOptions` e invocando `doc.Save`, você pode de forma confiável **salvar docx como pdf** e **converter word para pdf** sem surpresas de layout.  

Próximos passos? Experimente combinar esta abordagem com conformidade **PDF/A** para arquivamento, ou processar em lote uma pasta de arquivos DOCX com um simples loop `foreach`. Você também pode explorar **renderização personalizada** (por exemplo, adicionando marcas d'água) acessando a API `DocumentVisitor` do Aspose.Words.

Tem mais perguntas sobre manipulação de formas, incorporação de fontes ou ajuste de desempenho? Deixe um comentário abaixo, e feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Convert DOCX to PDF in Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}