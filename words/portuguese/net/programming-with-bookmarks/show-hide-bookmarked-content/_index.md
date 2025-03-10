---
title: Mostrar Ocultar Conteúdo Marcado em Documento Word
linktitle: Mostrar Ocultar Conteúdo Marcado em Documento Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como mostrar e ocultar conteúdo marcado em documentos do Word usando o Aspose.Words para .NET com este guia detalhado passo a passo.
weight: 10
url: /pt/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mostrar Ocultar Conteúdo Marcado em Documento Word

## Introdução

Pronto para mergulhar no mundo da manipulação de documentos com o Aspose.Words para .NET? Seja você um desenvolvedor procurando automatizar tarefas de documentos ou apenas alguém curioso sobre como manipular arquivos do Word programaticamente, você está no lugar certo. Hoje, exploraremos como mostrar e ocultar conteúdo marcado em um documento do Word usando o Aspose.Words para .NET. Este guia passo a passo fará de você um profissional no controle da visibilidade do conteúdo com base em marcadores. Vamos começar!

## Pré-requisitos

Antes de começarmos, há algumas coisas que você vai precisar:

1. Visual Studio: Qualquer versão compatível com .NET.
2.  Aspose.Words para .NET: Baixe-o[aqui](https://releases.aspose.com/words/net/).
3. Noções básicas de C#: Se você consegue escrever um programa simples "Hello World", está pronto para começar.
4. Um documento do Word com marcadores: usaremos um documento de exemplo com marcadores para este tutorial.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Isso garante que temos todas as ferramentas necessárias para nossa tarefa.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Com esses namespaces definidos, estamos prontos para começar nossa jornada.

## Etapa 1: Configurando seu projeto

Tudo bem, vamos começar configurando nosso projeto no Visual Studio.

### Criar um novo projeto

Abra o Visual Studio e crie um novo projeto Console App (.NET Core). Dê a ele um nome chamativo, como "BookmarkVisibilityManager".

### Adicionar Aspose.Words para .NET

Você precisará adicionar Aspose.Words for .NET ao seu projeto. Você pode fazer isso por meio do NuGet Package Manager.

1. Vá para Ferramentas > Gerenciador de Pacotes NuGet > Gerenciar Pacotes NuGet para Solução.
2. Pesquise por "Aspose.Words".
3. Instale o pacote.

Ótimo! Agora que nosso projeto está configurado, vamos prosseguir para carregar nosso documento.

## Etapa 2: Carregando o documento

Precisamos carregar o documento do Word que contém os marcadores. Para este tutorial, usaremos um documento de exemplo chamado "Bookmarks.docx".

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Este trecho de código define o caminho para o diretório do seu documento e carrega o documento no`doc` objeto.

## Etapa 3: Mostrar/Ocultar conteúdo marcado

Agora vem a parte divertida – mostrar ou ocultar o conteúdo com base nos favoritos. Vamos criar um método chamado`ShowHideBookmarkedContent` para lidar com isso.

Este é o método que alternará a visibilidade do conteúdo marcado:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Análise do Método

-  Recuperação de favoritos:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` busca o marcador.
- Percurso de nós: Percorremos os nós dentro do marcador.
-  Alternância de visibilidade: se o nó for um`Run` (uma sequência contígua de texto), definimos seu`Hidden` propriedade.

## Etapa 4: Aplicando o método

Com nosso método em prática, vamos aplicá-lo para mostrar ou ocultar conteúdo com base em um favorito.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Esta linha de código ocultará o conteúdo dentro do marcador chamado "MyBookmark1".

## Etapa 5: Salvando o documento

Por fim, vamos salvar nosso documento modificado.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Isso salva o documento com as alterações que fizemos.

## Conclusão

aí está! Você acabou de aprender como mostrar e ocultar conteúdo marcado em um documento do Word usando o Aspose.Words para .NET. Esta ferramenta poderosa torna a manipulação de documentos uma brisa, seja automatizando relatórios, criando modelos ou apenas mexendo com arquivos do Word. Boa codificação!

## Perguntas frequentes

### Posso alternar vários favoritos de uma só vez?
 Sim, você pode ligar para o`ShowHideBookmarkedContent` método para cada marcador que você deseja alternar.

### Ocultar conteúdo afeta a estrutura do documento?
Não, ocultar conteúdo afeta apenas sua visibilidade. O conteúdo permanece no documento.

### Posso usar esse método para outros tipos de conteúdo?
Este método alterna especificamente as execuções de texto. Para outros tipos de conteúdo, você precisará modificar a lógica de travessia do nó.

### O Aspose.Words para .NET é gratuito?
 Aspose.Words oferece um teste gratuito[aqui](https://releases.aspose.com/) , mas uma licença completa é necessária para uso em produção. Você pode comprá-lo[aqui](https://purchase.aspose.com/buy).

### Como posso obter suporte se tiver problemas?
 Você pode obter suporte da comunidade Aspose[aqui](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
