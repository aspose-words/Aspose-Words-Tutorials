---
title: Granularidade de comparação em documento do Word
linktitle: Granularidade de comparação em documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a comparar granularidade em documentos do Word, um recurso do Aspose.Words para .NET que permite que documentos sejam comparados caractere por caractere, relatando alterações feitas.
weight: 10
url: /pt/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Granularidade de comparação em documento do Word

Aqui está um guia passo a passo para explicar o código-fonte C# abaixo, que usa o recurso Comparar granularidade em documentos do Word do Aspose.Words para .NET.

## Etapa 1: Introdução

O recurso Compare Granularity do Aspose.Words for .NET permite que você compare documentos no nível de caractere. Isso significa que cada caractere será comparado e as alterações serão relatadas de acordo.

## Etapa 2: Configurando o ambiente

Antes de começar, você precisa configurar seu ambiente de desenvolvimento para trabalhar com Aspose.Words para .NET. Certifique-se de ter a biblioteca Aspose.Words instalada e de ter um projeto C# adequado para incorporar o código.

## Etapa 3: Adicionar os conjuntos necessários

Para usar o recurso Compare Granularity do Aspose.Words para .NET, você precisa adicionar os assemblies necessários ao seu projeto. Certifique-se de ter as referências adequadas ao Aspose.Words no seu projeto.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Etapa 4: Criando documentos

Nesta etapa, criaremos dois documentos usando a classe DocumentBuilder. Esses documentos serão usados para a comparação.

```csharp
// Crie o documento A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Crie o documento B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Etapa 5: Configurando opções de comparação

Nesta etapa, configuraremos as opções de comparação para especificar a granularidade da comparação. Aqui, usaremos granularidade em nível de caractere.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Etapa 6: Comparação de documentos

Agora vamos comparar os documentos usando o método Compare da classe Document. As alterações serão salvas no documento A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 O`Compare` método compara o documento A com o documento B e salva as alterações no documento A. Você pode especificar o nome do autor e a data da comparação para referência.

## Conclusão

Neste artigo, exploramos o recurso Compare Granularity do Aspose.Words para .NET. Esse recurso permite que você compare documentos no nível de caractere e relate alterações. Você pode usar esse conhecimento para executar comparações detalhadas de documentos em seus projetos.

### Código-fonte de exemplo para granularidade de comparação usando Aspose.Words para .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Conclusão

Neste tutorial, exploramos o recurso Comparison Granularity do Aspose.Words para .NET. Esse recurso permite que você especifique o nível de detalhes ao comparar documentos. Ao escolher diferentes níveis de granularidade, você pode executar comparações detalhadas no nível de caractere, palavra ou bloco, dependendo de seus requisitos específicos. O Aspose.Words para .NET fornece um recurso de comparação de documentos flexível e poderoso, facilitando a identificação de diferenças em documentos com vários níveis de granularidade.

### Perguntas frequentes

#### P: Qual é o propósito de usar a granularidade de comparação no Aspose.Words para .NET?

A: Granularidade de comparação no Aspose.Words para .NET permite que você especifique o nível de detalhes ao comparar documentos. Com esse recurso, você pode comparar documentos em diferentes níveis, como nível de caractere, nível de palavra ou até mesmo nível de bloco. Cada nível de granularidade fornece um nível diferente de detalhes nos resultados da comparação.

#### P: Como usar a granularidade de comparação no Aspose.Words para .NET?

R: Para usar a granularidade de comparação no Aspose.Words para .NET, siga estas etapas:
1. Configure seu ambiente de desenvolvimento com a biblioteca Aspose.Words.
2. Adicione os assemblies necessários ao seu projeto referenciando Aspose.Words.
3.  Crie os documentos que você deseja comparar usando o`DocumentBuilder` aula.
4.  Configure as opções de comparação criando um`CompareOptions` objeto e configuração do`Granularity` propriedade para o nível desejado (por exemplo,`Granularity.CharLevel` para comparação em nível de personagem).
5.  Use o`Compare`método em um documento, passando o outro documento e o`CompareOptions` objeto como parâmetros. Este método comparará os documentos com base na granularidade especificada e salvará as alterações no primeiro documento.

#### P: Quais são os níveis disponíveis de granularidade de comparação no Aspose.Words para .NET?

R: O Aspose.Words para .NET fornece três níveis de granularidade de comparação:
- `Granularity.CharLevel`: Compara documentos no nível do caractere.
- `Granularity.WordLevel`: Compara documentos no nível da palavra.
- `Granularity.BlockLevel`: Compara documentos no nível de bloco.

#### P: Como posso interpretar os resultados da comparação com granularidade em nível de caractere?

A: Com granularidade em nível de caractere, cada caractere nos documentos comparados é analisado para diferenças. Os resultados da comparação mostrarão alterações no nível de caractere individual, incluindo adições, exclusões e modificações.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
