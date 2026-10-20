---
category: general
date: 2026-10-20
description: Crie um documento Word programaticamente e adicione um botão de comando
  usando Aspose.Words. Aprenda a inserir um controle ActiveX e definir a legenda do
  botão.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: pt
lastmod: 2026-10-20
og_description: Crie um documento Word programaticamente e incorpore um botão de comando
  ActiveX. Este tutorial explica como inserir o controle e definir sua legenda com
  Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Criar documento Word programaticamente – adicionar botão ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Criar documento do Word programaticamente com um botão ActiveX
url: /pt/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word programaticamente com um botão ActiveX

Crie um documento Word programaticamente com Aspose.Words e, em seguida, adicione um botão de comando que os usuários podem clicar. Este guia orienta você a inserir um controle ActiveX, configurar suas propriedades e salvar o resultado como um arquivo **.docx**.

Você verá um exemplo completo e executável que pode copiar para uma aplicação console. Ao final do tutorial você poderá gerar um arquivo Word que contém um botão de comando totalmente funcional, e entenderá como **add command button**, **add activex control**, **insert activex button**, e **set button caption** sem sair do seu código C#.

## Pré-requisitos

* .NET 6.0 SDK ou posterior instalado  
* Visual Studio 2022 (ou qualquer IDE compatível com C#)  
* Um arquivo de licença do Aspose.Words para .NET (a versão de avaliação gratuita funciona para este exemplo)  
* Familiaridade básica com C# e o sistema de projetos .NET  

Nenhum pacote NuGet adicional é necessário além do **Aspose.Words**, pois o suporte a ActiveX está incorporado na biblioteca.

## Etapa 1: Configurar o projeto e adicionar Aspose.Words

1. Abra um terminal ou o Visual Studio e crie um novo projeto console:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Adicione o pacote Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Opcional) Se você possui um arquivo de licença, coloque‑o na raiz do projeto e adicione a linha a seguir no início do `Program.cs` para evitar marcas d'água de avaliação:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Etapa 2: Criar documento Word programaticamente – inicializar o documento

A primeira operação é **create Word document programmatically**. Você faz isso instanciando um objeto `Document` e um `DocumentBuilder` que permite editar o conteúdo do documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

O `Document` representa o arquivo inteiro, enquanto o `DocumentBuilder` mantém um cursor que pode ser movido para qualquer localização no documento. Essa separação mantém a API limpa e permite que você **add activex control** posteriormente sem gerenciar manualmente estruturas de baixo nível.

## Etapa 3: Adicionar botão de comando – inserindo um controle ActiveX

Agora você **add command button** inserindo um controle ActiveX do tipo `OleControlType.CommandButton`. O método `InsertForms2OleControl` requer o tipo de controle, uma localização (`Point`) e um tamanho (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

A chamada acima **insert activex button** no documento nas coordenadas exatas que você especificar. As coordenadas são medidas em pontos (1 pt ≈ 1/72 in). Se precisar do botão em um parágrafo específico, mova primeiro o cursor do builder:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Etapa 4: Definir legenda do botão – personalizando o texto do botão de comando

Um botão sem rótulo é confuso, portanto você **set button caption** para algo significativo. A propriedade `Caption` define o texto exibido no botão, enquanto `Name` fornece ao controle um identificador programático.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Se posteriormente exportar o documento para um formato habilitado para macros (`.docm`), o valor `OnClick` deve corresponder a um nome de macro VBA. Para um simples `.docx`, a propriedade é armazenada mas não executada, o que é adequado para a maioria dos cenários de automação.

## Etapa 5: Salvar o documento contendo o botão ActiveX

Após configurar o controle, você pode **save the document**. Escolha um diretório ao qual você tenha permissão de gravação e use a extensão `.docx` para máxima compatibilidade.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Ao abrir o arquivo gerado no Microsoft Word, você verá um botão rotulado **Submit** nas coordenadas especificadas. Clicar no botão no cliente desktop tentará executar a macro `SubmitForm` (se existir).

## Etapa 6: Verificar o resultado e solucionar problemas comuns

1. Abra `ActiveXCommandButton.docx` no Microsoft Word.  
2. Mude para **Design Mode** (aba Desenvolvedor → **Design Mode**) para ver as bordas do botão.  
3. Se o botão não aparecer, verifique se a aba **Developer** está habilitada e se sua versão do Word suporta controles ActiveX.  
4. Para arquivos habilitados para macro (`.docm`), certifique‑se de que o nome da macro em `OnClick` corresponde a uma rotina VBA; caso contrário, o Word exibirá um aviso de segurança.

### Dica profissional

Os controles ActiveX são apenas para Windows. Se precisar de interatividade multiplataforma, considere usar **Content Controls** (`RichTextContentControl`) em vez de um botão ActiveX.

## Código-fonte completo

Abaixo está o programa completo, pronto para execução. Copie‑o para `Program.cs` e execute `dotnet run`.



## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word com botão ActiveX – Guia C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Adicionar botão de comando ao documento Word com Aspose.Words – Guia completo](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Criar botão de documento Word com Aspose.Words – Exemplo de código completo](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}