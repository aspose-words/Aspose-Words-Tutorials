---
category: general
date: 2026-11-15
description: Aprenda como adicionar um gráfico de pizza a um documento Word com Aspose.Words
  for Java. Inclui conversão para rosquinha, fatia explodida e exemplo completo de
  código.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: pt
lastmod: 2026-11-15
og_description: Adicione um gráfico de pizza a um documento Word usando Aspose.Words
  para Java. Este tutorial mostra como explodir uma fatia e transformar o gráfico
  em um gráfico de rosca.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Adicione um gráfico de pizza a um documento do Word com Java – guia passo
  a passo
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Como inserir um gráfico de pizza em um documento Word usando Java
url: /pt/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar um gráfico de pizza a um documento Word – guia completo em Java

Se você precisar **adicionar um gráfico de pizza a um documento Word** programaticamente, este tutorial mostra exatamente como fazer isso com Aspose.Words for Java. Você verá todo o fluxo de trabalho: carregar um DOCX, criar um gráfico de pizza, explodir a primeira fatia e converter o gráfico em um donut definindo o tamanho do buraco.

O guia também cobre variações comuns — como adicionar múltiplas séries, personalizar cores e lidar com documentos que já contêm gráficos — para que você possa adaptar o código a projetos reais, como relatórios automatizados ou apresentações dinâmicas.

## Pré-requisitos

* Java 17 ou posterior (o código também compila com JDK 11+)
* Maven 3.6+ ou Gradle para gerenciamento de dependências
* Uma licença Aspose.Words for Java (a versão de avaliação gratuita funciona para testes)
* Um entendimento básico da sintaxe Java e da estrutura de projetos Maven

## Etapa 1: Configurar o projeto Maven e importar Aspose.Words

Crie um novo projeto Maven (ou adicione a um existente) e inclua a dependência Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Dica profissional:** Se você usar Gradle, a entrada equivalente é `implementation 'com.aspose:aspose-words:24.9'`.

A dependência traz as classes `Document`, `Chart` e `ChartType` que você precisará para manipular gráficos.

## Etapa 2: Carregar o documento alvo

Você pode começar a partir de um arquivo `.docx` existente ou criar um novo documento em branco. O exemplo abaixo carrega um modelo chamado `input.docx` localizado na pasta `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Se o arquivo não existir, o Aspose.Words criará automaticamente um novo documento vazio ao chamar `new Document()` sem um nome de arquivo.

## Etapa 3: Criar um gráfico de pizza e inseri‑lo no documento

O Aspose.Words trata um gráfico como uma forma que pode ser posicionada onde um parágrafo pode aparecer. O código a seguir cria um **gráfico de pizza**, adiciona uma única série de dados e insere o gráfico após o primeiro parágrafo.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Por que esta etapa é importante:**  
* `ChartType.PIE` indica ao Aspose.Words que deve renderizar um gráfico de pizza tradicional.  
* Adicionar uma série com rótulos de categoria e valores numéricos preenche as fatias automaticamente.  
* Inserir o gráfico como filho de um `Paragraph` mantém o fluxo do documento intacto.

## Etapa 4: Explodir a primeira fatia para destacá‑la

Uma *fatia explodida* chama a atenção para um ponto de dados específico. A API expõe `setExplode(boolean)` em um objeto `ChartSeries`. Definir isso na primeira série (índice 0) faz com que a primeira fatia se destaque.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Pergunta comum:** *E se eu tiver várias séries?*  
> Você pode direcionar uma série específica pelo seu índice, por exemplo, `pieChart.getSeries().get(1).setExplode(true)` para a segunda série.

## Etapa 5: Converter o gráfico de pizza em um donut definindo o tamanho do buraco

Um gráfico de donut é essencialmente um gráfico de pizza com um centro oco. O Aspose.Words permite definir o tamanho do buraco como uma porcentagem do raio do gráfico.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

O método `setHoleSize` aceita valores de **0** (pizza normal) a **100** (totalmente vazio). Um valor em torno de **30‑40** produz um donut visualmente equilibrado.

## Etapa 6: Salvar e verificar o resultado

Após todas as modificações, salve o documento. A linha a seguir grava o arquivo na pasta `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Saída esperada

Abra `final-pie-doughnut.docx` no Microsoft Word:

* Um gráfico de donut aparece onde estava o primeiro parágrafo.
* A fatia “Apples” está explodida (ligeiramente separada das demais).
* O gráfico mostra quatro fatias rotuladas *Apples*, *Bananas*, *Cherries*, *Dates* com as porcentagens fornecidas.

Se preferir saída em PDF, altere o `SaveFormat` para `SaveFormat.PDF`.

## Tratamento de casos limites e variações

### Adicionando múltiplas séries

Se precisar de várias séries (por exemplo, donut empilhado), adicione‑as sequencialmente:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Cores personalizadas

Você pode atribuir uma cor a cada fatia via `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Trabalhando com um gráfico existente

Se o documento já contém um gráfico e você deseja apenas modificá‑lo, localize a forma do gráfico:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Manipulação de licença

O Aspose.Words requer uma licença para uso em produção. Coloque seu arquivo `Aspose.Words.lic` no classpath e carregue‑o na inicialização da aplicação:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Não definir uma licença adicionará uma marca d'água ao documento gerado.

## Exemplo completo e executável

Abaixo está a classe Java completa que incorpora todas as etapas discutidas. Copie‑a para `src/main/java/com/example/AddPieChart.java` e execute `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Executar o programa gera o gráfico de donut descrito anteriormente. Ajuste `categories`, `values` ou `holeSize` conforme seus dados.

## Conclusão

Agora você sabe como **adicionar um gráfico de pizza a um documento Word** usando Java e Aspose.Words. O tutorial abordou o carregamento de um documento, a criação de um gráfico de pizza, a explosão de uma fatia, a conversão do gráfico em um donut e o tratamento de variações comuns, como múltiplas séries, cores personalizadas e gráficos existentes. Com essa base, você pode criar ferramentas de relatórios automatizados, gerar apresentações dinâmicas ou incorporar visualizações ricas diretamente em arquivos Word.

### O que explorar a seguir

* **add bar chart to Word document** – passos semelhantes, mas use `ChartType.BAR`.
* **customize chart legends and titles** – use `pieChart.getTitle().setText("...")` e `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.
* **export the Word document as PDF** – altere o `SaveFormat` para `PDF` para arquivos prontos para distribuição.
* **populate chart data from a database** – substitua os arrays estáticos por resultados de consultas JDBC.

Sinta‑se à vontade para experimentar diferentes tipos de gráficos, fontes de dados e opções de estilo. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como explodir a fatia de pizza em Java – tutorial de gráfico Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Criar gráfico de pizza com Aspose.Words Java – Guia completo passo a passo](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}