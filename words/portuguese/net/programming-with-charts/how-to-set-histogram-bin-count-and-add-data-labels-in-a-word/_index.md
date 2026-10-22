---
category: general
date: 2026-10-13
description: Defina a contagem de intervalos do histograma em um gráfico do Word com
  C# e adicione rótulos de dados para melhorar a legibilidade. Aprenda como carregar
  um documento do Word com C# e atualizar o gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set histogram bin count
- add data labels histogram
- how to update word chart
- enable chart data labels
- load word document c#
language: pt
lastmod: 2026-10-13
og_description: Defina a contagem de intervalos do histograma em um gráfico do Word
  usando C# e habilite os rótulos de dados para uma visualização mais clara. Siga
  este tutorial completo para carregar um documento do Word em C# e atualizar o gráfico.
og_image_alt: Screenshot of a Word histogram chart after setting bin count and enabling
  data labels
og_title: Defina a contagem de intervalos do histograma no gráfico do Word com C#
  – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Set histogram bin count in a Word chart with C# and add data labels
    to improve readability. Learn how to load a Word document C# and update the chart.
  headline: How to set histogram bin count and add data labels in a Word chart using
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart manipulation
title: Como definir a contagem de intervalos do histograma e adicionar rótulos de
  dados em um gráfico do Word usando C#
url: /pt/net/programming-with-charts/how-to-set-histogram-bin-count-and-add-data-labels-in-a-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como definir a contagem de intervalos de histograma e adicionar rótulos de dados em um gráfico do Word usando C#

Se você precisar **definir a contagem de intervalos de histograma** em um gráfico do Word, este guia mostra como fazer isso com C#. Você também aprenderá como **adicionar rótulos de dados ao histograma** para que cada intervalo exiba seu valor, facilitando a leitura do gráfico. A solução funciona com qualquer arquivo `.docx` que contenha um gráfico de histograma e usa a biblioteca Aspose.Words for .NET.

Atualizar um gráfico é uma tarefa comum ao gerar relatórios automaticamente. Ao final deste tutorial, você será capaz de **carregar documento Word C#**, modificar a contagem de intervalos do histograma, ativar os rótulos de dados e salvar o resultado sem edição manual.

## O que você aprenderá

* Como carregar um documento Word em C# (`load word document c#`).
* Como localizar o primeiro gráfico de histograma dentro do documento (`how to update word chart`).
* Os passos exatos para **definir a contagem de intervalos de histograma** e **ativar rótulos de dados no gráfico**.
* Dicas para lidar com múltiplos gráficos, diferentes tipos de gráficos e armadilhas comuns.

## Pré‑requisitos

