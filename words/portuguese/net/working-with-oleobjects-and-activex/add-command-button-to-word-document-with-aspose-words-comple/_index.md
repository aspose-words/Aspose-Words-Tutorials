---
category: general
date: 2026-07-29
description: Adicionar botão de comando ao documento Word usando Aspose.Words. Aprenda
  como definir as propriedades do controle ActiveX e definir a legenda do botão de
  comando em alguns passos fáceis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: pt
lastmod: 2026-07-29
og_description: Adicionar botão de comando ao documento Word com Aspose.Words. Este
  tutorial mostra como definir as propriedades do controle ActiveX e definir rapidamente
  a legenda do botão de comando.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Adicionar Botão de Comando ao Documento Word – Aspose.Words Passo a Passo
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Adicionar Botão de Comando a um Documento Word com Aspose.Words – Guia Completo
url: /pt/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar Botão de Comando ao Documento Word – Guia de Programação Completo

Já precisou **add command button to word document** mas não tinha certeza de quais chamadas de API usar? Você não está sozinho; muitos desenvolvedores encontram essa barreira ao tentar inserir controles interativos em um arquivo DOCX. A boa notícia é que o Aspose.Words torna isso surpreendentemente fácil. Neste guia, vamos percorrer a criação de um controle ActiveX CommandButton, **set activex control properties**, e **set command button caption** — tudo com código C# limpo que você pode copiar‑colar agora mesmo.

Ao final deste tutorial, você terá um arquivo Word totalmente funcional que contém um botão “Submit” clicável, pronto para ser aberto no Microsoft Word. Sem scripts VBA externos, sem ajustes manuais de UI — apenas controle programático puro.

## O que você aprenderá

* Como criar um documento Word em branco e um `DocumentBuilder`.
* A chamada de método exata para **add command button to word document** usando Aspose.Words.
* Formas de **set activex control properties** como tamanho, posição e nome.
* A técnica correta para **set command button caption** para que o botão exiba exatamente o que você deseja.
* Dicas para lidar com casos extremos, como diferentes tipos de botão, dimensionamento DPI e compatibilidade de versões do Word.

