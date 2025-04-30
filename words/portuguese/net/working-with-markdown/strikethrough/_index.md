---
"description": "Aprenda a aplicar a formatação tachada ao texto usando o Aspose.Words para .NET com nosso guia passo a passo. Aprimore suas habilidades de processamento de documentos."
"linktitle": "Tachado"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Tachado"
"url": "/pt/net/working-with-markdown/strikethrough/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tachado

## Introdução

Bem-vindo a este guia detalhado sobre como aplicar a formatação tachada a textos usando o Aspose.Words para .NET. Se você busca aprimorar suas habilidades de processamento de documentos e adicionar um toque único ao seu texto, está no lugar certo. Vamos lá!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

- Aspose.Words para .NET: Baixe [aqui](https://releases.aspose.com/words/net/).
- .NET Framework: certifique-se de ter o .NET Framework instalado no seu sistema.
- Ambiente de desenvolvimento: um IDE como o Visual Studio.
- Conhecimento básico de C#: É necessária familiaridade com programação em C#.

## Importar namespaces

Para começar, você precisará importar os namespaces necessários. Eles são essenciais para acessar a biblioteca Aspose.Words e seus recursos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: inicializar o DocumentBuilder

O `DocumentBuilder` class é uma ferramenta poderosa no Aspose.Words que permite adicionar conteúdo ao seu documento com facilidade.

```csharp
// Inicialize um DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Etapa 2: definir propriedade tachado

Agora, vamos aplicar a propriedade tachado ao nosso texto. Isso envolve definir a `StrikeThrough` propriedade do `Font` objetar a `true`.

```csharp
// Coloque o texto tachado.
builder.Font.StrikeThrough = true;
```

## Etapa 3: Escreva o texto com tachado

Com a propriedade tachado definida, agora podemos adicionar nosso texto. `Writeln` O método adicionará o texto ao documento.

```csharp
// Escreva o texto com Tachado.
builder.Writeln("This text will be StrikeThrough");
```

## Conclusão

E pronto! Você adicionou com sucesso a formatação tachado ao seu texto usando o Aspose.Words para .NET. Esta poderosa biblioteca abre um mundo de possibilidades para o processamento e personalização de documentos. Seja para criar relatórios, cartas ou qualquer outro tipo de documento, dominar esses recursos certamente aumentará sua produtividade e a qualidade dos seus resultados.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma poderosa biblioteca de processamento de documentos que permite aos desenvolvedores criar, manipular e converter documentos do Word programaticamente.

### Posso usar o Aspose.Words para .NET em um projeto comercial?
Sim, você pode usar o Aspose.Words para .NET em projetos comerciais. Para opções de compra, visite o site [página de compra](https://purchase.aspose.com/buy).

### Existe uma avaliação gratuita disponível do Aspose.Words para .NET?
Sim, você pode baixar uma versão de teste gratuita [aqui](https://releases.aspose.com/).

### Como obtenho suporte para o Aspose.Words para .NET?
Você pode obter suporte da comunidade Aspose e especialistas no [fórum de suporte](https://forum.aspose.com/c/words/8).

### Posso aplicar outras opções de formatação de texto usando o Aspose.Words para .NET?
Com certeza! O Aspose.Words para .NET suporta uma ampla gama de opções de formatação de texto, incluindo negrito, itálico, sublinhado e muito mais.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}