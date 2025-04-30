---
"description": "Aprenda a criar listas ordenadas em documentos do Word usando o Aspose.Words para .NET com nosso guia passo a passo. Perfeito para automatizar a criação de documentos."
"linktitle": "Lista ordenada"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Lista ordenada"
"url": "/pt/net/working-with-markdown/ordered-list/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lista ordenada

## Introdução

Então, você decidiu mergulhar no Aspose.Words para .NET para criar documentos incríveis do Word programaticamente. Ótima escolha! Hoje, vamos explicar como criar uma lista ordenada em um documento do Word. Vamos passo a passo, então, seja você um novato em programação ou um profissional experiente, este guia será muito útil. Vamos começar!

## Pré-requisitos

Antes de mergulharmos no código, há algumas coisas que você precisa:

1. Aspose.Words para .NET: Certifique-se de ter o Aspose.Words para .NET instalado. Caso contrário, você pode baixá-lo. [aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Visual Studio ou qualquer outro IDE compatível com .NET.
3. Conhecimento básico de C#: você deve estar familiarizado com os conceitos básicos de C# para poder acompanhar facilmente.

## Importar namespaces

Para usar o Aspose.Words no seu projeto, você precisa importar os namespaces necessários. Isso é como configurar sua caixa de ferramentas antes de começar a trabalhar.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

Vamos dividir o código em etapas menores e explicar cada parte. Pronto? Vamos lá!

## Etapa 1: Inicializar o documento

Antes de mais nada, você precisa criar um novo documento. Pense nisso como abrir um documento do Word em branco no seu computador.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Aqui, estamos inicializando um novo documento e um objeto DocumentBuilder. O DocumentBuilder é como uma caneta, permitindo que você escreva conteúdo no documento.

## Etapa 2: Aplicar formato de lista numerada

Agora, vamos aplicar um formato de lista numerada padrão. É como configurar seu documento do Word para usar marcadores numerados.

```csharp
builder.ListFormat.ApplyNumberDefault();
```

Esta linha de código configura a numeração da sua lista. Fácil, não é?

## Etapa 3: Adicionar itens de lista

Agora, vamos adicionar alguns itens à nossa lista. Imagine que você está anotando uma lista de compras.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

Com essas linhas, você adiciona os dois primeiros itens à sua lista.

## Etapa 4: Recuar a lista

E se você quiser adicionar subitens a um item? Vamos lá!

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

O `ListIndent` O método recua a lista, criando uma sublista. Agora você está criando uma lista hierárquica, muito parecida com uma lista de tarefas aninhada.

## Conclusão

Criar uma lista ordenada em um documento do Word programaticamente pode parecer assustador no início, mas com o Aspose.Words para .NET, é moleza. Seguindo estes passos simples, você pode adicionar e gerenciar listas em seus documentos com facilidade. Seja para gerar relatórios, criar documentos estruturados ou simplesmente automatizar seus fluxos de trabalho, o Aspose.Words para .NET tem tudo o que você precisa. Então, por que esperar? Comece a programar e veja a mágica acontecer!

## Perguntas frequentes

### Posso personalizar o estilo de numeração da lista?  
Sim, você pode personalizar o estilo de numeração usando o `ListFormat` Propriedades. Você pode definir diferentes estilos de numeração, como algarismos romanos, letras, etc.

### Como adiciono mais níveis de recuo?  
Você pode usar o `ListIndent` método várias vezes para criar níveis mais profundos de sublistas. Cada chamada para `ListIndent` adiciona um nível de recuo.

### Posso misturar marcadores e listas numeradas?  
Com certeza! Você pode aplicar diferentes formatos de lista no mesmo documento usando o `ListFormat` propriedade.

### É possível continuar a numeração de uma lista anterior?  
Sim, você pode continuar numerando usando o mesmo formato de lista. O Aspose.Words permite controlar a numeração da lista em diferentes parágrafos.

### Como posso remover o formato de lista?  
Você pode remover o formato de lista chamando `ListFormat.RemoveNumbers()`. Isso transformará os itens da lista novamente em parágrafos normais.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}