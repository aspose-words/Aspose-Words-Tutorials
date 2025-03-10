---
title: Crie e personalize o gráfico usando a forma
linktitle: Crie e personalize o gráfico usando a forma
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a criar e personalizar gráficos em documentos do Word usando o Aspose.Words para .NET com este guia passo a passo. Perfeito para visualização de dados.
weight: 10
url: /pt/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie e personalize o gráfico usando a forma

## Introdução

Criar e personalizar gráficos em seus documentos é uma habilidade crucial no mundo atual, orientado por dados. Os gráficos podem ajudar a visualizar dados, tornando informações complexas mais digeríveis. O Aspose.Words para .NET é uma biblioteca poderosa que permite criar e manipular documentos do Word programaticamente. Neste tutorial, mostraremos a você o processo de criação e personalização de um gráfico de linhas usando o Aspose.Words para .NET. Ao final deste guia, você poderá criar gráficos com aparência profissional com facilidade.

## Pré-requisitos

Antes de mergulhar no código, certifique-se de ter o seguinte:

-  Biblioteca Aspose.Words para .NET: Você pode baixá-la[aqui](https://releases.aspose.com/words/net/).
- Visual Studio: qualquer versão que suporte .NET.
- Conhecimento básico de C#: entender os conceitos básicos de C# ajudará você a acompanhar o tutorial.

## Importar namespaces

Para começar, você precisa importar os namespaces necessários. Este passo é essencial, pois permite que você use as classes e métodos fornecidos pelo Aspose.Words para .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Etapa 1: Crie um novo documento

Primeiro, você precisa criar um novo documento do Word. Este documento servirá como tela para seu gráfico.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: Insira um gráfico

 Em seguida, você irá inserir um gráfico de linhas no documento. O`DocumentBuilder.InsertChart` método é usado para esta finalidade.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## Etapa 3: personalize o título do gráfico

Personalizar o título do gráfico pode ajudar a fornecer contexto para os dados que estão sendo exibidos. Você pode mostrar o título e definir seu texto usando o seguinte código:

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
// Observe que se um valor nulo ou vazio for especificado como texto do título, o título gerado automaticamente será exibido.
```

## Etapa 4: ajuste a posição da legenda

A legenda ajuda a identificar diferentes séries de dados no seu gráfico. Você pode personalizar sua posição e configurações de sobreposição assim:

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## Etapa 5: Salve o documento

Por fim, você precisa salvar o documento. Este passo garante que todas as suas alterações sejam gravadas no arquivo.

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## Conclusão

Neste tutorial, abordamos como criar e personalizar um gráfico de linhas em um documento do Word usando o Aspose.Words para .NET. Seguindo o guia passo a passo, agora você pode criar gráficos visualmente atraentes que comunicam seus dados de forma eficaz. O Aspose.Words para .NET oferece uma ampla gama de opções de personalização, permitindo que você adapte os gráficos às suas necessidades específicas.

## Perguntas frequentes

### Posso usar o Aspose.Words for .NET para criar outros tipos de gráficos?

 Sim, o Aspose.Words para .NET suporta vários tipos de gráficos, incluindo gráficos de barras, gráficos de pizza e muito mais. Você pode explorar a documentação[aqui](https://reference.aspose.com/words/net/) para mais detalhes.

### Como posso testar o Aspose.Words para .NET antes de comprar?

 Você pode baixar uma versão de teste gratuita em[aqui](https://releases.aspose.com/). Isso permite que você teste a biblioteca e seus recursos antes de fazer uma compra.

### Existe alguma maneira de obter suporte se eu tiver problemas?

 Absolutamente. Você pode acessar o suporte através dos fóruns da comunidade Aspose[aqui](https://forum.aspose.com/c/words/8)A comunidade e a equipe da Aspose são muito receptivas.

### Como posso comprar uma licença para o Aspose.Words para .NET?

 Você pode comprar uma licença diretamente do site da Aspose[aqui](https://purchase.aspose.com/buy). Existem várias opções de licenciamento para atender a diferentes necessidades.

### E se eu precisar de uma licença temporária para um projeto de curto prazo?

 A Aspose oferece licenças temporárias, que você pode solicitar[aqui](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
