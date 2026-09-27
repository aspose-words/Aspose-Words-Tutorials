---
category: general
date: 2026-09-27
description: Aprenda como inserir um gráfico de pizza em um documento Word com Java,
  criar um gráfico de pizza no Word e exibir percentuais no gráfico de pizza para
  uma visão clara dos dados.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: pt
lastmod: 2026-09-27
og_description: Como inserir um gráfico de pizza em um documento do Word com Java.
  Este guia mostra como criar um gráfico de pizza no Word, exibir as porcentagens
  no gráfico e adicionar linhas de ligação.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Como inserir um gráfico de pizza em um documento Word usando Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Como inserir um gráfico de pizza em um documento Word usando Java
url: /pt/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como inserir um gráfico de pizza em um documento Word usando Java

Se você precisa **how to insert pie chart** em um arquivo Word, este guia o conduzirá por todo o processo. Você verá como **create pie chart in Word**, exibir porcentagens em cada fatia e adicionar linhas de ligação para um visual refinado.

A automação do Word costuma ser pesada, mas com Aspose.Words for Java você pode gerar documentos totalmente formatados programaticamente. Ao final deste tutorial, você terá um trecho de código Java executável que produz um documento Word contendo um gráfico de pizza estilizado.

## Pré-requisitos

Antes de começar, certifique-se de que você tem:

- Java 17 ou posterior instalado
- Maven ou Gradle para gerenciar dependências
- Aspose.Words for Java (versão 23.11 ou mais recente) adicionado ao seu projeto
- Familiaridade básica com a sintaxe Java

Você não precisa de experiência prévia com APIs de gráficos; as etapas abaixo cobrem tudo, desde a configuração do projeto até o resultado final.

## Etapa 1: Configurar a dependência Maven

Adicione a biblioteca Aspose.Words ao seu `pom.xml`. Esta única dependência fornece acesso a `Document`, `DocumentBuilder` e às classes de gráficos.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Se você usar Gradle, o equivalente é:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Dica:** Use a versão estável mais recente para se beneficiar de correções de bugs e novos recursos de gráficos.

## Etapa 2: Criar um novo documento e um builder

O objeto `Document` representa o arquivo Word, enquanto `DocumentBuilder` permite inserir conteúdo. Esta é a base para **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

O builder agora está pronto para posicionar objetos em qualquer lugar do documento.

## Etapa 3: Inserir um gráfico de pizza

Aspose.Words suporta vários tipos de gráficos; escolhemos `ChartType.PIE`. O tamanho é expresso em pontos (1 ponto = 1/72 polegada).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

Neste estágio, o gráfico contém uma série de dados padrão com valores de espaço reservado. Você pode substituir esses valores mais tarde, se necessário.

## Etapa 4: Acessar a série do gráfico

Um gráfico de pizza tem uma única série que contém os valores das fatias. Recupere-a para aplicar formatação.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Etapa 5: Explodir a primeira fatia

Explodir uma fatia chama a atenção para um ponto de dados específico. Este é um recurso visual comum quando você deseja destacar uma métrica importante.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Etapa 6: Exibir porcentagens em cada fatia

Exibir porcentagens diretamente no gráfico melhora a compreensão dos dados. Isso atende ao requisito de **show percentages on pie chart**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Etapa 7: Adicionar linhas de ligação para rótulos mais claros

Linhas de ligação conectam os rótulos das fatias às suas respectivas seções, eliminando ambiguidades. Isso cumpre **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Etapa 8: Salvar o documento

Por fim, grave o documento no disco. Você pode escolher qualquer pasta que tenha permissão de gravação.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Executar o programa cria `output/PieFormatted.docx`. Abra o arquivo no Microsoft Word e você verá um gráfico de pizza onde:

- A primeira fatia está explodida.
- Cada fatia mostra seu valor percentual.
- Linhas de ligação apontam das porcentagens para as fatias correspondentes.

### Saída esperada

![Gráfico de pizza formatado no Word](/images/pie-formatted.png){: .center-image alt="Gráfico de pizza formatado inserido em um documento Word"}

A captura de tela (o texto alternativo usa a palavra‑chave principal) ilustra a aparência final: um gráfico de pizza limpo e orientado a dados, pronto para relatórios, propostas ou painéis.

## Variações comuns e casos extremos

### Alterando valores das fatias

Se você precisar de dados personalizados, substitua os valores da série padrão:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Múltiplas séries (gráfico de rosquela)

Embora um gráfico de pizza simples tenha uma série, Aspose.Words também suporta gráficos de rosquela com múltiplas séries. Troque `ChartType.PIE` por `ChartType.DONUT` e repita as etapas de configuração da série.

### Exportando para PDF

Se seu fluxo de trabalho posterior exigir PDF, chame `doc.save("output/PieFormatted.pdf");` após a construção do gráfico. O layout visual permanece idêntico.

## Listagem completa do código-fonte

Abaixo está o arquivo Java completo e autônomo que você pode copiar e colar em sua IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Compile e execute o programa com `mvn compile exec:java -Dexec.mainClass=PieChartExample` (ou o comando equivalente do Gradle). O arquivo Word gerado conterá o gráfico de pizza totalmente formatado.

## Conclusão

Agora você sabe **how to insert pie chart** em um documento Word usando Java, como **create pie chart in Word**, como **show percentages on pie chart**, e como **add chart to word document** com linhas de ligação. O exemplo completo demonstra cada etapa, explica por que o código foi escrito dessa forma e fornece dicas para personalização.

Em seguida, você pode explorar:

- Adicionar rótulos de dados com fontes personalizadas (variações de **show percentages on pie chart**)
- Combinar múltiplos gráficos em um único documento (caso de uso **add chart to word document**)
- Automatizar a geração de relatórios com tabelas e gráficos juntos

Sinta-se à vontade para experimentar cores, ordem das fatias ou exportação para PDF. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ocultar eixo do gráfico em um documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Criar um gráfico de linhas no Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}