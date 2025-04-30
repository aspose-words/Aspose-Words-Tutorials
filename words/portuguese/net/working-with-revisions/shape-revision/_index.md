---
"description": "Aprenda a lidar com revisões de formas em documentos do Word usando o Aspose.Words para .NET com este guia completo. Domine o controle de alterações, a inserção de formas e muito mais."
"linktitle": "Revisão de forma"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Revisão de forma"
"url": "/pt/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Revisão de forma

## Introdução

Editar documentos do Word programaticamente pode ser uma tarefa desafiadora, especialmente quando se trata de lidar com formas. Seja criando relatórios, projetando modelos ou simplesmente automatizando a criação de documentos, a capacidade de rastrear e gerenciar revisões de formas é crucial. O Aspose.Words para .NET oferece uma API poderosa para tornar esse processo simples e eficiente. Neste tutorial, abordaremos os detalhes da revisão de formas em documentos do Word, garantindo que você tenha as ferramentas e o conhecimento necessários para gerenciar seus documentos com facilidade.

## Pré-requisitos

Antes de mergulharmos no código, vamos garantir que você tenha tudo o que precisa:

- Aspose.Words para .NET: Certifique-se de ter a biblioteca Aspose.Words instalada. Você pode [baixe aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: você deve ter um ambiente de desenvolvimento configurado, como o Visual Studio.
- Noções básicas de C#: familiaridade com a linguagem de programação C# e conceitos básicos de programação orientada a objetos.
- Documento do Word: um documento do Word para trabalhar ou você pode criar um durante o tutorial.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Eles nos darão acesso às classes e métodos necessários para manipular documentos e formas do Word.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Etapa 1: Configurando seu diretório de documentos

Antes de começarmos a trabalhar com as formas, precisamos definir o caminho para o diretório do nosso documento. É lá que salvaremos os documentos modificados.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Criando um novo documento

Vamos criar um novo documento do Word onde inseriremos e revisaremos formas.

```csharp
Document doc = new Document();
```

## Etapa 3: Inserindo uma forma embutida

Começaremos inserindo uma forma embutida no nosso documento sem rastrear revisões. Uma forma embutida é aquela que flui com o texto.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Etapa 4: Começando a rastrear revisões

Para rastrear alterações em nosso documento, precisamos habilitar o rastreamento de revisões. Isso é essencial para identificar modificações feitas em formas.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Etapa 5: Inserindo outra forma com revisões

Agora que o rastreamento de revisões está habilitado, vamos inserir outra forma. Desta vez, todas as alterações serão rastreadas.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Etapa 6: Recuperando e modificando formas

Podemos recuperar todas as formas do documento e modificá-las conforme necessário. Aqui, obteremos as formas e removeremos a primeira.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Etapa 7: Salvando o documento

Após fazer as alterações, precisamos salvar o documento. Isso garante que todas as revisões e modificações sejam armazenadas.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Etapa 8: Lidando com revisões de movimento de forma

Quando uma forma é movida, o Aspose.Words rastreia isso como uma revisão. Isso significa que haverá duas instâncias da forma: uma em seu local original e outra em seu novo local.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Conclusão

pronto! Você aprendeu com sucesso a lidar com revisões de formas em documentos do Word usando o Aspose.Words para .NET. Seja gerenciando modelos de documentos, automatizando relatórios ou simplesmente acompanhando alterações, essas habilidades são inestimáveis. Seguindo este guia passo a passo, você não apenas dominou o básico, como também adquiriu insights sobre técnicas mais avançadas de tratamento de documentos.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca poderosa que permite aos desenvolvedores criar, modificar e converter documentos do Word programaticamente usando C#.

### Posso rastrear alterações feitas em outros elementos em um documento do Word?
Sim, o Aspose.Words para .NET suporta o rastreamento de alterações em vários elementos, incluindo texto, tabelas e muito mais.

### Como posso obter uma avaliação gratuita do Aspose.Words para .NET?
Você pode obter uma avaliação gratuita do Aspose.Words para .NET [aqui](https://releases.aspose.com/).

### É possível aceitar ou rejeitar revisões programaticamente?
Sim, o Aspose.Words para .NET fornece métodos para aceitar ou rejeitar revisões programaticamente.

### Posso usar o Aspose.Words para .NET com outras linguagens .NET além de C#?
Com certeza! O Aspose.Words para .NET pode ser usado com qualquer linguagem .NET, incluindo VB.NET e F#.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}