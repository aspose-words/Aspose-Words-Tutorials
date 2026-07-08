---
category: general
date: 2026-06-30
description: Salvar documento como PDF em C# enquanto converte docx para PDF e trata
  formas embutidas. Siga este guia passo a passo para exportar Word para PDF corretamente.
draft: false
keywords:
- save document as pdf
- convert docx to pdf
- convert word to pdf
- save word as pdf
- how to export inline
language: pt
og_description: Salve o documento como PDF em C# com Aspose.Words. Aprenda como converter
  docx para PDF e exportar formas flutuantes como elementos embutidos.
og_title: Salvar documento como PDF em C# – Exportar formas em linha
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  headline: Save Document as PDF in C# – Export Inline Shapes
  type: TechArticle
- description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  name: Save Document as PDF in C# – Export Inline Shapes
  steps:
  - name: '**.NET 6+** (or .NET Framework 4.6+).'
    text: '**.NET 6+** (or .NET Framework 4.6+).'
  - name: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
    text: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
  - name: A sample `input.docx` that contains at least one floating picture or text
      box.
    text: A sample `input.docx` that contains at least one floating picture or text
      box.
  type: HowTo
tags:
- C#
- PDF
- Aspose.Words
title: Salvar documento como PDF em C# – Exportar formas em linha
url: /pt/net/programming-with-pdfsaveoptions/save-document-as-pdf-in-c-export-inline-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar Documento como PDF em C# – Exportar Formas Inline

Já se perguntou como **save document as PDF** diretamente do C# sem perder o layout das imagens flutuantes? Você não está sozinho. Muitos desenvolvedores encontram um obstáculo quando um arquivo Word contém imagens ou caixas de texto que flutuam sobre o texto — esses elementos frequentemente desaparecem ou se deslocam ao simplesmente chamar `doc.Save("output.pdf")`.  

Neste tutorial, vamos percorrer os passos exatos para **convert docx to pdf** enquanto preservamos esses objetos flutuantes como elementos inline, respondendo efetivamente à pergunta *how to export inline* shapes. Ao final, você terá um trecho pronto‑para‑executar que **save word as pdf** da maneira que espera.

## O que você aprenderá

- Carregar um arquivo `.docx` com Aspose.Words (ou qualquer biblioteca compatível).  
- Configurar `PdfSaveOptions` para que as formas flutuantes se tornem inline.  
- Executar a operação de salvamento para **convert word to pdf**.  
- Lidar com armadilhas comuns, como fontes ausentes ou imagens grandes.  

Sem ferramentas externas, sem manipulação manual de objetos COM de automação do Word — apenas código C# limpo e puro.

## Pré-requisitos

Antes de mergulharmos, certifique-se de que você tem:

1. **.NET 6+** (ou .NET Framework 4.6+).  
2. O pacote NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`).  
3. Um exemplo `input.docx` que contenha ao menos uma imagem flutuante ou caixa de texto.  

Se você estiver usando uma biblioteca PDF diferente, os conceitos permanecem os mesmos — procure uma propriedade semelhante a `ExportFloatingShapesAsInlineTag`.

## Etapa 1: Carregar o Documento Fonte – Conceitos Básicos de Save Document as PDF  

A primeira coisa a fazer é trazer o arquivo Word para a memória. É aqui que o processo de **save document as pdf** realmente começa.

```csharp
using Aspose.Words;

// Step 1: Load the source DOCX file
string inputPath = @"C:\MyDocs\input.docx";
Document doc = new Document(inputPath);
```

*Por que isso importa*: Carregar o documento valida que o arquivo existe e analisa todas as suas partes (estilos, imagens, cabeçalhos). Se o carregamento falhar, a conversão posterior para PDF nunca será executada, portanto capturar erros aqui economiza muito tempo de depuração.

## Etapa 2: Configurar as Opções de Salvamento PDF – Como Exportar Formas Inline  

Agora informamos à biblioteca como tratar as formas flutuantes. A flag principal é `ExportFloatingShapesAsInlineTag`. Defini‑la como `true` força que cada imagem ou caixa de texto flutuante seja renderizada **inline**, como um trecho regular de parágrafo.

```csharp
// Step 2: Prepare PDF save options
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // true → inline (text‑flow); false → keep as block‑level floating objects
    ExportFloatingShapesAsInlineTag = true,

    // Optional: improve compatibility with older PDF viewers
    Compliance = PdfCompliance.PdfA1b
};
```

*Por que isso importa*: Por padrão, Aspose.Words mantém as formas flutuantes em sua posição original, o que pode fazer com que sejam recortadas ou omitidas no PDF resultante. Habilitar a exportação inline garante que as formas se tornem parte do fluxo de texto, preservando a fidelidade visual em todos os leitores de PDF.

## Etapa 3: Salvar o Documento como PDF – Converter Word para PDF  

Com o documento carregado e as opções definidas, a etapa final é uma única linha que realmente **save document as pdf**.

```csharp
// Step 3: Save the document as a PDF file
string outputPath = @"C:\MyDocs\FloatingShapes.pdf";
doc.Save(outputPath, pdfOptions);
```

É isso! A chamada `doc.Save` grava um PDF que espelha o layout original do Word, com as imagens flutuantes agora posicionadas ordenadamente dentro do texto.

## Exemplo Completo Funcional  

Juntando tudo, aqui está um aplicativo console autônomo que você pode copiar‑colar, compilar e executar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToPdfInlineExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\MyDocs\input.docx";
            string outputPath = @"C:\MyDocs\FloatingShapes.pdf";

            // Load the DOCX file
            Document doc = new Document(inputPath);

            // Configure PDF options to export floating shapes as inline
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                ExportFloatingShapesAsInlineTag = true,
                Compliance = PdfCompliance.PdfA1b // optional, ensures PDF/A‑1b compliance
            };

            // Save as PDF
            doc.Save(outputPath, pdfOptions);

            Console.WriteLine($"Document successfully saved as PDF: {outputPath}");
        }
    }
}
```

