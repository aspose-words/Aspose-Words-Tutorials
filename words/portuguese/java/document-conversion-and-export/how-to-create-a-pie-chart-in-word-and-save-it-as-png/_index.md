---
category: general
date: 2026-10-07
description: Aprenda a criar um gráfico de pizza no Word, adicionar séries de dados
  e salvar o gráfico como PNG usando Java. Siga o guia passo a passo para obter resultados
  rápidos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: pt
lastmod: 2026-10-07
og_description: 'Crie um gráfico de pizza no Word rapidamente: este tutorial mostra
  como adicionar séries de dados, gerar o gráfico e salvar o gráfico do Word como
  uma imagem (PNG). Siga o exemplo de código completo.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Crie um gráfico de pizza no Word e exporte como PNG – guia
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Como criar um gráfico de pizza no Word e salvá‑lo como PNG
url: /pt/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um gráfico de pizza no Word e salvá‑lo como PNG

Se você precisa **criar objetos de gráfico de pizza** dentro de um arquivo Microsoft Word, este guia mostra exatamente como fazer isso com Java. Você também aprenderá a **adicionar séries de dados** ao gráfico e a **salvar o gráfico como PNG** para que a visualização possa ser reutilizada fora do Word.

Gerar um gráfico diretamente em um documento evita a exportação de dados para uma ferramenta gráfica separada. Ao final deste tutorial você terá um arquivo Word totalmente funcional que contém um gráfico de pizza e uma imagem PNG correspondente no disco.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou superior instalado.  
* O **GroupDocs.Viewer for Java** (ou uma biblioteca compatível que forneça as classes `Document`, `Chart`, `ChartType` e `ImageSaveOptions`).  
* Um projeto Maven ou Gradle onde você possa adicionar a dependência da biblioteca.  
* Um documento Word de entrada (`input.docx`) localizado em uma pasta que você possa referenciar a partir do código.

Se você estiver usando Maven, adicione a dependência (substitua `VERSION` pela versão mais recente):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Como criar um gráfico de pizza no Word

O núcleo da solução gira em torno de três ações:

1. Carregar o arquivo `.docx` de origem.  
2. **Adicionar séries de dados** a um novo objeto `Chart` do tipo `PIE`.  
3. **Salvar o gráfico como PNG** para obter um arquivo de imagem ao lado do documento Word.

A seguir, cada passo é explicado em detalhes, seguido pelo código Java exato que você precisa.

### Passo 1: Carregar o documento de origem

Você deve abrir o arquivo Word que receberá o gráfico. A classe `Document` lê o conteúdo `.docx` para a memória.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Por que isso importa*: Carregar o documento cria um modelo mutável. Todas as operações subsequentes de gráfico modificam essa representação em memória, que você persiste de volta ao disco posteriormente.

### Passo 2: Adicionar séries de dados ao gráfico

Criar um **gráfico de pizza** começa com uma instância `Chart`. O construtor recebe o `Document` pai e o tipo de gráfico (`ChartType.PIE`). Depois que o objeto do gráfico existir, você o preenche com valores numéricos e rótulos opcionais.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Por que isso importa*: O método `add` **adiciona séries de dados** ao gráfico. Cada entrada em `values` torna‑se uma fatia da pizza, enquanto `categories` fornece os rótulos da legenda. Você pode fornecer qualquer número de pontos; a biblioteca calculará automaticamente os ângulos das fatias.

### Passo 3: Salvar o gráfico como PNG

Uma vez que o gráfico faça parte do documento, você pode exportar a representação visual. O método `save` no objeto de gráfico subjacente grava um arquivo PNG no sistema de arquivos.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Por que isso importa*: Salvar o gráfico como PNG gera uma imagem raster que pode ser incorporada em páginas web, e‑mails ou relatórios sem exigir o arquivo Word original. O objeto `ImageSaveOptions` permite controlar o formato, a resolução e outras configurações de exportação.

## Gerar gráfico de pizza no Word – personalizando a aparência

Além dos passos básicos, você pode querer personalizar cores, títulos ou rótulos de dados. A maioria das bibliotecas expõe um objeto `ChartOptions` ou similar. Aqui está um exemplo rápido que adiciona um título e altera as cores das fatias:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Essas personalizações são opcionais, mas ilustram como você pode **gerar um gráfico de pizza no Word** que corresponda à sua identidade visual.

## Salvar gráfico do Word como imagem – abordagens alternativas

Se você precisa apenas da imagem e não do gráfico dentro do documento, pode pular a inserção da forma do gráfico no arquivo Word e chamar diretamente o método `save` após criar o gráfico. O código permanece o mesmo; basta omitir quaisquer etapas que adicionem o gráfico ao corpo do documento.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Essa técnica é útil quando você gera muitos gráficos em um processo em lote e só se importa com a saída PNG.

## Exemplo completo executável

Copie a classe a seguir para o seu projeto, ajuste os caminhos dos arquivos e execute-a. O programa irá:

1. Carregar `input.docx`.  
2. **Criar um gráfico de pizza**, **adicionar séries de dados** e incorporá‑lo ao documento.  
3. **Salvar o gráfico como PNG** (`radial.png`).  
4. Persistir o arquivo Word modificado como `output.docx`.



## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Criar gráfico de dispersão no Word usando Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Inserir gráfico de colunas no Word usando Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}