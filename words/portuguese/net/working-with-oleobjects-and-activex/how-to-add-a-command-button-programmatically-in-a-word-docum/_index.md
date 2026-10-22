---
category: general
date: 2026-10-13
description: Aprenda a adicionar um botão de comando programaticamente usando Aspose.Words.
  Este guia também mostra como criar um botão em um documento Word com código C# completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: pt
lastmod: 2026-10-13
og_description: Adicione um botão de comando programaticamente a um documento Word
  usando Aspose.Words. Siga este tutorial completo para criar um botão em um documento
  Word com C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Adicionar um botão de comando programaticamente a um documento Word – guia
  passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Como adicionar um botão de comando programaticamente em um documento do Word
url: /pt/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar um botão de comando programaticamente em um documento Word  

Se você precisar **adicionar um botão de comando programaticamente**, o Aspose.Words fornece uma API limpa que permite incorporar controles de formulário OLE diretamente em um arquivo .docx. Este tutorial orienta você em cada passo necessário para **criar um botão em um documento Word** que se comporta como um botão de formulário normal quando o documento é aberto no Microsoft Word.  

Você aprenderá como configurar o ambiente de desenvolvimento, inserir o botão, configurar suas propriedades e verificar o resultado. Nenhuma ferramenta externa é necessária — apenas um projeto .NET e a biblioteca Aspose.Words for .NET.  

## Pré-requisitos  

Antes de começar, certifique-se de que você tem:  

* .NET 6.0 SDK ou posterior instalado.  
* Uma versão recente do Aspose.Words for .NET (os exemplos usam 23.12, mas qualquer versão 22.x+ funciona).  
* Uma IDE como Visual Studio 2022 ou Visual Studio Code.  

O código funciona no Windows, macOS e Linux porque o Aspose.Words é independente de plataforma.  

## Etapa 1: Configurar o projeto e referenciar o Aspose.Words  

1. Crie um novo projeto de console:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Adicione o pacote NuGet Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Abra **Program.cs** e substitua seu conteúdo pelo esqueleto mostrado nas próximas etapas.  

Configurar o projeto dessa forma garante que o compilador possa localizar os namespaces `Aspose.Words` e `Aspose.Words.Drawing.Forms` necessários para os controles de formulário.  

## Etapa 2: Inicializar um documento em branco e um DocumentBuilder  

A classe `Document` representa todo o arquivo Word, enquanto `DocumentBuilder` fornece uma API fluente para adicionar conteúdo.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Por que esta etapa importa* – Sem um `DocumentBuilder` você não pode posicionar o botão com precisão na página. O builder também respeita a posição atual do cursor, facilitando a inserção de múltiplos controles posteriormente.  

## Etapa 3: Inserir o controle OLE de botão de comando  

O Aspose.Words trata um botão de comando como um controle OLE do tipo `ControlType.CommandButton`. Você define sua localização e tamanho com um `RectangleF` medido em pontos (1 ponto = 1/72 polegada).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Pontos principais**  

* A origem do retângulo (X, Y) é relativa ao canto superior esquerdo da página.  
* Alterar o `Width` ou `Height` modifica o tamanho visual do botão.  
* `InsertForms2OleControl` retorna um objeto `Forms2OleControl` que você pode configurar ainda mais.  

## Etapa 4: Configurar o nome e a legenda do botão  

O **name** (nome) é usado pelo mecanismo de macros do Word para identificar o controle, enquanto a **caption** (legenda) é o texto que o usuário vê.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Se você planeja adicionar macros VBA posteriormente, use um nome descritivo, pois o gravador de macros do Word faz referência a essa propriedade.  

## Etapa 5: (Opcional) Salvar o documento e verificar o resultado  

Salvar o arquivo permite que você o abra no Microsoft Word para confirmar que o botão aparece e funciona.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Ao abrir *CommandButtonDemo.docx* no Word, você deverá ver um botão rotulado **Submit** posicionado aproximadamente 1,4 polegadas da margem esquerda e 2,1 polegadas do topo da página. Clicar no botão não faz nada por padrão porque nenhuma macro está anexada, mas o controle visual está totalmente funcional.  

## Etapa 6: Casos de borda e armadilhas comuns  

| Situação | O que observar | Correção recomendada |
|-----------|-------------------|-----------------|
| **Botão sobrepõe texto existente** | O retângulo pode intersectar um parágrafo, causando problemas de layout. | Insira o botão após chamar `builder.Writeln()` para mover o cursor para uma nova linha, ou ajuste a coordenada `Y`. |
| **Documento abre com um aviso** | Algumas versões do Word sinalizam controles OLE que não têm um programa vinculado. | Garanta que o tipo de controle seja `CommandButton`; o Word o trata como um elemento de formulário padrão e não requer um programa externo. |
| **Executando no Linux em ambiente sem interface** | O Word não pode ser iniciado para testar a UI, mas o arquivo permanece válido. | Use um teste unitário que leia as propriedades do controle (`commandButton.Name`, `commandButton.Caption`) para verificar se foram definidas corretamente. |
| **Vários botões necessários** | Reutilizar o mesmo `DocumentBuilder` sem mover o cursor adiciona o botão sobre o anterior. | Chame `builder.MoveToDocumentEnd()` ou ajuste o valor `Y` do retângulo antes de cada inserção. |

Abordar esses casos de borda cedo economiza tempo ao escalar a solução para formulários completos com dezenas de controles.  

## Etapa 7: Exemplo completo e executável  

Abaixo está um programa autônomo que você pode copiar, colar e executar sem modificações (exceto a restauração do NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Saída esperada**  

Executar o programa imprime um caminho semelhante a:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Abrir o *CommandButtonDemo.docx* gerado mostra um único botão **Submit** colocado nas coordenadas definidas no código. Nenhum elemento de UI adicional aparece, confirmando que o fluxo **add command button programmatically** (adicionar botão de comando programaticamente) foi bem-sucedido.  

## Conclusão  

Agora você sabe como **add a command button programmatically** (adicionar um botão de comando programaticamente) a um documento Word usando Aspose.Words, e também entende como **create a Word document button** (criar um botão em documento Word) que pode ser posteriormente conectado a macros VBA ou ferramentas de automação externas. O processo consiste em inicializar um documento, inserir um controle OLE `CommandButton`, configurar suas propriedades e salvar o arquivo.  

A partir daqui você pode:  

* Adicionar mais controles (caixas de seleção, campos de texto) repetindo a etapa 3 com diferentes valores de `ControlType`.  
* Anexar macros VBA ao botão para executar ações como salvar um formulário ou enviar um e‑mail.  
* Gerar formulários completos dinamicamente percorrendo uma coleção de definições de campos orientada por dados.  

Experimente as coordenadas do retângulo e a legenda do botão para combinar com o design da sua UI. Feliz codificação!  


## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Adicionar um campo de formulário Combo Box a um documento Word com Aspose.Words para .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Adicionar um campo de formulário Check Box a um documento Word com Aspose.Words para .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Criar documento Word em branco com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}