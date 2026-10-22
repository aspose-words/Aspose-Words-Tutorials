---
category: general
date: 2026-09-11
description: Adicione um controle de conteúdo em um documento Word usando Aspose.Words.
  Siga este guia passo a passo para inserir programaticamente uma Tag de Documento
  Estruturado (SDT) de texto simples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control in word document
- StructuredDocumentTag
- DocumentBuilder
- Aspose.Words
- plain‑text SDT
- word automation
language: pt
lastmod: 2026-09-11
og_description: Adicione controle de conteúdo em documento Word com Aspose.Words.
  Este guia mostra como inserir programaticamente uma Tag de Documento Estruturado
  (SDT) de texto simples e personalizá‑la.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Adicionar controle de conteúdo em documento Word – tutorial completo do
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Add content control in Word document using Aspose.Words. Follow this
    step‑by‑step guide to insert a plain‑text Structured Document Tag (SDT) programmatically.
  headline: Add content control in Word document with Aspose.Words
  type: TechArticle
tags:
- word
- content‑control
- csharp
- aspose
title: Adicionar controle de conteúdo em documento Word com Aspose.Words
url: /pt/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar controle de conteúdo em documento Word com Aspose.Words

Se você precisa **adicionar controle de conteúdo em documento Word** programaticamente, este tutorial mostra exatamente como fazer isso com Aspose.Words para .NET. Seja você quem está construindo um serviço de geração de documentos ou automatizando a criação de formulários, aprenderá a inserir um Structured Document Tag (SDT) de texto simples e atribuir a ele um título significativo.

Neste guia você verá um exemplo completo e executável que cobre todas as importações necessárias, explica por que cada chamada de API é importante e demonstra como verificar o resultado. Nenhuma referência externa é necessária — basta copiar o código, executá‑lo e abrir o arquivo *.docx* gerado.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou superior instalado  
* Visual Studio 2022 (ou qualquer IDE C#)  
* Aspose.Words para .NET 23.5 ou mais recente – você pode obter o pacote NuGet de avaliação gratuita  

Esses itens constituem a configuração mínima para **automação de Word** com Aspose.Words.

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo projeto de console e adicione o pacote Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Agora abra `Program.cs` e adicione as diretivas `using` necessárias:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;
```

Esses namespaces dão acesso ao `DocumentBuilder`, `StructuredDocumentTag` e outros tipos centrais necessários para **adicionar controle de conteúdo em documento Word**.

## Etapa 2: Criar um novo documento e um DocumentBuilder

Um `DocumentBuilder` é o ponto de entrada principal para construir arquivos Word. Ele mantém um cursor que rastreia onde o próximo elemento será inserido.

```csharp
// Step 2: Initialize a new blank document and a builder
Document doc = new Document();                 // creates an empty .docx
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa*: O objeto `Document` representa todo o arquivo Word, enquanto o `DocumentBuilder` simplifica a inserção de parágrafos, tabelas e **controles de conteúdo** como Structured Document Tags.

## Etapa 3: Inserir um Structured Document Tag (SDT) de texto simples

O núcleo da nossa solução é o método `insertStructuredDocumentTag`. Ele cria um **controle de conteúdo** que pode conter texto simples, datas, listas suspensas etc. Aqui usamos o valor de enum `SdtType.PLAIN_TEXT`.

```csharp
// Step 3: Insert a plain‑text SDT at the current cursor position
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText,   // the type of control – plain‑text here
    true);               // true = the tag is shown as a placeholder in the UI
```

*Por que isso importa*: Definir `true` faz o controle aparecer como um marcador de posição em cinza‑claro, sinalizando aos usuários finais que eles devem preencher o campo.

## Etapa 4: Atribuir um título ao SDT para identificação posterior

Um título (ou tag) permite localizar o controle mais tarde, por exemplo quando for necessário substituir seu conteúdo programaticamente.

```csharp
// Step 4: Assign a title so you can find the control later
sdt.Title = "CustomerName";
```

O título não aparece na interface do documento, mas é armazenado no XML subjacente e pode ser consultado via API Aspose.Words.

## Etapa 5: Inserir texto de marcador de posição dentro do SDT

Para tornar o controle mais amigável, insira uma `Run` padrão que indique ao usuário o que digitar.

```csharp
// Step 5: Add placeholder text inside the SDT
Run placeholder = new Run(builder.Document, "Enter name here");
sdt.AppendChild(placeholder);
```

*Por que isso importa*: O objeto `Run` representa um trecho de texto. Ao adicioná‑lo ao SDT, você cria uma dica visível que desaparece assim que o usuário começa a digitar.

## Etapa 6: Salvar o documento

Por fim, grave o documento no disco para que você possa abri‑lo no Microsoft Word.

```csharp
// Step 6: Save the finished document
string outPath = "ContentControlExample.docx";
doc.Save(outPath);
Console.WriteLine($"Document saved to {outPath}");
```

Ao abrir `ContentControlExample.docx`, você verá um controle de conteúdo sombreado em cinza com o título **CustomerName** e o texto de marcador de posição *Enter name here*.

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar‑colar em `Program.cs`. Ele inclui todas as etapas, comentários e o tratamento de erros necessário.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;

namespace ContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document
            Document doc = new Document();

            // Initialize the DocumentBuilder – this controls where we insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text Structured Document Tag (SDT)
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,   // type of content control
                true);               // show as placeholder

            // Assign a title for later lookup (not visible in the UI)
            sdt.Title = "CustomerName";

            // Add placeholder text that instructs the user
            Run placeholder = new Run(builder.Document, "Enter name here");
            sdt.AppendChild(placeholder);

            // Save the document to the file system
            string outPath = "ContentControlExample.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Saída esperada

