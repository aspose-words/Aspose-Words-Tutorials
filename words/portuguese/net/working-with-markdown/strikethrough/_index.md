---
title: Tachado
linktitle: Tachado
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como aplicar formatação tachado ao texto usando o Aspose.Words para .NET com nosso guia passo a passo. Melhore suas habilidades de processamento de documentos.
weight: 10
url: /pt/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tachado

## Introdução

Bem-vindo a este guia detalhado sobre como aplicar formatação tachada ao texto usando o Aspose.Words para .NET. Se você está procurando aprimorar suas habilidades de processamento de documentos e adicionar um toque único ao seu texto, você está no lugar certo. Vamos mergulhar!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

-  Aspose.Words para .NET: Baixe-o[aqui](https://releases.aspose.com/words/net/).
- .NET Framework: certifique-se de ter o .NET Framework instalado no seu sistema.
- Ambiente de desenvolvimento: Um IDE como o Visual Studio.
- Conhecimento básico de C#: É necessária familiaridade com programação em C#.

## Importar namespaces

Para começar, você precisará importar os namespaces necessários. Eles são essenciais para acessar a biblioteca Aspose.Words e seus recursos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: inicializar o DocumentBuilder

 O`DocumentBuilder` class é uma ferramenta poderosa no Aspose.Words que permite adicionar conteúdo ao seu documento com facilidade.

```csharp
// Inicialize um DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Etapa 2: Definir propriedade de tachado

Agora, vamos aplicar a propriedade strikethrough ao nosso texto. Isso envolve definir o`StrikeThrough` propriedade do`Font` objetar a`true`.

```csharp
// Coloque o texto tachado.
builder.Font.StrikeThrough = true;
```

## Etapa 3: Escreva o texto com tachado

 Com a propriedade strikethrough definida, agora podemos adicionar nosso texto. O`Writeln` O método adicionará o texto ao documento.

```csharp
// Escreva texto com Tachado.
builder.Writeln("This text will be StrikeThrough");
```

## Conclusão

E aí está! Você adicionou com sucesso a formatação tachado ao seu texto usando o Aspose.Words para .NET. Esta biblioteca poderosa abre um mundo de possibilidades para processamento e personalização de documentos. Quer você esteja criando relatórios, cartas ou qualquer outro tipo de documento, dominar esses recursos sem dúvida aumentará sua produtividade e a qualidade de suas saídas.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma poderosa biblioteca de processamento de documentos que permite aos desenvolvedores criar, manipular e converter documentos do Word programaticamente.

### Posso usar o Aspose.Words para .NET em um projeto comercial?
 Sim, você pode usar o Aspose.Words para .NET em projetos comerciais. Para opções de compra, visite o[página de compra](https://purchase.aspose.com/buy).

### Existe uma versão de avaliação gratuita disponível para o Aspose.Words para .NET?
 Sim, você pode baixar uma versão de teste gratuita[aqui](https://releases.aspose.com/).

### Como obtenho suporte para o Aspose.Words para .NET?
Você pode obter suporte da comunidade Aspose e especialistas no[fórum de suporte](https://forum.aspose.com/c/words/8).

### Posso aplicar outras opções de formatação de texto usando o Aspose.Words para .NET?
Com certeza! O Aspose.Words for .NET suporta uma ampla gama de opções de formatação de texto, incluindo negrito, itálico, sublinhado e muito mais.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
