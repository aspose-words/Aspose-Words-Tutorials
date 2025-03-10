---
title: Criar marcador em documento do Word
linktitle: Criar marcador em documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a criar marcadores em documentos do Word usando o Aspose.Words para .NET com este guia detalhado passo a passo. Perfeito para navegação e organização de documentos.
weight: 10
url: /pt/net/programming-with-bookmarks/create-bookmark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar marcador em documento do Word

## Introdução

Criar marcadores em um documento do Word pode mudar o jogo, especialmente quando você quer navegar por documentos grandes sem esforço. Hoje, vamos percorrer o processo de criação de marcadores usando o Aspose.Words para .NET. Este tutorial o levará passo a passo, garantindo que você entenda cada parte do processo. Então, vamos mergulhar de cabeça!

## Pré-requisitos

Antes de começar, você precisa ter o seguinte:

1.  Biblioteca Aspose.Words para .NET: Baixe e instale em[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Visual Studio ou qualquer outro ambiente de desenvolvimento .NET.
3. Conhecimento básico de C#: Compreensão dos conceitos básicos de programação em C#.

## Importar namespaces

Para trabalhar com o Aspose.Words para .NET, você precisa importar os namespaces necessários:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: Configurar o documento e o DocumentBuilder

Inicializar o documento

Primeiro, precisamos criar um novo documento e inicializá-lo`DocumentBuilder`. Este é o ponto de partida para adicionar conteúdo e marcadores ao seu documento.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Explicação: O`Document` objeto é sua tela. O`DocumentBuilder` é como sua caneta, que permite que você escreva conteúdo e crie marcadores no documento.

## Etapa 2: Crie o marcador principal

Iniciar e terminar o marcador principal

Para criar um marcador, você precisa especificar os pontos inicial e final. Aqui, criaremos um marcador chamado "My Bookmark".

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

 Explicação: O`StartBookmark` o método marca o início do marcador e`Writeln` adiciona texto dentro do marcador.

## Etapa 3: Crie um marcador aninhado

Adicionar marcador aninhado dentro do marcador principal

Você pode aninhar marcadores dentro de outros marcadores. Aqui, adicionamos "Marcador aninhado" dentro de "Meu marcador".

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

 Explicação: Aninhar marcadores permite uma organização de conteúdo mais estruturada e hierárquica. O`EndBookmark` método fecha o marcador atual.

## Etapa 4: adicione texto fora do marcador aninhado

Continuar adicionando conteúdo

Após o marcador aninhado, podemos continuar adicionando mais conteúdo dentro do marcador principal.

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

Explicação: Isso garante que o marcador principal englobe tanto o marcador aninhado quanto o texto adicional.

## Etapa 5: Configurar opções de salvamento de PDF

Configurar opções de salvamento de PDF para favoritos

Ao salvar o documento como PDF, podemos configurar opções para incluir marcadores.

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

 Explicação: O`PdfSaveOptions` A classe permite que você especifique como o documento deve ser salvo como PDF. A`BookmarksOutlineLevels` propriedade define a hierarquia dos marcadores no PDF.

## Etapa 6: Salve o documento

Salvar o documento como PDF

Por fim, salve o documento com as opções especificadas.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

 Explicação: O`Save` método salva o documento no formato e local especificados. O PDF agora incluirá os marcadores que criamos.

## Conclusão

Criar marcadores em um documento do Word usando o Aspose.Words para .NET é simples e imensamente útil para navegação e organização de documentos. Não importa se você está gerando relatórios, criando eBooks ou gerenciando documentos grandes, os marcadores facilitam a vida. Siga as etapas descritas neste tutorial e você terá um PDF marcado pronto em pouco tempo.

## Perguntas frequentes

### Posso criar vários favoritos em níveis diferentes?

Absolutamente! Você pode criar quantos marcadores forem necessários e definir seus níveis hierárquicos ao salvar o documento como PDF.

### Como atualizo o texto de um favorito?

 Você pode navegar até o marcador usando`DocumentBuilder.MoveToBookmark` e então atualize o texto.

### É possível excluir um favorito?

 Sim, você pode excluir um favorito usando o`Bookmarks.Remove` método especificando o nome do marcador.

### Posso criar favoritos em outros formatos além de PDF?

Sim, o Aspose.Words suporta marcadores em vários formatos, incluindo DOCX, HTML e EPUB.

### Como posso garantir que os marcadores apareçam corretamente no PDF?

 Certifique-se de definir o`BookmarksOutlineLevels` corretamente no`PdfSaveOptions`. Isso garante que os marcadores sejam incluídos no esboço do PDF.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
