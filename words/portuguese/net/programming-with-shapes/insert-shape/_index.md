---
title: Inserir forma
linktitle: Inserir forma
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a inserir e manipular formas em documentos do Word usando o Aspose.Words para .NET com nosso guia passo a passo.
weight: 10
url: /pt/net/programming-with-shapes/insert-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir forma

## Introdução

Quando se trata de criar documentos do Word visualmente atraentes e bem estruturados, as formas podem desempenhar um papel vital. Não importa se você está adicionando setas, caixas ou até mesmo formas personalizadas complexas, a capacidade de manipular esses elementos programaticamente oferece flexibilidade inigualável. Neste tutorial, exploraremos como inserir e manipular formas em documentos do Word usando o Aspose.Words para .NET.

## Pré-requisitos

Antes de mergulhar no tutorial, certifique-se de ter os seguintes pré-requisitos:

1.  Aspose.Words para .NET: Baixe e instale a versão mais recente do[Página de lançamentos da Aspose](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Um ambiente de desenvolvimento .NET adequado, como o Visual Studio.
3. Conhecimento básico de C#: Familiaridade com a linguagem de programação C# e conceitos básicos.

## Importar namespaces

Para começar, você precisará importar os namespaces necessários no seu projeto C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Etapa 1: configure seu projeto

Antes de começar a inserir formas, você precisa configurar seu projeto e adicionar a biblioteca Aspose.Words for .NET.

1. Criar um novo projeto: Abra o Visual Studio e crie um novo projeto de aplicativo de console C#.
2. Adicionar Aspose.Words para .NET: Instale a biblioteca Aspose.Words para .NET por meio do Gerenciador de Pacotes NuGet.

```bash
Install-Package Aspose.Words
```

## Etapa 2: Inicializar o documento

Primeiro, você precisará inicializar um novo documento e um construtor de documentos, que ajudará na construção do documento.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inicializar um novo documento
Document doc = new Document();

// Inicialize um DocumentBuilder para ajudar a construir o documento
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 3: Insira uma forma

Agora, vamos inserir uma forma no documento. Começaremos adicionando uma caixa de texto simples.

```csharp
// Insira uma forma de caixa de texto no documento
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Gire a forma
shape.Rotation = 30.0;
```

Neste exemplo, inserimos uma caixa de texto na posição (100, 100) com largura e altura de 50 unidades cada. Também giramos a forma em 30 graus.

## Etapa 4: adicione outra forma

Vamos adicionar outra forma ao documento, desta vez sem especificar a posição.

```csharp
// Adicionar outra forma de caixa de texto
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Gire a forma
secondShape.Rotation = 30.0;
```

Este trecho de código insere outra caixa de texto com as mesmas dimensões e rotação da primeira, mas sem especificar sua posição.

## Etapa 5: Salve o documento

 Após adicionar as formas, o passo final é salvar o documento. Usaremos o`OoxmlSaveOptions` para especificar o formato de salvamento.

```csharp
// Defina opções de salvamento com conformidade
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Salvar o documento
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Conclusão

E aí está! Você inseriu e manipulou formas com sucesso em um documento do Word usando o Aspose.Words para .NET. Este tutorial cobriu o básico, mas o Aspose.Words oferece muitos recursos mais avançados para trabalhar com formas, como estilos personalizados, conectores e formas de grupo.

 Para obter informações mais detalhadas, visite o[Aspose.Words para documentação .NET](https://reference.aspose.com/words/net/).

## Perguntas frequentes

### Como faço para inserir diferentes tipos de formas?
Você pode mudar o`ShapeType` no`InsertShape` método para inserir diferentes tipos de formas, como círculos, retângulos e setas.

### Posso adicionar texto dentro das formas?
 Sim, você pode usar o`builder.Write` método para adicionar texto dentro das formas depois de inseri-las.

### É possível estilizar as formas?
 Sim, você pode estilizar as formas definindo propriedades como`FillColor`, `StrokeColor` , e`StrokeWeight`.

### Como posiciono formas em relação a outros elementos?
 Use o`RelativeHorizontalPosition` e`RelativeVerticalPosition` propriedades para posicionar formas em relação a outros elementos no documento.

### Posso agrupar várias formas?
 Sim, o Aspose.Words para .NET permite que você agrupe formas usando o`GroupShape` aula.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
