---
category: general
date: 2026-11-25
description: Aprenda a criar um gráfico de pizza em Java, inserir o gráfico de pizza
  em um documento Word, destacar fatias do gráfico e alterar a orientação do gráfico
  com exemplos de código claros.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: pt
lastmod: 2026-11-25
og_description: Crie um gráfico de pizza em Java, insira o gráfico de pizza em um
  documento, destaque uma fatia do gráfico e altere a orientação do gráfico com código
  passo a passo.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Criar um gráfico de pizza em Java – inserir, explodir fatia e girar
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Como criar um gráfico de pizza, inseri‑lo e personalizar a orientação no Java
url: /pt/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um gráfico de pizza, inseri‑lo e personalizar a orientação em Java

Se você precisa **criar um gráfico de pizza** dentro de um documento Word, este guia mostra exatamente como fazer isso. Você verá como **inserir gráfico de pizza**, explodir uma fatia para destaque e **alterar a orientação do gráfico** com uma simples rotação.

O tutorial cobre tudo o que você precisa — desde a configuração da biblioteca Aspose.Words para Java até a produção de um arquivo final `.docx` que exibe um gráfico de pizza girado e explodido. Nenhuma documentação externa é necessária; basta seguir os passos e executar o código.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou superior instalado.  
* Maven ou Gradle para gerenciar dependências.  
* Uma licença válida do Aspose.Words para Java (ou use o modo de avaliação gratuito).

Adicione a dependência do Aspose.Words ao seu `pom.xml` (Maven) ou `build.gradle` (Gradle). Exemplo para Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Dica profissional:** Mantenha a versão da biblioteca atualizada; a versão mais recente (24.10 no momento da escrita) inclui correções de bugs para renderização de gráficos.

## Etapa 1: Criar gráfico de pizza e inseri‑lo no documento

O primeiro passo é **criar gráficos de pizza** e incorporá‑los em um arquivo Word. O código abaixo cria um documento simples, adiciona um espaço reservado para gráfico e insere um gráfico de pizza com tamanho 400 × 300 pixels.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Por que isso importa:** `builder.insertChart` cria um espaço reservado que o Aspose.Words converte automaticamente em um gráfico OOXML quando o documento é salvo. O argumento `ChartType.PIE` indica à biblioteca que deve renderizar um gráfico de pizza, atendendo ao requisito de **inserir gráfico de pizza**.

## Etapa 2: Explodir fatia da pizza para destacar um segmento

Explodir uma fatia chama a atenção para um ponto de dado específico. A linha a seguir explode a primeira fatia (índice 0) em 10 pontos:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Você pode mudar o índice para direcionar outra fatia ou ajustar a distância de explosão para um efeito mais sutil. Explodir uma fatia é a forma padrão de **explodir fatia de pizza** no Aspose.Words.

## Etapa 3: Alterar a orientação do gráfico girando‑o

Girar o gráfico oferece uma nova perspectiva visual. Use `setRotationAngle` para girar todo o gráfico no sentido horário (o ângulo é medido em graus).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

A chamada acima satisfaz os requisitos de **girar gráfico de pizza** e **alterar a orientação do gráfico**. Qualquer ângulo entre 0 e 360 graus é aceito.

## Exemplo completo executável

Juntando tudo, aqui está um programa completo e autocontido que cria um gráfico de pizza, explode uma fatia e gira o gráfico. Execute‑o a partir da sua IDE ou da linha de comando com `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Saída esperada

* Um arquivo chamado **CreatePieChartDemo.docx** aparece no diretório de trabalho.  
* Ao abrir o arquivo no Microsoft Word, é exibido um gráfico de pizza de 400 × 300 pixels.  
* A primeira fatia (Q1) está deslocada para fora em 10 pontos, criando o efeito de **explodir fatia de pizza**.  
* Todo o gráfico está inclinado em 45 graus, demonstrando **alterar a orientação do gráfico** e **girar gráfico de pizza**.

## Variações comuns e casos de borda

| Situação | Como adaptar o código |
|-----------|-----------------------|
| **Tamanho de gráfico diferente** | Altere os argumentos `400, 300` em `insertChart`. |
| **Múltiplas séries** | Adicione mais objetos `ChartSeries` a `chart.getSeries()`. |
| **Explodir outra fatia** | Use `setExplode(sliceIndex, distance)` com o `sliceIndex` desejado. |
| **Sem rotação necessária** | Omitir a chamada `setRotationAngle` ou definir o ângulo para `0`. |
| **Exportar para PDF em vez de DOCX** | Após construir o documento, chame `doc.save("output.pdf")` especificando o formato PDF. |

> **Cuidado:** Usar uma distância de explosão negativa lança `IllegalArgumentException`. Sempre forneça um valor não negativo.

## Dica de desempenho

Se você gerar muitos gráficos dentro de um loop, reutilize um único `DocumentBuilder` e chame `insertChart` apenas para cada iteração. Isso reduz o consumo de memória e acelera o processamento.

## Conclusão

Agora você sabe como **criar gráfico de pizza**, **inserir gráfico de pizza**, **explodir fatia de pizza** e **girar gráfico de pizza** usando Aspose.Words para Java. O exemplo completo demonstra todo o fluxo de trabalho — desde a inicialização do documento até a gravação de um arquivo que visualiza um gráfico de pizza girado e explodido.

Em seguida, você pode explorar **alterar a orientação do gráfico** mais a fundo aplicando efeitos 3‑D, ou experimentar outros tipos de gráfico como **Bar** ou **Line**. Os mesmos padrões de API se aplicam, portanto estender este tutorial é simples.

Sinta‑se à vontade para modificar os dados, o índice da fatia ou o ângulo de rotação para atender às suas necessidades de relatório e compartilhe seus resultados com a comunidade!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Como inserir um gráfico de pizza em um documento Word usando Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Como explodir fatia de pizza em Java – tutorial de gráficos Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}