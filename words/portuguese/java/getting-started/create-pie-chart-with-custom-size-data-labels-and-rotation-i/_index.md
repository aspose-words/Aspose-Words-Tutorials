---
category: general
date: 2026-11-22
description: Crie um gráfico de pizza em Java e aprenda como definir o tamanho do
  gráfico, adicionar rótulos de dados, exibir porcentagens e girar a primeira fatia
  para um impacto visual claro.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: pt
lastmod: 2026-11-22
og_description: Crie um gráfico de pizza em Java, defina o tamanho do gráfico, exiba
  as porcentagens nos rótulos de dados e gire a primeira fatia — tudo em um único
  exemplo executável.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Criar gráfico de pizza com tamanho personalizado, rótulos e rotação em Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Criar gráfico de pizza com tamanho personalizado, rótulos de dados e rotação
  em Java
url: /pt/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar gráfico de pizza com tamanho personalizado, rótulos de dados e rotação em Java

Se você precisa **create pie chart** em Java, este guia o conduz por todo o processo. Você aprenderá como **set chart size**, habilitar **show percentages pie chart**, adicionar **data labels pie chart** e **rotate pie chart slice** para que a primeira fatia comece em um ângulo de 45 graus.

O exemplo usa **Aspose.Slides for Java**, uma biblioteca amplamente utilizada para manipular arquivos PowerPoint. Os mesmos conceitos se aplicam a outras bibliotecas de gráficos; basta substituir as chamadas de API pelos equivalentes em seu conjunto de ferramentas.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou posterior instalado  
* Maven 3.8+ (ou Gradle) para gerenciamento de dependências  
* Um entendimento básico da sintaxe Java  
* Acesso ao binário do Aspose.Slides for Java (você pode obter uma avaliação gratuita no site oficial)

Adicione a dependência ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Criar gráfico de pizza – exemplo completo

O programa a seguir cria um slide PowerPoint que contém um gráfico de pizza com tamanho personalizado, rótulos de dados em porcentagem e a primeira fatia rotacionada.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Por que cada passo importa

| Passo | Objetivo | Como se relaciona com as palavras‑chave |
|------|----------|----------------------------------------|
| **Inserir gráfico** | **Create pie chart** – o objeto principal que renderizará o visual. | Atende diretamente ao requisito *create pie chart*. |
| **Definir dimensões** | A chamada `addChart(..., 400, 300)` demonstra **set chart size**. | Controla a largura (400 px) e a altura (300 px). |
| **Mostrar porcentagens** | `setShowPercentage(true)` faz o gráfico **show percentages pie chart** em cada fatia. | Os usuários frequentemente precisam de porcentagens em vez de valores brutos. |
| **Adicionar rótulos de dados** | A configuração `DataLabelFormat` adiciona **data labels pie chart** com a visibilidade desejada. | Os rótulos melhoram a legibilidade e são personalizáveis. |
| **Rotacionar fatia** | `setFirstSliceAngle(45)` rotaciona o gráfico para que a primeira fatia comece em um ângulo de 45 graus, atendendo **rotate pie chart slice**. | Melhora a ênfase visual de uma fatia específica. |

## Divisão passo a passo

### 1. Inserir um gráfico de pizza e definir o tamanho do gráfico

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*O método `addChart` cria o gráfico e simultaneamente **set chart size** para 400 × 300 pontos.*  
Se precisar de um tamanho diferente, ajuste os dois últimos argumentos.

### 2. Preencher o gráfico com dados

A demonstração adiciona três categorias e uma única série. Substitua os números codificados por dados de um banco de dados, CSV ou entrada do usuário conforme necessário.

### 3. Mostrar porcentagens em cada fatia

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Habilitar `setShowPercentage(true)` garante que o gráfico **show percentages pie chart** calcule automaticamente a participação de cada fatia no total.*

### 4. Adicionar rótulos de dados detalhados

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Você pode alternar outras opções de rótulo (`setShowValue`, `setShowSeriesName`, etc.) para personalizar a experiência de **add data labels pie chart**.

### 5. Rotacionar a primeira fatia

```java
chart.setFirstSliceAngle(45);
```

*Chamar `setFirstSliceAngle(45)` **rotate pie chart slice** para que o primeiro segmento comece em um ângulo de 45 graus, destacando‑o.*

### 6. Salvar e visualizar o resultado

Executar o programa gera `output/PieChartDemo.pptx`. Abra‑o no PowerPoint ou em qualquer visualizador compatível para ver o gráfico de pizza final:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Captura de tela de um gráfico de pizza criado com tamanho personalizado, rótulos de porcentagem e a primeira fatia rotacionada"}

A imagem acima demonstra o resultado do **create pie chart**, confirmando que o tamanho, os rótulos, as porcentagens e a rotação foram aplicados corretamente.

## Variações comuns e casos extremos

| Situação | Ajuste |
|----------|--------|
| **Dimensões diferentes do gráfico** | Altere os parâmetros de largura/altura em `addChart`. |
| **Múltiplas séries** | Adicione objetos `IChartSeries` adicionais; cada série pode ter suas próprias configurações de rótulo. |
| **Formato de rótulo personalizado** | Use `series.getDataLabelFormat().setNumberFormat("0.0%")` para controlar casas decimais. |
| **Rotacionar para outro ângulo** | Passe qualquer inteiro (0‑360) para `setFirstSliceAngle`. |
| **Exportar como imagem** | Após salvar, chame `chart.writeAsSvg(outPath)` ou `chart.writeAsPng(outPath)` para uma versão raster. |

> **Dica profissional:** Se você planeja gerar muitos gráficos em um loop, reutilize o mesmo objeto `Presentation` e substitua apenas os dados do gráfico. Isso reduz o consumo de memória e acelera o processamento.

## Conclusão

Agora você sabe como **create pie chart** em Java, **set chart size**, habilitar **show percentages pie chart**, **add data labels pie chart** e **rotate pie chart slice** para melhor ênfase visual. O exemplo completo e executável demonstra cada passo, desde a inicialização até a gravação do arquivo PowerPoint final.

### O que vem a seguir?

* Explore outros tipos de gráfico (Bar, Line, Area) usando o mesmo enum `ChartType`.  
* Combine vários gráficos em um único slide para dashboards.  
* Exporte gráficos para PNG ou SVG para uso em aplicações web.  

Sinta‑se à vontade para experimentar cores, legendas e efeitos de animação — suas visualizações de dados são limitadas apenas pela imaginação. Boa criação de gráficos!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [como inserir gráfico de pizza no Word – adicionar rótulo de dados percentual](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Como explodir fatia de pizza em Java – tutorial de gráfico Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Inserir gráfico de pizza em Java – Explodir, Rotacionar e Destacar Fatias](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}