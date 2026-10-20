---
category: general
date: 2026-08-07
description: Recuperar o separador de nota de rodapé usando Aspose.Words para .NET.
  Aprenda a extrair separadores de notas de rodapé e notas de fim, inspecionar tipos
  de nós e modificá-los em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: pt
lastmod: 2026-08-07
og_description: recuperar separador de nota de rodapé com Aspose.Words para .NET.
  Este guia mostra como extrair separadores de notas de rodapé e notas de fim, verificar
  seus tipos de nó e salvar as alterações.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: recuperar separador de nota de rodapé em C# – tutorial passo a passo do
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: recuperar separador de nota de rodapé em C# – guia completo do Aspose.Words
url: /pt/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# recuperar separador de nota de rodapé em C# – guia completo do Aspose.Words

Se você precisa **recuperar o separador de nota de rodapé** de um documento Word, este tutorial mostra exatamente como fazer isso com Aspose.Words para .NET. Seja construindo um serviço de processamento de documentos ou limpando a formatação de notas de rodapé, você verá um exemplo completo e executável que extrai tanto os separadores de notas de rodapé quanto de notas de fim.

Neste guia você aprenderá como carregar um arquivo `.docx`, chamar as propriedades `FootnoteSeparator` e `EndnoteSeparator`, inspecionar os objetos `Node` retornados e, opcionalmente, substituir a linha do separador. Nenhuma documentação externa é necessária — tudo o que você precisa está incluído abaixo.

## Pré-requisitos

* .NET 6.0 ou posterior (o código também funciona no .NET Framework 4.7.2)
* Pacote NuGet Aspose.Words para .NET (versão 24.9 ou mais recente)
* Um documento Word que contém notas de rodapé e/ou notas de fim (por exemplo, `Footnotes.docx`)

You can add the Aspose.Words package with the following CLI command:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo projeto de console ou adicione o código a um existente. As diretivas `using` necessárias estão listadas abaixo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Esses namespaces dão acesso à classe `Document`, à hierarquia `Node` e à enumeração `NodeType` necessárias para operações de **recuperar separador de nota de rodapé**.

## Etapa 2: Carregar o documento que contém notas de rodapé e notas de fim

A primeira operação em qualquer fluxo de trabalho do Aspose.Words é carregar o arquivo de origem. Substitua o caminho placeholder pela localização real do seu `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Carregar o arquivo prepara a árvore interna de nós, o que é essencial para **recuperar o separador de nota de rodapé**, pois os nós do separador vivem dentro dessa árvore.

## Etapa 3: Recuperar o nó do separador de nota de rodapé

Agora você pode **recuperar o separador de nota de rodapé** acessando a propriedade `FootnoteSeparator` do objeto `Document`. Esse nó representa a linha que separa as notas de rodapé do texto principal.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

O `NodeType` será `Paragraph` para uma linha de separador padrão. Conhecer o tipo de nó ajuda a decidir se você precisa modificar o separador ou substituí‑lo completamente.

## Etapa 4: Recuperar o nó do separador de nota de fim

De forma semelhante, você pode **recuperar o separador de nota de fim** usando a propriedade `EndnoteSeparator`. Esse nó separa as notas de fim do conteúdo principal.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Ambos os nós de separador compartilham o mesmo `NodeType` (`Paragraph`) na maioria dos documentos, mas podem ser personalizados de forma independente.

## Etapa 5: Inspecionar ou modificar o conteúdo do separador (opcional)

Se precisar mudar a aparência visual do separador — como substituir uma linha de traços por uma regra fina — você pode editar o nó `Paragraph` diretamente. Abaixo está um exemplo que substitui o texto padrão do separador por uma string personalizada.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Depois de modificar os nós, você pode salvar o documento para ver as alterações refletidas no Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Saída esperada no console

Ao executar o programa com o `Footnotes.docx` original, você deverá ver algo semelhante a:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Se você abrir `Footnotes_Updated.docx` no Microsoft Word, os separadores de nota de rodapé e nota de fim exibirão o texto personalizado que você inseriu.

## Perguntas comuns e casos extremos

**E se o documento não tiver notas de rodapé?**  
A propriedade `FootnoteSeparator` ainda retorna um nó `Paragraph` porque o Word sempre inclui um placeholder de separador. O nó ficará vazio, então você pode adicionar conteúdo com segurança ou deixá‑lo como está.

**Posso recuperar o separador para uma seção específica?**  
Os separadores de notas de rodapé e de fim são de âmbito de documento, não de seção. Se precisar de controle ao nível da seção, você deve trabalhar com `Section.FootnoteOptions` e `Section.EndnoteOptions` em vez dos nós de separador globais.

**Isso funciona com .NET Core?**  
Sim. Aspose.Words para .NET é multiplataforma, e o mesmo código roda no Windows, Linux e macOS com .NET 6+.

**Qual tipo de nó devo esperar?**  
Tanto `FootnoteSeparator` quanto `EndnoteSeparator` retornam um nó `Paragraph` (`NodeType.Paragraph`). Se você encontrar um tipo diferente, o documento pode estar corrompido, e você deve recarregar ou validar o arquivo de origem.

## Código-fonte completo para copiar‑e‑colar rapidamente

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Copie o código para um arquivo `Program.cs`, ajuste os caminhos dos arquivos e execute `dotnet run`. O programa demonstra o fluxo completo de **recuperar separador de nota de rodapé**, desde o carregamento do documento até a persistência das alterações.

## Conclusão

Agora você sabe como **recuperar o separador de nota de rodapé** e **recuperar o separador de nota de fim** usando Aspose.Words para .NET, inspecionar seu `document node type` e, opcionalmente, substituir seu conteúdo. Essa técnica permite automatizar a formatação de notas de rodapé, gerar linhas de separador personalizadas ou validar a estrutura do documento em qualquer aplicação C#.

Em seguida, você pode explorar tópicos relacionados, como **extração de notas de rodapé em C#** para textos de notas individuais, ou aprender como **modificar marcas de referência de notas de rodapé** usando `FootnoteOptions`. Ambos os conceitos se baseiam diretamente nos fundamentos da árvore de nós abordados aqui.

Feliz codificação, e sinta‑se à vontade para experimentar diferentes estilos de separador para combinar com a identidade visual do seu projeto!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Processamento de Texto com Nota de Rodapé e Nota de Fim](/words/english/net/working-with-footnote-and-endnote/)
- [Adicionar Conteúdo Usando Document Builder no Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/)
- [Trabalhando com Nota de Rodapé e Nota de Fim](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}