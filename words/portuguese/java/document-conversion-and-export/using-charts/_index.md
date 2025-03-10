---
title: Usando gráficos no Aspose.Words para Java
linktitle: Usando gráficos
second_title: API de processamento de documentos Java Aspose.Words
description: Aprenda a criar e personalizar gráficos no Aspose.Words para Java. Explore tipos de gráficos, formatação e propriedades de eixo para visualização de dados.
weight: 12
url: /pt/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Usando gráficos no Aspose.Words para Java


## Introdução ao uso de gráficos no Aspose.Words para Java

Neste tutorial, exploraremos como trabalhar com gráficos usando o Aspose.Words para Java. Você aprenderá a criar vários tipos de gráficos, personalizar propriedades de eixo, formatar rótulos de dados e muito mais. Vamos mergulhar!

## Criando um gráfico de linhas

Para criar um gráfico de linhas, use o seguinte código:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Excluir série gerada padrão.
chart.getSeries().clear();

// Adicionando uma série com dados e rótulos de dados.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Ou vincule o código de formato a uma célula de origem.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Criando outros tipos de gráficos

Você pode criar diferentes tipos de gráficos como coluna, área, bolha, dispersão e mais usando técnicas semelhantes. Aqui está um exemplo de inserção de um gráfico de coluna simples:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Excluir série gerada padrão.
chart.getSeries().clear();

// Criando categorias e adicionando dados.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Personalizando propriedades do eixo

Você pode personalizar as propriedades do eixo, como alterar o tipo do eixo, definir marcas de escala, formatar rótulos e muito mais. Aqui está um exemplo de definição das propriedades do eixo XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Limpe as séries padrão e adicione seus dados.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Altere o eixo X para ser uma categoria em vez de uma data.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); //Medido em unidades de exibição do eixo Y (centenas).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Formatando rótulos de dados

Você pode formatar rótulos de dados com diferentes formatos de números. Aqui está um exemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Limpe as séries padrão e adicione seus dados.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Personalizações adicionais de gráficos

Você pode personalizar ainda mais seus gráficos ajustando limites, unidades de intervalo entre rótulos, ocultando eixos de gráficos e muito mais. Explore os snippets de código fornecidos para saber mais sobre essas opções.

## Conclusão

Neste tutorial, exploramos como trabalhar com gráficos usando o Aspose.Words para Java. Você aprendeu a criar vários tipos de gráficos, personalizar propriedades de eixo, formatar rótulos de dados e muito mais. O Aspose.Words para Java fornece ferramentas poderosas para adicionar representações visuais de dados aos seus documentos, aprimorando a maneira como você apresenta informações.

## Perguntas frequentes

### Como posso adicionar várias séries a um gráfico?

 Você pode adicionar várias séries a um gráfico usando o`chart.getSeries().add()` método. Certifique-se de especificar o nome da série, categorias e valores de dados.

### Como posso formatar rótulos de dados com formatos numéricos personalizados?

Você pode formatar rótulos de dados acessando o`DataLabels` propriedades de uma série e definindo o código de formato desejado usando`getNumberFormat().setFormatCode()`.

### Como posso personalizar as propriedades do eixo em um gráfico?

 Você pode personalizar as propriedades do eixo, como tipo, marcas de escala, rótulos e muito mais acessando o`ChartAxis` propriedades como`setCategoryType()`, `setCrosses()` , e`setMajorTickMark()`.

### Como posso criar outros tipos de gráficos, como gráficos de dispersão ou de área?

 Você pode criar vários tipos de gráficos especificando o apropriado`ChartType` ao inserir o gráfico usando`builder.insertChart(ChartType.TYPE, width, height)`.

### Como posso ocultar um eixo do gráfico?

 Você pode ocultar um eixo do gráfico definindo o`setHidden(true)` propriedade do eixo.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
