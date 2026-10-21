---
category: general
date: 2026-08-04
description: Posicionamento personalizado de rótulos de dados para gráficos em C#
  permite centralizar os rótulos nas fatias do gráfico. Siga este guia passo a passo
  usando a API de gráficos do Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: pt
lastmod: 2026-08-04
og_description: Posicionamento Personalizado de Rótulos de Dados para Gráficos em
  C# mostra como centralizar todos os rótulos de dados em cada fatia de um gráfico
  do Word. Domine o posicionamento de rótulos de dados em gráficos com Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Posicionamento Personalizado de Rótulos de Dados em Gráficos no C# – guia
  passo a passo
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Posicionamento Personalizado de Rótulos de Dados para Gráficos em C#
url: /pt/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Posicionamento Personalizado de Rótulos de Dados para Gráficos em C#

**Custom Data‑Label Placement for Charts** permite que você controle exatamente onde cada rótulo aparece em um gráfico dentro de um documento Word. Neste tutorial você aprenderá como centralizar todos os rótulos de dados em cada fatia usando C# e a API de gráficos do Aspose.Words.

Você receberá um exemplo completo e executável que carrega um arquivo `.docx`, acessa a primeira forma de gráfico, altera o `Position` de cada rótulo para `Center` e salva o documento atualizado. Nenhuma referência externa é necessária — apenas a biblioteca Aspose.Words for .NET e um ambiente básico de desenvolvimento C#.

**What you’ll learn**

* Como carregar um documento Word que contém um gráfico.  
* Como localizar a forma de gráfico com a API de gráficos do Aspose.Words.  
* Como aplicar **chart data label positioning** a cada série no gráfico.  
* Como salvar o documento para que os rótulos centralizados apareçam no Word.  

**Prerequisites**

* .NET 6.0 (ou posterior) instalado.  
* Visual Studio 2022 (ou qualquer IDE C#).  
* Uma referência ao pacote NuGet `Aspose.Words`.  
* Um arquivo Word (`Chart.docx`) que contenha ao menos um gráfico.

---

## Posicionamento Personalizado de Rótulos de Dados para Gráficos – passo 1: carregar o documento

A primeira ação é abrir o arquivo Word que contém o gráfico. `Document` é o ponto de entrada para qualquer manipulação com Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Por que esta etapa é importante*: Sem carregar o documento você não pode acessar o objeto do gráfico. A validação garante que você receba um erro claro se o arquivo não contiver um gráfico, evitando uma referência nula posteriormente.

---

## Usando a API de gráficos do Aspose.Words para acessar formas de gráfico

Aspose.Words trata um gráfico como um objeto `Chart` aninhado dentro de um `Shape`. Você o recupera fazendo cast do nó filho apropriado.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Por que esta etapa é importante*: Acessar diretamente o `Chart` lhe dá controle total sobre séries, pontos de dados e propriedades dos rótulos. Se a forma não for um gráfico, o código aborta cedo com uma mensagem informativa.

---

## Definindo o posicionamento dos rótulos de dados do gráfico em C#

Agora itere por cada série e cada rótulo de dados, definindo o `Position` para `Center`. Este é o núcleo do **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Pro tip**: Se precisar de um posicionamento diferente (por exemplo, `InsideEnd` para um gráfico de colunas), altere o valor do enum conforme necessário. O enum `ChartDataLabelPosition` cobre todas as posições padrão suportadas pelo Word.

*Por que esta etapa é importante*: Alterar `label.Position` atualiza a representação OOXML subjacente, de modo que o rótulo apareça centralizado quando o documento for aberto no Microsoft Word.

---

## Salvando o documento Word com rótulos atualizados

Após modificar o gráfico, persista as alterações de volta para um arquivo. Você pode sobrescrever o original ou criar uma nova cópia.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Por que esta etapa é importante*: Salvar grava o OOXML atualizado no disco. Abrir `ChartLabelsCentered.docx` no Word mostrará cada rótulo de fatia centralizado, confirmando que o **Custom Data‑Label Placement for Charts** foi bem-sucedido.

---

## Casos de borda e variações

| Situação | Como lidar |
|-----------|---------------|
| **Múltiplos gráficos** no mesmo documento | Percorra `doc.GetChildNodes(NodeType.Shape, true)` e verifique `shape.HasChart` para cada forma. |
| **Tipos diferentes de gráfico** (pizza, rosquinha, barra) | O mesmo `ChartDataLabelPosition.Center` funciona para gráficos do tipo pizza. Para gráficos de barra/coluna você pode preferir `InsideEnd` ou `OutsideEnd`. |
| **Texto do rótulo precisa de formatação** | Acesse `label.TextProperties` para definir tamanho da fonte, cor ou negrito. |
| **Executando no .NET Core** | Certifique‑se de referenciar a versão .NET Standard do Aspose.Words; a API é idêntica. |

---

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar‑colar em uma aplicação console. Ele inclui todas as diretivas `using` necessárias e tratamento de erros.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Resultado esperado**: Abra `ChartLabelsCentered.docx` no Microsoft Word. Cada fatia do gráfico agora exibe seu rótulo de dados diretamente no centro da fatia, proporcionando uma aparência visual mais limpa.

---

## Conclusão

Agora você tem uma solução completa de **Custom Data‑Label Placement for Charts** em C#. Ao carregar o documento, acessar o gráfico via a API de gráficos do Aspose.Words, definir `ChartDataLabelPosition.Center` para cada rótulo e salvar o arquivo, você pode automatizar o posicionamento de rótulos para qualquer gráfico baseado em Word.

Em seguida, explore outras opções de **posicionamento de rótulos de dados de gráfico** como `InsideEnd` ou `OutsideEnd`, ou experimente a **manipulação de gráficos em C#** para alterar cores, adicionar legendas ou gerar gráficos do zero. Essas extensões se baseiam diretamente nas técnicas abordadas aqui e ampliam suas habilidades de automação de gráficos em documentos Word. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}