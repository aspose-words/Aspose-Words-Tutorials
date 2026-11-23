---
category: general
date: 2026-11-22
description: Aprenda a inserir um controle Forms2Ole no Word com C#. Este guia passo
  a passo aborda o DocumentBuilder, a colocação de botões de comando e a gravação
  do .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: pt
lastmod: 2026-11-22
og_description: Insira o controle Forms2Ole no Word com C#. Siga este guia para adicionar
  um botão de comando usando Aspose.Words e DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Inserir o controle Forms2Ole no Word com C# – guia completo
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Como inserir o controle Forms2Ole no Word usando C# e Aspose.Words
url: /pt/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como inserir o controle Forms2Ole no Word usando C# e Aspose.Words

Se você precisa **inserir o controle Forms2Ole no Word**, este tutorial mostra exatamente como fazer isso com C#. Seja construindo um modelo preenchível ou automatizando a criação de formulários, a solução abaixo permite que você adicione um botão de comando programaticamente.

Você aprenderá como criar um documento em branco, usar `DocumentBuilder` para posicionar o controle e salvar o resultado como um `.docx`. O guia também aborda armadilhas comuns, como sistemas de coordenadas e compatibilidade com versões mais antigas do Word.

## Pré-requisitos

Antes de começar, certifique-se de que você tem:

* .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
* Aspose.Words for .NET (pacote NuGet `Aspose.Words`)
* Um entendimento básico de C# e do modelo de objeto do Word
* Uma IDE como Visual Studio ou VS Code

## Passo 1: Configurar o projeto e importar namespaces

Crie um novo aplicativo console e adicione o pacote Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

No `Program.cs` importe os namespaces necessários:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Dica profissional:** Use a versão mais recente do Aspose.Words para obter suporte total à API `Forms2OleControl`.

## Passo 2: Criar um documento em branco e inicializar DocumentBuilder

A classe `Document` representa o arquivo Word, enquanto `DocumentBuilder` fornece métodos para inserir conteúdo.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funciona como um cursor; após esta linha você pode começar a posicionar elementos em qualquer lugar do documento.

## Passo 3: Definir a posição e o tamanho do botão

O Word mede coordenadas em pontos (1 pt ≈ 1/72 in). A estrutura `Rectangle` de `System.Drawing` descreve os limites do controle.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` posiciona o controle no canto superior esquerdo da página atual.
* Ajuste `x` e `y` para mover o botão para outro local (por exemplo, `new Rectangle(150, 200, 100, 30)`).

## Passo 4: Inserir o botão de comando Forms2Ole

Agora use `InsertForms2OleControl` para adicionar o controle. O método requer o tipo de controle, um nome e os limites definidos acima.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

O objeto `Forms2OleControl` retornado permite que você modifique propriedades como `Enabled`, `Visible` ou até mesmo associe um nome de macro posteriormente.

### Por que usar Forms2Ole?

* **Compatibilidade legada** – Os controles Forms2Ole funcionam no Word 97‑2003 (`.doc`) e em arquivos `.docx` mais recentes.
* **Suporte a macros** – Eles podem acionar macros VBA, tornando‑os ideais para modelos interativos.
* **Posicionamento preciso** – Ao contrário dos controles de conteúdo, você controla coordenadas exatas.

## Passo 5: Salvar o documento

Finalmente, grave o arquivo no disco. Escolha uma pasta na qual você tenha permissão de escrita.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Abra `output.docx` no Microsoft Word. Você verá um botão rotulado **ClickMe** no canto superior esquerdo da primeira página. Clicá‑lo no Word não fará nada até que você atribua uma macro, mas o controle está totalmente funcional.

## Tratando casos de borda comuns

| Situação | Como resolver |
|-----------|-------------------|
| **Botão aparece fora da página** | Verifique se as coordenadas do `Rectangle` estão dentro das margens da página. Use `builder.PageSetup.PageWidth` e `PageHeight` para calcular limites seguros. |
| **Controle não visível em versões antigas do Word** | Salve o documento como `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) para garantir compatibilidade do Forms2Ole com Word 97‑2003. |
| **Precisa mudar a legenda** | Após a inserção, defina `commandButton.Caption = "Submit";`. |
| **Atribuir uma macro** | Defina `commandButton.MacroName = "MyMacro"`; a macro deve existir no projeto VBA do documento. |
| **Múltiplos botões** | Repita o Passo 4 com diferentes valores de `Rectangle` e nomes únicos. |

## Exemplo completo e executável

Juntando tudo, aqui está um programa autocontido que você pode copiar, colar e executar:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Saída esperada:** Após executar o programa, `output.docx` abre no Word com um botão clicável rotulado *Click Me!* posicionado no canto superior esquerdo da primeira página.

## Conclusão

Agora você sabe como **inserir o controle Forms2Ole no Word** usando C# e Aspose.Words. O processo envolve criar um `Document`, posicionar um `Rectangle` e chamar `InsertForms2OleControl` via `DocumentBuilder`. Com o exemplo completo de código e orientações sobre casos de borda, você pode integrar botões de comando em qualquer fluxo de trabalho automatizado do Word.

### Próximos passos

* Explore outros valores de `ControlType` como `CheckBox` ou `OptionButton`.
* Combine controles Forms2Ole com macros VBA para formulários interativos.
* Use `DocumentBuilder.MoveTo` para posicionar botões em parágrafos ou tabelas específicos.
* Revise a documentação **Forms2Ole** da Aspose.Words para configurações avançadas de propriedades.

Feliz codificação e aproveite a criação de documentos Word mais ricos com C# e Aspose.Words!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Como inserir botão de comando OLE em um documento Word usando C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [como adicionar controle ActiveX no Word com Aspose.Words – guia passo a passo](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Adicionar botão de comando ao documento Word com Aspose.Words – Guia completo](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}