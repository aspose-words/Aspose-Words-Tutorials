---
category: general
date: 2026-11-18
description: Crie um documento Word em branco e insira um botão ActiveX com C#. Aprenda
  como adicionar o controle, definir a legenda do botão e salvar o arquivo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: pt
lastmod: 2026-11-18
og_description: Crie um documento Word em branco e insira um botão ActiveX usando
  C#. Siga este tutorial completo para adicionar o controle, definir a legenda do
  botão e salvar o resultado.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Crie um documento Word em branco e insira um botão ActiveX – guia passo
  a passo
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Crie um documento Word em branco e insira um botão ActiveX
url: /pt/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie um documento Word em branco e insira um botão ActiveX

Se você precisa **criar um documento Word em branco** e colocar um botão ActiveX interativo dentro dele, este guia mostra exatamente como fazer isso com Aspose.Words para .NET. Você verá o código completo, entenderá por que cada linha é importante e aprenderá como **definir a legenda do botão** para que o controle pareça pronto para a interação do usuário.

Além do objetivo principal, abordaremos **como inserir ActiveX**, os passos **como adicionar controle** a um arquivo Word e as nuances de **inserir botão ActiveX** com uma legenda personalizada. Ao final, você terá um padrão reutilizável para qualquer cenário de automação de documentos que exija elementos de UI incorporados.

## O que você aprenderá

* Como **criar um documento Word em branco** programaticamente.  
* As chamadas de API exatas necessárias para **inserir botão ActiveX** e configurar suas propriedades.  
* Como **definir a legenda do botão** para que o controle exiba o texto desejado.  
* Dicas para salvar o arquivo em um local de sua escolha e lidar com armadilhas comuns.

### Pré-requisitos

* .NET 6.0 ou superior (o código também funciona com .NET Framework 4.6+).  
* Aspose.Words para .NET instalado (`Install-Package Aspose.Words`).  
* Familiaridade básica com C# e Visual Studio ou qualquer IDE compatível com .NET.

---

## Crie um documento Word em branco com Aspose.Words

O primeiro passo é instanciar um objeto `Document` vazio. Esse objeto representa um arquivo Word que não contém conteúdo até que adicionemos algo.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Por que isso importa*: Um `Document` vazio fornece uma tela limpa. Você pode adicionar posteriormente parágrafos, tabelas ou controles sem se preocupar com formatação existente.

---

## Inicialize um DocumentBuilder para trabalhar com o documento

`DocumentBuilder` é uma classe auxiliar que permite inserir conteúdo na posição atual do cursor. Ela rastreia automaticamente onde você está no documento.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Por que isso importa*: Sem um `DocumentBuilder` você precisaria manipular a árvore de nós de baixo nível manualmente. O builder simplifica a inserção de texto, imagens e controles ActiveX.

---

## Como inserir um botão ActiveX (insert activex button)

Agora usamos `InsertForms2OleControl` para incorporar um controle ActiveX. O método requer três argumentos:

1. O tipo de controle (`OleControlType.CommandButton`).  
2. Um nome interno para o controle (usado por VBA ou código de macro).  
3. Um `RectangleF` que define a posição e o tamanho na página.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Por que isso importa*: Este é o núcleo de **como inserir activex** em um documento Word. As coordenadas do retângulo são expressas em pontos (1 ponto = 1/72 polegada). Ajuste-as para posicionar o botão onde você precisar.

### Dica

Se você precisar que o botão apareça em uma página específica, mova primeiro o cursor do builder:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Como definir a legenda do botão (set button caption)

Depois que o controle é colocado, você pode modificar suas propriedades. A propriedade mais visível é `Caption`, que determina o texto exibido no botão.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Por que isso importa*: Os usuários veem a legenda, não o nome interno. Alterá‑la torna o botão significativo no documento final.

---

## Salve o documento contendo o botão

Finalmente, grave o documento no disco. Você pode escolher qualquer formato suportado (`.docx`, `.pdf`, etc.). Aqui salvamos como um documento Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Por que isso importa*: Persistir o arquivo permite que você o abra no Microsoft Word e teste o botão. Quando o documento for aberto, o botão aparecerá com a legenda “Press”.

### Resultado esperado

Abrir `with_button.docx` no Word mostra uma página em branco com um botão retangular rotulado **Press**. Clicar no botão não faz nada por padrão porque nenhuma macro VBA está anexada, mas o controle está totalmente funcional e pode ser conectado a código posteriormente.

---

## Como adicionar controle a um parágrafo específico (how to add control)

Às vezes você quer o botão dentro de um parágrafo específico, por exemplo após algum texto instrucional. Use `MoveTo` para posicionar o builder antes de inserir o controle.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Por que isso importa*: Este padrão demonstra **como adicionar controle** em contexto, garantindo que o layout do documento permaneça lógico.

---

## Armadilhas comuns e como evitá‑las

| Problema | Por que acontece | Solução |
|----------|------------------|---------|
| Botão aparece fora da página | As coordenadas do retângulo estão fora das margens da página | Use `builder.PageSetup` para obter as dimensões da página e calcular um `RectangleF` seguro. |
| Legenda não é exibida | `Caption` definido antes que o controle esteja totalmente inicializado | Defina `Caption` **depois** da chamada `InsertForms2OleControl`, como mostrado na Etapa 4. |
| Documento salva sem o botão | O cursor do builder foi movido após a inserção sem confirmar as alterações | Mantenha o builder na mesma página ou chame `builder.Document.UpdatePageLayout()` antes de salvar. |

---

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar, colar e executar. Ele cria um arquivo Word em branco, insere um botão ActiveX, define sua legenda e salva o resultado.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Saída**: Após executar o programa, abra `C:\Temp\with_button.docx` no Microsoft Word. Você verá uma única página com o texto “Abaixo está um botão ActiveX criado programaticamente:” seguido por um botão rotulado **Press**.

---

## Conclusão

Agora você sabe como **criar um documento Word em branco**, **inserir um botão ActiveX**, **definir a legenda do botão** e **salvar** o resultado usando Aspose.Words para .NET. O mesmo padrão pode ser estendido a outros controles ActiveX (caixas de seleção, caixas de lista, etc.) alterando `OleControlType`.

Em seguida, você pode explorar **como inserir eventos de botão ActiveX** com VBA, ou **como adicionar controle** a documentos existentes que já contêm conteúdo. Ambos os tópicos se baseiam diretamente nos conceitos abordados aqui.

Feliz codificação, e sinta‑se à vontade para experimentar diferentes tamanhos, posições e legendas para atender aos requisitos de UI da sua aplicação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar documento Word C# com um botão de comando ActiveX](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Como adicionar botão ActiveX em um documento Word com Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}