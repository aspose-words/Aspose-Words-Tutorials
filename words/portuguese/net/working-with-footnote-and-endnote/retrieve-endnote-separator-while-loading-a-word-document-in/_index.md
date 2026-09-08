---
category: general
date: 2026-09-08
description: Recupere o separador de notas de fim e exiba o separador de notas de
  rodapé ao carregar um documento Word usando Aspose.Words para .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: pt
lastmod: 2026-09-08
og_description: Recupere o separador de notas finais e exiba o separador de notas
  de rodapé ao carregar um documento Word usando Aspose.Words para .NET.
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: Recuperar separador de nota final ao carregar um documento Word em C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: Recuperar separador de nota de fim ao carregar um documento Word em C#
url: /pt/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Recuperar separador de nota final ao carregar um documento Word em C#

Se você precisa **recuperar o separador de nota final** de um arquivo Word, este guia mostra exatamente como fazer isso. Você também aprenderá como **carregar documento Word** com Aspose.Words e **exibir o texto do separador de nota de rodapé** no console, tudo em um único exemplo executável.

Trabalhar com notas de rodapé e notas finais é uma necessidade comum em aplicações jurídicas, acadêmicas ou de publicação. Este tutorial cobre tudo o que você precisa — desde abrir o arquivo até lidar com casos em que um separador está ausente — para que você possa integrar a solução em qualquer projeto .NET sem adivinhações.

## O que este tutorial cobre

* Como **carregar documento Word** usando a API Aspose.Words.  
* Como **recuperar o separador de nota final** e por que o separador é importante.  
* Como **exibir o separador de nota de rodapé** no console para depuração ou registro.  
* Tratamento de casos extremos quando um documento não contém notas de rodapé ou notas finais.  
* Um exemplo de código completo, pronto para copiar e colar, que roda em .NET 6 ou posterior.

### Pré-requisitos

| Requisito | Motivo |
|-------------|--------|
| .NET 6 SDK or newer | Fornece o runtime para o exemplo em C#. |
| Aspose.Words for .NET (NuGet package `Aspose.Words`) | A biblioteca que expõe `Document.Footnotes` e `Document.Endnotes`. |
| A Word file (`Footnotes.docx`) that contains at least one footnote or endnote | Demonstrar os separadores. |
| Any IDE (Visual Studio, Rider, VS Code) | Para compilar e executar o programa. |

> **Dica profissional:** Se você não tem um documento com notas de rodapé, crie um rapidamente no Microsoft Word: Inserir → Nota de rodapé → digite algum texto, então salve como `Footnotes.docx`.

## Carregar documento Word com Aspose.Words

O primeiro passo é **carregar o documento Word** na memória. Aspose.Words lê o formato do arquivo e constrói um modelo de objetos que você pode consultar.

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*Por que isso importa*: Carregar o documento é pré-requisito para qualquer manipulação posterior. Se o caminho do arquivo estiver incorreto, `Document` lança `FileNotFoundException`, portanto verifique o caminho antes de executar.

## Recuperar parágrafo do separador de nota de rodapé

Um separador de nota de rodapé é o parágrafo que separa visualmente o texto principal da lista de notas de rodapé. Recuperá‑lo permite que você inspecione ou modifique sua formatação.

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*Por que isso importa*: **Exibir o separador de nota de rodapé** ajuda a verificar se o parágrafo correto está sendo acessado, especialmente quando você precisa aplicar um estilo personalizado (por exemplo, uma linha ou uma fonte específica).

## Recuperar parágrafo do separador de nota final

Agora nós **recuperamos o separador de nota final**. O processo espelha o tratamento de notas de rodapé, mas usa a coleção `Endnotes`.

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*Por que isso importa*: A etapa de **recuperar o separador de nota final** é essencial quando você precisa ajustar a quebra visual entre o conteúdo principal e a lista de notas finais — comum em publicações acadêmicas onde as notas finais aparecem ao final de um capítulo.

### Tratamento de separadores ausentes

Tanto `Footnotes.Separator` quanto `Endnotes.Separator` retornam `null` quando o documento não define um separador. Sempre verifique se é `null` antes de chamar `GetText()` para evitar um `NullReferenceException`. Se você precisar de um separador padrão, pode criar um:

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

Este código injeta um separador mínimo para que o processamento posterior possa contar com sua existência.

## Saída esperada no console

Quando o exemplo for executado contra um documento que contém uma nota de rodapé e uma nota final, você deverá ver algo semelhante a:

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

Se o documento não possuir notas de rodapé ou notas finais, o programa imprime as mensagens correspondentes de “não encontrado”, demonstrando um tratamento de erro elegante.

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar para um novo projeto de console C#. Nenhum código adicional é necessário.

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

Salve o arquivo como `Program.cs`, adicione o pacote NuGet Aspose.Words (`dotnet add package Aspose.Words`) e execute `dotnet run`. O programa imprimirá os textos dos separadores ou informará se eles estiverem ausentes.

## Variações comuns e cenários hipotéticos

| Cenário | Como adaptar o código |
|----------|-----------------------|
| **Múltiplos separadores personalizados** | Use `doc.Footnotes.Separator` para substituir o padrão, então adicione parágrafos de separador adicionais manualmente com `doc.Footnotes.Add(separatorParagraph)`. |
| **Alterar o estilo do separador** | Depois de recuperar o separador, modifique seu `ParagraphFormat` (por exemplo, `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`). |
| **Trabalhando com arquivos .doc** | A mesma API funciona; apenas certifique‑se de que o caminho do arquivo termine com `.doc`. |
| **Processando muitos documentos** | Envolva o carregamento e a recuperação do separador em um loop `foreach`; reutilize uma única instância `Document` apenas se você a redefinir com `doc = new Document(path)`. |

## Checklist de boas práticas

- ✅ **Sempre verifique se é `null`** antes de acessar o texto do separador.  
- ✅ **Remova espaços** (trim) do resultado de `GetText()` para eliminar caracteres de quebra de linha ocultos.  
- ✅ **Dispose** de objetos `Document` grandes se você processar muitos arquivos em lote (use `using` ou chame `doc.Dispose()`).  
- ✅ **Registre** o texto do separador apenas em desenvolvimento; evite expô‑lo em logs de produção, a menos que seja necessário.  

## Conclusão

Agora você sabe como **recuperar o separador de nota final** enquanto **carrega o documento Word** e **exibe o separador de nota de rodapé** em uma aplicação console .NET. O exemplo completo demonstra o carregamento, a consulta e o tratamento seguro de separadores ausentes, proporcionando uma base sólida para qualquer tarefa de manipulação de notas de rodapé ou notas finais.

Em seguida, você pode explorar:

* **Personalizar a formatação de notas de rodapé/nota final** – ajuste fontes, bordas ou estilos de numeração.  
* **Extrair o conteúdo de notas de rodapé/nota final** – itere as coleções `doc.Footnotes` ou `doc.Endnotes`.  
* **Salvar o documento modificado** – use `doc.Save("output.docx")` para persistir as alterações.

Sinta‑se à vontade para experimentar diferentes arquivos Word, estilos de separador e recursos do Aspose.Words. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como carregar documentos Word usando Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)
- [Obter separador de estilo de parágrafo em documento Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Criar e estilizar um documento Word no Aspose.Words para .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}