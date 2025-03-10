---
title: Inserir documento em substituir
linktitle: Inserir documento em substituir
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como inserir perfeitamente um documento do Word em outro usando o Aspose.Words para .NET com nosso guia detalhado passo a passo. Perfeito para desenvolvedores que buscam agilizar o processamento de documentos.
weight: 10
url: /pt/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir documento em substituir

## Introdução

Olá, mestres dos documentos! Já se viu atolado em código, tentando descobrir como inserir um documento do Word em outro perfeitamente? Não tema, porque hoje estamos mergulhando no mundo do Aspose.Words para .NET para tornar essa tarefa fácil. Vamos percorrer um guia detalhado passo a passo sobre como usar essa biblioteca poderosa para inserir documentos em pontos específicos durante uma operação de localizar e substituir. Pronto para se tornar um mago do Aspose.Words? Vamos começar!

## Pré-requisitos

Antes de começarmos a usar o código, há algumas coisas que você precisa ter em mente:

-  Visual Studio: Certifique-se de ter o Visual Studio instalado em sua máquina. Se você ainda não o tem, você pode baixá-lo em[aqui](https://visualstudio.microsoft.com/).
-  Aspose.Words para .NET: Você precisará da biblioteca Aspose.Words. Você pode obtê-la em[Site Aspose](https://releases.aspose.com/words/net/).
- Conhecimento básico de C#: um conhecimento básico de C# e .NET ajudará você a acompanhar este tutorial.

Certo, com isso resolvido, vamos colocar a mão na massa com algum código!

## Importar namespaces

Primeiro, precisamos importar os namespaces necessários para trabalhar com Aspose.Words. Isso é como reunir todas as suas ferramentas antes de começar um projeto. Adicione essas diretivas using no topo do seu arquivo C#:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Agora que temos nossos pré-requisitos em vigor, vamos dividir o processo em etapas pequenas. Cada etapa é crucial e nos deixará mais perto de nossa meta.

## Etapa 1: Configurando o diretório de documentos

Primeiro, precisamos especificar o diretório onde nossos documentos estão armazenados. Isso é como preparar o palco antes da grande performance.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Substituir`"YOUR DOCUMENT DIRECTORY"` com o caminho para seu diretório. É aqui que seus documentos viverão e respirarão.

## Etapa 2: Carregue o documento principal

Em seguida, carregamos o documento principal no qual queremos inserir outro documento. Pense nisso como nosso estágio principal, onde toda a ação vai acontecer.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Este código carrega o documento principal do diretório especificado.

## Etapa 3: Defina as opções Localizar e Substituir

Para encontrar o local específico onde queremos inserir nosso documento, usamos a funcionalidade de localizar e substituir. É como usar um mapa para encontrar o local exato para nossa nova adição.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Aqui, estamos definindo a direção para trás e especificando um manipulador de retorno de chamada personalizado que definiremos a seguir.

## Etapa 4: Execute a operação de substituição

Agora, dizemos ao nosso documento principal para procurar um texto de espaço reservado específico e substituí-lo por nada, enquanto usamos nosso retorno de chamada personalizado para inserir outro documento.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Este código executa a operação de localização e substituição e, em seguida, salva o documento atualizado.

## Etapa 5: Crie um manipulador de retorno de chamada de substituição personalizado

Nosso manipulador de retorno de chamada personalizado é onde a mágica acontece. Este manipulador definirá como a inserção do documento é realizada durante a operação de localizar e substituir.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Insira um documento após o parágrafo que contém o texto da correspondência.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Remova o parágrafo com o texto correspondente.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Aqui, carregamos o documento a ser inserido e então chamamos um método auxiliar para realizar a inserção.

## Etapa 6: Defina o método de inserção de documento

A peça final do nosso quebra-cabeça é o método que realmente insere o documento no local especificado.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Verifique se o destino da inserção é um parágrafo ou tabela
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Crie um NodeImporter para importar nós do documento de origem
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Percorrer todos os nós de nível de bloco nas seções do documento de origem
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Pular o último parágrafo vazio de uma seção
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Importe e insira o nó no destino
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Este método cuida de importar nós do documento a serem inseridos e colocá-los no lugar certo no documento principal.

## Conclusão

aí está! Um guia abrangente para inserir um documento em outro usando o Aspose.Words para .NET. Seguindo essas etapas, você pode automatizar facilmente as tarefas de montagem e manipulação de documentos. Quer você esteja construindo um sistema de gerenciamento de documentos ou apenas precise agilizar seu fluxo de trabalho de processamento de documentos, o Aspose.Words é seu fiel companheiro.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words for .NET é uma biblioteca poderosa para manipular documentos do Word programaticamente. Ela permite que você crie, modifique, converta e processe documentos do Word com facilidade.

### Posso inserir vários documentos de uma vez?
Sim, você pode modificar o manipulador de retorno de chamada para lidar com múltiplas inserções iterando em uma coleção de documentos.

### Existe um teste gratuito disponível?
 Absolutamente! Você pode baixar uma versão de teste gratuita em[aqui](https://releases.aspose.com/).

### Como obtenho suporte para o Aspose.Words?
 Você pode obter suporte visitando o[Fórum Aspose.Words](https://forum.aspose.com/c/words/8).

### Posso manter a formatação do documento inserido?
 Sim, o`NodeImporter` A classe permite que você especifique como a formatação é tratada ao importar nós de um documento para outro.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
