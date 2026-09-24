---
category: general
date: 2026-09-24
description: Insira um gráfico de pizza no Word em um DOCX usando Aspose.Words para
  Java. Aprenda a definir o tamanho do buraco, explodir a fatia da pizza, destacar
  a fatia do gráfico de pizza e criar um gráfico DOCX sem esforço.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: pt
lastmod: 2026-09-24
og_description: Inserir gráfico de pizza em um DOCX com Aspose.Words for Java. Domine
  a configuração do tamanho do buraco, exploda fatias do gráfico, destaque fatias
  do gráfico de pizza e crie o gráfico DOCX em minutos.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Inserir gráfico de pizza em Java – tutorial passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Inserir palavra de gráfico de pizza em Java – guia completo
url: /pt/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir gráfico de pizza em Word – guia completo

Se você precisa **inserir gráfico de pizza** em um arquivo DOCX, este tutorial mostra exatamente como fazer isso com Aspose.Words for Java. Você verá todo o fluxo de trabalho, desde a criação do documento até a personalização do gráfico, de modo que a fatia seja destacada, o tamanho do buraco seja definido como zero e a fatia seja realçada.

Trabalhar com gráficos em documentos Word costuma parecer uma preocupação separada do processamento de texto comum, mas o Aspose.Words unifica ambos. Nos passos abaixo, você também aprenderá a **criar docx chart** que podem ser abertos no Microsoft Word, Google Docs ou em qualquer outro visualizador compatível com DOCX.

## O que você vai alcançar

* **Inserir gráfico de pizza** em um documento em branco  
* **Definir tamanho do buraco** para transformar o gráfico em um círculo completo (sem donut)  
* **Explodir fatia do gráfico** para chamar a atenção para um segmento específico  
* **Realçar fatia do gráfico** com formatação personalizada  
* **Criar docx chart** que pode ser compartilhado ou editado posteriormente  

### Pré‑requisitos

* Java 17 ou superior (o código também compila com Java 8)  
* Biblioteca Aspose.Words for Java (versão 23.9 ou mais recente)  
* Uma IDE ou ferramenta de build (Maven/Gradle) que consiga resolver a dependência Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Como inserir gráfico de pizza em um DOCX usando Aspose.Words

O primeiro passo é criar um novo documento em branco e obter um `DocumentBuilder`. O builder fornece acesso direto ao fluxo de conteúdo do documento, tornando trivial **inserir gráfico de pizza**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Por que isso importa
`Document` representa todo o arquivo Word, enquanto `DocumentBuilder` é a API de alto nível que permite inserir parágrafos, tabelas e gráficos sem lidar com XML de baixo nível. Começar com um documento limpo garante que o gráfico adicionado seja o único conteúdo, o que é perfeito para aprendizado ou para gerar relatórios baseados em modelos.

## Definir tamanho do buraco para criar um círculo completo

Por padrão, o Aspose.Words cria um gráfico donut quando você solicita um gráfico de pizza. Para que o gráfico seja um círculo verdadeiro, você deve **definir tamanho do buraco** como `0`. Isso remove o buraco interno e produz a aparência clássica de pizza.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Dica prática
Se mais tarde você decidir mudar para um gráfico donut, basta alterar o valor de `holeSize` para uma porcentagem (por exemplo, `30`). A mesma API funciona para ambos os tipos de gráfico.

## Explodir fatia do gráfico para realçar um segmento

Explodir uma fatia faz com que ela se destaque visualmente. A operação **explodir fatia do gráfico** move a fatia escolhida para fora, por uma porcentagem do raio do gráfico.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Por que explodir?
Uma fatia explodida atrai o olhar do leitor para o ponto de dados mais importante — perfeito para dashboards ou resumos executivos. O valor `20` significa 20 % do raio; você pode ajustá‑lo entre `0` (sem explosão) e `100` (totalmente destacada).

## Realçar fatia do gráfico com formatação personalizada

Além de explodir, você pode querer **realçar fatia do gráfico** alterando sua cor de preenchimento ou borda. Enquanto o código de demonstração foca na explosão, você pode estendê‑lo da seguinte forma:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Observação de especialista
Alterar a cor de preenchimento de uma fatia específica requer acesso ao objeto `DataPoint`. Se houver várias séries, itere sobre `series.getDataPoints()` e aplique estilos condicionalmente.

## Salvar e verificar o gráfico docx criado

Por fim, você **cria docx chart** ao salvar o `Document`. O arquivo resultante pode ser aberto no Microsoft Word para visualizar o gráfico de pizza formatado.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Saída esperada
Abrir `PieChartFormatted.docx` mostra um único gráfico de pizza:

* O gráfico ocupa uma área de 400 × 300 pt.  
* O tamanho do buraco é `0`, portanto o gráfico é uma pizza completa.  
* A primeira fatia está explodida em 20 % e colorida de vermelho (se você adicionou a formatação opcional).  

Agora você tem um **create docx chart** que pode ser distribuído, incorporado em e‑mails ou editado programaticamente.

---

## Variações comuns e casos de borda

| Cenário | Como adaptar o código |
|----------|----------------------|
| **Múltiplas séries** | Percorra `pieChart.getChart().getSeries()` e defina `Explosion` ou `FillColor` por série. |
| **Dados dinâmicos** | Preencha a série com valores de um banco de dados ou CSV antes de chamar `setExplosion`. |
| **Tamanho de gráfico diferente** | Altere os argumentos de largura/altura em `insertChart(ChartType.PIE, width, height)`. |
| **Exportar para PDF** | Após salvar o DOCX, chame `doc.save("output.pdf")` para gerar uma versão PDF do mesmo gráfico. |
| **Localização** | Use `DocumentBuilder.insertChart` com formatação numérica específica de locale para rótulos. |

### Dica profissional
Sempre chame `setHoleSize(0)` **depois** de `insertChart`. Se você definir antes da inserção, o Aspose.Words reverterá para o tamanho padrão de donut assim que o gráfico for criado.

---

## Recapitulação

Agora você sabe como **inserir gráfico de pizza** em um documento Word usando Java, como **definir tamanho do buraco** para obter um visual de pizza completa, como **explodir fatia do gráfico** para chamar a atenção e como **realçar fatia do gráfico** com cores personalizadas. O exemplo completo também demonstra como **criar docx chart** pronto para distribuição.

---

## Próximos passos

* Explore outros tipos de gráfico (`BAR`, `LINE`, `SCATTER`) com `ChartType`.  
* Combine a geração de gráficos com mail merge para produzir relatórios personalizados.  
* Integre o DOCX gerado em um serviço web que devolve o arquivo sob demanda.  

Se encontrar problemas, lembre‑se de verificar se está usando uma versão compatível do Aspose.Words e se o diretório de saída existe e tem permissão de escrita.

Happy coding!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}