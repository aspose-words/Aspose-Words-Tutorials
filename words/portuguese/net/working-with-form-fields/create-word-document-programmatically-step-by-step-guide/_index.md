---
category: general
date: 2026-08-04
description: Crie documento Word programaticamente usando C#. Aprenda como adicionar
  programaticamente um botão de comando com Aspose.Words em apenas alguns passos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: pt
lastmod: 2026-08-04
og_description: Crie um documento Word programaticamente com Aspose.Words. Este guia
  mostra como adicionar programaticamente um botão de comando, configurá‑lo e salvar
  o arquivo.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Criar documento Word programaticamente – tutorial completo em C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Criar documento Word programaticamente – guia passo a passo
url: /pt/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word programaticamente – tutorial completo em C#

Se você precisa **create word document programmatically**, este guia mostra exatamente como fazer isso com Aspose.Words para .NET. Em apenas algumas linhas de C# você pode gerar um arquivo `.docx` em branco, **programmatically add command button** controles, definir suas propriedades e salvar o resultado.

As etapas abaixo cobrem tudo, desde a configuração do projeto até o tratamento de casos extremos, para que você possa copiar o código para sua própria aplicação e executá-lo sem modificações.

## O que você vai alcançar

* Inicializar um novo documento Word totalmente na memória.  
* **Programmatically add command button** controles OLE em qualquer localização e tamanho.  
* Configurar a legenda (caption) do botão, o nome interno e outras propriedades OLE.  
* Salvar o documento gerado em disco ou em um stream para processamento adicional.

### Pré-requisitos

* .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+).  
* Uma licença válida do Aspose.Words para .NET (ou uma avaliação gratuita).  
* Familiaridade básica com C# e Visual Studio (ou qualquer IDE de sua escolha).  

> **Dica profissional:** Se você executar o exemplo sem uma licença, o Aspose.Words adicionará uma pequena marca d'água de avaliação na primeira página.

## Etapa 1: Configurar o projeto e importar os namespaces necessários

Crie um novo Console App (ou integre a um serviço existente) e adicione o pacote NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Em seguida, inclua os namespaces essenciais no topo do seu arquivo `.cs`:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Essas importações dão acesso a `Document`, `DocumentBuilder`, `Forms2OleControl` e à estrutura `RectangleF` usada para posicionamento.

## Etapa 2: Inicializar um novo documento Word

A primeira operação em qualquer fluxo de **create word document programmatically** é instanciar um objeto `Document`. Esse objeto reside apenas na memória até que você o salve explicitamente.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funciona como um cursor que rastreia onde o próximo elemento será colocado. Usá‑lo mantém o código conciso e reflete a forma como você digitaria diretamente no Word.

## Etapa 3: Inserir um controle OLE de botão de comando

Aspose.Words fornece o método `InsertForms2OleControl` para incorporar objetos OLE como botões de comando, caixas de seleção ou caixas de combinação. O método requer três argumentos:

1. O valor enum `ControlType` (aqui `CommandButton`).  
2. Um `RectangleF` que define a posição X‑Y e a largura‑altura do controle (medido em pontos, onde 72 pt = 1 polegada).  
3. Opcionalmente, propriedades OLE adicionais (não necessárias para o botão básico).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Por que isso funciona:** `InsertForms2OleControl` cria um contêiner OLE no documento e retorna um wrapper `Forms2OleControl`. O wrapper permite manipular o objeto OLE subjacente (o botão real) sem lidar com interop COM de baixo nível.

## Etapa 4: Configurar a legenda e o nome interno do botão

Após a inserção, normalmente você deseja dar ao botão um rótulo visível ao usuário e um identificador interno que sua macro ou add‑in possa referenciar posteriormente.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` é o texto exibido no botão na interface do Word.  
* `Name` é o identificador programático usado por VBA ou scripts de automação externos.

### Opcional: Atribuir uma macro ao botão

Se você pretende executar uma macro VBA quando o botão for clicado, pode anexar o nome da macro:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Caso extremo:** Quando o documento de destino for aberto em uma máquina sem a macro, o Word exibirá um aviso de segurança. Sempre assine suas macros ou informe os usuários sobre as configurações necessárias.

## Etapa 5: Salvar o documento

Você pode gravar o arquivo em disco, em um `MemoryStream` ou diretamente em um objeto de resposta em uma API web. A abordagem mais simples para uma demonstração de console é salvar em uma pasta local:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

O `.docx` resultante abre no Microsoft Word com um botão de comando funcional que exibe “Click Me”. Clicar no botão acionará a macro atribuída (se houver) ou simplesmente exibirá uma mensagem padrão.

## Exemplo completo em funcionamento

Copie o programa a seguir para `Program.cs` e execute-o. Ele demonstra todo o fluxo de **create word document programmatically**, incluindo tratamento de erros.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Resultado esperado:** Ao abrir `CommandButton.docx` no Word, aparece um botão rotulado “Click Me”. Passar o mouse sobre o botão revela o nome `cmdClickMe` no painel de propriedades.

## Perguntas comuns e solução de problemas

| Pergunta | Resposta |
|----------|----------|
| *Posso adicionar o botão a um documento existente?* | Sim. Carregue o arquivo com `new Document("Existing.docx")`, então use a mesma chamada `InsertForms2OleControl`. |
| *Quais unidades o `RectangleF` usa?* | Pontos (1 polegada = 72 pt). Ajuste os valores para posicionar o botão com precisão. |
| *O botão funcionará no Word para Mac?* | Controles OLE são suportados apenas no Word para Windows. No Mac, o botão aparece como uma imagem estática. |
| *Preciso de uma licença para uso em produção?* | Uma licença comercial remove as marcas d'água de avaliação e desbloqueia toda a funcionalidade. |
| *Como altero o tamanho do botão após a inserção?* | Modifique `commandButton.Width` e `commandButton.Height` ou reinsira com um novo `RectangleF`. |

## Expandindo a solução

Agora que você sabe como **programmatically add command button** controles, pode explorar os tópicos relacionados a seguir:

* **Insert other form controls** – use `ControlType.CheckBox`, `ControlType.OptionButton`, etc. (cobre a palavra‑chave secundária *Aspose.Words InsertForms2OleControl*).  
* **Populate the document with dynamic data** – mesclar dados de um banco de dados em tabelas ou campos de mala‑direta.  
* **Export to PDF** – após adicionar o botão, chame `doc.Save("output.pdf", SaveFormat.Pdf)` para gerar uma versão PDF (relevante para *C# Word automation*).  

## Conclusão

Agora você tem um padrão completo e pronto para produção para **create word document programmatically** e **programmatically add command button** usando Aspose.Words para .NET. O tutorial abordou a configuração do projeto, a inicialização do documento, a inserção do botão OLE, a configuração de propriedades e a gravação do arquivo. Sinta‑se à vontade para adaptar o código para inserir outros controles de formulário, anexar macros ou integrar a lógica em serviços web ou tarefas em segundo plano.

Boa codificação e aproveite a automação de documentos Word!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word com Aspose.Words – Guia passo a passo](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Criar um documento Word com tabela usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}