---
"description": "Aprenda a criar e personalizar listas com marcadores em documentos do Word usando o Aspose.Words para .NET com este guia passo a passo."
"linktitle": "Lista com marcadores"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Lista com marcadores"
"url": "/pt/net/working-with-markdown/bulleted-list/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lista com marcadores

## Introdução

Pronto para mergulhar no mundo do Aspose.Words para .NET? Hoje, vamos mostrar como criar uma lista com marcadores nos seus documentos do Word. Seja para organizar ideias, listar itens ou apenas adicionar um pouco de estrutura ao seu documento, listas com marcadores são super úteis. Então, vamos começar!

## Pré-requisitos

Antes de começarmos a codificação, vamos garantir que você tenha tudo o que precisa:

1. Aspose.Words para .NET: Certifique-se de ter a biblioteca Aspose.Words instalada. Se ainda não a tiver, você pode [baixe aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: ambiente de desenvolvimento AC# como o Visual Studio.
3. Conhecimento básico de C#: um entendimento básico de programação em C# ajudará você a acompanhar.

## Importar namespaces

Antes de mais nada, vamos importar os namespaces necessários. Isso é como preparar o cenário para que nosso código funcione sem problemas.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Agora, vamos dividir o processo em etapas fáceis e gerenciáveis.

## Etapa 1: Criar um novo documento

Certo, vamos começar criando um novo documento. É aqui que toda a mágica vai acontecer.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Etapa 2: aplicar o formato de lista com marcadores

Em seguida, aplicaremos um formato de lista com marcadores. Isso informa ao documento que estamos prestes a iniciar uma lista com marcadores.

```csharp
builder.ListFormat.ApplyBulletDefault();
```

## Etapa 3: personalizar a lista com marcadores

Aqui, personalizaremos a lista de marcadores de acordo com nossa preferência. Neste exemplo, usaremos um hífen (-) como marcador.

```csharp
builder.ListFormat.List.ListLevels[0].NumberFormat = "-";
```

## Etapa 4: Adicionar itens de lista

Agora, vamos adicionar alguns itens à nossa lista com marcadores. É aqui que você pode ser criativo e adicionar o conteúdo que precisar.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

## Etapa 5: Adicionar subitens

Para tornar as coisas mais interessantes, vamos adicionar alguns subitens sob o "Item 2". Isso ajuda a organizar os subpontos.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
builder.ListFormat.ListOutdent(); // Retornar ao nível da lista principal
```

## Conclusão

E pronto! Você acabou de criar uma lista com marcadores em um documento do Word usando o Aspose.Words para .NET. É um processo simples, mas incrivelmente poderoso para organizar seus documentos. Seja para criar listas simples ou listas aninhadas complexas, o Aspose.Words tem tudo o que você precisa.

Sinta-se à vontade para experimentar diferentes estilos e formatos de lista para atender às suas necessidades. Boa programação!

## Perguntas frequentes

### Posso usar diferentes símbolos de marcadores na lista?
   Sim, você pode personalizar os símbolos de marcadores alterando o `NumberFormat` propriedade.

### Como adiciono mais níveis de recuo?
   Use o `ListIndent` método para adicionar mais níveis e `ListOutdent` para voltar a um nível mais alto.

### É possível misturar listas com marcadores e listas numéricas?
   Com certeza! Você pode alternar entre os formatos de marcadores e números usando o `ApplyNumberDefault` e `ApplyBulletDefault` métodos.

### Posso estilizar o texto nos itens da lista?
   Sim, você pode aplicar diferentes estilos, fontes e formatações ao texto dentro dos itens da lista usando o `Font` propriedade do `DocumentBuilder`.

### Como posso criar uma lista com marcadores de várias colunas?
   Você pode usar a formatação de tabela para criar listas com várias colunas, onde cada célula contém uma lista com marcadores separada.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}