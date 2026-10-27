---
category: general
date: 2026-10-13
description: Crie um novo documento Word em C# e insira um controle de conteúdo com
  texto de espaço reservado. Aprenda como definir o texto de espaço reservado e salvar
  o documento Word de forma eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: pt
lastmod: 2026-10-13
og_description: Criar novo documento Word em C# com Aspose.Words, inserir um controle
  de conteúdo, definir texto de espaço reservado e salvar o documento Word — tudo
  em um único guia.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Criar novo documento Word e inserir controle de conteúdo em C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Criar novo documento Word e inserir controle de conteúdo em C#
url: /pt/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie um novo documento Word e insira controle de conteúdo em C#

Se você precisa **criar um novo documento Word** programaticamente, este guia mostra como fazer isso com Aspose.Words para .NET. Você aprenderá a **inserir controle de conteúdo**, atribuir **texto de espaço reservado** e, finalmente, **salvar documento Word C#** com código que pode copiar para o seu projeto.

O tutorial percorre cada passo, explica por que cada chamada de API é importante e aborda variações comuns, como adicionar um SDT de texto rico ou lidar com documentos existentes. Ao final, você terá um exemplo completo e executável que pode adaptar para faturas, contratos ou qualquer saída Word baseada em modelo.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+)
* Pacote NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`)
* Uma IDE como Visual Studio 2022 ou Visual Studio Code

Nenhuma biblioteca adicional é necessária.

## Crie um novo documento Word com Aspose.Words

O primeiro passo é instanciar um objeto `Document`. Esse objeto representa um arquivo Word vazio na memória.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` fornece uma API fluente para inserir elementos na posição atual do cursor. Como o documento está vazio, o cursor começa no início da primeira (e única) seção.

## Insira controle de conteúdo (StructuredDocumentTag)

Um **controle de conteúdo** no Word é chamado de Structured Document Tag (SDT). O código a seguir cria um SDT de texto simples, define seu título e especifica o texto de espaço reservado que aparece quando o usuário abre o arquivo.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Por que isso importa:**  
* `SdtType.PlainText` restringe o conteúdo a uma única linha de texto simples, ideal para campos simples como nome ou e‑mail.  
* Definir `PlaceholderName` fornece uma pista visual (`Enter name here`) que orienta o usuário final.  

Se precisar de um campo mais rico (por exemplo, texto multilinha ou seletor de data), substitua `SdtType.PlainText` por `SdtType.RichText` ou `SdtType.Date`.

## Adicione texto opcional ao redor

A maioria dos modelos inclui um rótulo antes do controle de conteúdo. Você pode adicioná‑lo com a mesma instância de `DocumentBuilder`:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

O arquivo Word resultante mostra:

```
Customer Name: [Enter name here]
```

## Salve o documento Word no estilo C#

Por fim, grave o documento no disco. Aspose.Words determina automaticamente o formato a partir da extensão do arquivo.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ao abrir `output.docx` no Microsoft Word, você verá o texto de espaço reservado dentro de um controle de conteúdo sombreado em cinza. Os usuários podem clicar no controle e substituir o espaço reservado pelo próprio valor.

## Exemplo completo e executável

Abaixo está um programa de console autocontido que reúne tudo. Copie o código para um novo projeto de console e execute-o.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Saída esperada** (console):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

Abrir `output.docx` mostra uma única linha com o rótulo *Customer Name:* seguido por um controle de conteúdo que exibe *Enter name here*.

## Variações comuns e casos de borda

| Cenário | Alteração de código | Motivo |
|----------|---------------------|--------|
| **Campo rich‑text** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Permite entrada multilinha e formatação básica. |
| **Controle somente leitura** | `sdt.LockContentControl = true;` | Impede que os usuários editem o conteúdo do controle. |
| **Pré‑popular com dados** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Insere um valor padrão que sobrescreve o espaço reservado. |
| **Adicionar a um documento existente** | Carregue com `new Document("template.docx")` em vez de um `Document` vazio | Habilita cenários de modelagem onde o controle é colocado em um layout pré‑definido. |
| **Múltiplos controles** | Repita o bloco de criação com títulos e espaços reservados diferentes | Útil para formulários que coletam várias informações. |

### Dica profissional

Ao gerar documentos grandes, reutilize uma única instância de `DocumentBuilder` em vez de criar uma nova para cada controle. Isso reduz o consumo de memória e melhora o desempenho.

## Testando o resultado

1. Execute o aplicativo de console.  
2. Abra `output.docx` no Microsoft Word.  
3. Verifique se o texto de espaço reservado aparece dentro de uma caixa sombreada em cinza.  
4. Clique na caixa, digite um nome e salve o arquivo. O texto inserido substitui o espaço reservado.

Se o espaço reservado não aparecer, confirme que você está usando a versão 23.9 ou posterior do Aspose.Words, pois versões mais antigas tinham um bug com `PlaceholderName` em SDTs de texto simples.

## Conclusão

Agora você sabe como **criar um novo documento Word**, **inserir controle de conteúdo**, **definir texto de espaço reservado** e **salvar documento Word C#** usando Aspose.Words. O exemplo completo demonstra o padrão padrão, e a tabela de variações mostra como adaptar a solução para cenários mais avançados.

Em seguida, você pode explorar:

* **Inserir controle de conteúdo para datas** – use a enumeração `SdtType.Date`.  
* **Popular um modelo com dados** – combine `StructuredDocumentTag` com campos de mala‑direta.  
* **Exportar para PDF** – chame `doc.Save("output.pdf")` após adicionar os controles.

Sinta‑se à vontade para experimentar diferentes tipos de SDT, configurações de bloqueio e estilos para atender aos requisitos do seu projeto. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}