---
title: Obter tipos de revisão de palavras
linktitle: Obter tipos de revisão de palavras
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como obter tipos de revisão de palavras em um documento do Word usando o Aspose.Words para .NET. Este guia passo a passo ajuda você a lidar com revisões de documentos de forma eficiente.
weight: 10
url: /pt/net/working-with-revisions/get-revision-types/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obter tipos de revisão de palavras

## Introdução

Já se viu atolado em um mar de revisões de documentos, imaginando quem moveu o quê e quando? Você não está sozinho. Lidar com revisões de documentos pode ser uma tarefa tediosa, especialmente ao lidar com documentos extensos. Mas não se preocupe! Com o Aspose.Words para .NET, você pode identificar e gerenciar facilmente essas revisões. Neste guia, mostraremos a você um processo passo a passo sobre como obter tipos de revisão de palavras em um documento do Word usando o Aspose.Words para .NET. Então, apertem os cintos e vamos mergulhar!

## Pré-requisitos

Antes de colocarmos a mão na massa com algum código, há algumas coisas que você precisa:

1.  Biblioteca Aspose.Words para .NET: Se você ainda não fez isso, baixe-o em[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE compatível com .NET.
3. Conhecimento básico de C#: Entender a linguagem de programação C# será benéfico.
4.  Um documento do Word com revisões: certifique-se de ter um`.docx`arquivo com alterações rastreadas para testar o código.

## Importar namespaces

Para começar, você precisará importar os namespaces necessários no seu projeto C#. Isso permitirá que você acesse as funcionalidades fornecidas pelo Aspose.Words para .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Vamos dividir o exemplo em várias etapas para melhor compreensão e implementação.

## Etapa 1: configure seu diretório de documentos

Primeiro, você precisa definir o caminho para o diretório dos seus documentos. É aqui que seu documento Word com revisões estará localizado.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Substituir`"YOUR DOCUMENT DIRECTORY"` com o caminho real para sua pasta de documentos.

## Etapa 2: carregue seu documento do Word

Em seguida, você precisa carregar o documento do Word no seu projeto. Este documento deve ter as revisões que você quer analisar.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

 Certifique-se de que o arquivo`Revisions.docx` existe no diretório especificado.

## Etapa 3: Acesse a coleção de parágrafos

Agora que seu documento está carregado, você precisa acessar os parágrafos dentro da primeira seção do corpo do documento. Isso ajudará você a iterar por cada parágrafo para verificar revisões.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Etapa 4: iterar pelos parágrafos e verificar as revisões

É aqui que a mágica acontece. Você vai iterar por cada parágrafo e verificar se ele foi movido (excluído ou inserido).

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

 Este loop percorre cada parágrafo e usa o`IsMoveFromRevision` e`IsMoveToRevision` propriedades para determinar se o parágrafo foi movido (excluído) ou movido (inserido).

## Conclusão

E aí está! Com apenas algumas linhas de código, você pode identificar facilmente os tipos de revisões no seu documento do Word usando o Aspose.Words para .NET. Esta biblioteca poderosa torna o manuseio de revisões de documentos muito fácil, permitindo que você se concentre em tarefas mais importantes. 

## Perguntas frequentes

### Posso usar o Aspose.Words for .NET para rastrear alterações feitas por usuários específicos?

Sim, o Aspose.Words para .NET fornece funcionalidade para acessar detalhes de revisão, incluindo o autor das alterações.

### Existe uma versão de avaliação gratuita disponível para o Aspose.Words para .NET?

 Absolutamente! Você pode obter um teste gratuito[aqui](https://releases.aspose.com/).

### Como posso solicitar uma licença temporária para o Aspose.Words para .NET?

 Você pode solicitar e aplicar uma licença temporária em[aqui](https://purchase.aspose.com/temporary-license/).

### Onde posso encontrar documentação mais detalhada do Aspose.Words para .NET?

 A documentação detalhada está disponível em[Site Aspose](https://reference.aspose.com/words/net/).

### Posso usar o Aspose.Words para .NET em um projeto não comercial?

Sim, o Aspose.Words para .NET pode ser usado em projetos comerciais e não comerciais, mas certifique-se de verificar os termos de licenciamento.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
