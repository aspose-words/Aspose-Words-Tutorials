---
"description": "Aprenda como mostrar e ocultar conteúdo marcado em documentos do Word usando o Aspose.Words para .NET com este guia detalhado passo a passo."
"linktitle": "Mostrar Ocultar Conteúdo Marcado em Documento do Word"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Mostrar Ocultar Conteúdo Marcado em Documento do Word"
"url": "/pt/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mostrar Ocultar Conteúdo Marcado em Documento do Word

## Introdução

Pronto para mergulhar no mundo da manipulação de documentos com o Aspose.Words para .NET? Seja você um desenvolvedor que busca automatizar tarefas com documentos ou apenas alguém curioso sobre como manipular arquivos do Word programaticamente, você está no lugar certo. Hoje, exploraremos como mostrar e ocultar conteúdo marcado em um documento do Word usando o Aspose.Words para .NET. Este guia passo a passo tornará você um especialista em controlar a visibilidade do conteúdo com base em marcadores. Vamos começar!

## Pré-requisitos

Antes de começarmos com o essencial, você vai precisar de algumas coisas:

1. Visual Studio: Qualquer versão compatível com .NET.
2. Aspose.Words para .NET: Baixe [aqui](https://releases.aspose.com/words/net/).
3. Noções básicas de C#: Se você consegue escrever um programa simples "Olá, Mundo", está pronto para começar.
4. Um documento do Word com marcadores: usaremos um documento de exemplo com marcadores para este tutorial.

## Importar namespaces

Primeiramente, vamos importar os namespaces necessários. Isso garante que tenhamos todas as ferramentas necessárias para nossa tarefa.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Com esses namespaces definidos, estamos prontos para começar nossa jornada.

## Etapa 1: Configurando seu projeto

Tudo bem, vamos começar configurando nosso projeto no Visual Studio.

### Criar um novo projeto

Abra o Visual Studio e crie um novo projeto de Aplicativo de Console (.NET Core). Dê a ele um nome chamativo, como "BookmarkVisibilityManager".

### Adicione Aspose.Words para .NET

Você precisará adicionar o Aspose.Words para .NET ao seu projeto. Isso pode ser feito por meio do Gerenciador de Pacotes NuGet.

1. Acesse Ferramentas > Gerenciador de Pacotes NuGet > Gerenciar Pacotes NuGet para Solução.
2. Pesquise por "Aspose.Words".
3. Instale o pacote.

Ótimo! Agora que nosso projeto está configurado, vamos prosseguir com o carregamento do documento.

## Etapa 2: Carregando o documento

Precisamos carregar o documento do Word que contém os favoritos. Para este tutorial, usaremos um documento de exemplo chamado "Bookmarks.docx".

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Este trecho de código define o caminho para o diretório do documento e carrega o documento no `doc` objeto.

## Etapa 3: Mostrar/Ocultar conteúdo marcado

Agora vem a parte divertida – mostrar ou ocultar o conteúdo com base nos favoritos. Vamos criar um método chamado `ShowHideBookmarkedContent` para lidar com isso.

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

- Recuperação de favoritos: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` busca o marcador.
- Percurso de nós: percorremos os nós dentro do marcador.
- Alternância de visibilidade: se o nó for um `Run` (uma sequência contígua de texto), definimos seu `Hidden` propriedade.

## Etapa 4: Aplicando o Método

Com nosso método em vigor, vamos aplicá-lo para mostrar ou ocultar conteúdo com base em um marcador.

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

E pronto! Você acabou de aprender a mostrar e ocultar conteúdo marcado em um documento do Word usando o Aspose.Words para .NET. Esta ferramenta poderosa facilita a manipulação de documentos, seja para automatizar relatórios, criar modelos ou apenas mexer em arquivos do Word. Boa programação!

## Perguntas frequentes

### Posso alternar vários favoritos de uma só vez?
Sim, você pode ligar para o `ShowHideBookmarkedContent` método para cada marcador que você deseja alternar.

### Ocultar conteúdo afeta a estrutura do documento?
Não, ocultar conteúdo afeta apenas sua visibilidade. O conteúdo permanece no documento.

### Posso usar esse método para outros tipos de conteúdo?
Este método alterna especificamente a execução de texto. Para outros tipos de conteúdo, você precisará modificar a lógica de travessia de nós.

### Aspose.Words para .NET é gratuito?
Aspose.Words oferece um teste gratuito [aqui](https://releases.aspose.com/), mas é necessária uma licença completa para uso em produção. Você pode comprá-lo [aqui](https://purchase.aspose.com/buy).

### Como posso obter suporte se tiver problemas?
Você pode obter suporte da comunidade Aspose [aqui](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}