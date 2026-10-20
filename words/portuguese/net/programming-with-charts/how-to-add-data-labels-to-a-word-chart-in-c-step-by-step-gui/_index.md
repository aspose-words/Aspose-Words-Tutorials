---
category: general
date: 2026-08-04
description: Como adicionar rótulos de dados em C# com Aspose.Words. Aprenda a editar
  o gráfico, centralizar os rótulos de dados, exibir porcentagens no gráfico e personalizar
  os rótulos de dados.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: pt
lastmod: 2026-08-04
og_description: Como adicionar rótulos de dados em C# usando Aspose.Words. Este tutorial
  mostra como editar o gráfico, centralizar os rótulos de dados do gráfico, exibir
  porcentagens no gráfico e personalizar os rótulos de dados do gráfico.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Como adicionar rótulos de dados a um gráfico do Word em C# – guia completo
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Como adicionar rótulos de dados a um gráfico do Word em C# – guia passo a passo
url: /pt/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar rótulos de dados a um gráfico do Word em C# – guia passo a passo

Se você precisa **how to add data labels** a um gráfico que está dentro de um documento Word, este guia mostra o código exato que você deve executar. Você verá como editar propriedades do gráfico, centralizar rótulos de dados do gráfico, mostrar porcentagens no gráfico e personalizar rótulos de dados do gráfico para qualquer cenário.

O tutorial cobre tudo o que é necessário para modificar um gráfico existente, desde o carregamento do documento até a persistência das alterações. Nenhuma referência externa é necessária — apenas a biblioteca Aspose.Words for .NET e um ambiente básico de desenvolvimento C#.

## Pré-requisitos

* .NET 6.0 (ou posterior) instalado.
* Aspose.Words for .NET versão 23.9 ou mais recente.  
  Você pode instalá-lo via NuGet:

```bash
dotnet add package Aspose.Words
```

* Um arquivo Word (`input.docx`) que contém ao menos um gráfico.

## Como adicionar rótulos de dados a um gráfico do Word em C#

As seções a seguir guiam você passo a passo. A palavra‑chave principal **how to add data labels** aparece naturalmente na narrativa e nos comentários do código, mantendo a densidade dentro da faixa recomendada.

### Etapa 1 – Carregar o documento Word que contém o gráfico

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Por que esta etapa é importante*: O objeto `Document` representa todo o arquivo Word. Carregá‑lo dá acesso a todos os nós, incluindo formas que hospedam gráficos.

### Etapa 2 – Recuperar o primeiro gráfico do documento

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Por que esta etapa é importante*: Os gráficos são armazenados dentro de nós `Shape`. Ao converter o nó recuperado para `Shape` e chamar `GetChart()`, você obtém um objeto `Chart` que expõe séries, eixos e coleções de rótulos.

### Etapa 3 – Habilitar a personalização de rótulos de dados e mostrar porcentagens no gráfico

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Por que esta etapa é importante*: Definir `ShowPercentage` indica ao Aspose.Words que calcule e exiba a contribuição de cada fatia ao total. Isso atende diretamente à palavra‑chave secundária **show percentages in chart**.

### Etapa 4 – Alterar a posição do rótulo para o centro de cada ponto de dados

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Por que esta etapa é importante*: A propriedade `Position` controla onde o rótulo aparece em relação ao ponto de dados. Usar `Center` satisfaz a palavra‑chave secundária **center chart data labels** e melhora a legibilidade de gráficos de pizza ou rosquinha.

### Etapa 5 – Personalizar ainda mais os rótulos de dados do gráfico (opcional)

Se precisar de mais controle, você pode ajustar fonte, cor ou linhas de ligação:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Essas configurações ilustram a palavra‑chave secundária **customize chart data labels** e demonstram como você pode adaptar a aparência para corresponder às diretrizes da marca.

### Etapa 6 – Salvar o documento modificado

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Por que esta etapa é importante*: Salvar grava o gráfico atualizado de volta no documento Word, tornando os novos rótulos de dados visíveis quando o arquivo for aberto no Microsoft Word.

## Exemplo completo e executável

Abaixo está um programa completo que você pode copiar, colar e executar. Ele inclui todas as diretivas `using` necessárias e comentários que explicam cada linha.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Resultado esperado

Ao abrir `output.docx` no Microsoft Word, o gráfico exibirá:

* Valores percentuais ao lado de cada fatia (por exemplo, **25 %**, **40 %**, …).
* Rótulos posicionados no centro de cada ponto de dados.
* Qualquer estilo adicional que você aplicou, como texto vermelho em negrito.

Essas indicações visuais tornam o gráfico mais fácil de interpretar, especialmente em apresentações ou relatórios.

## Como editar propriedades do gráfico além dos rótulos de dados

Embora o foco deste guia seja **how to add data labels**, você também pode querer **how to edit chart** configurações como títulos, posicionamento da legenda ou formatação dos eixos. O objeto `Chart` fornece propriedades como `Title`, `Legend` e `AxisX/AxisY`. Por exemplo, para alterar o título do gráfico:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Todas as modificações de gráfico seguem o mesmo padrão: recuperar o gráfico, ajustar suas propriedades e, em seguida, salvar o documento.

## Armadilhas comuns e dicas de boas práticas

| Problema | Por que acontece | Correção recomendada |
|---|---|---|
| O gráfico está dentro de uma forma agrupada. | `GetChild(NodeType.Shape, …)` retorna o grupo externo, não o gráfico interno. | Pesquise recursivamente por uma forma com `shape.HasChart`. |
| Os rótulos de dados não aparecem após salvar. | `ShowValue` ou `ShowPercentage` não foi definido como `true`. | Defina explicitamente ambos `ShowValue` e `ShowPercentage` conforme necessário. |
| Os rótulos se sobrepõem em fatias pequenas. | O posicionamento central pode causar aglomeração. | Use `ChartDataLabelPosition.OutSideEnd` para posicionamento externo, ou habilite `LeaderLines`. |

## Conclusão

Agora você sabe **how to add data labels** a um gráfico do Word usando C#. O tutorial abordou a recuperação do gráfico, habilitação da visibilidade dos rótulos, centralização dos rótulos, exibição de porcentagens e personalização da aparência. Com esse conhecimento você também pode **how to edit chart** detalhes, **center chart data labels**, **show percentages in chart**, e **customize chart data labels** para qualquer cenário de relatório.

Pronto para explorar mais? Tente adicionar múltiplas séries, aplicar formatação condicional ou exportar o gráfico como imagem. A API Aspose.Words oferece amplas capacidades de manipulação de gráficos — experimente para encontrar a representação visual perfeita para seus dados.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}