---
title: Adicionar texto marcado em documento do Word
linktitle: Adicionar texto marcado em documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como anexar texto marcado em um documento do Word usando Aspose.Words para .NET com este guia passo a passo. Perfeito para desenvolvedores.
weight: 10
url: /pt/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar texto marcado em documento do Word

## Introdução

Olá! Já tentou anexar texto de uma seção marcada em um documento do Word e achou complicado? Você está com sorte! Este tutorial o guiará pelo processo usando o Aspose.Words para .NET. Vamos dividi-lo em etapas simples para que você possa acompanhar facilmente. Vamos mergulhar e anexar esse texto marcado como um profissional!

## Pré-requisitos

Antes de começar, vamos garantir que você tenha tudo o que precisa:

-  Aspose.Words para .NET: Certifique-se de que você o tenha instalado. Se não, você pode[baixe aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: qualquer ambiente de desenvolvimento .NET, como o Visual Studio.
- Conhecimento básico de C#: entender os conceitos básicos de programação em C# ajudará.
- Documento do Word com marcadores: Um documento do Word com marcadores configurados, que usaremos para anexar texto.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Isso garantirá que tenhamos todas as ferramentas que precisamos na ponta dos dedos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Vamos dividir o exemplo em etapas detalhadas.

## Etapa 1: Carregue o documento e inicialize as variáveis

Tudo bem, vamos começar carregando nosso documento do Word e inicializando as variáveis que precisaremos.

```csharp
// Carregue os documentos de origem e destino.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inicialize o importador de documentos.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Encontre o marcador no documento de origem.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Etapa 2: Identifique os parágrafos inicial e final

Agora, vamos localizar os parágrafos onde o marcador começa e termina. Isso é crucial, pois precisamos lidar com o texto dentro desses limites.

```csharp
// Este é o parágrafo que contém o início do marcador.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Este é o parágrafo que contém o final do marcador.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Etapa 3: Validar os pais do parágrafo

Precisamos garantir que os parágrafos inicial e final tenham o mesmo pai. Este é um cenário simples para manter as coisas diretas.

```csharp
// Vamos nos limitar a um cenário razoavelmente simples.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Etapa 4: Identifique o nó a ser interrompido

Em seguida, precisamos determinar o nó onde pararemos de copiar o texto. Este será o nó imediatamente após o parágrafo final.

```csharp
// Queremos copiar todos os parágrafos desde o parágrafo inicial até (e incluindo) o parágrafo final,
// portanto, o nó em que paramos é aquele após o parágrafo final.
Node endNode = endPara.NextSibling;
```

## Etapa 5: Anexar texto marcado ao documento de destino

Por fim, vamos percorrer os nós do parágrafo inicial até o nó após o parágrafo final e anexá-los ao documento de destino.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Isso cria uma cópia do nó atual e o importa (o torna válido) no contexto
    // do documento de destino. Importar significa ajustar estilos e identificadores de lista corretamente.
    Node newNode = importer.ImportNode(curNode, true);

    // Anexe o nó importado ao documento de destino.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Salve o documento de destino com o texto anexado.
dstDoc.Save("appended_document.docx");
```

## Conclusão

E aí está! Você anexou com sucesso o texto de uma seção marcada em um documento do Word usando o Aspose.Words para .NET. Esta ferramenta poderosa torna a manipulação de documentos uma moleza, e agora você tem mais um truque na manga. Boa codificação!

## Perguntas frequentes

### Posso anexar texto de vários favoritos de uma só vez?
Sim, você pode repetir o processo para cada marcador e acrescentar o texto adequadamente.

### E se os parágrafos inicial e final tiverem pais diferentes?
exemplo atual assume que eles têm o mesmo pai. Para pais diferentes, um tratamento mais complexo é necessário.

### Posso manter a formatação original do texto anexado?
 Absolutamente! O`ImportFormatMode.KeepSourceFormatting` garante que a formatação original seja preservada.

### É possível anexar texto a uma posição específica no documento de destino?
Sim, você pode anexar o texto a qualquer posição navegando até o nó desejado no documento de destino.

### E se eu precisar anexar texto de um favorito a uma nova seção?
Você pode criar uma nova seção no documento de destino e anexar o texto lá.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
