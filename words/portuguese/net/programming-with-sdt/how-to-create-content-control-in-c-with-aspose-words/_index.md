---
category: general
date: 2026-08-07
description: Como criar controle de conteúdo em C# usando Aspose.Words – aprenda a
  adicionar SDT, definir marcador de posição, escrever texto padrão e inserir controle
  de texto simples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create content control
- how to add sdt
- how to set placeholder
- how to write default text
- insert plain text control
language: pt
lastmod: 2026-08-07
og_description: Como criar um controle de conteúdo em C# com Aspose.Words. Este tutorial
  mostra como adicionar SDT, definir um marcador de posição, escrever texto padrão
  e inserir um controle de texto simples.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Como criar controle de conteúdo em C# – guia completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  headline: How to create content control in C# with Aspose.Words
  type: TechArticle
- description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  name: How to create content control in C# with Aspose.Words
  steps:
  - name: Expected output
    text: '- A `.docx` file on the desktop named `CustomerNameControl.docx`. - Inside
      the file, a single content control containing the text **John Doe**. - The placeholder
      text appears in light gray until the user types a new value.'
  - name: Adding multiple content controls
    text: You can repeat the **how to add sdt** steps to insert several controls in
      the same document. Just create a new `StructuredDocumentTag` for each field
      and move the builder accordingly.
  - name: Reading a placeholder programmatically
    text: 'If you need to verify that a placeholder was set correctly, inspect the
      `PlaceholderName` property:'
  - name: Using other SDT types
    text: Aspose.Words supports dropdown lists, date pickers, and rich‑text controls.
      Replace `SdtType.PlainText` with `SdtType.DropDownList` or `SdtType.RichText`
      to change the control type.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- SDT
title: Como criar controle de conteúdo em C# com Aspose.Words
url: /pt/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar controle de conteúdo em C# com Aspose.Words

Se você precisa **como criar controle de conteúdo** em um documento Word programaticamente, este guia mostra exatamente isso. Você verá como adicionar um SDT, definir um placeholder, escrever texto padrão e inserir um controle de texto simples — tudo com Aspose.Words para .NET.

O tutorial cobre cada passo, desde a configuração do projeto até a gravação do arquivo final `.docx`. Ao final, você será capaz de gerar documentos que contêm controles de conteúdo totalmente configurados, prontos para processamento posterior ou interação do usuário.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

