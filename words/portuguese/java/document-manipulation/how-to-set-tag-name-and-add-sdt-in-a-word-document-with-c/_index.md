---
category: general
date: 2026-09-08
description: Defina o nome da tag e crie um controle de conteúdo (SDT) em um documento
  Word usando C#. Aprenda como adicionar SDT, escrever texto na tag e modificar o
  documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: pt
lastmod: 2026-09-08
og_description: Defina o nome da tag e crie um controle de conteúdo (SDT) em um documento
  Word usando C#. Siga este guia passo a passo para adicionar SDT, escrever texto
  na tag e modificar o documento.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Defina o nome da tag e adicione SDT em um documento Word – Guia C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Como definir o nome da tag e adicionar SDT em um documento Word com C#
url: /pt/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como definir o nome da tag e adicionar SDT em um documento Word com C#

Se você precisa **definir o nome da tag** para um StructuredDocumentTag (SDT) ao trabalhar com arquivos Word, este guia mostra exatamente como fazer. Você verá um exemplo completo e executável que **cria um controle de conteúdo**, grava texto na tag e **modifica o documento Word** de ponta a ponta.

Os desenvolvedores costumam perguntar, *“como adicionar sdt* a um .docx existente e então *escrever texto na tag*?” – a resposta está em usar a API Aspose.Words for .NET. Ao final deste tutorial você será capaz de abrir um arquivo Word, inserir um SDT de texto simples, definir seu nome de tag, preenchê-lo com conteúdo e salvar as alterações sem deixar recursos pendentes.

## Pré-requisitos

* .NET 6.0 ou posterior instalado.
* Uma licença válida do Aspose.Words for .NET (ou você pode trabalhar com a versão de avaliação).
* Visual Studio 2022 (ou qualquer IDE que suporte C#).
* Um documento Word de entrada (`input.docx`) colocado em uma pasta que você possa referenciar no código.

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo projeto Console App e adicione o pacote NuGet Aspose.Words:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Em seguida, adicione as diretivas `using` necessárias no início do `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Esses namespaces dão acesso a `Document`, `DocumentBuilder` e à classe `StructuredDocumentTag`, que são essenciais para **modificar um documento Word**.

## Etapa 2: Carregar o documento Word existente

A primeira operação é carregar o arquivo que você deseja editar. Esta etapa é necessária para todo cenário em que você **modifica o conteúdo de um documento Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Por que carregamos o documento primeiro** – O objeto `Document` representa todo o pacote .docx na memória. Só depois de carregá-lo você pode inserir com segurança novos nós, como um SDT.

## Etapa 3: Inserir um StructuredDocumentTag (SDT) e definir seu nome de tag

Agora respondemos à questão principal: **como adicionar sdt** e **definir o nome da tag**. Usamos `DocumentBuilder.InsertStructuredDocumentTag` com `SdtType.PlainText`. O segundo argumento é o nome da tag, que você pode referenciar posteriormente programaticamente ou via a interface do Word.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Explicação** – `InsertStructuredDocumentTag` retorna uma instância de `StructuredDocumentTag`. Ao passar `"MyTag"` nós **definimos o nome da tag** diretamente no momento da criação. Se precisar alterá-lo depois, você pode atribuir um novo valor a `sdt.Tag`.

## Etapa 4: Gravar texto na tag recém‑criada

Depois que o SDT existe, normalmente você quer **escrever texto na tag** para que os usuários finais vejam um conteúdo de placeholder ou padrão. O método `SetText` faz exatamente isso.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Por que usar SetText** – Atribuir diretamente à propriedade `Text` substituiria toda a hierarquia de nós. `SetText` atualiza com segurança o texto interno do controle de conteúdo enquanto preserva sua estrutura.

## Etapa 5: Salvar o documento modificado

Finalmente, persista as alterações em um novo arquivo. Isso completa o fluxo de trabalho de **modificar documento Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Quando você abrir `output.docx` no Microsoft Word, verá um controle de conteúdo de texto simples rotulado **MyTag** contendo o texto “Sample content”. O controle pode ser editado manualmente, e o nome da tag permanece acessível via as ferramentas de desenvolvedor do Word.

## Código-fonte completo

Abaixo está o programa completo e autocontido. Copie-o para `Program.cs` e execute; nenhum trecho adicional é necessário.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Saída esperada no console

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Como o arquivo Word resultante se parece

![Documento Word mostrando um controle de conteúdo chamado MyTag com o texto “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Exemplo de definição de nome de tag em um documento Word"}

*A captura de tela ilustra o SDT com o **nome da tag** definido como *MyTag* e o texto incorporado visível.*

## Variações comuns e casos de borda

| Situação | Como lidar |
|-----------|------------------|
| **Criar um SDT de rich‑text** | Use `SdtType.RichText` em vez de `PlainText`. |
| **Definir um nome de tag diferente após a inserção** | `sdt.Tag = "NewTag";` – você pode reatribuir o nome da tag a qualquer momento. |
| **Adicionar o SDT dentro de um parágrafo específico** | Mova o cursor do builder (`builder.MoveToParagraph(index)`) antes de chamar `InsertStructuredDocumentTag`. |
| **Múltiplos SDTs no mesmo documento** | Repita as etapas 3‑4 para cada controle; cada um pode ter um nome de tag exclusivo. |
| **Trabalhar com documentos protegidos** | Garanta que o documento esteja desprotegido (`doc.Unprotect()`) antes de inserir um SDT. |

## Dicas profissionais para automação robusta de Word

* **Licencie cedo** – Chame `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` no início do `Main` para evitar marcas d'água de avaliação.
* **Descartar objetos** – Envolva `Document` em um bloco `using` se você estiver direcionando o .NET Framework para garantir que os manipuladores de arquivos sejam liberados.
* **Validar a existência da tag** – Ao ler um documento posteriormente, use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` para localizar tags pela propriedade `Tag`.
* **Desempenho** – Para documentos grandes, carregue apenas as seções necessárias usando `LoadOptions` com `LoadFormat.Docx` e `LoadFormat.Auto`.  

## Conclusão

Agora você sabe como **definir o nome da tag**, **criar um controle de conteúdo**, **escrever texto na tag** e **modificar um documento Word** usando C#. O exemplo completo demonstra o padrão padrão para **como adicionar sdt** e persistir alterações com segurança.  

A partir daqui

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Adicionar conteúdo usando Document Builder no Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Documento Word – Como remover conteúdo](/words/english/net/remove-content/)
- [Criar documento Word com Aspose.Words – Guia passo a passo](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}