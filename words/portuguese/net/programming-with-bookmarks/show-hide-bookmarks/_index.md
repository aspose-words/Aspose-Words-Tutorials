---
title: Mostrar ocultar marcadores em documento do Word
linktitle: Mostrar ocultar marcadores em documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como mostrar ou ocultar marcadores dinamicamente em um documento do Word usando Aspose.Words for .NET com nosso guia passo a passo. Perfeito para desenvolvedores.
weight: 10
url: /pt/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mostrar ocultar marcadores em documento do Word

## Introdução

Você já precisou ocultar ou mostrar determinadas partes do seu documento do Word de forma dinâmica? Bem, você está com sorte! Com Aspose.Words for .NET, você pode gerenciar facilmente a visibilidade do conteúdo marcado em seus documentos. Este tutorial irá orientá-lo no processo de mostrar e ocultar marcadores em um documento do Word usando Aspose.Words for .NET. Detalharemos o código passo a passo, portanto, seja você um desenvolvedor experiente ou um novato, achará este guia fácil de seguir.

## Pré-requisitos

Antes de mergulharmos no código, vamos ter certeza de que você tem tudo o que precisa:

1.  Aspose.Words for .NET: Certifique-se de ter a biblioteca Aspose.Words for .NET instalada. Se não, você pode baixá-lo[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: um IDE como o Visual Studio.
3. Conhecimento básico de C#: Familiaridade com programação C# será benéfica.
4. Um documento do Word: um exemplo de documento do Word com marcadores.

## Importar namespaces

Antes de começar com o código, você precisa importar os namespaces necessários. Adicione o seguinte no início do seu arquivo C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Etapa 1: carregue seu documento

Em primeiro lugar, você precisa carregar o documento do Word que contém os favoritos. Veja como você pode fazer isso:

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Explicação

- dataDir: Este é o caminho do diretório onde seu documento do Word está localizado.
-  Documento doc: Isso inicializa uma nova instância do`Document` class com seu arquivo especificado.

## Etapa 2: mostrar ou ocultar conteúdo marcado

A seguir, definiremos um método para mostrar ou ocultar o conteúdo marcado. Aqui está o método completo:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{marcador MERGEFIELD}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Explicação

- Marcador bm: busca o marcador do documento.
- Construtor DocumentBuilder: Ajuda na navegação e modificação do documento.
- Campo campo: Insere um campo IF para verificar a condição do marcador.
- Nó currentNode: percorre os nós para encontrar o início e o fim do campo.

## Etapa 3: execute a função Mostrar/Ocultar

 Agora você precisa ligar para o`ShowHideBookmarkedContent` método, passando o documento, o nome do marcador e o sinalizador de visibilidade:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Explicação

- doc: Seu objeto de documento.
- "MyBookmark1": O nome do favorito que você deseja mostrar/ocultar.
- false: O sinalizador de visibilidade (verdadeiro para mostrar, falso para ocultar).

## Etapa 4: salve seu documento

Por fim, salve o documento modificado:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Explicação

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": O caminho e o nome do novo documento onde as alterações serão salvas.

## Conclusão

E aí está! Você aprendeu com sucesso como mostrar e ocultar marcadores em um documento do Word usando Aspose.Words for .NET. Esta técnica pode ser extremamente útil para gerar documentos dinamicamente com conteúdo condicional.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words for .NET é uma poderosa biblioteca de processamento de documentos que permite aos desenvolvedores criar, modificar e converter documentos do Word programaticamente.

### Como obtenho o Aspose.Words para .NET?
 Você pode baixar Aspose.Words para .NET em[aqui](https://releases.aspose.com/words/net/). Um teste gratuito também está disponível.

### Posso usar este método para outros tipos de marcadores?
Sim, este método pode ser adaptado para gerenciar a visibilidade de quaisquer marcadores em seu documento do Word.

### E se o meu documento não contiver o marcador especificado?
Se o marcador não existir, o método gerará um erro. Certifique-se de que o marcador exista antes de tentar mostrá-lo/ocultá-lo.

### Como posso obter suporte se encontrar problemas?
 Você pode obter suporte da comunidade Aspose[aqui](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
