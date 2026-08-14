---
category: general
date: 2026-08-14
description: Como adicionar SDT rapidamente com Aspose.Words. Aprenda a criar um placeholder
  de Word e inserir um controle de texto simples em um arquivo .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: pt
lastmod: 2026-08-14
og_description: Como adicionar SDT em C# usando Aspose.Words. Siga este tutorial para
  criar um placeholder de Word e inserir um controle de texto simples para documentos
  dinâmicos.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Como adicionar SDT em C# – guia passo a passo de placeholders no Word
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Como adicionar SDT em C# – guia completo para placeholders do Word
url: /pt/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar SDT em C# – guia completo para marcadores de posição no Word

Se você precisa **how to add sdt** em um arquivo Word, este tutorial mostra as etapas exatas usando Aspose.Words for .NET. Ao final do guia, você será capaz de **create word placeholder** tags que permitem que os usuários finais digitem diretamente em um documento, e entenderá como **insert plain text control** de forma confiável.

Trabalhar com Structured Document Tags (SDTs) elimina a necessidade de campos de formulário manuais e oferece uma maneira limpa e programática de criar contratos, relatórios ou cartas dinâmicas. O exemplo abaixo cobre tudo, desde a configuração do projeto até a gravação do arquivo .docx final, para que você possa copiar‑colar o código em sua própria solução sem perder nenhuma dependência.

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
- Visual Studio 2022 ou qualquer IDE C# que você prefira
- Uma licença Aspose.Words for .NET (uma licença temporária gratuita funciona para testes)
- Familiaridade básica com a sintaxe C# e o conceito de SDTs

> **Dica profissional:** Se você planeja distribuir os documentos gerados, incorpore um arquivo de licença para evitar a marca d'água de avaliação.

## Etapa 1: Configurar o projeto e importar Aspose.Words

Crie uma nova aplicação console e adicione o pacote NuGet Aspose.Words:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Essas diretivas `using` dão acesso às classes `Document`, `DocumentBuilder` e `StructuredDocumentTag` que são necessárias para operações de **insert plain text control**.

## Etapa 2: Inicializar o documento e o builder

O primeiro bloco de código cria um documento Word vazio e um `DocumentBuilder` que permite escrever conteúdo nele.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funciona como um cursor; cada chamada subsequente adiciona conteúdo na posição atual. Inicializar o documento é a base para todo cenário de **how to add sdt**, pois o SDT deve pertencer a uma instância `Document` ativa.

## Etapa 3: Inserir um Structured Document Tag (SDT) de texto simples

Agora nós **insert plain text control** que funciona como um marcador de posição onde o usuário pode digitar um nome, uma data ou qualquer valor personalizado.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` indica ao Aspose.Words para criar um campo de texto simples.
- `SdtAppearanceTags.Default` fornece à tag o estilo visual padrão do Word (uma caixa sombreada quando o documento é aberto no Word).

## Etapa 4: Configurar o SDT com um título e texto de marcador de posição

Um SDT bem nomeado torna o documento autoexplicativo para os usuários finais. Aqui nós **create word placeholder** metadados e definimos a dica que aparece dentro do campo.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` é o identificador interno que você pode usar posteriormente ao extrair ou atualizar o valor programaticamente.
- `PlaceholderName` é a dica em cinza exibida no Word, indicando ao usuário o que digitar.

## Etapa 5: Adicionar conteúdo ao redor

Um documento raramente consiste em um único SDT. Normalmente você precisa de parágrafos regulares antes e depois do marcador de posição. Use o método `WriteLine` do builder para adicionar texto estático.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

A chamada a `InsertNode` coloca o SDT criado anteriormente exatamente onde você precisa, preservando o fluxo de texto ao redor.

## Etapa 6: Salvar o documento em um arquivo .docx

Finalmente, persista o documento no disco. O caminho pode ser absoluto ou relativo à pasta do projeto.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Abrir `SDT.docx` no Microsoft Word mostra um marcador de posição cinza que contém **Enter name here**. Os usuários podem clicar no campo, digitar um valor, e o documento manterá esse valor ao ser salvo novamente.

## Exemplo completo e executável

Juntando todas as peças, você obtém um programa autônomo que pode ser executado imediatamente:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Saída esperada** ao executar o programa:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Abrir o `SDT.docx` gerado mostra:

```
Dear [Enter name here],
After the SDT
```

O texto entre colchetes é o marcador de posição **insert plain text control** que os usuários podem substituir.

## Variações comuns e casos extremos

| Situação | Como adaptar o código |
|-----------|-----------------------|
| **Multiple placeholders** | Chame `InsertStructuredDocumentTag` repetidamente e dê a cada tag um `Title` exclusivo. |
| **Rich‑text SDT** | Use `StructuredDocumentTagType.RichText` em vez de `PlainText`. |
| **Lock the placeholder** | Defina `plainTextTag.LockContentControl = true;` para impedir que os usuários excluam o campo. |
| **Pre‑populate with a value** | Atribua `plainTextTag.Text = "John Doe";` antes de salvar. |
| **Conditional appearance** | Use `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` para um controle de caixa de seleção. |

Essas variações permitem que você **create word placeholder** estruturas que correspondem a quase qualquer cenário semelhante a formulário.

## Dicas de solução de problemas

- **Placeholder not visible** – Certifique-se de abrir o arquivo no Microsoft Word (ou em um visualizador compatível). Alguns editores leves ocultam SDTs.
- **License warning** – Se você vir uma marca d'água de avaliação, verifique se o seu arquivo de licença foi carregado corretamente (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – Após inserir um SDT, o cursor do builder permanece *depois* da tag. Se precisar adicionar texto *dentro* da tag, use `builder.MoveTo(plainTextTag);` antes de escrever.

## Conclusão

Agora você sabe **how to add sdt** a um documento Word usando Aspose.Words for .NET, como **create word placeholder** tags, e como **insert plain text control** que os usuários podem editar diretamente no Word. O exemplo completo demonstra inicialização, inserção de tags, configuração, conteúdo ao redor e salvamento — tudo em um único programa executável.

Em seguida, explore tópicos relacionados como **insert rich text control**, **populate SDTs from a database**, ou **convert the final document to PDF**. Todos esses se baseiam nos mesmos fundamentos abordados aqui, para que você possa expandir seu pipeline de automação com confiança.

Feliz codificação, e sinta-se à vontade para experimentar diferentes tipos de SDT para atender às suas necessidades de automação de documentos!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Como criar intervalos editáveis em documentos somente leitura usando Aspose.Words para Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Adicionar marcadores Word com Aspose.Words para Java – Inserir, Atualizar, Excluir](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}