---
category: general
date: 2026-07-20
description: Inserir gráfico de pizza em Java com um guia passo a passo. Aprenda como
  explodir uma fatia, como girar o gráfico de pizza, destacar a fatia do gráfico de
  pizza e personalizar a fatia do gráfico de pizza.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: pt
lastmod: 2026-07-20
og_description: Insira um gráfico de pizza em Java e domine como explodir fatias,
  girar o gráfico de pizza, destacar fatias do gráfico e personalizar as fatias para
  relatórios visuais refinados.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Inserir Gráfico de Pizza em Java – Explodir, Rotacionar e Destacar
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Inserir Gráfico de Pizza em Java – Explodir, Rotacionar e Destacar Fatias
url: /pt/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir Gráfico de Pizza em Java – Explodir, Rotacionar e Destacar Fatias

Já precisou **inserir gráfico de pizza** em um relatório Java, mas não tinha certeza de como fazer uma única fatia sobressair? Você não está sozinho. Seja construindo um painel, gerando uma fatura ou apenas visualizando os resultados de uma pesquisa, um gráfico de pizza bem‑estilizado pode transformar números brutos em insights instantaneamente compreensíveis.

Neste tutorial você verá um exemplo completo, pronto‑para‑executar, que mostra como inserir um gráfico de pizza, **como explodir uma fatia**, **como rotacionar o gráfico de pizza**, e até **destacar a fatia do gráfico de pizza** com cores personalizadas. Ao final, você terá um trecho reutilizável que pode ser inserido em qualquer projeto Java que use a popular biblioteca *JFreeChart* (ou qualquer API similar).

## Pré-requisitos

- Java 17 ou posterior (o código compila em versões mais antigas, mas usaremos a sintaxe moderna `var` para brevidade).  
- Maven ou Gradle para obter a dependência `org.jfree:jfreechart`.  
- Um entendimento básico de classes Java e do conceito de um construtor de gráficos.  

Se você nunca adicionou uma biblioteca a um projeto Maven, basta inserir isto no seu `pom.xml`:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

É isso—nenhuma configuração extra necessária.

## Etapa 1: Inserir Gráfico de Pizza – Criar o Builder e o Objeto Chart

Primeiro de tudo: precisamos de um *builder* (pense nele como uma fábrica) que saiba como produzir gráficos. No JFreeChart, o `ChartFactory` faz o trabalho pesado.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Por que começamos com o conjunto de dados? Porque o gráfico em si é apenas um invólucro visual em torno dos números. Ao **inserir gráfico de pizza** aqui já temos uma tela de 400 × 300 (o tamanho será aplicado mais tarde quando o renderizarmos para uma imagem).

## Etapa 2: Como Explodir uma Fatia – Enfatizar o Primeiro Segmento

Agora que o gráfico existe, vamos fazer a primeira fatia se destacar. Explodir uma fatia a desloca ligeiramente do círculo, atraindo o olhar do leitor.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Observe que usamos a frase **como explodir uma fatia** no nome do método; isso deixa a intenção cristalina. O método `setExplodePercent` recebe uma chave (o rótulo da fatia) e uma porcentagem, permitindo ajustar a distância de “pop‑out” conforme necessário.

## Etapa 3: Como Rotacionar o Gráfico de Pizza – Alterar o Ângulo Inicial

Um gráfico de pizza padrão começa na posição das 12 horas. Às vezes você quer que a primeira fatia comece em outro lugar—talvez para alinhar com um mock‑up de design ou combinar com outro gráfico.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Chamar `rotateChart(chart, 45)` rotaciona todo o gráfico de pizza para que a fatia “Apples” comece em um ângulo de 45 graus, exatamente o que o requisito **como rotacionar o gráfico de pizza** pede.

## Etapa 4: Destacar a Fatia do Gráfico de Pizza – Cores e Rótulos Personalizados

Além de explodir, você pode querer dar a uma fatia uma cor única ou um rótulo em negrito para realmente **destacar a fatia do gráfico de pizza**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Aqui nós **personalizamos a fatia do gráfico de pizza** alterando sua pintura e estilo de rótulo. Sinta-se à vontade para trocar a cor ou a fonte para combinar com a paleta da sua marca.

## Etapa 5: Renderizar o Gráfico para uma Imagem (Opcional, mas Útil)

A maioria dos aplicativos reais precisa do gráfico como PNG, JPEG ou até PDF. Abaixo está uma maneira rápida de gravar o gráfico em um arquivo.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Executar o fluxo completo produzirá um PNG de 400 × 300 que se parece com isto:

![Exemplo de inserção de gráfico de pizza](image.png){: alt="Exemplo de inserção de gráfico de pizza mostrando uma fatia explodida e rotacionada"}

## Exemplo Completo em Funcionamento

Juntando tudo, aqui está um método `main` que você pode copiar‑colar em uma nova classe Java e executar:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Saída Esperada

Executar o programa cria um arquivo chamado **fruit-pie.png**. Abra‑o e você verá:

- Um gráfico de pizza 400 × 300 intitulado “Fruit Distribution”.  
- A fatia “Apples” explodida para fora em 15 %.  
- Todo o gráfico rotacionado para que “Apples” comece na posição de 45 graus.  
- A explosão

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Inserir Gráfico de Dispersão](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Inserir Gráfico de Área](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}