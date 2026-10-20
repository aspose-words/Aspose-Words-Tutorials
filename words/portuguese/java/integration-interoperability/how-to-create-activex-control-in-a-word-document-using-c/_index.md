---
category: general
date: 2026-08-20
description: Aprenda a criar um controle ActiveX, definir o tamanho do botão e adicionar
  o botão ao Word com um exemplo completo em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: pt
lastmod: 2026-08-20
og_description: Crie um controle ActiveX em um arquivo Word com C#. Este tutorial
  mostra como definir o tamanho do botão, adicionar o botão ao Word e criar um botão
  clicável.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Crie um controle ActiveX no Word – guia passo a passo em C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Como criar um controle ActiveX em um documento do Word usando C#
url: /pt/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um controle ActiveX em um documento Word usando C#

Se você precisa **criar um controle ActiveX** dentro de um arquivo Microsoft Word, este guia mostra exatamente como fazer isso. Você verá como **adicionar um botão ao Word**, definir as dimensões do botão e tornar o controle clicável — tudo com um pequeno programa C# autônomo.

Neste tutorial você irá:

* Entender por que um controle ActiveX é útil para documentos Word interativos.  
* Aprender o código exato necessário para **definir o tamanho do botão** e atribuir uma legenda.  
* Ver como **criar um botão clicável** que pode ser posteriormente conectado a uma macro ou lógica externa.  

Os passos funcionam com Aspose.Words .NET 23.12 ou posterior e exigem apenas um ambiente de desenvolvimento .NET.

> **Pré‑requisito** – Você tem uma licença válida do Aspose.Words (ou está usando a versão de avaliação) e o Visual Studio 2022 ou qualquer IDE C#.

---

## Como criar um controle ActiveX em um documento Word

O primeiro passo é instanciar um `Document` vazio e um `DocumentBuilder`. O builder fornece a API de alto nível para inserir objetos como controles ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

O método `InsertActiveXButton` (definido a seguir) contém a lógica para **como inserir o botão** e configurá‑lo.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Executar o programa cria **ActiveXButton.docx**. Abrir o arquivo no Word mostra um botão rotulado **Submit**. O controle está totalmente funcional — ao clicar, ele dispara o evento padrão `CommandButton_Click`, que você pode vincular posteriormente a uma macro VBA.

### Por que isso funciona

* `InsertForms2OleControl` indica ao Word que insira um objeto OLE do tipo **CommandButton**, que é a classe clássica de botão ActiveX.  
* Os argumentos de largura e altura **definem o tamanho do botão**; o Word converte os valores de pontos (1 pt ≈ 1/72 pol).  
* Nomear o controle (`Name = "btnSubmit"`) facilita localizá‑lo a partir do VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Definir tamanho e legenda do botão

Se precisar de uma aparência diferente, ajuste os argumentos numéricos na chamada `InsertForms2OleControl`. A assinatura do método é:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – O identificador programático da classe ActiveX (`"CommandButton"` para um botão padrão).  
* **width / height** – Tamanho em pontos. Para um botão de 2 cm de largura, use `width = 56.7` (2 cm ≈ 56.7 pt).  

Você também pode modificar a legenda após a inserção:

```csharp
commandButton.Caption = "Send Request";
```

Alterar a legenda não afeta o tamanho, mas altera o feedback visual para o usuário.

### Dica profissional

Se quiser um botão quadrado, defina ambas as dimensões com o mesmo valor:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Adicionar botão ao Word e torná‑lo clicável

O código acima já **adiciona o botão ao Word**. Para fazer o botão executar uma ação, você deve escrever uma macro VBA que trate o evento `Click`. Aqui está uma macro mínima que você pode colar no editor VBA do Word (`Alt+F11` → Inserir → Módulo):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Como o controle se chama `btnSubmit`, o Word mapeia automaticamente o evento `Click` para `btnSubmit_Click`. Esta é a forma padrão de **criar um botão clicável** sem bibliotecas externas.

> **Observação:** As configurações de segurança de macro no Word podem bloquear controles ActiveX. Certifique‑se de que “Habilitar todas as macros” ou “Habilitar macros VBA” esteja selecionado para o documento, ou assine digitalmente a macro para uso em produção.

---

## Perguntas comuns: como inserir botão e solução de problemas

### 1. E se o botão não aparecer após salvar?

* Verifique se a versão do Aspose.Words suporta `InsertForms2OleControl`. Versões anteriores à 22.5 não possuem esse recurso.  
* Garanta que o formato de arquivo de destino seja `.docx` ou `.doc`. Formatos antigos como `.rtf` não podem armazenar objetos ActiveX.

### 2. Posso inserir o botão em um marcador específico?

Sim. Mova o builder para o marcador antes de chamar `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Como **definir o tamanho do botão** dinamicamente com base no comprimento do texto?

Calcule a largura necessária usando o método `Graphics.MeasureString` (de `System.Drawing`) e converta pixels para pontos (`points = pixels * 72 / DPI`). Em seguida, passe a largura calculada para `InsertForms2OleControl`.

### 4. Existe uma maneira de adicionar vários botões em um loop?

Com certeza. Envolva a lógica de inserção em um `for` loop e ajuste as propriedades `Left` e `Top` para cada iteração:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Saída esperada

Ao executar o programa e abrir **ActiveXButton.docx**:

* Aparece um único botão **Submit** próximo ao canto superior‑esquerdo da primeira página.  
* O tamanho do botão corresponde às dimensões fornecidas (`100 pt × 30 pt`).  
* Se você adicionou a macro VBA, ao clicar no botão aparece uma caixa de mensagem: “You clicked the Submit button!”.

Você criou com sucesso um **controle ActiveX**, **definiu o tamanho do botão** e **adicionou o botão ao Word**, além de aprender **como inserir botão** e **criar um botão clicável** para futuras tarefas de automação.

---

## Conclusão

Neste tutorial você aprendeu a **criar um controle ActiveX** dentro de um documento Word com C#. Seguindo os passos, você pode **definir o tamanho do botão**, dar ao controle um nome significativo e **adicionar o botão ao Word** para que ele se torne um **botão clicável** ligado a uma macro VBA.  

A partir daqui, você pode explorar:

* Vincular o botão a um add‑in COM .NET em vez de VBA.  
* Usar outras classes ActiveX como `CheckBox` ou `ComboBox`.  
* Automatizar a criação de formulários completos com múltiplos controles.

Sinta‑se à vontade para experimentar diferentes tamanhos


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}