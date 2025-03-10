---
title: Inserir documento na mala direta
linktitle: Inserir documento na mala direta
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como inserir documentos em campos de mala direta usando o Aspose.Words para .NET neste tutorial abrangente e passo a passo.
weight: 10
url: /pt/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir documento na mala direta

## Introdução

Bem-vindo ao mundo da automação de documentos com o Aspose.Words para .NET! Você já se perguntou como inserir documentos dinamicamente em campos específicos dentro de um documento principal durante uma operação de mala direta? Bem, você está no lugar certo. Este tutorial o guiará passo a passo pelo processo de inserção de documentos em campos de mala direta usando o Aspose.Words para .NET. É como montar um quebra-cabeça, onde cada peça se encaixa perfeitamente. Então, vamos lá!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1.  Aspose.Words para .NET: Você pode[baixe a última versão aqui](https://releases.aspose.com/words/net/) . Se você precisar comprar uma licença, você pode fazê-lo[aqui](https://purchase.aspose.com/buy) . Alternativamente, você pode obter um[licença temporária](https://purchase.aspose.com/temporary-license/) ou experimente com um[teste gratuito](https://releases.aspose.com/).
2. Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE C#.
3. Conhecimento básico de C#: A familiaridade com a programação em C# tornará este tutorial muito fácil.

## Importar namespaces

Primeiro, você precisará importar os namespaces necessários. Eles são como os blocos de construção do seu projeto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Vamos dividir o processo em etapas gerenciáveis. Cada etapa será construída sobre a anterior, levando você a uma solução completa.

## Etapa 1: Configurando seu diretório

Antes de começar a inserir documentos, você precisa definir o caminho para o seu diretório de documentos. É aqui que seus documentos são armazenados.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Carregando o documento principal

Em seguida, você carregará o documento principal. Este documento contém os campos de mesclagem onde outros documentos serão inseridos.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Etapa 3: Definindo o retorno de chamada de mesclagem de campos

Para lidar com o processo de mesclagem, você precisará definir uma função de retorno de chamada. Essa função será responsável por inserir documentos nos campos de mesclagem especificados.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Etapa 4: Executando a mala direta

Agora é hora de executar a mala direta. É aqui que a mágica acontece. Você especificará o campo de mesclagem e o documento que deve ser inserido neste campo.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Etapa 5: Salvando o documento

Após a mala direta ser concluída, você salvará o documento modificado. Este novo documento terá o conteúdo inserido exatamente onde você quer.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Etapa 6: Criando o manipulador de retorno de chamada

O manipulador de retorno de chamada é uma classe que faz processamento especial para o campo de mesclagem. Ele carrega o documento especificado no valor do campo e o insere no campo de mesclagem atual.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Etapa 7: Inserindo o documento

Este método insere o documento especificado no parágrafo atual ou na célula da tabela.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Conclusão

E aí está! Você inseriu documentos com sucesso em campos específicos durante uma operação de mala direta usando o Aspose.Words para .NET. Esse recurso poderoso pode economizar muito tempo e esforço, especialmente ao lidar com grandes volumes de documentos. Pense nisso como ter um assistente pessoal que cuida de todo o trabalho pesado para você. Então, vá em frente e experimente. Boa codificação!

## Perguntas frequentes

### Posso inserir vários documentos em diferentes campos de mesclagem?
Sim, você pode. Basta especificar os campos de mesclagem apropriados e os caminhos de documentos correspondentes no`MailMerge.Execute` método.

### É possível formatar o documento inserido de forma diferente do documento principal?
 Com certeza! Você pode usar o`ImportFormatMode` parâmetro no`NodeImporter` para controlar a formatação.

### E se o nome do campo de mesclagem for dinâmico?
Você pode manipular nomes de campos de mesclagem dinâmicos passando-os como parâmetros para o manipulador de retorno de chamada.

### Posso usar esse método com diferentes formatos de arquivo?
Sim, o Aspose.Words suporta vários formatos de arquivo, incluindo DOCX, PDF e muito mais.

### Como lidar com erros durante o processo de inserção de documentos?
Implemente o tratamento de erros no seu manipulador de retorno de chamada para gerenciar quaisquer exceções que possam ocorrer.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
