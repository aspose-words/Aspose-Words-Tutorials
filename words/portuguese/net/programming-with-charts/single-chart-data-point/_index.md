---
title: Personalize um único ponto de dados do gráfico em um gráfico
linktitle: Personalize um único ponto de dados do gráfico em um gráfico
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a personalizar pontos de dados de gráficos únicos usando o Aspose.Words para .NET em um guia detalhado passo a passo. Aprimore seus gráficos com marcadores e tamanhos exclusivos.
weight: 10
url: /pt/net/programming-with-charts/single-chart-data-point/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Personalize um único ponto de dados do gráfico em um gráfico

## Introdução

Já se perguntou como você pode fazer seus gráficos se destacarem com pontos de dados exclusivos? Bem, hoje é seu dia de sorte! Estamos mergulhando na personalização de um único ponto de dados de gráfico usando o Aspose.Words para .NET. Aperte o cinto para um passeio por um tutorial passo a passo que não é apenas informativo, mas também divertido e fácil de seguir.

## Pré-requisitos

Antes de começar, vamos garantir que você tenha todos os elementos essenciais em mãos:

-  Biblioteca Aspose.Words para .NET: certifique-se de ter a versão mais recente.[Baixe aqui](https://releases.aspose.com/words/net/).
- .NET Framework: certifique-se de ter o .NET Framework instalado na sua máquina.
- Noções básicas de C#: Uma noção básica de programação em C# será útil.
- Ambiente de Desenvolvimento Integrado (IDE): o Visual Studio é recomendado.

## Importar namespaces

Primeiramente, vamos importar os namespaces necessários para começar:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Etapa 1: inicializar o documento e o DocumentBuilder

Certo, vamos começar inicializando um novo documento e um DocumentBuilder. Este será o canvas para nosso gráfico.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Aqui,`dataDir` é o caminho do diretório onde você salvará seu documento. O`DocumentBuilder` A classe ajuda na construção do documento.

## Etapa 2: Insira um gráfico

Em seguida, vamos inserir um gráfico de linhas no documento. Este será nosso playground para personalizar pontos de dados.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

 O`InsertChart` O método pega o tipo de gráfico, largura e altura como parâmetros. Neste caso, estamos inserindo um gráfico de linhas com largura de 432 e altura de 252.

## Etapa 3: Acesse a série de gráficos

Agora, é hora de acessar a série dentro do nosso gráfico. Um gráfico pode ter várias séries, e cada série contém pontos de dados.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Aqui, estamos acessando as duas primeiras séries do nosso gráfico. 

## Etapa 4: personalizar pontos de dados

É aqui que a mágica acontece! Vamos personalizar pontos de dados específicos dentro de nossa série.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

Estamos buscando os pontos de dados da primeira série. Agora, vamos personalizar esses pontos.

### Personalizar ponto de dados 00

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

 Para`dataPoint00`, estamos definindo uma explosão (útil para gráficos de pizza), alterando o símbolo do marcador para um círculo e definindo o tamanho do marcador para 15.

### Personalizar ponto de dados 01

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

 Para`dataPoint01`, estamos mudando o símbolo do marcador para um losango e definindo o tamanho do marcador para 20.

### Personalizar ponto de dados na série 1

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

 Para o terceiro ponto de dados em`series1`, estamos configurando para inverter se o valor for negativo, alterando o símbolo do marcador para uma estrela e definindo o tamanho do marcador para 20.

## Etapa 5: Salve o documento

Por fim, vamos salvar nosso documento com todas as personalizações.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

 Esta linha salva o documento no diretório especificado com o nome`WorkingWithCharts.SingleChartDataPoint.docx`.

## Conclusão

aí está! Você personalizou com sucesso pontos de dados individuais em um gráfico usando o Aspose.Words para .NET. Ajustando algumas propriedades, você pode tornar seus gráficos muito mais informativos e visualmente atraentes. Então, vá em frente e experimente diferentes marcadores e tamanhos para ver o que funciona melhor para seus dados.

## Perguntas frequentes

### Posso personalizar pontos de dados em outros tipos de gráficos?

Com certeza! Você pode personalizar pontos de dados em vários tipos de gráficos, incluindo gráficos de barras, gráficos de pizza e muito mais. O processo é semelhante em diferentes tipos de gráficos.

### É possível adicionar rótulos personalizados aos pontos de dados?

 Sim, você pode adicionar rótulos personalizados aos pontos de dados usando o`ChartDataPoint.Label` propriedade. Isso permite que você forneça mais contexto para cada ponto de dados.

### Como posso remover um ponto de dados de uma série?

 Você pode remover um ponto de dados definindo sua visibilidade como falsa usando`dataPoint.IsVisible = false`.

### Posso usar imagens como marcadores para pontos de dados?

Embora o Aspose.Words não suporte o uso de imagens diretamente como marcadores, você pode criar formas personalizadas e usá-las como marcadores.

### É possível animar pontos de dados no gráfico?

O Aspose.Words para .NET não suporta animação para pontos de dados de gráficos. No entanto, você pode criar gráficos animados usando outras ferramentas e incorporá-los em seus documentos do Word.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
