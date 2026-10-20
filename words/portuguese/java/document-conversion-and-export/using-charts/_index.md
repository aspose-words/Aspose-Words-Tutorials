---
date: 2025-12-13
description: Aprenda a criar um gráfico de colunas e formatar os rótulos de dados
  do gráfico com Aspose.Words para Java. Explore a adição de várias séries, a alteração
  do tipo de eixo e a ocultação do eixo do gráfico.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Como criar gráfico de colunas usando Aspose.Words para Java
url: /pt/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um gráfico de colunas usando Aspose.Words para Java

Neste tutorial você **criará visualizações de gráfico de colunas** diretamente dentro de documentos Word usando Aspose.Words para Java. Vamos percorrer a criação de diferentes tipos de gráfico, a adição de múltiplas séries, a formatação de rótulos de dados do gráfico, a alteração do tipo de eixo e até mesmo a ocultação de um eixo do gráfico quando precisar de um visual mais limpo. Ao final, você terá uma abordagem sólida e pronta para produção para incorporar gráficos ricos em seus documentos.

## Respostas Rápidas
- **Qual é a classe principal para construir um gráfico?** `DocumentBuilder` com `insertChart`.
- **Qual método adiciona uma nova série?** `chart.getSeries().add(...)`.
- **Como formato os rótulos de dados do gráfico?** Use `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Posso ocultar um eixo?** Sim, chame `setHidden(true)` no objeto do eixo.
- **Preciso de licença para Aspose.Words?** Uma licença é necessária para uso em produção; uma versão de avaliação gratuita está disponível.

## O que é um gráfico de colunas e por que usá-lo?

Um gráfico de colunas exibe dados categóricos como barras verticais, tornando-o ideal para comparar valores entre grupos (vendas por região, despesas mensais, etc.). Em aplicações Java, gerar um gráfico de colunas com Aspose.Words permite incorporar esses visuais diretamente em arquivos Word / DOCX sem precisar do Excel ou de ferramentas externas.

## Como criar um gráfico de colunas

Abaixo está um exemplo simples que cria um gráfico de colunas básico. O código é idêntico ao trecho original – adicionamos apenas comentários explicativos para facilitar o entendimento.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Adicionar múltiplas séries

Você pode **adicionar múltiplas séries** a um gráfico de colunas chamando `chart.getSeries().add(...)` repetidamente, como mostrado acima. Cada série pode ter seu próprio conjunto de categorias e valores, permitindo comparar vários conjuntos de dados lado a lado.

## Como criar um gráfico de linhas com rótulos de dados personalizados

Se precisar de um gráfico de linhas em vez de um gráfico de colunas, o mesmo padrão se aplica. Este exemplo também demonstra **formatar rótulos de dados do gráfico** com diferentes formatos numéricos.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

### Adicionar rótulos de dados

A chamada `series1.hasDataLabels(true)` **adiciona rótulos de dados** à série, enquanto `setShowValue(true)` torna os valores reais visíveis no gráfico.

## Como alterar o tipo de eixo e personalizar propriedades do eixo

Alterar o tipo de eixo (por exemplo, de data para categoria) permite controlar como os pontos de dados são plotados. Este trecho também mostra como **ocultar o eixo do gráfico** se preferir um design minimalista.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Alterar tipo de eixo

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **altera o tipo de eixo** de um eixo baseado em datas para um eixo categórico, dando controle total sobre a colocação dos rótulos.

## Como formatar rótulos de dados do gráfico (formatos numéricos)

Você pode aplicar formatação numérica diretamente ao eixo ou aos rótulos de dados. Este exemplo formata os números do eixo Y com um separador de milhares.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Personalizações adicionais de gráficos

Além do básico, você pode ajustar limites, definir unidades de intervalo entre rótulos, ocultar eixos específicos e muito mais. Consulte a documentação da API Aspose.Words para Java para obter uma lista completa de propriedades.

## Perguntas Frequentes

**Q: Como posso adicionar múltiplas séries a um gráfico?**  
A: Use `chart.getSeries().add()` para cada série que desejar exibir. Cada chamada pode fornecer um nome exclusivo, um array de categorias e um array de valores.

**Q: Como formato rótulos de dados do gráfico com formatos numéricos personalizados?**  
A: Acesse o objeto `DataLabels` de uma série e chame `getNumberFormat().setFormatCode("seu formato")`. Você também pode vincular o formato a uma célula de origem com `isLinkedToSource(true)`.

**Q: Como posso ocultar um eixo do gráfico?**  
A: Chame `setHidden(true)` no `ChartAxis` que deseja ocultar (por exemplo, `chart.getAxisY().setHidden(true)`).

**Q: Qual a melhor forma de alterar o tipo de eixo?**  
A: Use `setCategoryType(AxisCategoryType.CATEGORY)` para eixos categóricos ou `AxisCategoryType.DATE` para eixos de data.

**Q: Como adiciono rótulos de dados a uma série?**  
A: Habilite-os com `series.hasDataLabels(true)` e então configure a visibilidade usando `series.getDataLabels().setShowValue(true)`.

## Conclusão

Cobremos tudo o que você precisa para **criar visualizações de gráfico de colunas** com Aspose.Words para Java — desde inserir gráficos básicos e adicionar múltiplas séries, até formatar rótulos de dados, alterar o tipo de eixo e ocultar eixos para um visual limpo. Incorpore essas técnicas em seus pipelines de relatórios ou geração de documentos para entregar documentos Word profissionais e orientados por dados.

---

**Última atualização:** 2025-12-13  
**Testado com:** Aspose.Words para Java 24.12 (mais recente)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}