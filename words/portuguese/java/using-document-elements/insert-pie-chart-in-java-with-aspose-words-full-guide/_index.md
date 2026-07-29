---
category: general
date: 2026-07-29
description: Insira um gráfico de pizza usando Aspose.Words para Java e aprenda como
  gerar um gráfico de rosca, formatar o gráfico de pizza, formatar o gráfico no Word
  e personalizar o tamanho do gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: pt
lastmod: 2026-07-29
og_description: Insira um gráfico de pizza com Aspose.Words for Java e aprenda rapidamente
  a gerar gráfico de rosca, formatar gráfico de pizza, formatar gráfico no Word e
  personalizar o tamanho do gráfico para documentos profissionais.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Inserir gráfico de pizza em Java – Tutorial completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Inserir gráfico de pizza em Java com Aspose.Words – Guia completo
url: /pt/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir gráfico de pizza em Java com Aspose.Words – Guia Completo

Já se perguntou como **inserir gráfico de pizza** em um documento Word a partir de código Java? Você não está sozinho—muitos desenvolvedores encontram esse obstáculo quando precisam de uma maneira rápida e programática de visualizar dados. A boa notícia? Com Aspose.Words for Java você pode fazer isso em apenas algumas linhas, e ainda pode **gerar gráfico de rosquinha**, **formatar gráfico de pizza**, **formatar gráfico Word**, e **personalizar o tamanho do gráfico** para combinar com sua identidade visual.

Neste tutorial, percorreremos um exemplo real que começa criando um documento em branco, insere um gráfico de pizza, ajusta algumas propriedades visuais e, finalmente, salva o arquivo. Ao final, você terá um trecho reutilizável que pode colar em qualquer projeto Java que precise de automação de gráficos. Sem bibliotecas extras, sem manipulação manual de interop com Office—apenas Java limpo e compilado.

## O que você precisará

- **Java 17** (ou qualquer JDK recente; a API é compatível retroativamente)
- **Aspose.Words for Java** 22.12 ou mais recente – você pode obter o artefato Maven ou o .jar no site da Aspose.
- Uma IDE modesta (IntelliJ IDEA, Eclipse, VS Code…) – qualquer que permita executar um método `main`.
- Opcional: um arquivo de licença se você não quiser a marca d'água de avaliação.

Se você tem tudo isso, podemos ir direto ao código.

## Etapa 1: Inserir gráfico de pizza com Aspose.Words

A primeira coisa que fazemos é **inserir gráfico de pizza** em um documento novo. Esta etapa prepara o terreno para tudo o mais, pois o objeto chart nos dá acesso a séries, pontos de dados e ajustes visuais.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Por que isso importa:** `DocumentBuilder.insertChart` não apenas cria o gráfico, mas também retorna um objeto `Chart` que podemos manipular. Os argumentos de largura e altura permitem que você **personalize o tamanho do gráfico** já na criação, de modo que não precise redimensionar depois.

## Etapa 2: Gerar gráfico de rosquinha (opcional)

Se o seu design requer um buraco no meio—pense em um clássico gráfico de rosquinha—Aspose torna isso uma única linha. A mesma instância `Chart` pode ser alterada de um pizza regular para uma rosquinha ajustando o tamanho do buraco.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Dica:** O tamanho do buraco só tem efeito para `ChartType.DONUT`. Se você mantiver o tipo como `PIE`, a chamada será ignorada, então sinta-se à vontade para experimentar.

## Etapa 3: Formatar fatias do gráfico de pizza

Um bom visual costuma destacar uma fatia específica. Aqui nós **formatamos o gráfico de pizza** explodindo a primeira fatia 20 pontos para fora. Isso atrai o olhar do leitor para o ponto de dado mais importante.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Dica de especialista:** Você pode percorrer `pieChart.getSeries()` se tiver várias séries e definir cores individuais, bordas ou rótulos de dados. Essa é a forma de **formatar gráficos Word** com estilo avançado.

## Etapa 4: Adicionar dados ao gráfico

