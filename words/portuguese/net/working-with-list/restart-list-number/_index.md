---
title: Número da lista de reinicialização
linktitle: Número da lista de reinicialização
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a reiniciar números de lista em documentos do Word usando o Aspose.Words para .NET. Este guia detalhado de 2000 palavras abrange tudo o que você precisa saber, da configuração à personalização avançada.
weight: 10
url: /pt/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Número da lista de reinicialização

## Introdução

Você está procurando dominar a arte da manipulação de listas em seus documentos do Word usando o Aspose.Words para .NET? Bem, você está no lugar certo! Neste tutorial, vamos nos aprofundar na reinicialização de números de lista, um recurso bacana que levará suas habilidades de automação de documentos para o próximo nível. Apertem os cintos e vamos começar!

## Pré-requisitos

Antes de começarmos o código, vamos garantir que você tenha tudo o que precisa:

1.  Aspose.Words para .NET: Você precisa ter o Aspose.Words para .NET instalado. Se você ainda não o instalou, você pode[baixe aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: certifique-se de ter um ambiente de desenvolvimento adequado, como o Visual Studio.
3. Conhecimento básico de C#: Um conhecimento básico de C# ajudará você a acompanhar o tutorial.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Eles são cruciais para acessar os recursos do Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Agora, vamos dividir o processo em etapas fáceis de seguir. Cobriremos tudo, desde a criação de uma lista até a reinicialização de sua numeração.

## Etapa 1: configure seu documento e construtor

Antes de começar a manipular listas, você precisa de um documento e de um DocumentBuilder. O DocumentBuilder é sua ferramenta de referência para adicionar conteúdo ao seu documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: Crie e personalize sua primeira lista

Em seguida, criaremos uma lista com base em um modelo e personalizaremos sua aparência. Neste exemplo, estamos usando o formato de número arábico com parênteses.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Aqui, definimos a cor da fonte como vermelha e alinhamos o texto à direita.

## Etapa 3: adicione itens à sua primeira lista

 Com sua lista pronta, é hora de adicionar alguns itens. O DocumentBuilder's`ListFormat.List` propriedade ajuda a aplicar o formato de lista ao texto.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Etapa 4: Reinicie a numeração da lista

Para reutilizar a lista e reiniciar sua numeração, você precisa criar uma cópia da lista original. Isso permite que você modifique a nova lista de forma independente.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

Neste exemplo, a nova lista começa no número 10.

## Etapa 5: Adicionar itens à nova lista

Assim como antes, adicione itens à sua nova lista. Isso demonstra a lista reiniciando no número especificado.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Etapa 6: Salve seu documento

Por fim, salve o documento no diretório especificado.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Conclusão

Reiniciar números de lista em documentos do Word usando o Aspose.Words para .NET é simples e incrivelmente útil. Não importa se você está gerando relatórios, criando documentos estruturados ou apenas precisa de melhor controle sobre suas listas, esta técnica tem tudo o que você precisa.

## Perguntas frequentes

### Posso usar outros modelos de lista além de NumberArabicParenthesis?

Com certeza! O Aspose.Words oferece vários modelos de lista, como marcadores, letras, algarismos romanos e muito mais. Você pode escolher o que melhor se adapta às suas necessidades.

### Como altero o nível da lista?

 Você pode alterar o nível da lista modificando o`ListLevels` propriedade. Por exemplo,`list1.ListLevels[1]` se referiria ao segundo nível da lista.

### Posso reiniciar a numeração em qualquer número?

 Sim, você pode definir o número inicial para qualquer valor inteiro usando o`StartAt` propriedade do nível de lista.

### É possível ter formatações diferentes para diferentes níveis de lista?

De fato! Cada nível de lista pode ter suas próprias configurações de formatação, como fonte, alinhamento e estilo de numeração.

### E se eu quiser continuar a numeração de uma lista anterior em vez de reiniciar?

Se quiser continuar numerando, não precisa criar uma cópia da lista. Simplesmente continue adicionando itens à lista original.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
