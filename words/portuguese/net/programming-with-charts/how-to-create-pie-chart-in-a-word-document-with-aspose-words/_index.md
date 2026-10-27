---
category: general
date: 2026-09-21
description: Aprenda a criar um gráfico de pizza e inseri‑lo no Word usando Aspose.Words,
  adicionar rótulos de dados ao gráfico de pizza e mostrar porcentagens no gráfico
  de pizza em apenas alguns passos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: pt
lastmod: 2026-09-21
og_description: Crie um gráfico de pizza no Word usando Aspose.Words, insira o gráfico
  no Word, adicione rótulos de dados ao gráfico de pizza e mostre as porcentagens
  no gráfico de pizza — tudo com exemplos de código claros.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Crie um gráfico de pizza no Word com Aspose.Words – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Como criar um gráfico de pizza em um documento Word com Aspose.Words
url: /pt/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um gráfico de pizza em um documento Word com Aspose.Words

Se você precisa **criar um gráfico de pizza** programaticamente, o Aspose.Words torna isso simples. Neste tutorial você verá como **inserir gráfico no Word**, configurar as séries, **adicionar rótulos de dados ao gráfico de pizza**, e finalmente **exibir percentuais no gráfico de pizza** para que a visualização transmita valores exatos. Ao final, você terá um exemplo completo e executável que pode ser inserido em qualquer projeto .NET.

Este guia cobre tudo o que você precisa saber: pacotes NuGet necessários, o código C# completo, explicações sobre por que cada chamada de API é importante e dicas para personalizar o gráfico. Nenhuma documentação externa é necessária — basta copiar, executar e adaptar.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior instalado.  
* Visual Studio 2022 (ou qualquer IDE que suporte .NET).  
* Uma licença do Aspose.Words for .NET (a avaliação gratuita funciona para testes).  
* Familiaridade básica com C# e estruturas de documentos Word.

Se você já possui esses itens, pode seguir direto para o código.

## Etapa 1: Configurar o projeto e importar Aspose.Words

Crie um novo projeto de console e adicione o pacote NuGet Aspose.Words:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

O pacote inclui o namespace `Aspose.Words.Drawing.Charts`, que contém as classes `Chart` e `ChartSeries` que usaremos.

> **Dica profissional:** Mantenha seu arquivo de licença (`Aspose.Words.lic`) na raiz do projeto e carregue‑o na inicialização para evitar marcas d'água de avaliação.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Etapa 2: Criar um documento em branco e um DocumentBuilder

Um `Document` representa o arquivo Word, enquanto `DocumentBuilder` fornece uma API fluente para inserir conteúdo.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa:** O `DocumentBuilder` mantém o ponto de inserção atual, garantindo que o gráfico apareça exatamente onde você deseja no fluxo do documento.

## Etapa 3: Inserir um gráfico de pizza no documento Word

Agora nós **inserimos o gráfico no Word**. O método `InsertChart` recebe o tipo de gráfico, a largura e a altura (em pontos).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Neste ponto o gráfico contém uma série de dados padrão com valores de espaço reservado (25, 25, 25, 25). Você pode substituí‑los mais tarde, se necessário.

## Etapa 4: Acessar a primeira série e personalizar os rótulos de dados

Um gráfico de pizza normalmente tem uma única série. Para **adicionar rótulos de dados ao gráfico de pizza**, recuperamos a série e habilitamos a exibição de percentual.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Por que definimos `ShowPercentage`:** Essa flag indica ao Aspose.Words para calcular a contribuição de cada fatia e renderizá‑la como percentual. A propriedade `Position` garante que o rótulo não se sobreponha à fatia, melhorando a legibilidade — especialmente quando as fatias são pequenas.

## Etapa 5: (Opcional) Substituir os dados de espaço reservado

Se você quiser valores específicos, substitua os pontos padrão:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Os percentuais exibidos serão ajustados automaticamente para refletir os novos valores.

## Etapa 6: Salvar o documento

Por fim, grave o documento no disco. A extensão determina o formato; `.docx` cria um arquivo Word moderno.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Executar o programa gera um arquivo chamado **PieChart.docx** na pasta de saída. Ao abri‑lo no Microsoft Word, você verá um gráfico de pizza com cada fatia rotulada pelo seu percentual, posicionado fora das fatias.

### Resultado esperado

Ao abrir o documento gerado, você deverá ver:

* Um único gráfico de pizza, 400 × 300 pt de tamanho.  
* Quatro fatias (ou quantos pontos você adicionou).  
* Rótulos de percentual como “40 %”, “30 %”, etc., exibidos fora de cada fatia.

Se os rótulos aparecerem dentro das fatias, verifique se `ChartDataLabelPosition.OutsideEnd` foi definido corretamente.

## Etapa 7: Variações comuns e casos de borda

### Adicionar um título ao gráfico

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Alterar cores das fatias

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Manipular uma série vazia

Se sua fonte de dados puder estar vazia, proteja‑se contra `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Exportar para PDF em vez de Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

A mesma lógica de renderização do gráfico se aplica; o Aspose.Words converte o layout do Word para PDF automaticamente.

## Listagem completa do código fonte

Abaixo está o programa completo, pronto‑para‑executar. Copie‑o para `Program.cs` e execute `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Conclusão

Agora você sabe como **criar um gráfico de pizza** em um arquivo Word usando Aspose.Words, **inserir gráfico no Word**, **adicionar rótulos de dados ao gráfico de pizza** e **exibir percentuais no gráfico de pizza**. O exemplo demonstra todo o fluxo de trabalho — desde a configuração do projeto até o documento final — para que você possa adaptá‑lo a dashboards, relatórios ou geração automática de faturas.

Em seguida, explore tópicos relacionados como **como exibir percentuais nas legendas do gráfico**, personalização de cores do gráfico ou conversão do documento Word para PDF para distribuição. Experimente diferentes tipos de gráfico (Bar, Line) usando o mesmo método `InsertChart` para ampliar suas capacidades de automação.

Boa criação de gráficos!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}