> **Pré-requisito:** Visual Studio (ou qualquer IDE C#) com Aspose.Words para .NET instalado (pacote NuGet `Aspose.Words`). Não é necessária experiência prévia com ActiveX.

## Etapa 1: Configurar o Projeto e Importar Namespaces

Antes de podermos **add command button to word document**, precisamos de um projeto C# que faça referência ao Aspose.Words. Crie um novo aplicativo console .NET e, em seguida, adicione o pacote NuGet:

```bash
dotnet add package Aspose.Words
```

Agora traga os namespaces necessários para o seu arquivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Essas três diretivas `using` dão acesso às classes `Document`, `DocumentBuilder` e `Forms2OleControl`, que alimentam a inserção de ActiveX.

*Dica:* Se você estiver usando o Visual Studio, o IDE sugerirá adicionar esses automaticamente ao digitar os nomes das classes.

## Etapa 2: Criar um Documento em Branco e um Builder

Um novo objeto `Document` representa um arquivo Word vazio. O `DocumentBuilder` é nossa prática “caneta” que nos permite desenhar, inserir texto e — crucialmente — colocar controles ActiveX.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Neste ponto, o documento é apenas uma tela em branco — pense nele como uma folha limpa de papel aguardando seu botão de comando.

## Etapa 3: Inserir o Controle ActiveX CommandButton

Agora finalmente **add command button to word document**. O Aspose.Words fornece o método `InsertForms2OleControl`, que aceita o tipo de controle e as dimensões. Usaremos `Forms2OleControlType.CommandButton` e daremos uma largura confortável de 150 pontos e uma altura de 30 pontos.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

O método retorna uma instância `Forms2OleControl`, que usaremos para **set activex control properties** na próxima etapa.

## Etapa 4: Configurar o Controle – Nome, Legenda e Posição

### Definindo a Legenda

A legenda é o texto que aparece no próprio botão. Para **set command button caption**, basta atribuir uma string à propriedade `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Você pode mudar `"Submit"` para qualquer coisa — “Save”, “Export”, “Launch”, etc. — e o Word exibirá exatamente esse texto.

### Nomeando o Controle

Dar ao controle um nome significativo facilita a referência posterior (por exemplo, ao automatizar macros do Word). Definiremos a propriedade `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Posicionando na Página

O Word usa pontos (1/72 de polegada) para layout. Ajuste as propriedades `Left` e `Top` para posicionar o botão onde precisar:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Se precisar alinhar o botão em relação a um parágrafo, você pode mover o cursor do builder primeiro, então inserir o controle; as coordenadas serão relativas a essa posição.

*Caso extremo:* Em monitores de alta DPI, o tamanho visual pode aparecer ligeiramente diferente no Word. Para manter o tamanho físico do botão consistente entre dispositivos, você pode calcular os pontos com base na DPI alvo (normalmente 96 DPI para o Word).

## Etapa 5: Salvar o Documento

Com o botão totalmente configurado, persistir o arquivo é uma única linha:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

O `CommandButton.docx` resultante contém um botão ActiveX totalmente funcional. Abra‑o no Microsoft Word e você verá um botão “Submit” posicionado exatamente onde você o colocou.

### Resultado Esperado

1. O documento Word abre com uma única página.  
2. Um botão retangular rotulado **Submit** aparece nas coordenadas especificadas.  
3. Se você clicar com o botão direito no botão e escolher **Properties**, verá o nome `btnSubmit` e outras propriedades que definiu.

## Etapa 6: Variações Avançadas e Armadilhas Comuns

### Inserindo Outros Tipos de ActiveX

O método `InsertForms2OleControl` não se limita a botões de comando. Você pode incorporar caixas de seleção, botões de opção ou até objetos ActiveX personalizados:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

O mesmo padrão de **set activex control properties** se aplica — basta trocar o enum de tipo.

### Lidando com Versões do Word

Versões mais antigas do Word (pré‑2007) usam o formato binário `.doc`, que armazena controles ActiveX de forma diferente. O Aspose.Words converte automaticamente o controle ao salvar como `.doc`, mas algumas propriedades (como posicionamento preciso) podem mudar. Se você direcionar formatos legados, teste a saída na versão específica do Word que precisar.

### Configurações de Segurança

O Word pode desativar controles ActiveX em máquinas com segurança de macro rigorosa. Para evitar a caixa de diálogo “Security Warning”, considere:

* Assinar o documento com um certificado confiável.  
* Instruir os usuários a habilitar conteúdo ActiveX para aquele local de arquivo.  
* Usar uma alternativa sem macro (por exemplo, controles de conteúdo simples) se a segurança for uma preocupação.

## Etapa 7: Exemplo Completo Funcional

Abaixo está o programa completo, pronto‑para‑executar, que incorpora todas as etapas que discutimos. Copie‑o para o seu `Program.cs`, ajuste o caminho de saída se necessário e clique em **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**O que este código faz:**

* Inicia com um documento novo.  
* Insere um botão de comando, **sets activex control properties**, e **sets command button caption**.  
* Adiciona um breve parágrafo explicativo.  
* Salva o arquivo como `CommandButton.docx`.

Execute o programa, abra o arquivo gerado e você verá o botão posicionado abaixo do texto explicativo.

## Conclusão

Acabamos de demonstrar como **add command button to word document** usando Aspose.Words, como **set activex control properties**, e como **set command button caption** — tudo em um trecho C# conciso e pronto para produção. A abordagem escala: troque o tipo de controle, ajuste as dimensões ou faça um loop sobre uma fonte de dados para inserir dezenas de botões automaticamente.

Quer ir além? Experimente:

* Vincular o botão a uma macro que aciona a exportação de dados.  
* Adicionar imagens ou ícones personalizados dentro do botão usando a propriedade `Picture`.  
* Construir um formulário completo com múltiplos controles ActiveX (caixas de texto, caixas de combinação, etc.).

Experimentar é a melhor forma de dominar a automação do Word. Se encontrar algum problema, lembre‑se de verificar novamente seus cálculos de DPI e as configurações de segurança do Word. Boa codificação, e que seus documentos sejam cada vez mais interativos!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Adicionar Conteúdo Usando Document Builder no Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar Documento Word com Cabeçalho e Rodapé Usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}