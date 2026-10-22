---
category: general
date: 2026-10-07
description: Aprenda como inserir um botão de comando OLE em um documento Word com
  Aspose.Words C#. Guia passo a passo cobrindo DocumentBuilder, propriedades e como
  salvar o arquivo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: pt
lastmod: 2026-10-07
og_description: Inserir botão de comando OLE em um documento Word usando C#. Siga
  este tutorial conciso para adicionar, configurar e salvar um CommandButton funcional
  com Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Inserir botão de comando OLE no Word com C# – guia completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Como inserir um botão de comando OLE em um documento Word usando C#
url: /pt/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como inserir um botão de comando OLE em um documento Word usando C#

Se você precisa **inserir um botão de comando OLE** em um arquivo Word programaticamente, este guia mostra exatamente como fazer isso com Aspose.Words para .NET. Seja criando um relatório preenchido por formulário ou automatizando um modelo que requer interação do usuário, as etapas abaixo fornecem uma solução completa e executável.

Você aprenderá como criar um documento em branco, usar o `DocumentBuilder` para colocar um `Forms2OleControl`, definir a legenda e o nome do botão e, finalmente, salvar o `.docx`. Nenhuma ferramenta externa é necessária além da biblioteca Aspose.Words.

## Pré-requisitos

* .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+)
* Uma licença válida do Aspose.Words para .NET ou uma chave de avaliação gratuita
* Visual Studio 2022 (ou qualquer IDE C# que você prefira)
* Familiaridade básica com a sintaxe C# e conceitos OLE do Word

> **Dica:** Se você estiver usando a avaliação gratuita, o documento gerado conterá uma pequena marca d'água. Uma versão licenciada a remove automaticamente.

## Etapa 1: Instalar o Aspose.Words

Adicione o pacote Aspose.Words ao seu projeto via NuGet:

```bash
dotnet add package Aspose.Words
```

O pacote inclui os namespaces `Aspose.Words.Drawing` e `Aspose.Words.Drawing.Ole` necessários para controles OLE.

## Etapa 2: Inserir botão de comando OLE com DocumentBuilder

O núcleo do tutorial é o método `InsertForms2OleControl`. Ele cria um **Forms2 OLE CommandButton** em uma localização e tamanho específicos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Por que isso funciona

* `DocumentBuilder` é a API principal para criar documentos Word programaticamente.  
* `InsertForms2OleControl` instrui o Aspose.Words a incorporar um **controle Forms2 OLE**, que é a tecnologia de formulário legada do Word que suporta botões de comando, caixas de seleção, etc.  
* O valor enum `OleControlType.CommandButton` especifica que o controle inserido é um **botão de comando** — o tipo exato que você solicitou ao querer **inserir um botão de comando OLE**.  
* O `Rectangle` determina a posição visual. Ajuste as coordenadas X/Y ou a largura/altura para corresponder ao seu layout.

## Etapa 3: Salvar o documento

Depois de configurar o botão, grave o documento no disco. Você pode escolher qualquer formato suportado pelo Aspose.Words (`.docx`, `.pdf`, `.odt`, …). Para este tutorial, salvaremos como um documento Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ao abrir `CommandButton.docx` no Microsoft Word, você verá um botão clicável rotulado **Click Me**. Ao pressioná‑lo no Word, ele aciona a caixa de diálogo padrão “Run Macro” porque o botão é um controle de formulário OLE; você pode posteriormente anexar uma macro ou código VBA, se necessário.

## Etapa 4: Verificar o resultado (saída esperada)

Abra o arquivo gerado:

1. O botão aparece nas coordenadas especificadas (aproximadamente 1,4 pol do lado esquerdo e superior da página).  
2. A legenda exibe **Click Me**.  
3. A propriedade Name (`cmdSubmit`) está visível no painel **Developer → Properties** do Word, o que é útil quando você precisa referenciar o controle a partir do VBA.

![Exemplo de inserção de botão de comando OLE em documento Word](insert-ole-button.png)

*Texto alternativo da imagem*: **Exemplo de inserção de botão de comando OLE em documento Word** (inclui a palavra‑chave principal para acessibilidade e SEO).

## Casos Limites & Perguntas Frequentes

### 1. E se o botão não aparecer onde eu espero?

* O Word usa pontos, não pixels. Converta pixels da tela para pontos (`points = pixels * 72 / DPI`).  
* Certifique‑se de que o retângulo não intersecte as margens da página; caso contrário, o Word pode deslocar o controle.

### 2. Posso inserir o botão em um documento existente?

Sim. Carregue o documento com `new Document("Existing.docx")` e use o mesmo fluxo de trabalho do `DocumentBuilder`. Apenas lembre‑se de mover o cursor do builder (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.) antes de chamar `InsertForms2OleControl`.

### 3. Como anexo uma macro ao botão?

O Aspose.Words não cria código VBA, mas você pode incorporar uma macro após o documento ser gerado:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Isso funciona com .NET Core no Linux?

O controle OLE é um recurso específico do Windows porque depende do COM. No Linux, o botão será inserido, mas aparecerá como uma imagem estática sem comportamento interativo. Para formulários interativos multiplataforma, considere usar controles de conteúdo (`StructuredDocumentTag`) em vez disso.

### 5. E se eu precisar de um tamanho diferente ou de vários botões?

Crie objetos `Rectangle` adicionais com coordenadas únicas e repita a chamada `InsertForms2OleControl`. Cada botão pode ter seu próprio `Caption` e `Name`.

## Exemplo Completo Funcional

Abaixo está o programa completo que você pode copiar‑colar em uma aplicação console. Ele inclui todas as diretivas `using` necessárias, tratamento de erros e comentários.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Execute o programa, abra o `CommandButton.docx` gerado e você verá o botão **Click Me** pronto para personalizações adicionais.

## Conclusão

Agora você sabe como **inserir um botão de comando OLE** em um documento Word usando C# e Aspose.Words. O tutorial abordou:

* Instalar o pacote Aspose.Words  
* Usar `DocumentBuilder.InsertForms2OleControl` com `OleControlType.CommandButton`  
* Definir propriedades do botão (`Caption`, `Name`)  
* Salvar e verificar a saída  

A partir daqui, você pode explorar tópicos relacionados, como **Aspose.Words OLE control** para caixas de seleção, caixas de combinação ou incorporação de planilhas Excel completas. Também pode experimentar a automação de **Word OLE command button** em modelos maiores, ou substituir controles OLE por **content controls** modernos para melhor suporte multiplataforma.

Sinta‑se à vontade para adaptar os valores do retângulo, adicionar vários botões ou anexar macros VBA para atender às necessidades da sua aplicação. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}