---
category: general
date: 2026-08-10
description: Crie um documento Word programaticamente com Aspose.Words, depois adicione
  um botão de controle ActiveX. Insira um botão de comando ActiveX em minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: pt
lastmod: 2026-08-10
og_description: Crie um documento Word programaticamente usando Aspose.Words, depois
  adicione um botão de controle ActiveX ao Word. Aprenda como inserir rapidamente
  um botão de comando ActiveX.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Criar documento Word programaticamente – adicionar um botão ActiveX em C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Criar documento Word programaticamente e adicionar botão ActiveX
url: /pt/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word programaticamente e adicionar botão ActiveX

Se você precisa **criar documentos Word programaticamente**, este guia o conduz por todo o processo com Aspose.Words para .NET. Você também aprenderá como **adicionar elementos de controle ActiveX ao Word** e **inserir objetos de botão de comando ActiveX** em um exemplo único e autocontido.

Gerar arquivos Word a partir de código elimina a etapa manual de abrir o Microsoft Word, permitindo que você crie relatórios, faturas ou contratos baseados em dados automaticamente. Ao final deste tutorial você terá um aplicativo console C# pronto‑para‑executar que produz um arquivo `.docx` contendo um **ActiveX CommandButton** interativo.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou superior (o código também funciona com .NET Framework 4.6+)
* Visual Studio 2022 ou qualquer IDE que ofereça suporte ao desenvolvimento .NET
* Uma licença válida do Aspose.Words para .NET (você pode usar a chave de avaliação gratuita para testes)
* Familiaridade básica com a sintaxe C# e o conceito de controles COM/ActiveX

> **Dica profissional:** Se você pretende distribuir o documento gerado para usuários que não têm o Word instalado, incorpore os arquivos de runtime do controle ActiveX ao lado do `.docx` ou forneça um modelo habilitado para macro.

## Criar documento Word programaticamente – configuração inicial

Primeiro, adicione o pacote NuGet Aspose.Words ao seu projeto:

```bash
dotnet add package Aspose.Words
```

Em seguida, crie um novo projeto console (caso ainda não tenha um):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Abra o arquivo `Program.cs` gerado – substituiremos seu conteúdo pela solução completa abaixo.

## Etapa 1: Importar namespaces e configurar a licença

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Por que isso importa*: Importar `Aspose.Words.Drawing` fornece acesso a `Forms2OleControl`, a classe que representa um controle ActiveX dentro de um documento Word. Definir a licença logo no início evita avisos de tempo de execução em produção.

## Etapa 2: Criar um documento em branco e um DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

O objeto `Document` é a representação em memória de um arquivo `.docx`. `DocumentBuilder` funciona como um cursor que você move pelo documento para inserir elementos.

## Etapa 3: Inserir um controle ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` cria um objeto OLE que o Word trata como um controle ActiveX. O sistema de coordenadas usa pontos (1 ponto = 1/72 polegada), que corresponde ao motor de layout do Word.

## Etapa 4: Definir a legenda do botão e propriedades opcionais

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Definir a propriedade `Caption` é a forma mais comum de rotular o botão. Se precisar que o botão execute uma macro VBA, atribua o nome da macro a `OnAction`. Este tutorial foca na parte visual; a integração de macros é abordada na seção “Próximos passos”.

## Etapa 5: Salvar o documento

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Ao executar o programa, você verá uma mensagem no console confirmando que `ActiveX_CommandButton.docx` foi gravado no disco.

### Código‑fonte completo (pronto para copiar‑colar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Executar o trecho produz um arquivo Word que contém um **botão de comando ActiveX** clicável. Abra o arquivo no Microsoft Word, alterne para **Modo de Design** (guia Desenvolvedor → Modo de Design) e você verá o botão renderizado exatamente onde o posicionou.

## Etapa 6: Verificar o resultado

1. Abra `ActiveX_CommandButton.docx` no Microsoft Word.  
2. Ative a guia **Desenvolvedor** caso ela não esteja visível (`Arquivo → Opções → Personalizar Faixa de Opções → marcar Desenvolvedor`).  
3. Clique em **Modo de Design**. O botão deve aparecer com o rótulo “Submit”.  
4. Se você adicionou uma macro `OnAction`, clique no botão com o Modo de Design desativado para disparar a macro.

Se o botão não aparecer, verifique se as configurações de segurança do Word permitem controles ActiveX (`Arquivo → Opções → Central de Confiança → Configurações da Central de Confiança → Configurações de ActiveX`).

## Perguntas frequentes e casos de borda

| Pergunta | Resposta |
|----------|----------|
| **Posso inserir outros tipos de ActiveX?** | Sim. O enum `Forms2OleControlType` inclui `CheckBox`, `OptionButton`, `ComboBox`, etc. Substitua `CommandButton` pelo valor do enum desejado |

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}