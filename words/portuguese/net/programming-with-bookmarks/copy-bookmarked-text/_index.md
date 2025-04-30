---
"description": "Copie facilmente textos marcados entre documentos do Word usando o Aspose.Words para .NET. Aprenda como com este guia passo a passo."
"linktitle": "Copiar texto marcado em documento do Word"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Copiar texto marcado em documento do Word"
"url": "/pt/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Copiar texto marcado em documento do Word

## Introdução

Já se viu precisando copiar seções específicas de um documento do Word para outro? Bem, você está com sorte! Neste tutorial, mostraremos como copiar texto marcado de um documento do Word para outro usando o Aspose.Words para .NET. Seja para criar um relatório dinâmico ou automatizar a geração de documentos, este guia simplificará o processo para você.

## Pré-requisitos

Antes de começarmos, certifique-se de ter o seguinte:

- Biblioteca Aspose.Words para .NET: Você pode baixá-la em [aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: Visual Studio ou qualquer outro ambiente de desenvolvimento .NET.
- Conhecimento básico de C#: familiaridade com programação em C# e framework .NET.

## Importar namespaces

Para começar, certifique-se de ter os namespaces necessários importados no seu projeto:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Etapa 1: Carregue o documento de origem

Primeiro, você precisa carregar o documento de origem que contém o texto marcado que você deseja copiar.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

Aqui, `dataDir` é o caminho para o diretório do seu documento e `Bookmarks.docx` é o documento de origem.

## Etapa 2: Identifique o marcador

Em seguida, identifique o marcador que você deseja copiar do documento de origem.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

Substituir `"MyBookmark1"` com o nome real do seu marcador.

## Etapa 3: Crie o Documento de Destino

Agora, crie um novo documento onde o texto marcado será copiado.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Etapa 4: Importar conteúdo marcado

Para garantir que os estilos e a formatação sejam preservados, use `NodeImporter` para importar o conteúdo marcado do documento de origem para o documento de destino.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Etapa 5: Defina o método AppendBookmarkedText

É aqui que a mágica acontece. Defina um método para lidar com a cópia do texto marcado:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Etapa 6: Salve o documento de destino

Por fim, salve o documento de destino para verificar o conteúdo copiado.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Conclusão

pronto! Você copiou com sucesso o texto marcado de um documento do Word para outro usando o Aspose.Words para .NET. Este método é poderoso para automatizar tarefas de manipulação de documentos, tornando seu fluxo de trabalho mais eficiente e simplificado.

## Perguntas frequentes

### Posso copiar vários favoritos de uma vez?
Sim, você pode iterar por vários favoritos e usar o mesmo método para copiar cada um.

### O que acontece se o marcador não for encontrado?
O `Range.Bookmarks` a propriedade retornará `null`, portanto, certifique-se de lidar com esse caso para evitar exceções.

### Posso preservar a formatação do marcador original?
Com certeza! Usando `ImportFormatMode.KeepSourceFormatting` garante que a formatação original seja preservada.

### Existe um limite para o tamanho do texto marcado?
Não há limite específico, mas o desempenho pode variar com documentos extremamente grandes.

### Posso copiar texto entre diferentes formatos de documentos do Word?
Sim, o Aspose.Words suporta vários formatos do Word, e o método funciona em todos esses formatos.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}