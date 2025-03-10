---
title: Mover nó no documento rastreado
linktitle: Mover nó no documento rastreado
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como mover nós em um documento do Word rastreado usando o Aspose.Words para .NET com nosso guia detalhado passo a passo. Perfeito para desenvolvedores.
weight: 10
url: /pt/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mover nó no documento rastreado

## Introdução

Olá, entusiastas do Aspose.Words! Se você já precisou mover um nó em um documento do Word enquanto rastreia revisões, você está no lugar certo. Hoje, vamos mergulhar em como fazer isso usando o Aspose.Words para .NET. Você não só aprenderá o processo passo a passo, mas também aprenderá algumas dicas e truques para tornar sua manipulação de documentos suave e eficiente.

## Pré-requisitos

Antes de colocarmos a mão na massa com algum código, vamos garantir que você tenha tudo o que precisa:

-  Aspose.Words para .NET: Baixe-o[aqui](https://releases.aspose.com/words/net/).
- Ambiente .NET: certifique-se de ter um ambiente de desenvolvimento .NET compatível configurado.
- Conhecimento básico de C#: Este tutorial pressupõe que você tenha um conhecimento básico de C#.

Pegou tudo? Ótimo! Vamos para os namespaces que precisamos importar.

## Importar namespaces

Primeiro, precisamos importar os namespaces necessários. Eles são essenciais para trabalhar com Aspose.Words e manipular nós de documentos.

```csharp
using Aspose.Words;
using System;
```

Certo, vamos dividir o processo em etapas gerenciáveis. Cada etapa será explicada em detalhes para garantir que você entenda o que está acontecendo em cada ponto.

## Etapa 1: Inicializar o documento

 Para começar, precisamos inicializar um novo documento e usar um`DocumentBuilder` para adicionar alguns parágrafos.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Adicionando alguns parágrafos
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Verifique a contagem do parágrafo inicial
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Etapa 2: Comece a rastrear revisões

Em seguida, precisamos começar a rastrear revisões. Isso é crucial, pois nos permite ver as alterações feitas no documento.

```csharp
// Comece a rastrear revisões
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Etapa 3: mover nós

Agora vem a parte central da nossa tarefa: mover um nó de um local para outro. Vamos mover o terceiro parágrafo e colocá-lo antes do primeiro parágrafo.

```csharp
// Defina o nó a ser movido e seu intervalo final
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Mova os nós dentro do intervalo definido
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Etapa 4: Pare de rastrear revisões

Depois de mover os nós, precisamos parar de rastrear as revisões.

```csharp
// Parar de rastrear revisões
doc.StopTrackRevisions();
```

## Etapa 5: Salve o documento

Por fim, vamos salvar nosso documento modificado no diretório especificado.

```csharp
// Salvar o documento modificado
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Produza a contagem final do parágrafo
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Conclusão

E aí está! Você moveu com sucesso um nó em um documento rastreado usando o Aspose.Words para .NET. Esta biblioteca poderosa facilita a manipulação de documentos do Word programaticamente. Não importa se você está criando, editando ou rastreando alterações, o Aspose.Words tem tudo o que você precisa. Então, vá em frente e experimente. Boa codificação!

## Perguntas frequentes

### O que é Aspose.Words para .NET?

Aspose.Words for .NET é uma biblioteca de classes para trabalhar com documentos do Word programaticamente. Ela permite que desenvolvedores criem, editem, convertam e imprimam documentos do Word dentro de aplicativos .NET.

### Como faço para rastrear revisões em um documento do Word usando o Aspose.Words?

 Para rastrear revisões, use o`StartTrackRevisions` método sobre o`Document` objeto. Isso habilitará o rastreamento de revisão, mostrando quaisquer alterações feitas no documento.

### Posso mover vários nós no Aspose.Words?

Sim, você pode mover vários nós iterando sobre eles e usando métodos como`InsertBefore` ou`InsertAfter` para colocá-los no local desejado.

### Como faço para parar de rastrear revisões no Aspose.Words?

 Use o`StopTrackRevisions` método sobre o`Document` objetar a interrupção do rastreamento de revisões.

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?

 Você pode encontrar documentação detalhada[aqui](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
