---
title: Código Cercado
linktitle: Código Cercado
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como adicionar código cercado e sequências de informações a documentos do Word usando o Aspose.Words para .NET. Guia passo a passo incluso. Aprimore suas habilidades de formatação de documentos.
weight: 10
url: /pt/net/working-with-markdown/fenced-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Código Cercado

## Introdução

Olá, colega programador! Hoje, estamos mergulhando no mundo do Aspose.Words para .NET para dominar a arte de adicionar código cercado e código cercado com sequências de informações aos seus documentos do Word. Imagine seu documento do Word como uma tela, e você, o artista, está prestes a pintar com a precisão de um desenvolvedor experiente. Com o Aspose.Words, você obtém o poder de aprimorar programaticamente seus documentos com blocos de código estruturados e formatados, fazendo seus documentos técnicos brilharem com profissionalismo e clareza.

## Pré-requisitos

Antes de começarmos o tutorial, vamos garantir que você tenha tudo o que precisa:

- Conhecimento básico de C#: Uma compreensão geral de C# ajudará você a entender os conceitos rapidamente.
-  Aspose.Words para .NET: Você precisa ter o Aspose.Words para .NET instalado. Se você ainda não o tem, pegue-o[aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE C# com o qual você se sinta confortável.

## Importar namespaces

Primeiro, você precisa importar os namespaces necessários. Isso é como reunir todas as suas ferramentas antes de começar um projeto.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Agora, vamos detalhar o processo passo a passo.

## Etapa 1: Configurando seu projeto

Antes de podermos criar blocos de código bonitos e formatados em nosso documento do Word, precisamos configurar um novo projeto no Visual Studio.

1. Criar um novo projeto: Abra o Visual Studio e crie um novo aplicativo de console C#.
2. Adicionar Aspose.Words Referência: Instale o Aspose.Words via NuGet Package Manager. Você pode fazer isso clicando com o botão direito do mouse no seu projeto no Solution Explorer, selecionando "Manage NuGet Packages" e pesquisando por Aspose.Words.

## Etapa 2: inicializar o DocumentBuilder

Agora que seu projeto está configurado, vamos inicializar o DocumentBuilder, que será nossa principal ferramenta para adicionar conteúdo ao documento do Word.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Etapa 3: Crie um estilo para código cercado

Para adicionar código fenced, primeiro precisamos criar um estilo. Pense nisso como definir o tema para nosso bloco de código.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Etapa 4: Adicionar código cercado ao documento

Com nosso estilo pronto, agora podemos adicionar um bloco de código cercado ao documento.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Etapa 5: Crie um estilo para código cercado com string de informações

Às vezes, você pode querer especificar a linguagem de programação ou adicionar informações extras ao seu bloco de código. Vamos criar um estilo para isso.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Etapa 6: Adicionar código cercado com sequência de informações ao documento

Agora, vamos adicionar um bloco de código cercado com uma string de informação para indicar que é código C#.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Conclusão

Parabéns! Você acabou de adicionar blocos de código cercados e código cercado com sequências de informações aos seus documentos do Word usando o Aspose.Words para .NET. Esta é apenas a ponta do iceberg. Com o Aspose.Words, você pode automatizar e aprimorar o processamento de seus documentos para novos patamares. Continue explorando e boa codificação!

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca poderosa que permite aos desenvolvedores criar, manipular e converter documentos do Word programaticamente.

### Posso usar o Aspose.Words com outras linguagens de programação?
O Aspose.Words oferece suporte principalmente a linguagens .NET, mas há versões disponíveis para Java, Python e outras linguagens.

### O Aspose.Words é gratuito?
 Aspose.Words é um produto comercial, mas você pode baixar uma versão de avaliação gratuita[aqui](https://releases.aspose.com/)para explorar suas características.

### Como posso obter suporte para o Aspose.Words?
 Você pode obter suporte da comunidade e dos desenvolvedores do Aspose[aqui](https://forum.aspose.com/c/words/8).

### Quais outros recursos o Aspose.Words oferece?
O Aspose.Words oferece uma ampla variedade de recursos, incluindo conversão de documentos, geração de documentos baseada em modelos, relatórios e muito mais.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
