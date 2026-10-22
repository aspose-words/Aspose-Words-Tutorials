---
category: general
date: 2026-09-05
description: Crie um documento Word usando Aspose.Words C# e aprenda como inserir
  um botão de comando ActiveX, definir o tamanho do botão e adicionar funcionalidade
  interativa ao botão.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: pt
lastmod: 2026-09-05
og_description: Crie um documento Word em C# e insira um botão de comando ActiveX.
  Este tutorial mostra como definir o tamanho do botão e adicionar recursos interativos
  ao botão.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Criar documento Word com botão de comando ActiveX em C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Como criar um documento Word com um botão de comando ActiveX em C#
url: /pt/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word com um botão de comando ActiveX em C#

Se você precisa **criar documento Word** programaticamente e incorporar um elemento de UI clicável, este guia mostra exatamente como fazer. Usando Aspose.Words para .NET você pode **criar documento Word**, **adicionar botão de comando** e controlar sua aparência — tudo sem abrir o Microsoft Word.

Você aprenderá **como inserir controles ActiveX**, **definir o tamanho do botão** e fazer o botão se comportar como um componente de UI interativo. Não é necessária experiência prévia com COM ou VBA; apenas um ambiente de desenvolvimento .NET e a biblioteca Aspose.Words.

## O que você alcançará

* **Criar um documento Word** do zero com C#.
* **Inserir um botão de comando ActiveX** (o clássico controle “Click Me”).
* **Definir o tamanho do botão** e a posição com precisão.
* Opcionalmente adicionar lógica simples de **botão interativo** (por exemplo, um placeholder de macro).
* Salvar o arquivo como `.docx` que pode ser aberto no Microsoft Word ou em qualquer visualizador compatível.

### Pré-requisitos

| Requisito | Motivo |
|-------------|--------|
| .NET 6.0 ou posterior | Fornece o runtime para código C#. |
| Aspose.Words for .NET (última versão) | Fornece as APIs `Document`, `DocumentBuilder` e `Forms2OleControl` usadas no exemplo. |
| Visual Studio 2022 (ou qualquer IDE C#) | Facilita compilar e executar o exemplo. |
| Conhecimento básico de C# | Necessário para entender o fluxo do código. |

> **Dica profissional:** Se você estiver usando uma versão de avaliação do Aspose.Words, certifique-se de definir a licença antes de executar o código para evitar marcas d'água de avaliação.

## Como criar documento Word – fluxo de trabalho geral

O processo consiste em quatro etapas lógicas:

1. **Inicializar um novo documento** e um `DocumentBuilder` para editá-lo.  
2. **Inserir um botão de comando ActiveX** usando `InsertForms2OleControl`.  
3. **Configurar o botão** – legenda, tamanho e posição.  
4. **Salvar** o documento no disco.

Cada passo é explicado em sua própria seção abaixo.

![Documento Word com um botão ActiveX](/images/activex-button.png "Captura de tela de um documento Word que contém um botão de comando ActiveX criado com C#")

## Como inserir botão de comando ActiveX

A parte **como inserir activex** começa com o método `InsertForms2OleControl`. Este método cria um controle baseado em COM que o Word trata como um objeto ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Por que isso funciona:** `OleControlType.CommandButton` indica ao Aspose.Words que crie o clássico botão estilo VB. O tamanho e a localização são expressos em pontos (1 ponto = 1/72 polegada), o que fornece controle preciso sobre o layout.

## Como adicionar botão de comando e definir o tamanho do botão

Depois que o controle é inserido, você pode ajustar suas propriedades visuais. A etapa **adicionar botão de comando** também cobre **definir o tamanho do botão**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Explicação:**  

* `Caption` é o rótulo exibido no botão.  
* `Width` e `Height` permitem **definir o tamanho do botão** após a inserção inicial — útil quando o tamanho depende de dados em tempo de execução.  
* `Left` e `Top` reposicionam o controle sem recriar o documento.

> **Erro comum:** Esquecer de usar pontos em vez de pixels fará o botão aparecer muito pequeno ou muito grande. Sempre converta valores de pixel (`px * 72 / DPI`) se você começar a partir de medições de tela.

## Como adicionar botão interativo (opcional)

Um botão ActiveX pode executar uma macro ao ser clicado, mas incorporar código VBA a partir de C# está fora do escopo de um fluxo de trabalho puro do Aspose.Words. Em vez disso, você pode adicionar uma propriedade placeholder que o Word reconhecerá como nome de macro.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Quando o usuário abre o `.docx` gerado no Word, clicar no botão tentará executar `MyMacroName`. Se a macro não existir, o Word solicitará ao usuário que a crie.

**Por que você pode usar isso:** Para formulários corporativos onde uma macro preenche campos, o código C# só precisa colocar o botão; a lógica da macro reside no projeto VBA do documento.

## Salvar o documento e verificar o resultado

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Saída esperada:** Abrir `CommandButton.docx` no Microsoft Word mostra um botão rotulado **Click Me** posicionado 100 pts da margem esquerda e 120 pts do topo. As dimensões do botão são **200 pts × 80 pts**. Clicar no botão aciona o placeholder da macro (se presente).

## Exemplo completo em funcionamento

Abaixo está o programa completo e executável que reúne tudo. Copie-o para um novo projeto Console App, adicione o pacote NuGet Aspose.Words e execute.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Execute o programa, então abra o arquivo gerado. Você verá o **botão interativo** pronto para personalizações adicionais.

## Perguntas frequentes

| Pergunta | Resposta |
|----------|--------|
| **Isso funciona com .NET Core?** | Sim. Aspose.Words suporta .NET Standard, então o mesmo código funciona em .NET 5/6/7. |
| **Posso usar outros controles ActiveX (ex.: CheckBox)?** | Absolutamente. Substitua `OleControlType.CommandButton` por `OleControlType.CheckBox`, `OleControlType.OptionButton`, etc. |
| **E se eu precisar de um botão maior em uma página paisagem?** | Ajuste as propriedades `Width`, `Height`, `Left` e `Top` proporcionalmente. Lembre-se de que os pontos permanecem os mesmos independentemente da orientação da página. |
| **É necessária uma macro para que o botão seja clicável?** | Não. O botão funciona totalmente como um elemento de UI; uma macro apenas adiciona comportamento personalizado ao ser clicado. |

## Conclusão

Agora você sabe como **criar documento Word** com Aspose.Words, **adicionar botão de comando**, **definir o tamanho do botão**, e opcionalmente vincular o botão a uma macro para comportamento de **adicionar botão interativo**. Essa abordagem permite automatizar a criação de formulários, gerar relatórios dinâmicos ou construir protótipos de UI baseados em Word diretamente a partir de C#.

Em seguida, você pode explorar:

* **Como inserir caixas de seleção ActiveX** para formulários de pesquisa.  
* **Como adicionar conteúdo de texto rico** ao redor do botão usando `DocumentBuilder`.  
* **Como proteger o documento** mantendo o botão funcional.  

Fique à vontade para experimentar diferentes tipos de controle, tamanhos e nomes de macro para se adequar ao seu cenário específico. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word com Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Inserir imagem inline em documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Criar um documento Word com tabela usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}