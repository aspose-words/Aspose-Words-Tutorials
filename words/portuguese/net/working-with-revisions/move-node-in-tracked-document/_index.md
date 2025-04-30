---
"description": "Aprenda a mover nós em um documento do Word rastreado usando o Aspose.Words para .NET com nosso guia passo a passo detalhado. Perfeito para desenvolvedores."
"linktitle": "Mover nó no documento rastreado"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Mover nó no documento rastreado"
"url": "/pt/net/working-with-revisions/move-node-in-tracked-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mover nó no documento rastreado

## Introdução

Olá, entusiastas do Aspose.Words! Se você já precisou mover um nó em um documento do Word enquanto monitorava revisões, está no lugar certo. Hoje, vamos nos aprofundar em como fazer isso usando o Aspose.Words para .NET. Você não apenas aprenderá o processo passo a passo, como também aprenderá algumas dicas e truques para tornar a manipulação do seu documento tranquila e eficiente.

## Pré-requisitos

Antes de colocarmos a mão na massa com algum código, vamos garantir que você tenha tudo o que precisa:

- Aspose.Words para .NET: Baixe [aqui](https://releases.aspose.com/words/net/).
- Ambiente .NET: certifique-se de ter um ambiente de desenvolvimento .NET compatível configurado.
- Conhecimento básico de C#: Este tutorial pressupõe que você tenha um conhecimento básico de C#.

Entendeu tudo? Ótimo! Vamos passar para os namespaces que precisamos importar.

## Importar namespaces

Antes de mais nada, precisamos importar os namespaces necessários. Eles são essenciais para trabalhar com o Aspose.Words e manipular nós de documentos.

```csharp
using Aspose.Words;
using System;
```

Certo, vamos dividir o processo em etapas gerenciáveis. Cada etapa será explicada em detalhes para garantir que você entenda o que está acontecendo em cada ponto.

## Etapa 1: Inicializar o documento

Para começar, precisamos inicializar um novo documento e usar um `DocumentBuilder` para adicionar alguns parágrafos.

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

Em seguida, precisamos começar a monitorar as revisões. Isso é crucial, pois nos permite ver as alterações feitas no documento.

```csharp
// Comece a rastrear revisões
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Etapa 3: mover nós

Agora vem a parte central da nossa tarefa: mover um nó de um local para outro. Moveremos o terceiro parágrafo e o colocaremos antes do primeiro.

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

Depois de mover os nós, precisamos parar de rastrear revisões.

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

E pronto! Você moveu com sucesso um nó em um documento rastreado usando o Aspose.Words para .NET. Esta poderosa biblioteca facilita a manipulação programática de documentos do Word. Seja para criar, editar ou rastrear alterações, o Aspose.Words tem tudo o que você precisa. Então, vá em frente e experimente. Boa programação!

## Perguntas frequentes

### O que é Aspose.Words para .NET?

Aspose.Words para .NET é uma biblioteca de classes para trabalhar com documentos do Word programaticamente. Ela permite que desenvolvedores criem, editem, convertam e imprimam documentos do Word em aplicativos .NET.

### Como posso rastrear revisões em um documento do Word usando o Aspose.Words?

Para acompanhar as revisões, use o `StartTrackRevisions` método sobre o `Document` objeto. Isso permitirá o rastreamento de revisões, exibindo quaisquer alterações feitas no documento.

### Posso mover vários nós no Aspose.Words?

Sim, você pode mover vários nós iterando sobre eles e usando métodos como `InsertBefoue` or `InsertAfter` para colocá-los no local desejado.

### Como faço para parar de rastrear revisões no Aspose.Words?

Use o `StopTrackRevisions` método sobre o `Document` objetar a parar de rastrear revisões.

### Onde posso encontrar mais documentação sobre o Aspose.Words para .NET?

Você pode encontrar documentação detalhada [aqui](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}