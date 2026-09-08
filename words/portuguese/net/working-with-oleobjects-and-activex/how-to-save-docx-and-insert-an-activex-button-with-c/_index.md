---
category: general
date: 2026-09-08
description: Como salvar docx ao inserir um controle ActiveX em C#. Siga este guia
  passo a passo para adicionar um botão de comando programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: pt
lastmod: 2026-09-08
og_description: Como salvar docx ao inserir um controle ActiveX em C#. Este tutorial
  orienta você na criação de um documento Word programaticamente, adicionando um botão
  de comando e persistindo o arquivo.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: Como salvar docx e incorporar um botão ActiveX em C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: Como salvar docx e inserir um botão ActiveX com C#
url: /pt/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como salvar docx e inserir um botão ActiveX com C#

Se você precisa criar programaticamente um documento Word e depois salvar o docx com um botão interativo, este guia mostra como fazer isso. Você aprenderá a inserir um controle ActiveX, adicionar um botão ActiveX e salvar o arquivo .docx resultante usando C# e a biblioteca Aspose.Words.

O tutorial cobre cada passo necessário para **criar documento Word programaticamente**, incorporar um **botão de comando** e persistir o arquivo no disco. Não é necessária experiência prévia com objetos COM, mas você deve ter conhecimentos básicos de C# e o Visual Studio instalado.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior  
* Visual Studio 2022 (ou qualquer IDE C#)  
* Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
* Compreensão da estrutura de projetos C#  

Esses itens garantem que o código compile e execute sem configuração adicional.

## Etapa 1: Configurar um novo projeto de console C#

Crie uma aplicação console que hospedará a lógica de automação do Word.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

O comando acima cria uma pasta chamada **WordActiveXDemo**, adiciona a referência ao Aspose.Words e prepara o projeto para compilação.

## Etapa 2: Criar um documento Word programaticamente

Abra o arquivo `Program.cs` gerado e adicione as diretivas `using` necessárias.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Agora instancie um objeto `Document` vazio. Esse objeto representa todo o arquivo Word na memória.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

A classe `Document` é o ponto de entrada para todas as operações de processamento de Word. Neste estágio o documento não contém páginas, mas o Aspose.Words criará uma seção padrão automaticamente quando você adicionar conteúdo.

## Etapa 3: Inserir um controle ActiveX – adicionar botão activex

Um objeto **Forms2OleControl** permite incorporar um controle ActiveX dentro de um parágrafo Word. O código a seguir insere um **CommandButton** com largura de 150 pt e altura de 30 pt.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` cria o controle e devolve uma instância tipada de `Forms2OleControl`, que você pode configurar ainda mais. O método adiciona automaticamente um novo parágrafo para hospedar o controle, portanto você não precisa gerenciar objetos de parágrafo manualmente.

## Etapa 4: Configurar o botão de comando – como adicionar propriedades ao botão de comando

Defina as propriedades **Name** e **Caption** do botão para torná‑lo identificável em tempo de execução e amigável ao usuário na interface.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

O atributo `Name` é útil quando você posteriormente manipular o evento de clique do botão via VBA ou uma macro Word. O `Caption` é o texto que o usuário final vê na superfície do botão.

### Dica profissional
Se você planeja automatizar o tratamento de cliques a partir de C#, incorpore uma macro VBA que faça referência a `cmdSubmit`. O Word solicitará ao usuário que habilite macros quando o documento for aberto, o que é o comportamento padrão de segurança para controles ActiveX.

## Etapa 5: Como salvar docx

Depois que o controle estiver no lugar, persista o documento em um arquivo .docx. O método `Save` escolhe automaticamente o formato apropriado com base na extensão do arquivo.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Salvar o arquivo conclui o fluxo **como salvar docx**. O arquivo resultante pode ser aberto no Microsoft Word, onde o botão ActiveX aparecerá na primeira página. Quando você clicar no botão, o Word exibirá uma mensagem de espaço reservado a menos que uma macro esteja anexada.

## Etapa 6: Executar o programa e verificar o resultado

Compile e execute a aplicação console:

```bash
dotnet run
```

Após a conclusão do programa, abra `C:\Temp\CommandButton.docx` no Microsoft Word:

* O documento contém uma única página com um botão **Submit** próximo ao topo.  
* Passar o mouse sobre o botão mostra a dica com o nome `cmdSubmit`.  
* Nenhum conteúdo é perdido, e o tamanho do arquivo é comparável ao de um .docx em branco padrão.

Se o botão não aparecer, confirme que:

1. As configurações do **Centro de Confiabilidade** do Word permitem controles ActiveX.  
2. O arquivo foi salvo com a extensão `.docx` (não `.doc`).  

## Casos de borda e variações comuns

| Situação | Ajuste recomendado |
|-----------|------------------------|
| Você precisa de um tamanho de botão diferente | Altere os argumentos de largura e altura em `InsertForms2OleControl`. |
| Você quer o botão em uma página específica | Use `builder.MoveToDocumentEnd();` após adicionar páginas, ou insira uma quebra de página antes do controle. |
| Você deve suportar ambientes sem Aspose.Words | Use o Open XML SDK para inserir um elemento `w:object`, mas o código torna‑se consideravelmente mais complexo. |
| Documento habilitado para macro é necessário | Salve com a extensão `.docm` (`document.Save("MyDoc.docm");`) e incorpore um módulo VBA que trate `cmdSubmit_Click`. |

## Código‑fonte completo

A seguir está o programa completo e autocontido que você pode copiar para `Program.cs` e executar sem modificações (exceto o caminho de saída).

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
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Saída esperada no console

```
Document saved to C:\Temp\CommandButton.docx
```

Abrir o arquivo no Word exibe um botão rotulado **Submit**. Clicar no botão aciona o comportamento padrão do ActiveX (uma caixa de mensagem indicando que nenhuma macro está anexada).

## Conclusão

Este tutorial demonstrou **como salvar docx** enquanto incorpora um **controle ActiveX**, especificamente um **add activex button** que funciona como um botão de comando. Agora você sabe como **criar documento Word programaticamente**, configurar as propriedades do botão e persistir o arquivo para interação do usuário final.

A partir daqui você pode explorar:

* Adicionar macros VBA para tratar `cmdSubmit_Click`.  
* Inserir outros controles ActiveX, como caixas de seleção ou caixas de combinação.  
* Gerar documentos de várias páginas com múltiplos elementos interativos.  

Experimente diferentes tipos de controle e opções de layout para construir modelos Word ricos e interativos que otimizem seus processos de negócios.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [how to recover docx – C# guide for corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [How to Save Word as Markdown – Complete C# Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}