| Requisito | Por que é importante |
|-----------|----------------------|
| .NET 6.0 ou posterior | Fornece o runtime para Aspose.Words. |
| Aspose.Words for .NET (v23.9 ou mais recente) | Oferece a API `Chart` usada para modificar gráficos do Word. |
| Um arquivo Word (`input.docx`) que contém um gráfico de histograma | O código funciona em um histograma existente; você pode criar um manualmente no Word para teste. |
| Visual Studio 2022 (ou qualquer IDE C#) | Facilita compilar e executar o exemplo. |

Instale o pacote NuGet com o seguinte comando:

```bash
dotnet add package Aspose.Words
```

> **Dica profissional:** Se você planeja processar muitos documentos, habilite a licença do Aspose.Words para remover as marcas d'água de avaliação.

## Etapa 1: Carregar o documento Word (load word document c#)

A primeira operação é abrir o arquivo `.docx` que contém o histograma. Usar `Document.Load` garante que todas as partes do documento, incluindo os gráficos, estejam disponíveis na memória.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Path to the source document
string inputPath = @"C:\Docs\input.docx";

// Load the Word document
Document doc = new Document(inputPath);
```

> **Por que esta etapa é importante:** Carregar o documento é a base para qualquer modificação. Se o arquivo não puder ser aberto, as etapas subsequentes falharão com uma `FileNotFoundException`.

## Etapa 2: Localizar o gráfico de histograma (how to update word chart)

O Word armazena gráficos como nós `Shape`. Precisamos encontrar a primeira forma e convertê‑la para `Chart`. Se o seu documento contiver vários gráficos, você pode iterar sobre todas as formas e inspecionar `chart.ChartType`.

```csharp
// Retrieve the first shape in the document (depth‑first search)
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Ensure the shape really is a chart
if (shape?.Chart == null)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Cast the shape to a Chart object
Chart histogramChart = shape.Chart;
```

> **Caso extremo:** Se o documento não contiver um gráfico, `GetChild` retorna `null`. A verificação acima impede uma `NullReferenceException`.

## Etapa 3: Definir a contagem de intervalos do histograma (set histogram bin count)

A granularidade visual de um histograma é controlada pela propriedade `BinCount`. Definir um valor maior cria mais barras, o que pode revelar uma distribuição de dados mais detalhada.

```csharp
// Verify that the chart is a histogram
if (histogramChart.ChartType != ChartType.Histogram)
{
    throw new InvalidOperationException("The selected chart is not a histogram.");
}

// Set the desired number of bins (e.g., 15)
histogramChart.HistogramChart.BinCount = 15;
```

> **Por que você precisa disso:** Ajustar a contagem de intervalos permite adaptar o gráfico ao público. Uma contagem pequena simplifica a visualização, enquanto uma contagem maior fornece mais detalhes.

## Etapa 4: Habilitar rótulos de dados no gráfico (add data labels histogram / enable chart data labels)

Os rótulos de dados tornam o valor de cada intervalo visível diretamente no gráfico. Isso é especialmente útil quando o histograma é impresso ou exportado para PDF.

```csharp
// Turn on data labels for each bin
histogramChart.HistogramChart.ShowLabels = true;

// Optional: customize label format (e.g., show percentage)
histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";
```

> **Dica prática:** Se você preferir porcentagens em vez de contagens brutas, defina `NumberFormat = "0%"` e ajuste `ShowPercentage = true`.

## Etapa 5: Salvar o documento modificado

Após as alterações, grave o documento de volta no disco. Você pode sobrescrever o arquivo original ou criar um novo.

```csharp
// Path to the output document
string outputPath = @"C:\Docs\output.docx";

// Save the updated document
doc.Save(outputPath);
```

Abrir `output.docx` no Microsoft Word agora mostra um histograma com 15 intervalos e rótulos de dados visíveis.

## Etapa 6: Verificar o resultado (saída esperada)

Para garantir que a operação foi bem‑sucedida sem inspeção visual, você pode ler programaticamente as propriedades de volta:

```csharp
// Reload the saved file for verification
Document verifyDoc = new Document(outputPath);
Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
```

O console deve exibir:

```
BinCount: 15
ShowLabels: True
```

Se os valores coincidirem, o histograma foi atualizado corretamente.

## Exemplo completo executável

Juntando tudo, aqui está um programa autônomo que você pode copiar, colar e executar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // ---------- Step 2: Locate the histogram chart ----------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape?.Chart == null)
            throw new InvalidOperationException("No chart found in the document.");

        Chart histogramChart = shape.Chart;

        // ---------- Step 3: Set histogram bin count ----------
        if (histogramChart.ChartType != ChartType.Histogram)
            throw new InvalidOperationException("The chart is not a histogram.");

        histogramChart.HistogramChart.BinCount = 15;

        // ---------- Step 4: Enable chart data labels ----------
        histogramChart.HistogramChart.ShowLabels = true;
        histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";

        // ---------- Step 5: Save the modified document ----------
        string outputPath = @"C:\Docs\output.docx";
        doc.Save(outputPath);

        // ---------- Step 6: Verify the changes ----------
        Document verifyDoc = new Document(outputPath);
        Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

        Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
        Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
    }
}
```

Execute o programa, depois abra `output.docx` para ver o histograma atualizado.

## Perguntas comuns e casos extremos

| Pergunta | Resposta |
|----------|----------|
| **E se o documento contiver mais de um gráfico?** | Use `doc.GetChildNodes(NodeType.Shape, true)` para obter uma coleção, então itere e verifique cada `Chart.ChartType`. |
| **Posso mudar a largura do intervalo em vez da contagem?** | Sim. Use `histogramChart.HistogramChart.BinWidth` para especificar uma largura fixa; ao definir `BinCount` será ignorado. |
| **A API é compatível com .NET Core?** | Aspose.Words for .NET suporta .NET Core, .NET 5+ e .NET Framework. O mesmo código funciona em todos os runtimes suportados. |
| **Como ocultar a legenda após adicionar rótulos?** | Defina `histogramChart.Legend.Visible = false;`. Isso mantém o gráfico limpo quando os rótulos já transmitem os dados. |

## Conclusão

Agora você sabe como **definir a contagem de intervalos de histograma** e **adicionar rótulos de dados** a um gráfico do Word usando C#. Ao carregar o documento, localizar o histograma, ajustar `BinCount`, habilitar `ShowLabels` e salvar o arquivo, você pode automatizar atualizações de gráficos em qualquer pipeline de relatórios.  

A partir daqui, você pode explorar:

* **how to update word chart** cores e estilos,
* **enable chart data labels** para outros tipos de gráficos (pizza, barra, linha),
* Gerar gráficos a partir de dados brutos com Aspose.Words ou Aspose.Cells,
* Incorporar o documento atualizado em um PDF usando Aspose.PDF.

Experimente diferentes contagens de intervalos e formatos de rótulo para encontrar o equilíbrio visual que melhor atende ao seu público. Feliz codificação!  

![Word histogram after


## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}