---
category: general
date: 2026-09-21
description: Crie um documento Word em branco e aprenda como inserir um gráfico de
  radar em um arquivo Word usando o DocumentBuilder – guia passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: pt
lastmod: 2026-09-21
og_description: Crie um documento Word em branco e insira um gráfico de radar em um
  arquivo Word com Aspose.Words. Siga este tutorial para gerar rapidamente um gráfico
  em um documento Word.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Crie um documento Word em branco e adicione um gráfico de radar – guia completo
  de C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Como criar um documento Word em branco e adicionar um gráfico de radar em C#
url: /pt/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento Word em branco e adicionar um gráfico de radar em C#

Se você precisa **criar um documento Word em branco** e incorporar um gráfico de radar (radial), este tutorial oferece uma solução pronta‑para‑executar. Você verá como usar Aspose.Words .NET para gerar o arquivo, inserir o gráfico e salvar o resultado — tudo em alguns passos concisos.

Um documento em branco fornece uma tela limpa para qualquer cenário de geração automática de relatórios, e adicionar um gráfico de radar permite visualizar dados multidimensionais diretamente no Word. Ao final deste guia, você será capaz de gerar um documento Word com gráfico sem edição manual.

## O que você aprenderá

* Como **criar um documento Word em branco** programaticamente com C#.
* O código exato para **como inserir um gráfico de radar** usando `DocumentBuilder`.
* Formas de **inserir gráfico em arquivo Word** e personalizar seu tamanho.
* Como **gerar um documento Word com gráfico** e verificar a saída.
* Dicas para **adicionar arquivos de gráfico radial ao Word**, incluindo armadilhas comuns.

### Pré-requisitos

* .NET 6.0 ou superior (o código também funciona com .NET Framework 4.6+).
* Aspose.Words for .NET (pacote NuGet `Aspose.Words` versão 23.9 ou mais recente).
* Familiaridade básica com C# e Visual Studio ou seu IDE preferido.

## Criar um documento Word em branco com C#

O primeiro passo é instanciar um objeto `Document` vazio. Esse objeto representa um arquivo `.docx` completamente em branco.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` cria a estrutura do arquivo, mas ainda não contém seções ou páginas. Aspose.Words adiciona automaticamente uma seção padrão quando você começa a inserir conteúdo, por isso o próximo passo funciona sem configuração extra.

## Como inserir um gráfico de radar no arquivo Word

Um gráfico de radar (também chamado de gráfico radial) visualiza pontos de dados em eixos que irradiam de um ponto central. Aspose.Words fornece `DocumentBuilder.insertChart` para esse propósito.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` devolve um objeto `Chart` que pode ser configurado ainda mais. O gráfico aparece na primeira página do documento em branco porque o builder está posicionado no início do documento por padrão.

## Inserir gráfico em um arquivo Word – adicionando séries de dados

Um gráfico sem dados é invisível. Preencha o gráfico de radar com uma ou mais séries para torná‑lo significativo.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Você pode adicionar quantas séries precisar. Cada série pode ter um nome distinto, que aparece na legenda do gráfico. Os pontos de dados correspondem aos eixos radiais; a ordem em que você os adiciona define sua posição ao redor do círculo.

## Gerar um documento Word com gráfico – salvando o arquivo

Depois de construir o gráfico, persista o documento no disco. Escolha um local onde você tenha permissão de gravação.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Ao abrir o arquivo `.docx` resultante no Microsoft Word, você verá uma página em branco com um gráfico de radar dimensionado em 400 × 300 pontos, preenchido com os dados de exemplo.

### Saída esperada

* Um arquivo `RadialChartExample.docx` na sua área de trabalho.
* A primeira página contém um gráfico de radar com cinco pontos de dados rotulados como “Series 1”.
* Nenhum texto adicional aparece porque o documento começou em branco.

## Adicionar gráfico radial ao Word – lidando com casos de borda comuns

### 1. Alterar o tamanho do gráfico após a inserção

Se as dimensões iniciais não se ajustarem ao seu layout, redimensione o gráfico assim:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Inserir o gráfico em um local específico

Você pode mover o cursor do builder para um bookmark, célula de tabela ou parágrafo antes de chamar `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Personalizar a aparência do gráfico

Aspose.Words expõe todo o modelo de objeto do gráfico, permitindo definir títulos, rótulos dos eixos e cores.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Lidar com fontes ausentes

Se o ambiente de destino não possuir uma fonte usada no gráfico, Aspose.Words substitui por uma fonte padrão. Para garantir consistência, incorpore as fontes necessárias:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Exportar para outros formatos

O mesmo documento pode ser salvo como PDF, HTML ou PNG sem alterações adicionais de código:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Exemplo completo e executável

Juntando todas as partes, você obtém um único programa que pode copiar, colar e executar.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Execute este programa, abra o arquivo gerado e você verá um gráfico de radar profissional pronto para distribuição.

## Conclusão

Agora você sabe como **criar um documento Word em branco**, **como inserir um gráfico de radar** e **gerar um documento Word com gráfico** usando Aspose.Words. Seguindo os passos acima, você também pode **adicionar arquivos de gráfico radial ao Word** em qualquer pipeline de geração automática de relatórios, personalizar tamanho, estilo e exportar para formatos adicionais.

**Próximos passos**

* Explore outros tipos de gráfico (`ChartType.Column`, `ChartType.Pie`) para ampliar seu conjunto de ferramentas de relatório.
* Combine vários gráficos em uma única página chamando `InsertChart` repetidamente.
* Integre dados de um banco de dados ou arquivo CSV para preencher as séries dinamicamente.
* Consulte a documentação do Aspose.Words para opções avançadas de formatação, como rótulos de dados condicionais e modelos de gráfico.

Sinta‑se à vontade para experimentar o código, ajustar dimensões ou substituir os dados de exemplo por métricas reais de negócios. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}