---
category: general
date: 2026-08-20
description: Adicione linhas de chamada ao gráfico de pizza em Java rapidamente. Aprenda
  a inserir, explodir, recolorir e rotular fatias usando a API de Chart.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: pt
lastmod: 2026-08-20
og_description: Adicione linhas de ligação ao gráfico de pizza em Java com um exemplo
  conciso. Siga este guia para inserir, explodir, recolorir e rotular fatias usando
  a API Chart.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Adicionar linhas de ligação ao gráfico de pizza em Java – guia passo a passo
  da API de gráficos
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Como adicionar linhas de ligação ao gráfico de pizza em Java com a API de Chart
url: /pt/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar linhas de ligação a um gráfico de pizza em Java com a Chart API

Se você precisa **adicionar linhas de ligação a um gráfico de pizza** em Java, este guia o conduzirá por todo o processo. Você verá como inserir um gráfico de pizza, explodir uma fatia para ênfase, mudar sua cor e, finalmente, habilitar linhas de ligação que rotulam o segmento explodido.

O exemplo usa a Chart API padrão encontrada em muitas bibliotecas de relatórios Java. Nenhuma ferramenta externa é necessária, e o código roda em qualquer ambiente JDK 8+.

## O que você alcançará

* Criar um `Chart` do tipo `ChartType.PIE` com um tamanho personalizado.  
* Explodir a primeira fatia para chamar atenção.  
* Definir a cor do setor da fatia explodida como azul.  
* **Adicionar linhas de ligação a um gráfico de pizza** para que o rótulo da fatia esteja claramente conectado.

Você já deve ter um projeto Java com a biblioteca Chart no classpath. Se estiver usando Maven, adicione a dependência mostrada na seção de pré-requisitos.

## Pré-requisitos

* JDK 8 ou mais recente instalado.  
* A biblioteca Chart (por exemplo, `com.example.chart:chart-api:2.5.0`).  
* Familiaridade básica com classes Java e chamadas de método.

---

## Como adicionar linhas de ligação a um gráfico de pizza

Abaixo está um programa completo e executável que demonstra cada passo. O código foi deliberadamente autônomo para que você possa copiar, colar e executá-lo sem modificações.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Explicação de cada passo

| Passo | O que o código faz | Por que isso importa |
|------|-------------------|----------------|
| **1️⃣ Inserir um gráfico de pizza** | `builder.insertChart(ChartType.PIE, 400, 300)` cria um gráfico de pizza de 400 × 300 pixels. | Estabelece o contêiner do gráfico e define suas dimensões, o que afeta o posicionamento dos rótulos e o comprimento das linhas de ligação. |
| **2️⃣ Explodir a primeira fatia** | `setExplosion(20)` desloca a fatia em 20 % do raio. | Uma fatia explodida chama a atenção do observador e torna a linha de ligação visível. |
| **3️⃣ Definir cor do setor** | `setSectorColor(Color.BLUE)` altera o preenchimento da fatia para azul. | O contraste de cores melhora a legibilidade, especialmente quando a fatia está destacada. |
| **4️⃣ Habilitar linhas de ligação** | `setLeaderLines(true)` ativa as linhas de conexão que ligam a fatia ao seu rótulo. | As linhas de ligação garantem que o rótulo permaneça legível mesmo quando a fatia é movida para fora. |

A chamada `saveAsPng` é opcional, mas útil para verificar o resultado visual. Após executar o programa, você deverá ver uma imagem semelhante à abaixo.

![Adicionar linhas de ligação a um gráfico de pizza](https://example.com/assets/pie-leader-lines.png "Adicionar linhas de ligação a um gráfico de pizza – fatia explodida com cor azul e linhas de ligação")

*Figura: Um gráfico de pizza onde a primeira fatia está explodida, colorida de azul, e conectada ao seu rótulo por uma linha de ligação.*

## Personalizando linhas de ligação (avançado)

A chamada básica `setLeaderLines(true)` usa o estilo padrão da biblioteca. Você pode controlar ainda mais a aparência:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Essas opções são úteis quando você precisa combinar com a identidade corporativa ou melhorar a acessibilidade.

### Manipulando múltiplas séries

Se o seu gráfico de pizza contém mais de uma série, talvez queira linhas de ligação apenas para uma fatia específica. Use o índice da série para direcionar o elemento correto:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Quando uma fatia não está explodida, a linha de ligação geralmente é ocultada automaticamente, mas você pode forçá‑la com `setLeaderLineEnabled(true)`.

## Armadilhas comuns e como evitá‑las

| Armadilha | Sintoma | Correção |
|----------|---------|----------|
| **Linhas de ligação não visíveis** | O gráfico é renderizado sem conectores. | Certifique‑se de que a fatia está explodida (`setExplosion` > 0) ou habilite explicitamente as linhas de ligação na fatia. |
| **Sobreposição de rótulos** | Os rótulos colidem entre si. | Aumente o tamanho do gráfico ou defina `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Cor não aplicada** | A fatia permanece com a cor padrão. | Verifique se está direcionando o índice de série correto (`getSeries().get(0)`). |
| **Imagem não salva** | `saveAsPng` lança uma exceção. | Verifique as permissões de gravação do diretório de saída e se a biblioteca suporta exportação PNG. |

Abordar esses problemas cedo evita surpresas em tempo de execução e produz um gráfico refinado.

## Listagem completa do código-fonte

Para sua conveniência, aqui está o arquivo fonte completo novamente, incluindo importações e comentários:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Executar este programa gera `pie-with-leader-lines.png`, que exibe um gráfico de pizza com uma fatia azul explodida e linhas de ligação claras apontando para o rótulo da fatia.

## Conclusão

Agora você sabe como **adicionar linhas de ligação a um gráfico de pizza** em Java usando a Chart API. O processo consiste em inserir um `ChartType.PIE`, explodir a fatia desejada, personalizar sua cor e habilitar linhas de ligação. Com as opções de estilo opcionais, você pode ajustar finamente a cor da linha, espessura e posicionamento do rótulo para atender a qualquer requisito visual.

Em seguida, considere explorar tópicos relacionados como **explosão de gráfico de pizza Java**, **set sector color Chart API**, e **uso de builder.insertChart** para criar visualizações mais sofisticadas, como gráficos de rosca, pizzas empilhadas ou painéis interativos.

Fique à vontade para experimentar diferentes índices de fatia, cores e estilos de linhas de ligação — seus gráficos se tornarão mais informativos e visualmente atraentes a cada ajuste. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Adicionar valores de data e hora ao eixo de um gráfico](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Inserir gráfico de colunas no Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}