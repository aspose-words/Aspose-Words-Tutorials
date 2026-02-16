---
date: 2026-02-16
description: Aprenda como adicionar várias séries a gráficos no Aspose.Words for Java,
  alterar as marcas de escala dos eixos, aplicar um formato numérico personalizado
  e gerar documentos Word com gráficos de linhas e colunas.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Adicionar múltiplas séries a gráficos no Aspose.Words para Java
url: /pt/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar Múltiplas Séries a Gráficos no Aspose.Words para Java

## Introdução ao Uso de Gráficos no Aspose.Words para Java

Neste tutorial você aprenderá **como adicionar múltiplas séries** a um gráfico usando Aspose.Words para Java, por que personalizar as marcas de escala dos eixos e aplicar um formato numérico personalizado é importante, e como gerar um documento Word rico em gráficos. Seja para criar um gráfico de linhas para dados financeiros ou um gráfico de colunas para números de vendas, os passos abaixo orientarão você na criação, estilização e ajuste fino de gráficos programaticamente.

## Respostas Rápidas
- **Como adiciono múltiplas séries?** Use `chart.getSeries().add(...)` para cada série que deseja exibir.  
- **Posso mudar as marcas de escala dos eixos?** Sim – use `setMajorTickMark()` e `setMinorTickMark()` nos objetos de eixo.  
- **Qual formato posso aplicar aos rótulos de dados?** Qualquer formato numérico compatível com Excel, por exemplo, `"$"#,##0.00` ou `0.00%`.  
- **Quais tipos de gráfico são suportados?** Linha, coluna, área, bolha, dispersão e muitos outros via `ChartType`.  
- **É necessária uma licença para produção?** Uma licença válida do Aspose.Words para Java é necessária para funcionalidade completa.

## O que significa “adicionar múltiplas séries” em um gráfico?
Adicionar múltiplas séries significa inserir mais de um conjunto de dados na mesma área do gráfico, permitindo comparar diferentes categorias ou períodos lado a lado. Cada série aparece como sua própria linha, coluna ou conjunto de marcadores, proporcionando ao leitor uma história visual mais rica.

## Por que usar Aspose.Words para Java para gerar documentos Word com gráficos?
- **Controle total** sobre o tipo de gráfico, layout e estilo sem abrir o Word manualmente.  
- **Geração programática** que se encaixa em pipelines de relatórios automatizados.  
- **Multiplataforma** – funciona em qualquer ambiente compatível com Java.  
- **API rica** para personalizar eixos, rótulos de dados e formatos numéricos.

## Pré‑requisitos
- Java Development Kit (JDK) 8 ou superior.  
- Biblioteca Aspose.Words para Java adicionada ao seu projeto (Maven/Gradle ou JAR).  
- Uma licença válida do Aspose para produção (opcional para avaliação).

## Guia Passo a Passo

### Etapa 1: Crie um gráfico de linhas e **adicione múltiplas séries**
Abaixo está o código principal que cria um gráfico de linhas, limpa as séries padrão e, em seguida, adiciona três séries distintas com rótulos de dados personalizados.

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

> **Dica profissional:** Chame `chart.getSeries().add(...)` quantas vezes for necessário para **adicionar múltiplas séries** – cada chamada cria uma nova linha (ou coluna, etc.) no mesmo gráfico.

### Etapa 2: **Crie um gráfico de colunas** (create column chart java)
O próximo trecho mostra como inserir um gráfico de colunas simples, útil para comparar categorias lado a lado.

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

### Etapa 3: **Mude as marcas de escala dos eixos** (change axis tick marks)
Personalizar os eixos X e Y melhora a legibilidade. O código a seguir demonstra como alterar as marcas de escala, inverter a ordem e definir pontos de cruzamento personalizados.

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

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Etapa 4: **Aplique um formato numérico personalizado** (apply custom number format)
Você pode formatar números dos eixos ou rótulos de dados com qualquer padrão suportado pelo Excel. Abaixo está um exemplo conciso que formata o eixo Y com um padrão de separador de milhar.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Etapa 5: Gere o documento Word final (generate chart word document)
Após configurar séries, eixos e rótulos, basta chamar `doc.save(...)` conforme mostrado nos trechos acima. O arquivo `.docx` resultante contém gráficos totalmente funcionais que podem ser abertos e editados no Microsoft Word.

## Casos de Uso Comuns
- **Painéis financeiros** – gráficos de linhas com múltiplas séries para receita, despesas e lucro.  
- **Relatórios de vendas** – gráficos de colunas comparando vendas trimestrais por região.  
- **Acompanhamento de projetos** – gráficos de área ou dispersão visualizando o progresso ao longo do tempo.  

## Personalizações Adicionais de Gráficos
Além do básico, você pode ajustar limites, ocultar eixos (`axis.setHidden(true)`), mudar cores, adicionar legendas e muito mais. Consulte a referência da API Aspose.Words para Java para a lista completa de opções.

## Conclusão
Neste guia abordamos como **adicionar múltiplas séries** a gráficos, criar gráficos de linhas e colunas, **mudar as marcas de escala dos eixos**, **aplicar formatos numéricos personalizados** e, finalmente, **gerar um documento Word rico em gráficos**. Com Aspose.Words para Java você tem uma maneira poderosa, orientada a código, de incorporar visualizações de dados profissionais diretamente em seus documentos.

## Perguntas Frequentes

**Q: Como posso adicionar múltiplas séries a um gráfico?**  
A: Chame `chart.getSeries().add()` para cada série que deseja exibir. Cada chamada cria um novo conjunto de dados que aparece como sua própria linha, coluna ou grupo de marcadores.

**Q: Como formato rótulos de dados com um formato numérico personalizado?**  
A: Acesse o objeto `DataLabels` da série e use `getNumberFormat().setFormatCode("seu padrão")`. Também é possível vincular o formato a uma célula de origem com `isLinkedToSource(true)`.

**Q: Como posso mudar as marcas de escala dos eixos?**  
A: Use `setMajorTickMark()` e `setMinorTickMark()` em `ChartAxis`. As opções incluem `CROSS`, `INSIDE`, `OUTSIDE` e `NONE`.

**Q: Posso criar outros tipos de gráfico, como dispersão ou área?**  
A: Sim – especifique o `ChartType` desejado (por exemplo, `ChartType.SCATTER`, `ChartType.AREA`) ao chamar `builder.insertChart(...)`.

**Q: Como oculto um eixo que não preciso?**  
A: Chame `axis.setHidden(true)` no `ChartAxis` que deseja ocultar.

**Última atualização:** 2026-02-16  
**Testado com:** Aspose.Words para Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}