**Saída esperada** (no console):

```
Document successfully saved as PDF: C:\MyDocs\FloatingShapes.pdf
```

Abra `FloatingShapes.pdf` em qualquer visualizador; você verá a imagem que antes flutuava agora incorporada confortavelmente dentro do parágrafo, exatamente como esperado.

## Por que Exportar Formas Flutuantes como Inline?  

Formas flutuantes são ótimas no Word porque permitem posicionar imagens em qualquer lugar da página. No entanto, PDF é um formato *orientado a página* — não há conceito de “float” da mesma forma que o Word tem. Quando o motor de conversão as deixa como objetos de nível de bloco, elas podem:

- Sobrepor outro conteúdo.  
- Ser cortadas nas margens da página.  
- Desaparecer completamente em leitores de PDF mais antigos.

Ao convertê‑las para elementos **inline**, você garante que o PDF respeite a ordem de leitura e que leitores de tela possam interpretar o documento corretamente — importante para conformidade de acessibilidade.

## Armadilhas Comuns ao Converter Docx para PDF  

| Problema | Sintoma | Correção |
|----------|---------|----------|
| Fontes ausentes | Texto aparece como “□” ou padrão Arial | Incorporar fontes via `PdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.Always`. |
| Imagens grandes causam picos de memória | Exceção Out‑of‑memory em DOCX grande | Reduzir escala das imagens antes da conversão ou definir `PdfSaveOptions.ImageCompression = PdfImageCompression.Jpeg;` |
| Exportação inline não aplicada | Formas flutuantes ainda flutuam no PDF | Verifique se está usando a versão mais recente do Aspose.Words; o nome da propriedade mudou em versões mais antigas. |
| Erros de caminho | `FileNotFoundException` | Use `Path.Combine` e garanta que o diretório exista (`Directory.CreateDirectory`). |

## Avançado: Exportar Apenas Formas Específicas Inline  

Às vezes você deseja uma conversão *seletiva* inline — apenas certas imagens, não todas. Você pode conseguir isso iterando os nós do documento antes de salvar:

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.WrapType == WrapType.Inline)
        continue; // already inline

    // Example condition: only convert pictures larger than 300px
    if (shape.HasImage && shape.Width > 300)
        shape.WrapType = WrapType.Inline;
}
```

Depois de ajustar o `WrapType`, execute a mesma chamada `doc.Save`. Isso lhe dá controle granular sobre o comportamento **how to export inline**.

## Dicas Profissionais & Melhores Práticas  

- **Dica profissional:** Defina `pdfOptions.Compliance = PdfCompliance.PdfA1b` se sua organização exigir PDF/A para arquivamento.  
- **Fique atento a:** Seções ocultas (`SectionBreakContinuous`) que podem esconder formas flutuantes; execute `doc.UpdatePageLayout()` antes de salvar.  
- **Dica de desempenho:** Reutilize uma única instância de `PdfSaveOptions` se estiver convertendo muitos arquivos em lote; isso reduz a sobrecarga de alocação.  
- **Teste:** Sempre abra o PDF resultante em pelo menos dois visualizadores (Adobe Reader, Edge) para verificar a consistência do layout.

## Visão Geral Visual  

![Fluxograma de salvar documento como PDF](https://example.com/flowchart.png "Fluxograma de salvar documento como PDF")

*Texto alternativo:* **Fluxograma de salvar documento como PDF** – ilustra o processo de três etapas de carregar um DOCX, configurar exportação inline e salvar como PDF.

## Conclusão  

Agora você tem um método sólido e pronto para produção de **save document as PDF** em C# enquanto lida com objetos flutuantes da maneira correta. Ao configurar `ExportFloatingShapesAsInlineTag`, você garante que cada imagem, gráfico ou caixa de texto se torne parte do fluxo de texto, eliminando as falhas típicas que afligem uma abordagem ingênua de **convert word to pdf**.

Experimente: tente converter um relatório complexo com múltiplas imagens flutuantes, depois experimente a lógica seletiva de inline para manter algumas formas flutuando onde devem estar. Da próxima vez que precisar **convert docx to pdf**, você saberá exatamente como preservar cada elemento visual.

Sinta-se à vontade para deixar um comentário se encontrar algum problema ou descobrir um atalho inteligente. Feliz codificação!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [salvar docx como pdf com Aspose.Words – Guia Completo C#](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)
- [Salvar Word como PDF com Aspose.Words – Guia Completo C#](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [converter word para pdf em C# usando Aspose.Words – Guia](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}