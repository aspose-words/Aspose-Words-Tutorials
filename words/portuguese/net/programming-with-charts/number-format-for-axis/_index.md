---
title: Formato numérico para eixo em um gráfico
linktitle: Formato numérico para eixo em um gráfico
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a formatar números de eixos de gráficos usando o Aspose.Words para .NET com este guia passo a passo. Melhore a legibilidade e o profissionalismo do seu documento sem esforço.
weight: 10
url: /pt/net/programming-with-charts/number-format-for-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formato numérico para eixo em um gráfico

## Introdução

Olá! Você já trabalhou com gráficos em seus documentos e desejou poder formatar os números em seu eixo para torná-los mais profissionais? Bem, você está com sorte! Neste tutorial, vamos nos aprofundar em como você pode conseguir exatamente isso usando o Aspose.Words para .NET. Esta biblioteca poderosa permite que você manipule documentos do Word de uma forma que é tão fácil quanto uma torta. E hoje, estamos nos concentrando em dar a esses eixos de gráfico uma reformulação com formatos de números personalizados.

## Pré-requisitos

Antes de começarmos, vamos garantir que você tenha tudo o que precisa. Aqui está uma lista de verificação rápida:

-  Aspose.Words para .NET: Certifique-se de que você o tenha instalado. Se não, você pode[baixe aqui](https://releases.aspose.com/words/net/).
- .NET Framework: certifique-se de ter um .NET Framework compatível instalado.
- Ambiente de desenvolvimento: Um IDE como o Visual Studio funcionará perfeitamente.
- Conhecimento básico de C#: Isso ajudará você a acompanhar os exemplos de codificação.

## Importar namespaces

Primeiro, você precisa importar os namespaces necessários no seu projeto. Isso é como lançar a fundação antes de construir uma casa. Adicione as seguintes diretivas using no topo do seu arquivo de código:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Agora, vamos dividir o processo em etapas simples e fáceis de seguir.

## Etapa 1: Configurando o documento

Título: Inicialize seu documento

Primeiro, você precisa criar um novo documento e um construtor de documentos. Pense neste passo como preparar sua tela e pincel antes de começar sua obra-prima.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Aqui,`dataDir` é o caminho para o diretório do seu documento onde você salvará o arquivo final.`Document` e`DocumentBuilder` são classes do Aspose.Words que ajudam você a criar e manipular documentos do Word.

## Etapa 2: Inserindo um gráfico

Título: Adicionar um gráfico ao seu documento

Em seguida, vamos adicionar um gráfico ao seu documento. É aqui que a mágica começa. Vamos inserir um gráfico de colunas que atuará como nossa tela em branco.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 O`InsertChart` O método insere um gráfico do tipo especificado (Coluna neste caso) e dimensões no documento.

## Etapa 3: Personalizando a série de gráficos

Título: Preencha seu gráfico com dados

Agora, precisamos adicionar alguns dados ao nosso gráfico. Este passo é semelhante a preencher seu gráfico com informações significativas.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

 Aqui, estamos adicionando uma nova série chamada "Aspose Series 1" com cinco pontos de dados. O`Series.Clear` O método garante que todos os dados pré-existentes sejam removidos antes de adicionar nossa nova série.

## Etapa 4: Formatando os números dos eixos

Título: Embeleze seus números de eixo

Por fim, vamos formatar os números no eixo Y para torná-los mais legíveis. Isso é como dar os retoques finais na sua arte.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

 O`FormatCode` propriedade permite que você defina um formato personalizado para os números no eixo. Neste exemplo,`#,##0`garante que números grandes sejam exibidos com vírgulas para milhares.

## Etapa 5: Salvando o documento

Título: Salve sua obra-prima

Agora que tudo está configurado, é hora de salvar seu documento. Este passo é a grande revelação do seu trabalho.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

 Aqui, o`Save` método salva o documento no caminho especificado com o nome do arquivo`WorkingWithCharts.NumberFormatForAxis.docx`.

## Conclusão

E aí está! Você formatou com sucesso os números no eixo Y do seu gráfico usando o Aspose.Words para .NET. Isso não só faz com que seus gráficos pareçam mais profissionais, mas também melhora a legibilidade. O Aspose.Words oferece uma infinidade de recursos que podem ajudar você a criar documentos Word impressionantes programaticamente. Então, por que não explorar mais e ver o que mais você pode fazer?

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca poderosa que permite aos desenvolvedores criar, manipular e converter documentos do Word programaticamente.

### Posso formatar outros aspectos do gráfico além dos números dos eixos?
Com certeza! O Aspose.Words for .NET permite que você formate títulos, rótulos e até mesmo personalize a aparência do gráfico.

### Existe uma versão de avaliação gratuita disponível para o Aspose.Words para .NET?
 Sim, você pode obter um[teste gratuito aqui](https://releases.aspose.com/).

### Posso usar o Aspose.Words para .NET com outras linguagens .NET além de C#?
Sim, o Aspose.Words para .NET é compatível com qualquer linguagem .NET, incluindo VB.NET e F#.

### Onde posso encontrar documentação mais detalhada?
 A documentação detalhada está disponível em[Página de documentação do Aspose.Words para .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