Executar o programa exibe:

```
Document saved to ContentControlExample.docx
```

Abrir o arquivo gerado no Word mostra um único controle de conteúdo com o marcador de posição cinza **Enter name here**. O controle pode ser editado, excluído ou acessado programaticamente mais tarde usando seu título *CustomerName*.

## Variações comuns e casos de borda

| Cenário | Como adaptar o código |
|----------|----------------------|
| **Múltiplos controles de conteúdo** | Chame `InsertStructuredDocumentTag` repetidamente, atribuindo um `Title` exclusivo a cada chamada. |
| **Controle de conteúdo Rich‑text** | Use `SdtType.RichText` em vez de `PlainText`. |
| **Controle de seleção de data** | Use `SdtType.Date` e, opcionalmente, defina `sdt.DateDisplayFormat`. |
| **Bloquear o controle** | Defina `sdt.LockContentControl = true` para impedir que os usuários o removam. |
| **Localizar um controle posteriormente** | Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` e filtre por `Title`. |

Essas variações ilustram a flexibilidade do **Aspose.Words** quando você precisa **adicionar controle de conteúdo em documento Word** para diferentes cenários de preenchimento de formulários.

## Dicas profissionais

* **Desempenho** – Se você estiver gerando muitos documentos em um loop, reutilize uma única instância de `DocumentBuilder` e chame `doc.Clone()` para cada iteração, evitando a construção repetida de objetos.  
* **Estilização** – Você pode aplicar um `ParagraphFormat` ou `Font` ao `Run` de marcador de posição para combinar com o tema visual do seu documento.  
* **Validação** – Após inserir um controle, você pode inspecionar `sdt.IsShowingPlaceholderText` para confirmar que o marcador de posição está sendo exibido corretamente.  

## Conclusão

Agora você sabe como **adicionar controle de conteúdo em documento Word** com Aspose.Words, desde a criação de um `DocumentBuilder` até a inserção de um `StructuredDocumentTag` de texto simples, atribuição de título e adição de texto de marcador de posição. O exemplo completo pode ser estendido para outros tipos de SDT, múltiplos controles e opções avançadas de bloqueio ou estilização.

Pronto para avançar? Explore os tópicos relacionados:

* **Trabalhando com tabelas dentro de controles de conteúdo** – use `DocumentBuilder.InsertTable` após o SDT.  
* **Extraindo dados de controles preenchidos** – recupere o nó `Sdt` pelo título e leia sua propriedade `Text`.  
* **Usando o OpenXML SDK** – uma abordagem alternativa caso você prefira uma biblioteca gratuita e suportada pela Microsoft.

Experimente o código, adapte‑o ao seu fluxo de geração de formulários e aproveite o poder da automação programática de Word.


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}