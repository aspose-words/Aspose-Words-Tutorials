---
category: general
date: 2026-08-07
description: Aprenda como adicionar um controle ActiveX em um documento Word usando
  C#. Inclui associar macro a um botão e adicionar exemplos de botões clicáveis no
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: pt
lastmod: 2026-08-07
og_description: como adicionar controle ActiveX em um documento Word usando Aspose.Words.
  Siga este guia para inserir um botão, associar macro ao botão e adicionar palavra
  de botão clicável.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: como adicionar controle ActiveX no Word – tutorial completo em C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: como adicionar controle ActiveX no Word com Aspose.Words – guia passo a passo
url: /pt/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# como adicionar controle activex no Word com Aspose.Words

Se você precisa **como adicionar controle activex** em um arquivo Microsoft Word programaticamente, este tutorial mostra os passos exatos usando Aspose.Words para .NET. Você verá como inserir um botão de comando, definir sua legenda e **associar macro ao botão** para que o controle reaja quando o usuário clicar nele. Ao final, você terá um arquivo `.docm` habilitado para macro que contém um botão totalmente funcional.

Adicionar um botão ActiveX é uma necessidade comum ao criar modelos interativos, como solicitações de empréstimo, formulários de integração de funcionários ou relatórios automatizados. Este guia percorre cada linha de código, explica **por que** cada passo importa e cobre as armadilhas típicas que você pode encontrar.

## Pré-requisitos

* .NET 6 (ou .NET Core 3.1 / .NET Framework 4.8) instalado.
* Uma licença válida do Aspose.Words for .NET ou uma chave de avaliação temporária.
* Visual Studio 2022 (ou qualquer IDE que suporte C#).
* Familiaridade básica com macros do Word (VBA) se você planeja escrever a macro que o botão acionará.

> **Dica profissional:** Ao executar o exemplo, salve a saída em uma pasta na qual você tenha permissão de gravação, caso contrário `doc.Save` lançará uma exceção.

## Como adicionar controle ActiveX em um documento Word usando Aspose.Words

O núcleo da solução é um pequeno programa C# que cria um novo documento, insere um controle ActiveX **CommandButton**, e salva o arquivo como um documento habilitado para macro (`.docm`). O código está completo e pronto para copiar‑colar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Por que cada linha importa

| Line | Purpose |
|------|---------|
| `Document doc = new Document();` | Instancia um novo pacote Word na memória. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Fornece uma API fluente para inserir conteúdo, incluindo controles ActiveX. |
| `InsertForms2OleControl` | O único método Aspose.Words que cria um controle ActiveX; você especifica o tipo de controle (`CommandButton`) e sua geometria. |
| `commandButton.Caption = "Click Me";` | Define a **palavra do botão clicável** que o usuário final vê. Sem legenda o botão aparece em branco. |
| `commandButton.OnAction = "MyMacro";` | **associar macro ao botão** – informa ao Word qual macro VBA executar quando o controle for clicado. |
| `doc.Save("CommandButton.docm");` | Persiste o documento como um arquivo habilitado para macro; um `.docx` comum removeria o controle e a macro. |

> **Nota:** As coordenadas (esquerda, superior) são medidas em pontos (1 pt ≈ 1/72 in). Ajuste-as para posicionar o botão onde você precisar na página.

## Como associar macro ao botão

A propriedade `OnAction` vincula o botão a uma macro VBA chamada `MyMacro`. Você ainda precisa criar essa macro dentro do arquivo Word, seja manualmente ou injetando código VBA programaticamente (Aspose.Words não grava código VBA). Aqui está uma macro mínima que você pode adicionar usando o editor **Developer → Visual Basic** do Word:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Quando o usuário abre `CommandButton.docm` e clica no botão, o Word executa `MyMacro` e exibe uma caixa de mensagem. Se a segurança de macro estiver definida como **Disable all macros without notification**, o botão aparecerá desabilitado. Oriente os usuários a habilitar macros para o documento ou assinar a macro com um certificado confiável.

### Armadilhas comuns ao associar uma macro

* **Configurações de segurança de macro** – Se o documento for aberto em uma máquina com políticas de segurança rígidas, a macro pode ser bloqueada. Forneça instruções para reduzir o nível de segurança ou assinar a macro.
* **Conflitos de nomes** – O nome da macro deve ser único dentro do projeto VBA do documento; caso contrário, o Word exibirá erros de “duplicate procedure name”.
* **Word 64‑bit vs 32‑bit** – Os controles ActiveX funcionam da mesma forma, mas o editor VBA pode exibir mensagens de aviso diferentes dependendo da versão do Office.

## Como adicionar palavra de botão clicável a um formulário Word

A propriedade `Caption` é o que os usuários veem no botão. Você pode personalizá‑la ainda mais:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Se você precisar que a legenda mude dinamicamente com base na entrada do usuário, pode acessar o controle posteriormente via modelo de objeto do Word:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Caso extremo: Legendas longas

O Word trunca legendas que excedem a largura do botão. Para evitar o corte, aumente o argumento de largura em `InsertForms2OleControl` ou encurte o texto. Testar com diferentes idiomas (por exemplo, alemão ou japonês) é recomendável porque a largura dos caracteres varia.

## Como adicionar palavra de botão de comando para automação de formulário

Além da legenda visual, o conceito de **palavra de botão de comando** cobre o nome programático do controle. Aspose.Words não expõe uma propriedade direta `Name` para controles ActiveX, mas você pode definir o campo `AltText`, que o Word trata como identificador do controle:

```csharp
commandButton.AltText = "SubmitButton";
```

Posteriormente, no VBA, você pode referenciar o botão pelo seu valor `AltText`:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Essa técnica é útil quando você tem vários botões e precisa diferenciá‑los programaticamente.

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode compilar e executar como uma aplicação console. Ele inclui estilização opcional, associação de macro e um bloco de comentários descrevendo cada passo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Resultado esperado:** Ao abrir `SubmitForm.docm` no Microsoft Word, é exibido um botão com borda azul rotulado *Submit Form*. Clicar no botão aciona a macro VBA `SubmitMacro` (desde que você tenha adicionado a macro ao documento). O botão pode ser movido, redimensionado ou estilizado ainda mais usando o mesmo objeto `Forms2OleControl`.

## Testando a solução

1. Compile e execute o aplicativo console C#.
2. Abra o `SubmitForm.docm` gerado no Word.
3. Se solicitado, habilite macros.
4. Clique no botão *Submit Form* – você deverá ver a caixa de mensagem definida em `SubmitMacro`.

Se o botão aparecer mas não fizer nada, verifique novamente se o nome da macro corresponde exatamente (`SubmitMacro`) e se a segurança de macro não está bloqueando a execução.

## Perguntas frequentes

| Question | Answer |
|----------|--------|
| *Posso adicionar mais de um botão ActiveX?* | Sim. Chame `InsertForms2OleControl` várias vezes com coordenadas diferentes. Use valores distintos de `OnAction` e `AltText` para diferenciá‑los. |
| *O controle ActiveX é visível no Word Online?* | Não. |

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Add a New Section to Word Document | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}