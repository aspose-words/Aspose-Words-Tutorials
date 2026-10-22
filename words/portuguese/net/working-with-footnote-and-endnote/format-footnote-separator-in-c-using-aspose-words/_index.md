---
category: general
date: 2026-08-10
description: Formate o separador de notas de rodapé em C# com Aspose.Words para personalizar
  linhas de notas de rodapé e notas de fim. Aprenda a formatar notas de rodapé em
  C# em minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: pt
lastmod: 2026-08-10
og_description: Formate o separador de notas de rodapé em C# usando Aspose.Words.
  Siga este tutorial para estilizar separadores de notas de rodapé e notas de fim
  rapidamente e de forma confiável.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Formatar separador de nota de rodapé em C# – guia completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Formatar separador de nota de rodapé em C# usando Aspose.Words
url: /pt/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatar separador de nota de rodapé em C# usando Aspose.Words

Se você precisa **formatar o separador de nota de rodapé** em um documento Word, este guia mostra como fazer isso com Aspose.Words para .NET. Você verá um exemplo completo e executável que altera o alinhamento e a cor do parágrafo do separador, e aprenderá como aplicar a mesma técnica aos separadores de nota de fim.

O tutorial cobre cada passo — desde o carregamento do arquivo de origem até a gravação do documento modificado — para que você possa copiar‑colar o código em seu próprio projeto sem pesquisas adicionais.

## O que você precisará

Antes de começar, certifique‑se de que tem:

* .NET 6.0 ou superior (o código também funciona com .NET Framework 4.6+)
* Uma licença válida do Aspose.Words para .NET (a versão de avaliação gratuita serve para testes)
* Um arquivo Word que contenha ao menos uma nota de rodapé ou nota de fim (por exemplo, `Footnotes.docx`)
* Visual Studio 2022 ou qualquer IDE C# de sua preferência

Ter esses itens prontos permite que você foque na **lógica de formatação de notas de rodapé em C#** em vez de na configuração do ambiente.

## Etapa 1: Carregar o documento que contém notas de rodapé e notas de fim

A primeira operação é criar um objeto `Document` que aponte para o seu arquivo de origem. O Aspose.Words lê todo o pacote DOCX para a memória, dando acesso total aos nós de notas de rodapé e notas de fim.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Por que isso importa*: Carregar o documento é pré‑requisito para qualquer manipulação. Se o caminho do arquivo estiver errado, o Aspose.Words lança uma `FileNotFoundException`, portanto verifique o caminho antes de prosseguir.

## Etapa 2: Recuperar os nós de separador e separador de continuação

Os separadores de notas de rodapé e de fim são armazenados como nós especiais dentro das coleções `Footnotes` e `Endnotes`. Cada coleção expõe as propriedades `Separator` e `ContinuationSeparator` que retornam uma referência a um `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Por que isso importa*: O nó `Separator` representa a linha que visualmente separa o texto principal do bloco de nota de rodapé. Ao obter uma referência, você pode modificar seu formato de parágrafo, fonte ou até substituir o nó completamente.

## Etapa 3: Alterar o estilo visual do separador de nota de rodapé

Na maioria dos documentos Word o separador é um único parágrafo que contém um traço ou um asterisco. O código abaixo verifica se o separador é um `Paragraph` e, em caso afirmativo, centraliza‑o e altera a cor do texto para cinza.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Estilizando o separador de continuação (opcional)

O separador de continuação aparece quando uma nota de rodapé se estende por várias páginas. Você pode estilizar‑lo da mesma forma:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Por que isso importa*: Alinhar o separador melhora a legibilidade, e mudar a cor o diferencia do texto de parágrafo normal. Você pode substituir `ParagraphAlignment.Center` por `Left` ou `Right` para adequar‑o às diretrizes de design do seu documento.

## Etapa 4: Salvar o documento modificado

Depois de aplicar o estilo desejado, grave o documento de volta ao disco. Você pode sobrescrever o arquivo original ou criar uma nova versão.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Ao abrir `Footnotes_Styled.docx` no Microsoft Word, o separador de nota de rodapé aparecerá centralizado e cinza, exatamente como especificado no código.

## Variações avançadas

### Formatando o separador de nota de fim

Se o seu documento também usa notas de fim, você pode aplicar a mesma lógica à coleção `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Usando uma string personalizada para o separador

Às vezes você quer que o separador seja uma série de asteriscos (`***`). Substitua as execuções existentes por uma nova execução:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Lidando com documentos sem nó de separador

Um caso raro é um documento que omite o nó de separador (por exemplo, quando o autor o excluiu). Nesse cenário `document.Footnotes.Separator` retorna `null`. Proteja‑se contra isso:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Armadilhas comuns e como evitá‑las

| Armadilha | Por que acontece | Solução |
|-----------|------------------|---------|
| **Separador não é um `Paragraph`** | Alguns modelos Word utilizam uma `Table` ou `Shape` como separador. | Verifique o tipo do nó com `is Paragraph` antes de fazer o cast. |
| **Coleção `Runs` está vazia** | O separador pode ser um parágrafo vazio. | Verifique `Runs.Count > 0` antes de acessar `Runs[0]`. |
| **Licença não aplicada** | Sem licença, o Aspose.Words insere uma marca d'água e pode limitar o uso da API. | Chame `License license = new License(); license.SetLicense("Aspose.Words.lic");` no início do seu programa. |
| **Gravando em pasta somente leitura** | O método `Save` lança uma `UnauthorizedAccessException`. | Garanta que o diretório de destino tenha permissões de gravação. |

Tratar essas questões antecipadamente evita exceções em tempo de execução e garante uma experiência tranquila ao **modificar o separador de nota de rodapé**.

## Exemplo completo e executável

A seguir, um aplicativo console autocontido que demonstra cada passo discutido acima. Copie o código para um novo projeto console .NET, substitua os caminhos dos arquivos e execute.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Resultado esperado**  

Ao abrir `Footnotes_Styled.docx`:

* A linha do separador de nota de rodapé está centralizada sob o texto principal.  
* Sua cor aparece como cinza claro, tornando‑a visualmente distinta.  
* Se o documento contiver notas de fim, seus separadores também ficam centralizados e cinza (ou ardósia).

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais, com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}