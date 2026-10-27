---
category: general
date: 2026-07-20
description: Adicione rótulos de gráfico de pizza com Aspose.Words para .NET. Aprenda
  como alterar os rótulos de gráfico de pizza, exibir rótulos de porcentagem e atualizar
  rapidamente os rótulos das séries do gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: pt
lastmod: 2026-07-20
og_description: Adicione rótulos de gráfico de pizza em C# com Aspose.Words. Domine
  a alteração de rótulos de gráfico de pizza, exiba rótulos de porcentagem e atualize
  os rótulos das séries do gráfico em apenas alguns passos.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Adicionar rótulos de gráfico de pizza em C# – Tutorial completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Adicionar rótulos de gráfico de pizza em C# usando Aspose.Words – Guia Completo
url: /pt/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar rótulos de gráfico de pizza em C# usando Aspose.Words – Guia Completo

Precisa **adicionar rótulos de gráfico de pizza** a um documento Word usando C#? Com Aspose.Words você pode facilmente **alterar rótulos de gráfico de pizza** e **exibir percentuais de gráfico de pizza** diretamente no arquivo — sem necessidade de ajustes manuais no Word.

Neste tutorial vamos percorrer os passos exatos para **exibir rótulos de percentual**, reposicioná‑los e até **atualizar rótulos de séries de gráfico** para dados dinâmicos. Ao final, você terá um trecho reutilizável que pode inserir em qualquer projeto .NET.

> **Pré‑visualização rápida:** Depois de seguir o guia, ao abrir o `.docx` salvo será exibido um gráfico de pizza onde cada fatia está rotulada com seu percentual, posicionado fora da fatia para máxima legibilidade.

---

## O que você precisará

- **Aspose.Words for .NET** (a versão mais recente em 2026). Você pode obtê‑lo no NuGet: `Install-Package Aspose.Words`.
- Um **documento Word** que já contenha um gráfico de pizza ou donut (vamos chamá‑lo de `Chart.docx`).
- Familiaridade básica com **C#** e Visual Studio (ou sua IDE favorita).

Isso é tudo — sem bibliotecas extras, sem interop COM, apenas código gerenciado puro.

---

## Adicionar rótulos de gráfico de pizza – Implementação completa

Segue um programa **completo e executável** em C# console que carrega um documento, modifica o primeiro gráfico de pizza e salva o resultado. Cada linha está comentada para que você entenda **por que** estamos fazendo o que fazemos, não apenas **o que**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Resultado esperado

Abrir `ChartWithCustomLabels.docx` no Microsoft Word. Você deverá ver o gráfico de pizza **com rótulos de percentual posicionados fora de cada fatia**. Os rótulos aparecem como “35 %”, “20 %”, etc., tornando o gráfico imediatamente compreensível.

---

## Alterar rótulos de gráfico de pizza: posicionamento e formatação

Se você só precisa **alterar rótulos de gráfico de pizza** sem exibir percentuais, pode ajustar a propriedade `Position` para uma das seguintes:

| Enum de Posição | Efeito Visual |
|-----------------|---------------|
| `InsideEnd`   | Rótulos ficam dentro da fatia, bem na borda. |
| `Center`      | Rótulos aparecem no centro da fatia (bom para pizzas pequenas). |
| `OutsideEnd`  | Rótulos ficam fora da fatia, conectados por uma linha guia (padrão). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Dica profissional:** `OutsideEnd` funciona melhor quando o gráfico tem muitas fatias; evita sobreposição de texto.

---

## Exibir rótulos de percentual em um gráfico de pizza

A propriedade `ShowPercentage` é uma **flag booleana**. Definir como `true` indica ao Aspose.Words que calcule a contribuição de cada fatia com base na fonte de dados subjacente.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Você também pode combiná‑la com `ShowValue` se precisar tanto dos números brutos **quanto** dos percentuais:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Quando ambas as flags estão habilitadas, o rótulo aparece como “45 % (120)”.

---

## Atualizar rótulos de séries de gráfico para dados dinâmicos

Frequentemente você gera gráficos dinamicamente — pense em vendas mensais ou resultados de pesquisas. Para **atualizar rótulos de séries de gráfico** programaticamente, modifique a coleção `Series` antes de manipular os rótulos de dados:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Este trecho demonstra como **atualizar rótulos de séries de gráfico** para qualquer série, não apenas a primeira. É útil ao criar relatórios que combinam dados reais e previsões.

---

## Casos Limites e Armadilhas Comuns

| Situação | O que observar | Correção |
|----------|----------------|----------|
| **O gráfico não é de pizza/donut** | `Position` pode não ter efeito visual. | Verifique se `chart.Type` é `ChartType.Pie` ou `ChartType.Doughnut`. |
| **Nenhum gráfico encontrado** | `GetChild` retorna `null`. | Adicione uma cláusula de proteção (veja o código) e registre uma mensagem útil. |
| **Versão antiga do Word** | Alguns recursos de rótulo são ignorados. | Salve como `.docx` (formato moderno) para garantir suporte total. |
| **Grande número de fatias** | Rótulos podem se sobrepor mesmo com `OutsideEnd`. | Considere reduzir o número de fatias ou aumentar o tamanho do gráfico. |

---

## Exemplo Completo Funcional (Copiar‑Colar)

Abaixo está o **programa completo** que você pode copiar para um novo projeto console. Basta substituir `YOUR_DIRECTORY` pela pasta que contém `Chart.docx`.



## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Definir Opções Padrão para Rótulos de Dados em um Gráfico](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Personalizar Série Única de Gráfico em um Gráfico](/words/english/net/programming-with-charts/single-chart-series/)
- [Inserir Gráfico de Colunas no Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}