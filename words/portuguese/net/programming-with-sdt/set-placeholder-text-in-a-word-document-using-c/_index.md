---
category: general
date: 2026-10-20
description: Defina texto de espaço reservado em um documento Word usando C#. Aprenda
  como adicionar controle e definir o espaço reservado rapidamente com Aspose.Words
  para .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: pt
lastmod: 2026-10-20
og_description: Defina texto de espaço reservado em um documento Word com C#. Este
  tutorial mostra como adicionar controle, definir espaço reservado e gerar arquivos
  Word programaticamente.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Defina texto de espaço reservado em um documento Word com C# – guia passo
  a passo
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Definir texto de espaço reservado em um documento Word usando C#
url: /pt/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir texto de espaço reservado em um documento Word usando C#

Se você precisar **definir texto de espaço reservado** em um arquivo Microsoft Word ao gerá‑lo com C#, este guia mostra exatamente como. Você verá uma solução concisa, de ponta a ponta, que adiciona um controle de conteúdo, define seu espaço reservado e salva o documento — tudo com Aspose.Words para .NET.

Muitos desenvolvedores se perguntam **como adicionar controle** a um documento Word ou **como definir espaço reservado** sem abrir o Word manualmente. Este tutorial responde a essas perguntas e também demonstra uma forma limpa de **gerar arquivos Word C#** que estão prontos para a entrada do usuário.

## O que você vai alcançar

* Criar um documento Word em branco programaticamente.
* Inserir um Structured Document Tag (SDT) de texto simples, que é o nome técnico para um controle de conteúdo.
* Atribuir um título significativo e texto de espaço reservado ao SDT.
* Salvar o arquivo `.docx` resultante no disco.

Nenhuma ferramenta adicional é necessária além da biblioteca Aspose.Words e de um ambiente de desenvolvimento .NET 6 (ou posterior).

## Pré-requisitos

* .NET 6 SDK ou mais recente instalado.  
* Visual Studio 2022 (ou qualquer IDE que suporte .NET).  
* Pacote NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`).  

> **Dica profissional:** Use a versão de avaliação gratuita do Aspose.Words se você estiver apenas testando; ela adiciona uma marca d'água, mas funciona da mesma forma que a versão licenciada.

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo projeto de console e adicione as diretivas `using` necessárias. Elas trazem as classes principais do Aspose.Words e o namespace de marcação para o escopo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Por que esta etapa importa:* Importar `Aspose.Words.Markup` fornece acesso a `StructuredDocumentTag`, `SdtType` e `MarkupLevel` — os objetos necessários para **adicionar controle** e **definir espaço reservado**.

## Etapa 2: Criar um documento em branco e um DocumentBuilder

Um `Document` representa todo o arquivo Word, enquanto um `DocumentBuilder` fornece um cursor conveniente para inserir elementos.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que esta etapa importa:* Começar com um documento limpo garante que o espaço reservado que você definir apareça exatamente onde pretende, sem interferência de conteúdo existente.

## Etapa 3: Criar o controle de conteúdo (Structured Document Tag)

Aqui criamos um SDT de texto simples, atribuímos um título e definimos o texto de espaço reservado que o usuário verá quando o controle estiver vazio.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Por que esta etapa importa:* A propriedade `Title` permite referenciar o controle posteriormente (por exemplo, para vinculação de dados). `PlaceholderName` é precisamente o **texto de espaço reservado** que você deseja que apareça, orientando o usuário final.

## Etapa 4: Inserir o controle na posição atual do cursor

Usando o `DocumentBuilder`, insira o SDT no documento onde o builder está posicionado atualmente.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Por que esta etapa importa:* Inserir o nó anexa o controle ao DOM do documento. Se precisar adicionar vários espaços reservados, você pode mover o cursor do builder e repetir esta etapa.

## Etapa 5: Salvar o documento

Finalmente, grave o documento no disco. Substitua `YOUR_DIRECTORY` por um caminho real em sua máquina.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ao abrir `SDT.docx` no Microsoft Word, você verá uma caixa de texto em linha sombreada em cinza que exibe **Enter name here**. Clicar dentro da caixa limpa o espaço reservado, permitindo que o usuário digite um nome de cliente.

### Saída esperada

| Local do arquivo | Pré‑visualização do conteúdo |
|------------------|------------------------------|
| `C:\Temp\SDT.docx` | Espaço reservado em linha **Enter name here** dentro de um controle de conteúdo de texto simples intitulado *CustomerName*. |

## Casos de borda e variações

| Situação | Ajuste recomendado |
|----------|--------------------|
| **Múltiplos espaços reservados** | Crie objetos `StructuredDocumentTag` adicionais com valores diferentes de `Title` e `PlaceholderName`, e então insira cada um onde for necessário. |
| **Espaço reservado de texto rico** | Use `SdtType.RichText` em vez de `PlainText` para permitir formatação dentro do espaço reservado. |
| **Controle de nível de bloco** | Altere `MarkupLevel.Inline` para `MarkupLevel.Block` para que o controle se comporte como um parágrafo completo. |
| **Espaço reservado não visível** | Certifique‑se de que as configurações de visualização do documento no Word não estejam definidas para ocultar controles de conteúdo (`File → Options → Advanced → Show content controls`). |
| **Salvar em um stream** | Chame `doc.Save(stream, SaveFormat.Docx)` se precisar enviar o arquivo via HTTP em vez de gravá‑lo no disco. |

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar, colar e executar. Ele inclui todas as etapas acima em um único método `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Execute o programa, abra o arquivo gerado e você verá o texto de espaço reservado pronto para a entrada do usuário.

## Perguntas comuns respondidas

**Q: Isso funciona com .NET Core?**  
A: Sim. Aspose.Words para .NET é compatível com .NET Core, .NET 5 e .NET 6+. O mesmo código roda sem alterações.

**Q: Posso definir um valor padrão além do espaço reservado?**  
A: Use `sdt.SetText("Default value")` após criar o SDT. O espaço reservado desaparece assim que um valor é definido.

**Q: E se eu precisar recuperar o valor inserido mais tarde?**  
A: Carregue o documento, localize o SDT pelo seu `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) e leia `sdt.GetText()`.

## Conclusão

Agora você sabe como **definir texto de espaço reservado** em um documento Word usando C#. Ao criar um `StructuredDocumentTag` de texto simples, atribuir um título e um espaço reservado, inseri‑lo com um `DocumentBuilder` e salvar o arquivo, você pode **adicionar controle** e **gerar Word C#** programaticamente.  

A partir daqui você pode explorar:

* Adicionar controles de texto rico ou lista suspensa (`SdtType.RichText`, `SdtType.DropDownList`).  
* Preencher múltiplos espaços reservados a partir de um banco de dados.  
* Converter o `.docx` gerado para PDF com Aspose.Words.

Experimente diferentes tipos de controle e estilos de espaço reservado para atender às necessidades da sua aplicação. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Definir texto de espaço reservado no Aspose.Words – Guia completo em C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Criar documento Word programaticamente – adicionar controle de conteúdo e espaço reservado](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Como adicionar controle de conteúdo e criar documento Word com Aspose – Completo](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}