---
category: general
date: 2026-08-14
description: Crie um gráfico de pizza no Word com Java usando Aspose.Words. Aprenda
  como adicionar dados de série ao gráfico e girar a fatia do gráfico de pizza em
  apenas algumas linhas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: pt
lastmod: 2026-08-14
og_description: Crie um gráfico de pizza no Word com Java usando Aspose.Words. Este
  tutorial mostra como adicionar dados de série ao gráfico e girar rapidamente um
  segmento do gráfico de pizza.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Crie um gráfico de pizza no Word com Java – guia completo de codificação
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Criar gráfico de pizza no Word com Java – guia passo a passo
url: /pt/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar pie chart no Word com Java – guia passo a passo

Se você precisa **criar pie chart no Word** programaticamente, este guia mostra exatamente como fazer isso com Java e Aspose.Words. Você aprenderá o fluxo de trabalho completo, desde inserir o gráfico até adicionar pontos de dados e girar a primeira fatia.

Gerar um gráfico diretamente em um arquivo `.docx` elimina a etapa manual de copiar‑colar e permite automatizar relatórios, faturas ou dashboards. Ao longo do caminho, também abordaremos **add series data to chart** e como **rotate pie chart slice** para melhor ênfase visual.

## Criar pie chart no Word – visão geral

Aspose.Words for Java fornece uma API fluente `DocumentBuilder` que pode inserir um objeto de gráfico em um documento Word. O tipo de gráfico que você escolher determina o layout padrão, e você pode personalizar as séries, cores, ângulos e até mudar para um formato doughnut com uma única chamada de método.

### Por que usar Aspose.Words?

* **No Microsoft Office required** – a biblioteca funciona em qualquer servidor ou ambiente CI.  
* **Full .docx fidelity** – o gráfico gerado tem aparência idêntica ao criado manualmente no Word.  
* **Single‑file dependency** – basta adicionar o JAR e você está pronto para usar.

## Como adicionar series data to chart

Um gráfico sem dados é apenas um placeholder. O objeto `Chart` expõe uma coleção `Series`; cada série contém uma lista de valores numéricos que correspondem a fatias (para um pie) ou pontos (para uma linha). Adicionar dados é simples:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**O que o código faz:**  
* `chart.getSeries()` retorna um `List<ChartSeries>`.  
* `get(0)` seleciona a primeira série porque um pie chart contém apenas uma série por definição.  
* `add(double)` adiciona um ponto de dado. Os valores são convertidos automaticamente em porcentagens que somam 100 % quando o gráfico é renderizado.

> **Dica profissional:** Se sua fonte de dados contiver mais de três categorias, continue adicionando valores da mesma forma. Aspose.Words criará automaticamente fatias adicionais.

## Girar fatia de pie chart

Às vezes você deseja que uma fatia específica comece em um ângulo determinado para que o segmento mais importante fique voltado ao observador. O método `setFirstSliceAngle(double)` gira todo o gráfico, movendo efetivamente o início da primeira fatia:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

O ângulo é medido em graus no sentido horário a partir do eixo vertical. Definir como `0` (padrão) coloca a primeira fatia no topo. Ajuste o valor para destacar uma fatia ou para atender a uma diretriz de design.

> **Pergunta comum:** *A rotação afeta a ordem dos dados?*  
> Não. A ordem dos dados permanece a mesma; apenas a posição inicial visual muda.

## Exemplo completo em Java

Abaixo está um programa completo, pronto‑para‑executar, que cria um documento Word com um pie chart, adiciona series data, gira a fatia e salva o arquivo. Todas as importações necessárias estão listadas, para que você possa copiar o código em qualquer IDE.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Saída esperada

* Um arquivo chamado **PieChart.docx** aparece na pasta `output`.  
* Abrir o arquivo no Microsoft Word exibe um pie chart colorido com três fatias (40 %, 30 %, 30 %).  
* O gráfico está girado 45° no sentido horário, de modo que a primeira fatia começa ligeiramente à direita do eixo vertical.

## Armadilhas comuns e boas práticas

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **Gráfico aparece em branco** | O documento foi salvo antes que o gráfico fosse totalmente renderizado. | Chame `doc.save()` **depois** de todas as modificações do gráfico. |
| **Valores das fatias não somam 100 %** | Adicionar números brutos que não representam porcentagens pode levar a dimensionamento inesperado. | Forneça valores que representem logicamente porções de um todo, ou deixe Aspose.Words calcular as porcentagens automaticamente. |
| **Rotação não tem efeito** | Usar `ChartType.DOUGHNUT` sem definir `holeSize` pode ocultar o efeito de rotação. | Mantenha o gráfico como `PIE` ou ajuste `holeSize` após definir o ângulo. |
| **Erros de caminho de arquivo** | Caminhos relativos podem ser resolvidos de forma diferente no Windows vs. Linux. | Use `Paths.get("output", "PieChart.docx").toString()` ou um caminho absoluto para código de produção. |

### Dicas para uso em produção

* **Reuse the `DocumentBuilder`** – você pode inserir vários gráficos no mesmo documento chamando `insertChart` repetidamente.  
* **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` para exibir porcentagens diretamente no gráfico.  
* **Performance** – gere o gráfico uma vez e clone-o (`chart.deepClone()`) se precisar de gráficos idênticos em vários locais.

## Girar fatia de pie chart – cenários avançados

* **Dynamic angle** – calcule o ângulo com base nos dados (por exemplo, faça a maior fatia começar no topo).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Multiple series** – embora um pie chart normalmente tenha uma série, Aspose.Words permite adicionar mais para pies empilhados. A rotação ainda se aplica apenas à primeira série.

## Conclusão

Agora você sabe como **create pie chart in Word** usando Java, como **add series data to chart**, e como **rotate pie chart slice** para ênfase visual. O exemplo completo demonstra todo o fluxo de trabalho — da inicialização do documento à gravação do arquivo final `.docx` — para que você possa integrar a geração de gráficos em qualquer pipeline de relatórios automatizado.

### O que vem a seguir?

* Explore outros tipos de gráficos (`ChartType.BAR`, `ChartType.LINE`) para ampliar seu conjunto de ferramentas de automação.  
* Combine a geração de gráficos com **mail merge** para produzir relatórios personalizados para cada destinatário.  
* Mergulhe na **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) para adequar à identidade visual da sua empresa.

Sinta-se à vontade para experimentar diferentes conjuntos de dados, ângulos e estilos de gráficos. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Como converter Word para PDF usando Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}