Um gráfico sem dados é apenas uma forma decorativa. Vamos alimentá-lo com um conjunto de dados simples—por exemplo, números de vendas trimestrais.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Por que fazemos isso:** Ao adicionar explicitamente objetos `ChartPoint` garantimos que o gráfico reflita nossa lógica de negócios. As chamadas `setShowCategoryName` e `setShowValue` fazem parte da **formatação do gráfico de pizza** para exibir tanto rótulos quanto números.

## Etapa 5: Ajustar aparência (personalizar tamanho e estilo do gráfico)

Além das dimensões iniciais, você pode querer ajustar a legenda do gráfico, o título ou até a fonte usada nos rótulos de dados. Tudo isso se enquadra em **personalizar o tamanho do gráfico** e formatação geral.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Caso especial:** Se mais tarde você decidir exportar o documento para PDF, os dados vetoriais do gráfico permanecem nítidos porque o tamanho é definido em pontos, não em pixels. Isso é uma vantagem para **formatar gráficos Word** e formatos subsequentes.

## Etapa 6: Salvar e visualizar o documento

A etapa final é tão simples quanto chamar `doc.save`. Isso grava um arquivo `.docx` que pode ser aberto no Microsoft Word, LibreOffice ou qualquer visualizador que suporte o formato OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Resultado:** Abra `PieChart.docx` e você verá um gráfico de pizza (ou rosquinha) com tamanho adequado, com uma fatia explodida, um título e uma legenda—tudo gerado sem nunca tocar na interface do usuário.

### Saída esperada

| Elemento | O que você verá |
|----------|------------------|
| Tipo de gráfico | Gráfico de pizza (ou rosquinha se `holeSize` > 0) |
| Explosão da fatia | Primeira fatia deslocada em 20 pts |
| Legenda | Posicionada à direita |
| Título | “Quarterly Sales Distribution” em negrito 14 pt |
| Rótulos de dados | Nome da categoria e valor mostrados em cada fatia |
| Documento | Um arquivo Word `.docx` padrão pronto para compartilhamento |

## Perguntas comuns e armadilhas

- **Preciso de licença?**  
  A versão de avaliação funciona bem para testes, mas adiciona uma marca d'água. Coloque seu arquivo `aspose.words.lic` no classpath para uma saída limpa.

- **Posso usar isso com Maven?**  
  Claro. Adicione a seguinte dependência ao seu `pom.xml`:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **E se eu tiver mais de uma série?**  
  Percorra `pieChart.getSeries()` e aplique `setExplosion`, `setFillColor` ou outras formatações por série. Essa é a forma de **formatar gráfico de pizza** para dados multidimensionais.

- **O gráfico é editável no Word após a geração?**  
  Sim—uma vez salvo, você pode abrir o documento e ajustar manualmente cores, fontes ou até converter o pizza em um gráfico de barras, se precisar.

## Conclusão

Acabamos de **inserir gráfico de pizza** em um documento Word usando Aspose.Words for Java, mostramos como **gerar gráfico de rosquinha**, demonstramos várias maneiras de **formatar gráfico de pizza**, abordamos as melhores práticas de **formatar gráficos Word** e aprendemos a **personalizar o tamanho do gráfico** para um visual refinado. O exemplo completo e executável acima pode ser inserido em qualquer projeto Java, proporcionando automação de gráficos instantânea sem a sobrecarga de interop COM ou instalações do Office.

O que vem a seguir? Experimente trocar a fonte de dados por um banco de dados ao vivo, adicionar cores condicionais com base em limites, ou exportar o mesmo documento para PDF para um relatório pronto para impressão. Cada um desses passos se baseia na fundação que estabelecemos, então a transição será suave.

Se encontrar algum problema ou tiver ideias para aprimoramentos adicionais—talvez um gráfico de barras empilhadas ou um gráfico de linhas—deixe um comentário abaixo. Boa criação de gráficos!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Formatar número de rótulo de dados em um gráfico](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Formato numérico para eixo em um gráfico](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}