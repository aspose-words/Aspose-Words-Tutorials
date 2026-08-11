---
category: general
date: 2026-08-10
description: Crie um documento Word com gráfico de pizza usando Aspose.Words. Aprenda
  como inserir o gráfico, personalizar as cores do gráfico de pizza e alterar a cor
  de uma fatia da pizza em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: pt
lastmod: 2026-08-10
og_description: Crie um documento Word com gráfico de pizza usando Aspose.Words. Este
  guia explica como inserir o gráfico, personalizar as cores do gráfico de pizza e
  alterar a cor de uma fatia do gráfico em uma aplicação C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Criar documento Word com gráfico de pizza – Guia Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Criar documento Word com gráfico de pizza usando Aspose.Words
url: /pt/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word com gráfico de pizza usando Aspose.Words

Se você precisa **criar documento Word com gráfico de pizza** programaticamente, este tutorial mostra exatamente como fazer. Vamos percorrer a inserção de um gráfico, **personalizar cores do gráfico de pizza**, e **alterar a cor de fatia da pizza** usando Aspose.Words para .NET.

Você verá um exemplo completo e executável que pode copiar para o Visual Studio, executar e abrir imediatamente o *.docx* gerado para verificar o gráfico de pizza estilizado. Nenhuma documentação externa é necessária — tudo o que você precisa está neste guia.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior instalado  
* Uma licença válida do Aspose.Words para .NET (ou uma chave de avaliação temporária)  
* Visual Studio 2022 (ou qualquer IDE C#)  

O código usa apenas os namespaces `Aspose.Words` e `Aspose.Words.Drawing.Charts`, portanto nenhum pacote NuGet adicional é necessário além da biblioteca Aspose.Words.

## Criar documento Word com gráfico de pizza – exemplo completo

O programa C# a seguir cria um novo documento Word, insere um gráfico de pizza, estiliza as duas primeiras fatias e salva o arquivo. Cada passo é explicado em detalhes.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Explicação de cada passo

| Etapa | O que faz | Por que importa |
|------|-----------|-----------------|
| **1** | Cria um novo `Document` e um `DocumentBuilder`. | O `DocumentBuilder` fornece métodos fluentes para inserir conteúdo, como gráficos, no arquivo Word. |
| **2** | Chama `InsertChart` com `ChartType.Pie` e um tamanho fixo. | `InsertChart` é o **como inserir gráfico**; especificar largura/altura garante que o gráfico caiba bem na página. |
| **3** | Adiciona uma série de dados com três categorias e valores numéricos. | Um gráfico de pizza sem dados é invisível; preenchê‑lo demonstra as etapas de estilo. |
| **4** | Define `Explosion` no primeiro ponto. | Explodir uma fatia chama atenção para um segmento específico — útil para destacar dados importantes. |
| **5** | Define `ForeColor` para os dois primeiros pontos. | Este é o núcleo de **personalizar cores do gráfico de pizza**; você pode usar qualquer `System.Drawing.Color`. |
| **6** | Mostra como **alterar a cor da fatia da pizza** para fatias adicionais. | Demonstrar que a estilização não está limitada às duas primeiras fatias; você pode colorir cada fatia individualmente. |
| **7** | Salva o documento como `PieChartStyled.docx`. | A saída final pode ser aberta no Microsoft Word, Google Docs ou qualquer visualizador compatível. |

#### Saída esperada

Abrir `PieChartStyled.docx` exibe uma única página com um gráfico de pizza de 400 × 300 pt:

* Fatia 1 (laranja) está explodida para fora.  
* Fatia 2 (verde) aparece adjacente à fatia explodida.  
* Fatia 3 (azul‑aço) preenche o segmento restante.

O gráfico reflete os valores dos dados (30, 45, 25) e as cores personalizadas que você definiu.

## Como estilizar o gráfico de pizza – dicas adicionais

* **Use cores do tema** – em vez de codificar `Color.Orange`, você pode obter cores do tema do documento:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Adicionar rótulos de dados** – se quiser porcentagens mostradas no gráfico:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Redimensionar dinamicamente** – calcule o tamanho do gráfico com base nas margens da página:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Essas variações demonstram a flexibilidade de **como estilizar o gráfico de pizza** além do exemplo básico.

## Perguntas frequentes respondidas

**Q: Isso funciona com .NET Core?**  
A: Sim. Aspose.Words para .NET é compatível com .NET Core, .NET 5, .NET 6 e posteriores. Basta referenciar o mesmo pacote NuGet.

**Q: E se eu precisar de um gráfico de rosquinha em vez de pizza?**  
A: Substitua `ChartType.Pie` por `ChartType.Doughnut`. As mesmas APIs de estilo (`Explosion`, `ForeColor`) se aplicam.

**Q: Posso inserir o gráfico em um documento existente?**  
A: Abra o arquivo existente com `new Document("Existing.docx")`, crie um `DocumentBuilder` para esse documento e chame `InsertChart` na posição do cursor desejada.

**Q: Como lidar com conjuntos de dados grandes?**  
A: Gráficos de pizza são melhores para um número limitado de categorias (geralmente < 10). Para muitas categorias, considere um gráfico de barras ou colunas.

## Recapitulação do código‑fonte completo

Abaixo está o programa completo em um único bloco para fácil copiar‑colar:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Executar este código produz o documento Word com o gráfico de pizza estilizado descrito anteriormente.

## Conclusão

Agora você sabe como **criar documentos Word com gráfico de pizza** usando Aspose.Words, **personalizar cores do gráfico de pizza** e **alterar a cor de fatia da pizza** programaticamente. O guia cobriu a inserção do gráfico, o preenchimento de dados, a explosão de uma fatia, a aplicação de cores personalizadas e a gravação do resultado.  

A partir daqui, você pode explorar tópicos relacionados, como **como inserir gráficos** de tipos diferentes de pizza, adicionar legendas ou gerar relatórios de várias páginas com múltiplos gráficos. Experimente diferentes esquemas de cores e conjuntos de dados para atender às suas necessidades de relatório.

Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir gráfico de colunas no Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Inserir gráfico de área em documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Criar gráfico de dispersão no Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}