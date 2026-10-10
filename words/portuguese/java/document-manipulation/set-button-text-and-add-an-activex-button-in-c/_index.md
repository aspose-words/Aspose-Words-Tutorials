---
category: general
date: 2026-10-10
description: Defina o texto do botão e adicione um botão ActiveX em C# usando Aspose.Words.
  Aprenda a inserir o botão, criar o controle do botão e personalizar a legenda em
  um documento Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: pt
lastmod: 2026-10-10
og_description: Defina o texto do botão e adicione um botão ActiveX em C# com Aspose.Words.
  Siga este guia passo a passo para inserir um botão, criar o controle do botão e
  personalizar sua legenda.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Defina o texto do botão e adicione um botão ActiveX em C# – guia completo
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Definir o texto do botão e adicionar um botão ActiveX em C#
url: /pt/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir texto do botão e adicionar um botão ActiveX em C#

Se você precisa **set button text** em um botão ActiveX dentro de um documento Word, este guia mostra exatamente como fazer. Ao final do tutorial você será capaz de **insert button**, criar um **button control** e personalizar sua legenda com apenas algumas linhas de código C#.

Trabalhar com controles ActiveX é comum quando você deseja formulários interativos no Word — seja ao criar um modelo de contrato, uma pesquisa ou uma ferramenta interna. O exemplo usa Aspose.Words for .NET, uma biblioteca que permite manipular arquivos Word sem precisar do Microsoft Office instalado.

## Prerequisites

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou versão posterior instalada  
* Visual Studio 2022 (ou qualquer IDE que suporte C#)  
* Uma licença do Aspose.Words for .NET (a avaliação gratuita funciona para aprendizado)  

Você também precisa de uma referência ao pacote NuGet `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## How to insert button into a Word document

O primeiro passo é criar um novo `Document` e um `DocumentBuilder`. O builder é o ponto de entrada para adicionar conteúdo, incluindo controles ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `Document` representa o arquivo .docx completo, enquanto `DocumentBuilder` fornece métodos de alto nível como `InsertParagraph` e `InsertFormField`. Começar com um documento limpo garante que o botão apareça exatamente onde você deseja.

## Create button control with Forms2OleControl

Agora criamos o controle de botão propriamente dito. `Forms2OleControl` é a classe que o Aspose.Words usa para todos os objetos ActiveX, e o tipo `COMMANDBUTTON` é renderizado como um botão clicável no Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Explanation:**  
* `InsertForms2OleControl` coloca o controle nas coordenadas exatas que você fornece.  
* O tamanho é definido em pontos (1 point = 1/72 polegada). Ajuste esses números para se adequar ao seu layout.

## Add ActiveX control and give it a unique name

Todo objeto ActiveX deve ter um nome distinto para que você possa referenciá‑lo posteriormente (por exemplo, ao manipular eventos em VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tip:** Evite espaços ou caracteres especiais no nome; o Word trata o nome como um identificador em seu modelo interno de formulários.

## Set button text (caption) on the ActiveX button

É aqui que a palavra‑chave principal **set button text** entra em ação. A propriedade `Caption` define o rótulo que os usuários veem no botão.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Você pode alterar a legenda a qualquer momento antes de salvar o documento. Se precisar localizar a interface posteriormente, basta chamar `SetCaption` novamente com uma string diferente.

## Save the document and verify the result

Por fim, grave o documento no disco. Abrir o arquivo no Microsoft Word mostrará o botão com a legenda personalizada.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Expected output:** Quando você abrir *ActiveXButton.docx* no Word, verá um botão posicionado nas coordenadas especificadas, rotulado **Click Me**. Clicar no botão disparará o comportamento padrão de um botão de comando do Word (que pode ser customizado depois com VBA).

![Set button text example](https://example.com/activex-button.png){alt="Exemplo de definir texto do botão"}

## Add ActiveX button and handle events (optional)

Se você precisar que o botão execute uma ação personalizada, pode adicionar uma macro VBA que reage ao evento `Click`. A macro pode ser injetada programaticamente, mas isso está fora do escopo deste tutorial. A parte importante é que o botão já está presente e sua legenda está definida — pronto para qualquer tratamento de evento que você escolher.

## Common pitfalls and how to avoid them

| Problema | Por que acontece | Correção |
|----------|------------------|----------|
| Botão aparece desalinhado | As coordenadas estão em pontos, não em pixels | Converta valores de pixel para pontos (`points = pixels * 72 / DPI`) |
| A legenda não muda após salvar | `SetCaption` chamado depois de `Save` | Sempre defina a legenda **antes** de chamar `doc.Save` |
| Controle não visível em versões antigas do Word | Algumas versões antigas do Word não suportam totalmente ActiveX | Teste na versão alvo do Word; considere usar um `CheckBox` ou `DropDownList` como alternativa |
| Aviso de licença na saída | Licença de avaliação expira | Aplique uma licença válida do Aspose.Words via `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Full, runnable example

Abaixo está o programa completo que você pode copiar, colar e executar. Ele inclui todas as diretivas `using` necessárias e demonstra todo o fluxo de trabalho, da criação do documento à gravação.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Execute o programa com `dotnet run`. Após a execução, abra *ActiveXButton.docx* para confirmar que a legenda do botão está **Click Me**.

## Recap of what you learned

* Você aprendeu como **set button text** em um botão ActiveX usando Aspose.Words.  
* Viu os passos exatos para **how to insert button**, **create button control** e **add activex control** a um documento Word.  
* Agora possui um trecho de código reutilizável que pode ser adaptado para qualquer projeto de automação Word baseado em formulários.

## Next steps

* Explore outros valores de `Forms2OleControlType` como `CHECKBOX` ou `LISTBOX` para criar formulários mais ricos.  
* Combine o botão com uma macro VBA para realizar cálculos ou validações de dados.  
* Use a API `FormField` do Aspose.Words para ler a entrada do usuário depois que o documento for preenchido.

Sinta‑se à vontade para experimentar tamanho, posição e legenda para atender aos requisitos de design. Se encontrar algum problema, a documentação do Aspose.Words oferece referências detalhadas para cada classe usada neste tutorial.

Happy coding!

## What Should You Learn Next?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}