---
category: general
date: 2026-09-21
description: Aprenda a criar um botão de comando ActiveX em um documento Word com
  Aspose.Words e C#. Guia passo a passo cobre inserção, posicionamento e salvamento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: pt
lastmod: 2026-09-21
og_description: Crie um botão de comando ActiveX em um documento Word usando C# e
  Aspose.Words. Siga este tutorial completo para inserir, posicionar e salvar o botão
  programaticamente.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Crie um botão de comando ActiveX no Word com C# – guia completo
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Como criar um botão de comando ActiveX no Word usando C#
url: /pt/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um botão de comando ActiveX no Word usando C#

Se você precisar **criar um botão de comando ActiveX** dentro de um arquivo Word, este guia mostra as etapas exatas. Usando Aspose.Words para .NET, você pode adicionar, posicionar e configurar o botão totalmente a partir de código C#.

A inserção programática de um botão ActiveX elimina o trabalho manual de UI e permite a geração automatizada de documentos para formulários, relatórios ou modelos interativos. Neste tutorial, você aprenderá a usar **DocumentBuilder**, o método **InsertForms2OleControl** e propriedades relacionadas para obter um botão totalmente funcional.

## O que você precisará

* .NET 6.0 SDK ou posterior (o código também funciona com .NET Framework 4.7+)
* Aspose.Words para .NET (pacote NuGet `Aspose.Words`)
* Uma IDE como Visual Studio 2022 ou VS Code
* Conhecimento básico de C# e conceitos de documentos Word

Nenhuma instalação adicional do Office é necessária porque o Aspose.Words funciona independentemente do Microsoft Word.

## Etapa 1: Configurar o projeto C#

Crie um novo projeto de console e adicione o pacote Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

A biblioteca `Aspose.Words` fornece a classe **DocumentBuilder** que usaremos para manipular o documento.

## Etapa 2: Inicializar o documento e o builder

O primeiro bloco de código cria um documento em branco e uma instância de `DocumentBuilder`. Esse objeto é o ponto de entrada para todas as operações de processamento de Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa:** `DocumentBuilder` mantém a posição atual do cursor, de modo que qualquer inserção subsequente aparecerá exatamente onde você posicionar o cursor.

## Etapa 3: Inserir o botão de comando ActiveX

O método **InsertForms2OleControl** cria um controle ActiveX do tipo solicitado. Aqui solicitamos um `CommandButton` e especificamos seu tamanho em pontos (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Explicação:**  
* `OleControlType.CommandButton` indica ao Aspose.Words que crie um botão em vez de outro tipo de controle.  
* O método retorna um objeto `Forms2OleControl`, que expõe campos de posicionamento e propriedades.

## Etapa 4: Posicionar o botão e definir suas propriedades

Após a inserção, você pode mover o botão para qualquer local da página e atribuir a ele um nome programático e uma legenda visível.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Dica profissional:** O sistema de coordenadas começa no canto superior esquerdo da página. Ajuste `Left` e `Top` para alinhar o botão com outros campos de formulário.

## Etapa 5: Salvar o documento

Finalmente, grave o documento no disco. O arquivo conterá o botão ActiveX, pronto para ser aberto no Microsoft Word, onde o botão se tornará interativo.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Ao abrir `ActiveXCommandButton.docx` no Word, você verá um botão rotulado **Submit** no local especificado. Clicar nele no Word acionará o comportamento padrão do botão de comando (que você pode personalizar posteriormente com VBA ou complementos do Word).

## Exemplo completo e executável

Juntando todas as peças, obtém‑se um programa autônomo que você pode copiar, colar e executar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Saída esperada:** O console imprime *“Document created successfully.”* e a pasta agora contém `ActiveXCommandButton.docx`. Abrindo o arquivo no Microsoft Word, aparece um botão **Submit** clicável posicionado 100 pt da margem esquerda e 150 pt do topo da página.

## Armadilhas comuns e como evitá‑las

| Problema | Por que acontece | Solução |
|----------|------------------|---------|
| O botão aparece fora da página | `Left`/`Top` values exceed page dimensions | Use `doc.FirstSection.PageSetup.PageWidth` e `PageHeight` para calcular coordenadas seguras |
| Botão não está visível no Word | The document was saved in a format that strips ActiveX controls (e.g., `.txt`) | Always save as `.docx` or `.doc` |
| Erro de tempo de execução `ArgumentOutOfRangeException` | Width or height is set to zero or negative | Ensure the size arguments passed to `InsertForms2OleControl` are positive numbers |

## Expandindo a solução

Você pode personalizar ainda mais o botão definindo propriedades adicionais como `Enabled`, `Visible`, ou anexando uma macro via VBA. A classe **Forms2OleControl** também permite inserir outros controles ActiveX, como caixas de seleção (`OleControlType.CheckBox`) ou caixas de combinação (`OleControlType.ComboBox`).

Se precisar gerar vários botões em um loop, encapsule a lógica de inserção em um método auxiliar:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Conclusão

Agora você sabe como **criar um botão de comando ActiveX** em um documento Word usando C# e Aspose.Words. O tutorial abordou a configuração do projeto, a inserção do botão com `InsertForms2OleControl`, seu posicionamento e a gravação do arquivo final. Com essa base, você pode automatizar formulários complexos, incorporar controles interativos e integrar documentos Word em soluções .NET maiores.

Em seguida, explore tópicos relacionados, como campos de formulário **Aspose.Words ActiveX**, estilização avançada do **C# DocumentBuilder**, ou a adição programática de **controle ActiveX no Word** para caixas de seleção e listas suspensas. Experimente diferentes coordenadas e tamanhos para atender aos requisitos específicos do seu layout. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word com Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Criar forma retangular no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Criar um documento Word com tabela usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}