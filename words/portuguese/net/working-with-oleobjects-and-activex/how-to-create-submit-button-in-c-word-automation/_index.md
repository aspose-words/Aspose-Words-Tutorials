---
category: general
date: 2026-08-23
description: Criar botão de envio em automação Word com C#. Aprenda a adicionar um
  botão ActiveX, definir o nome do botão, a legenda e o texto programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: pt
lastmod: 2026-08-23
og_description: Criar botão de envio em automação do Word com C#. Este guia mostra
  como adicionar um botão ActiveX, definir seu nome, legenda e texto usando o Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Criar botão de envio na automação do Word com C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Como criar um botão de envio na automação do Word em C#
url: /pt/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um botão de envio em automação Word com C#

Se você precisa **criar um botão de envio** dentro de um documento Word usando C#, este guia o conduzirá por todo o processo. Você verá como adicionar um botão ActiveX, atribuir um nome programático e definir a legenda do botão para que ele pareça um controle *Submit* comum.

Automatizar controles de formulário no Word pode substituir o trabalho manual de layout e garantir consistência em centenas de documentos. Nas etapas abaixo você também aprenderá a **definir o texto do botão**, **definir o nome do botão** e **definir a legenda do botão** — tudo essencial quando o botão participa de um fluxo de trabalho baseado em macros.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 (ou superior) instalado.  
* Uma referência ao **Aspose.Words for .NET** (a biblioteca que fornece `DocumentBuilder.InsertForms2OleControl`).  
* Familiaridade básica com C# e os controles de formulário ActiveX do Word.

Você pode instalar o Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

> **Dica:** Use a versão estável mais recente do Aspose.Words para se beneficiar de correções de bugs e novos recursos relacionados a controles ActiveX.

## Visão geral da solução

O tutorial está organizado em três etapas claras:

1. **Adicionar botão ActiveX** – use o método `InsertForms2OleControl` para inserir um botão de comando no documento.  
2. **Definir o nome do botão** – atribua um identificador programático exclusivo com a propriedade `Name`.  
3. **Definir a legenda do botão** – especifique o texto visível no botão via a propriedade `Caption` (que também controla o **definir texto do botão** que você vê na interface).

Ao final do guia, você terá uma rotina totalmente funcional de **criar botão de envio** que pode ser reutilizada em qualquer projeto de automação Word.

## Etapa 1: Adicionar um botão ActiveX ao documento

A primeira tarefa é **adicionar um botão activex** ao arquivo Word. O Aspose.Words expõe o enum `Forms2OleControlType.CommandButton` para esse propósito.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Por que esta etapa é importante:**  
Os controles ActiveX são os únicos elementos de formulário do Word que podem executar macros VBA ou interagir com código externo. Adicionar o controle cria um espaço reservado que as etapas posteriores podem configurar.

> **Caso especial:** Se o documento já contiver um controle com o mesmo nome, o Word renomeará automaticamente o novo (por exemplo, `CommandButton1`). Definir explicitamente o nome na próxima etapa evita essas colisões.

## Etapa 2: Definir o nome do botão

Um **definir nome do botão** confiável é crucial quando você precisa referenciar o controle a partir do VBA ou de outras partes do seu código C#. A propriedade `Name` fornece ao botão um identificador programático.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Por que você deve definir um nome:**  
Quando o documento for aberto, o VBA pode recuperar o botão via `ActiveDocument.InlineShapes("btnSubmit")`. Um nome significativo como `btnSubmit` também esclarece a intenção ao inspecionar o XML do documento.

> **Dica:** Mantenha os nomes curtos, alfanuméricos e iniciando com uma letra para permanecer compatível com as regras de nomenclatura do VBA.

## Etapa 3: Definir a legenda do botão (texto visível)

O texto que os usuários veem no botão é controlado pela propriedade **definir legenda do botão**. Na interface do Word isso aparece como o rótulo do botão, que também é o **definir texto do botão** que você deseja exibir.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Por que a legenda importa:**  
A legenda é o rótulo voltado ao usuário. Alterá‑la posteriormente não afeta o nome do botão, permitindo que você localize a interface sem quebrar nenhum código que dependa de `btnSubmit`.

> **Pergunta comum:** *Posso definir tanto Caption quanto Value?*  
> Para um `CommandButton`, `Caption` controla o rótulo, enquanto `Value` não é usado. Se precisar de um valor oculto, armazene‑o em uma propriedade personalizada do documento.

## Exemplo completo em funcionamento

Unindo as três etapas, você obtém uma rotina completa que pode ser inserida em qualquer aplicativo console ou Windows:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Saída esperada

Ao executar o programa, ele cria `SubmitButton.docx`. Quando você abrir o arquivo no Microsoft Word:

* Aparece um botão **Submit** na localização especificada.  
* O nome do botão é `btnSubmit` (verifique via *Developer → Design Mode → Properties*).  
* Clicar no botão no modo de design exibe a legenda *Submit*.

Agora você tem um bloco reutilizável para qualquer solução Word orientada a formulários.

## Considerações adicionais

### Tratamento de colisões de nomes

Se você executar a rotina várias vezes no mesmo documento, o Word pode renomear automaticamente controles duplicados. Para garantir unicidade, você pode prefixar um GUID:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Localizando a legenda do botão

Para documentos multilíngues, armazene as legendas em um arquivo de recursos e atribua‑as em tempo de execução:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Respondendo ao clique do botão

O próprio botão não contém lógica de clique em C#. Normalmente você anexa uma macro VBA:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Como você definiu **definir nome do botão** como `btnSubmit`, o nome da macro segue automaticamente a convenção `<Nome>_Click`.

## FAQ de solução de problemas

| Pergunta | Resposta |
|----------|----------|
| **Por que o botão aparece em branco?** | Certifique‑se de definir a propriedade `Caption`; sem ela o botão não exibe texto. |
| **Posso usar um controle ActiveX diferente?** | Sim. Substitua `Forms2OleControlType.CommandButton` por `CheckBox`, `OptionButton`, etc., porém as propriedades variam. |
| **Isso é compatível com .NET Core?** | O Aspose.Words for .NET suporta .NET 6+, portanto o mesmo código funciona em .NET Core e .NET Framework. |
| **E se o documento já possuir um botão?** | Use um `Name` exclusivo (por exemplo, adicionando um GUID) para evitar conflitos. |

## Conclusão

Agora você sabe como **criar um botão de envio** programaticamente em um documento Word usando C#. Seguindo as três etapas — **adicionar botão activex**, **definir nome do botão** e **definir legenda do botão** — você pode definir de forma confiável **texto do botão**, **nome do botão** e **legenda do botão** para qualquer solução de formulário automatizada.

A partir daqui, você pode explorar:

* Adicionar macros VBA que respondam ao clique do **botão de envio**.  
* Estilizar o botão com fontes ou cores personalizadas via o XML subjacente.  
* Gerar múltiplos botões em um loop para formulários dinâmicos.

Sinta‑se à vontade para experimentar diferentes legendas, nomes e posições para adequar ao seu fluxo de trabalho específico. Boa automação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}