- .NET 6.0 ou superior (o código também funciona com .NET Framework 4.7+)
- Uma licença do Aspose.Words para .NET ou uma chave de avaliação temporária
- Visual Studio 2022 (ou qualquer IDE que suporte C#)
- Familiaridade básica com a sintaxe C#

Nenhum pacote NuGet adicional é necessário além do `Aspose.Words`.

## Como criar controle de conteúdo – passo 1: configurar o projeto

Crie um novo aplicativo de console e adicione o pacote Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

O processo **como criar controle de conteúdo** começa com um objeto `Document` novo. Esse objeto representa o arquivo Word que você irá manipular.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Dica:** Mantenha a instância `DocumentBuilder` viva durante todo o ciclo de vida do documento; recriá‑la desnecessariamente adiciona sobrecarga.

## Como adicionar SDT – passo 2: inserir uma Structured Document Tag de texto simples

Um SDT (Structured Document Tag) é o nome técnico para um controle de conteúdo. Para **como adicionar sdt**, instancie um `StructuredDocumentTag` com o tipo desejado.

```csharp
        // Create a plain‑text SDT (content control)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document,
            SdtType.PlainText,   // Plain‑text control
            true);               // Is it a repeating section? false for single use

        // Give the control a title – this is how you reference it later
        sdt.Title = "CustomerName";

        // Insert the SDT at the current cursor position
        builder.InsertNode(sdt);
```

A opção `SdtType.PlainText` cria uma caixa de texto simples que os usuários podem editar. Definir a `Title` ajuda a localizar o controle quando você precisar recuperar ou modificar seu conteúdo posteriormente.

## Como definir placeholder – passo 3: configurar texto de placeholder

Um placeholder orienta o usuário final exibindo texto de exemplo antes que ele digite algo. Para **como definir placeholder**, atribua a propriedade `PlaceholderName`.

```csharp
        // Define the placeholder that appears when the control is empty
        sdt.PlaceholderName = "Enter name here";
```

Quando o documento for aberto no Microsoft Word, o texto placeholder cinza aparecerá dentro do controle até que o usuário forneça um valor.

## Como escrever texto padrão – passo 4: adicionar conteúdo inicial dentro do SDT

Se você quiser que o controle contenha conteúdo pré‑definido, deve mover o builder para dentro do SDT e escrever o texto. Isso demonstra **como escrever texto padrão**.

```csharp
        // Position the builder inside the SDT so we can add content
        builder.MoveTo(sdt);

        // Write the default text that will be visible initially
        builder.Write("John Doe");
```

A chamada a `MoveTo` altera a posição do cursor para o interior do SDT. Após `Write`, o controle exibe “John Doe” como seu valor inicial.

## Inserir controle de texto simples – passo 5: salvar o documento

Finalmente, persista o documento no disco. Isso completa a operação **inserir controle de texto simples**.

```csharp
        // Save the document with the content control embedded
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CustomerNameControl.docx");

        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ao abrir `CustomerNameControl.docx` no Word, você verá um controle de conteúdo de texto simples intitulado **CustomerName**, exibindo o placeholder “Enter name here” e o texto padrão “John Doe”.

### Saída esperada

- Um arquivo `.docx` na área de trabalho chamado `CustomerNameControl.docx`.
- Dentro do arquivo, um único controle de conteúdo contendo o texto **John Doe**.
- O texto placeholder aparece em cinza claro até que o usuário digite um novo valor.

## Variações adicionais e casos de borda

### Adicionando múltiplos controles de conteúdo

Você pode repetir os passos **como adicionar sdt** para inserir vários controles no mesmo documento. Basta criar um novo `StructuredDocumentTag` para cada campo e mover o builder conforme necessário.

```csharp
// Example: add a second control for "OrderNumber"
StructuredDocumentTag orderTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
orderTag.Title = "OrderNumber";
orderTag.PlaceholderName = "Enter order #";
builder.InsertNode(orderTag);
builder.MoveTo(orderTag);
builder.Write("12345");
```

### Lendo um placeholder programaticamente

Se precisar verificar se um placeholder foi definido corretamente, inspecione a propriedade `PlaceholderName`:

```csharp
string placeholder = sdt.PlaceholderName; // returns "Enter name here"
```

### Usando outros tipos de SDT

Aspose.Words suporta listas suspensas, seletores de data e controles de rich‑text. Substitua `SdtType.PlainText` por `SdtType.DropDownList` ou `SdtType.RichText` para mudar o tipo de controle.

## Armadilhas comuns e como evitá‑las

| Sintoma | Causa | Solução |
|---------|-------|-----|
| Placeholder nunca aparece | O documento foi salvo antes de o placeholder ser atribuído | Garanta que `PlaceholderName` seja definido **antes** de chamar `Save`. |
| Texto padrão está ausente | Builder não foi movido para dentro do SDT | Chame `builder.MoveTo(sdt)` antes de `builder.Write`. |
| Título do controle está vazio | Propriedade `Title` não foi definida | Sempre atribua um `Title` significativo para recuperação posterior. |

## Conclusão

Agora você sabe **como criar controle de conteúdo** em C# usando Aspose.Words, incluindo **como adicionar sdt**, **como definir placeholder**, **como escrever texto padrão** e **inserir controle de texto simples**. O exemplo completo compila em um arquivo Word pronto para uso que demonstra cada conceito.

A partir daqui, você pode explorar cenários mais avançados, como vincular controles de conteúdo a dados XML, manipular seções repetitivas ou converter o documento para PDF preservando os controles. Cada um desses tópicos se baseia diretamente nos fundamentos abordados neste tutorial.

Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Rich Text Box Content Control](/words/hindi/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/hongkong/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/spanish/net/programming-with-sdt/rich-text-box-content-control/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}