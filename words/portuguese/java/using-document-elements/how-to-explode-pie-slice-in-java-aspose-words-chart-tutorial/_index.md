---
category: general
date: 2026-08-07
description: Como explodir fatia de pizza em Java usando Aspose.Words. Aprenda a adicionar
  linhas de ligação ao gráfico de pizza, criar gráfico no Word e personalizar as fatias
  do gráfico de pizza.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: pt
lastmod: 2026-08-07
og_description: Como explodir uma fatia de pizza em Java com Aspose.Words. Este guia
  mostra como adicionar linhas de ligação ao gráfico de pizza, criar gráficos no Word
  e personalizar as fatias do gráfico de pizza para um impacto visual claro.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Como explodir uma fatia de pizza em Java – Guia Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Como explodir fatia de pizza em Java – tutorial de gráfico Aspose.Words
url: /pt/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como explodir fatia de pizza em Java – tutorial de gráfico Aspose.Words

Se você precisa saber **como explodir uma fatia de pizza** em um documento Word usando Java, este tutorial tem tudo o que você precisa. Também mostraremos **como adicionar linhas de ligação a gráficos de pizza**, **java create word chart** objects, e **customize pie chart slices** para um resultado refinado. Ao final deste guia, você terá um exemplo completo e executável que pode ser inserido em qualquer projeto Java.

![Como explodir fatia de pizza em Java – gráfico Aspose.Words](/images/pie-chart-exploded.png)

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java Development Kit (JDK) 8 ou superior.
* Maven ou Gradle para gerenciamento de dependências.
* Uma licença Aspose.Words for Java (a avaliação gratuita funciona para fins de aprendizado).
* Familiaridade básica com a sintaxe Java e conceitos orientados a objetos.

> **Dica profissional:** Embora o Aspose.Words ofereça um teste gratuito, a compra de uma licença remove a marca d'água de avaliação dos documentos gerados.

## O que este tutorial cobre

* Criar um novo documento Word do zero.  
* Inserir um **pie chart** usando o `DocumentBuilder`.  
* **Exploding a pie slice** para destacar um ponto de dados.  
* **Adding leader lines to pie** para rotulagem mais clara.  
* Personalizar a aparência das fatias, como cores e bordas.  
* Salvar o documento no disco e verificar o resultado.

---

## Como explodir uma fatia de pizza com Aspose.Words em Java

O primeiro passo é configurar o objeto de gráfico e explodir a fatia desejada. O Aspose.Words expõe o gráfico através da classe `Shape`, e cada fatia é um `ChartPoint`. Definindo a propriedade `Explosion` você controla o quão longe a fatia se desloca para fora.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Por que funciona:**  
`setExplosion(20)` informa ao mecanismo de gráfico para deslocar a fatia em 20 pontos a partir do centro do gráfico. O valor é relativo; números maiores criam um efeito mais dramático. Você pode explodir qualquer fatia alterando o índice (`get(1)`, `get(2)`, …).

## Adicionar linhas de ligação ao gráfico de pizza para rótulos mais claros

Linhas de ligação conectam o rótulo de uma fatia à sua borda, o que é especialmente útil quando as fatias estão explodidas ou quando o gráfico contém muitas seções pequenas. A chamada `setLeaderLines(true)` habilita esse recurso para toda a série.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Por que você precisa de linhas de ligação:**  
Quando uma fatia está explodida, o rótulo padrão pode sobrepor‑se a outros elementos. As linhas de ligação mantêm o rótulo legível ao desenhar uma linha curta da fatia até a caixa de texto.

## Java create Word chart – inserindo séries de dados

Um gráfico sem dados não é muito útil. Você deve preencher as séries com categorias e valores. Abaixo adicionamos três categorias que representam a participação de mercado.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Explicação:**  
`ChartSeries` contém tanto as categorias (os nomes das fatias) quanto os valores numéricos. Habilitar `ShowCategoryName` e `ShowPercentage` torna o gráfico autoexplicativo, o que combina bem com as linhas de ligação que adicionamos anteriormente.

## Personalizar fatias de gráfico de pizza além da explosão

Além de explodir uma fatia, você frequentemente deseja ajustar cores, bordas ou até mesmo ocultar uma fatia completamente. O trecho a seguir demonstra três personalizações comuns:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Por que personalizar as fatias:**  
Cores personalizadas fazem o gráfico alinhar‑se à identidade corporativa, enquanto bordas melhoram a legibilidade em páginas impressas. Ocultar uma fatia é útil quando você deseja manter o modelo de dados intacto, mas omitir temporariamente uma categoria da saída visual.

## Salvar o documento e verificar o resultado

Por fim, grave o documento no disco. Você pode abrir o `.docx` gerado no Microsoft Word, LibreOffice ou qualquer visualizador que suporte o formato.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Saída esperada:**  
Ao abrir `PieChartDemo.docx`, você verá um gráfico de pizza onde a primeira fatia (Product A) está explodida para fora, linhas de ligação apontam de cada fatia para seu rótulo, e as fatias aparecem nas cores verde, azul e laranja personalizadas. A fatia oculta (Product C) não será visível, mas as porcentagens ainda somarão 100 % porque os dados permanecem nas séries do gráfico.

---

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar, colar e executar após adicionar a dependência Aspose.Words ao seu projeto.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Dependência (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Como carregar documentos Word com Aspose.Words Java: Guia abrangente](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}