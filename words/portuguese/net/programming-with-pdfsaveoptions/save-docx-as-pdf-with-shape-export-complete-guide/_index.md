---
category: general
date: 2026-02-13
description: Salvar docx como pdf preservando formas flutuantes. Aprenda a converter
  Word para pdf, exportar formas e lidar com casos especiais em C#.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- how to export shapes
- convert word document pdf
- how to convert docx pdf
language: pt
og_description: Salve docx como pdf preservando formas flutuantes. Este guia mostra
  como converter Word para pdf, exportar formas e lidar com armadilhas comuns.
og_title: Salvar docx como pdf com Exportação de Formas – Guia Completo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Salvar docx como PDF com Exportação de Formas – Guia Completo
url: /pt/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-shape-export-complete-guide/
---

them.

Now produce final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar docx como pdf – Tutorial Full‑stack (C#)

Já precisou **salvar docx como pdf** e manter aqueles diagramas flutuantes exatamente iguais? Você não está sozinho. Muitos desenvolvedores se deparam com um obstáculo quando as formas do Word desaparecem ou ficam distorcidas após a conversão. A boa notícia? Com algumas linhas de C# você pode instruir a biblioteca a tratar cada forma como um elemento de nível de bloco, e o resultado é uma réplica fiel em PDF.

Neste guia percorreremos todo o processo: carregar um arquivo `.docx`, configurar as opções de **convert word to pdf** para que as formas sejam exportadas corretamente e, finalmente, gravar o PDF no disco. Ao final você saberá **como exportar formas**, entenderá as compensações dos diferentes modos de exportação e terá um exemplo de código pronto para executar que pode ser inserido em qualquer projeto .NET.

> **O que você receberá:** um exemplo completo e executável, explicações sobre *por que* cada configuração importa, dicas para casos extremos e ideias para expandir a solução (por exemplo, manipular imagens, fontes personalizadas ou PDFs protegidos por senha).

---

## Prerequisites

- .NET 6+ (ou .NET Framework 4.7+). A API que usamos funciona em ambos.
- Aspose.Words for .NET (versão de avaliação gratuita ou licenciada). Instale via NuGet: `Install-Package Aspose.Words`.
- Um documento Word (`input.docx`) que contém formas flutuantes (caixas de texto, auto‑shapes, SmartArt, etc.).
- Visual Studio 2022 ou qualquer IDE de sua preferência.

Nenhuma outra biblioteca de terceiros é necessária.

---

## Step‑by‑Step Implementation

Abaixo de cada passo você verá um pequeno trecho de código, uma explicação em português simples e uma nota sobre **como exportar formas** corretamente.

### ## Etapa 1 – Carregar o documento de origem (salvar docx como pdf)

```csharp
// Step 1: Load the source document
// This is the starting point for any conversion – you must have a Document object.
Document doc = new Document(@"C:\MyFolder\input.docx");
```

*Por que isso importa:* A classe `Document` representa todo o arquivo Word na memória. Se você pular esta etapa, não haverá nada para converter, e as opções de PDF subsequentes não terão o que agir.

### ## Etapa 2 – Configurar opções de salvamento PDF (como exportar formas)

```csharp
// Step 2: Configure PDF save options to export floating shapes as block‑level tags
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // ExportFloatingShapesAsInlineTag determines how shapes are rendered in PDF.
    // Setting it to Block ensures each shape gets its own block, preserving layout.
    ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block
};
```

**Explicação**

- `PdfSaveOptions` é um “conjunto de configurações” que indica ao Aspose.Words como traduzir os elementos do Word para PDF.
- A propriedade **ExportFloatingShapesAsInlineTag** tem três valores possíveis:
  1. **Inline** – as formas tornam‑se elementos inline (geralmente comprimidos no texto ao redor).
  2. **Block** – cada forma é colocada em seu próprio bloco, que é a forma mais segura de manter a aparência original.
  3. **Auto** – a biblioteca decide automaticamente (pode não escolher sempre a melhor opção).

Escolher **Block** é a abordagem recomendada quando você *precisa exportar formas* exatamente como aparecem no documento original. Isso evita o problema de “a forma desaparece” que muitos encontram ao simplesmente chamar `doc.Save("out.pdf")`.

### ## Etapa 3 – Salvar o documento como PDF (convert word to pdf)

```csharp
// Step 3: Save the document as PDF using the configured options
doc.Save(@"C:\MyFolder\FloatingShapes.pdf", pdfSaveOptions);
```

*O que você verá:* Após a execução desta linha, `FloatingShapes.pdf` fica em `C:\MyFolder`. Abra‑o, e você deverá ver cada caixa de texto, chamada e SmartArt posicionados exatamente como no `.docx` de origem.

---

## Exemplo Completo Funcional

Abaixo está o **programa completo** que você pode compilar e executar como um aplicativo de console. Ele inclui todas as declarações `using` necessárias e comentários para clareza.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX file you want to convert.
        // Replace the path with your own file location.
        Document doc = new Document(@"C:\MyFolder\input.docx");

        // 2️⃣ Set up PDF options – this is where we tell Aspose.Words
        //    how to handle floating shapes.
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // ExportFloatingShapesAsInlineTag = Block makes each shape a separate block.
            ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block,

            // Optional: preserve the original page size.
            PageMode = PdfPageMode.UseOutlines,

            // Optional: embed fonts to avoid missing‑glyph issues.
            EmbedFullFonts = true
        };

        // 3️⃣ Write the PDF to disk.
        string outPath = @"C:\MyFolder\FloatingShapes.pdf";
        doc.Save(outPath, pdfOptions);

        Console.WriteLine($"Successfully saved DOCX as PDF: {outPath}");
    }
}
```

**Saída esperada**

```
Successfully saved DOCX as PDF: C:\MyFolder\FloatingShapes.pdf
```

Abra o PDF resultante e verifique se todas as formas mantêm suas posições originais. Se alguma forma ainda parecer fora do lugar, verifique novamente se ela realmente é uma forma *flutuante* (em vez de uma imagem inline) no Word.

---

## Perguntas Frequentes & Casos Limítrofes

| Pergunta | Resposta |
|----------|----------|
| **Posso exportar formas como inline em vez de block?** | Sim – defina `ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Inline`. Isso pode ser útil para layouts simples, mas espere um fluxo de texto mais apertado e possível sobreposição. |
| **E se meu documento contiver imagens dentro de formas?** | A mesma opção funciona; o Aspose.Words rasteriza a forma junto com sua imagem. Para a maior fidelidade, também habilite `PdfSaveOptions.JpegQuality` se precisar de melhor compressão de imagem. |
| **Isso funciona com arquivos DOCX protegidos por senha?** | Carregue o documento com um objeto `LoadOptions` que fornece a senha, então continue normalmente. |
| **Posso converter vários arquivos DOCX em lote?** | Envolva a lógica de três etapas em um loop `foreach` sobre uma lista de arquivos. Lembre‑se de reutilizar `PdfSaveOptions` para desempenho. |
| **O PDF é compatível com leitores mais antigos (Acrobat 7)?** | Por padrão o Aspose.Words cria arquivos PDF 1.7. Defina `pdfOptions.Compliance = PdfCompliance.PdfA1b` para PDFs de nível de arquivamento que funcionam em leitores legados. |

---

## Dicas Profissionais & Armadilhas Comuns

- **Dica profissional:** Se notar pequenos deslocamentos verticais após a conversão, tente definir `pdfOptions.UsePdfDocumentStructure = true`. Isso força o motor PDF a respeitar a hierarquia de layout do Word.
- **Cuidado com:** Documentos que misturam formas flutuantes com tabelas ancoradas. Em alguns casos, a exportação em bloco pode empurrar uma tabela para uma nova página; você pode mitigar isso ajustando `pdfOptions.PageSetup` antes de salvar.
- **Observação de desempenho:** Reutilizar uma única instância de `PdfSaveOptions` para muitos arquivos reduz a pressão do GC e acelera conversões em lote.

---

## Referência Visual

![exemplo de salvar docx como pdf com formas flutuantes](image-placeholder.png "exemplo de salvar docx como pdf com formas flutuantes")

*A imagem ilustra como a forma permanece exatamente onde estava no arquivo Word original após a conversão.*

---

## Conclusão

Cobremos **como salvar docx como pdf** mantendo cada forma flutuante intacta, exploramos as configurações de **convert word to pdf** que importam e respondemos às perguntas mais comuns sobre “**como exportar formas**”. O exemplo de código completo está pronto para ser inserido em qualquer projeto C#, e os ajustes opcionais oferecem flexibilidade para cenários reais, como processamento em lote ou conformidade PDF/A.

### Próximos Passos

- Experimente **convert word document pdf** com diferentes níveis de conformidade (`PdfCompliance.PdfA2b`, `PdfCompliance.PdfUa`) para atender aos requisitos regulatórios.
- Experimente **how to convert docx pdf** para arquivos protegidos por senha — adicione `LoadOptions` com uma senha e `PdfSaveOptions` com `EncryptionDetails`.
- Explore outros formatos de saída (por exemplo, XPS, HTML) usando o mesmo objeto `Document`; a única mudança está no argumento de formato do método `Save`.

Tem mais perguntas? Deixe um comentário, e feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}