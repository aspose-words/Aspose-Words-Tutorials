---
category: general
date: 2026-10-13
description: 'Salvar documento modificado após personalizar um gráfico de pizza: explodir
  fatias, alterar o ângulo da primeira fatia e exibir rótulos de porcentagem em C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: pt
lastmod: 2026-10-13
og_description: Salve o documento modificado após personalizar um gráfico de pizza
  em C#. Aprenda como explodir fatias do gráfico, alterar o ângulo da primeira fatia
  e exibir rótulos de porcentagem.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Salvar documento modificado com fatias de gráfico de pizza explodidas –
  Guia C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Salvar documento modificado com fatias de gráfico de pizza explodidas em C#
url: /pt/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar documento modificado com fatias de gráfico de pizza explodidas em C#

Se você precisar **salvar documento modificado** após ajustar um gráfico de pizza no Word, este guia mostra exatamente como fazer. Você aprenderá a explodir fatias de gráfico de pizza, mudar o ângulo da primeira fatia e exibir rótulos de porcentagem — tudo com algumas linhas de código C#.

Personalizar gráficos é uma necessidade comum ao gerar relatórios, faturas ou painéis programaticamente. Ao final deste tutorial, você será capaz de carregar um arquivo DOCX, modificar a aparência do gráfico e **salvar documento modificado** pronto para distribuição.

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
- Aspose.Words para .NET 23.10 ou mais recente (versão de avaliação gratuita ou cópia licenciada)
- Um arquivo Word (`input.docx`) que contém um único gráfico de pizza
- Visual Studio 2022 ou qualquer IDE C#

> **Dica:** O pacote NuGet Aspose.Words é adicionado com `dotnet add package Aspose.Words`.

## Etapa 1: Carregar o documento Word que contém o gráfico

O primeiro passo é abrir o arquivo DOCX de origem. A classe `Document` representa todo o arquivo Word na memória.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Carregar o documento fornece acesso total a cada nó, incluindo formas que hospedam gráficos.

## Etapa 2: Recuperar a primeira forma de gráfico do documento

Os gráficos são armazenados dentro de nós `Shape`. Você pode localizar o primeiro gráfico com `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Se o documento contiver vários gráficos, ajuste o índice (`0`) ou itere pela coleção. Esta linha garante que você tenha uma referência ao objeto `Chart` que será modificado.

## Etapa 3: Explodir fatias de gráfico de pizza

Explodir uma fatia a separa do restante da pizza, facilitando a leitura do gráfico. A propriedade `Explode` funciona para toda a série.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Definir `Explode` como `true` **explodirá fatias de gráfico de pizza** para toda a série, o que é útil quando você deseja que cada fatia se destaque.

## Etapa 4: Alterar o ângulo da primeira fatia

Às vezes você precisa que a primeira fatia comece em um ângulo personalizado, por exemplo para alinhar com uma diretriz de design.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

A propriedade `FirstSliceAngle` **altera a primeira fatia** de orientação, girando toda a pizza para que a primeira fatia comece a 30 graus.

## Etapa 5: Exibir rótulos de porcentagem nas fatias de pizza

Exibir a contribuição numérica de cada fatia é frequentemente necessário em relatórios. A bandeira `DataLabel.ShowPercentage` ativa os valores de porcentagem.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Esta etapa **exibe rótulos de porcentagem** diretamente no gráfico, o que também atende ao requisito **exibir porcentagens no gráfico de pizza**.

## Etapa 6: Salvar o documento modificado

Depois que todas as personalizações forem aplicadas, persista as alterações em um novo arquivo. O método `Save` grava o DOCX atualizado no disco.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Agora você tem um **documento modificado salvo** que contém um gráfico de pizza explodido, uma primeira fatia rotacionada e rótulos de porcentagem visíveis.

![Salvar documento modificado mostrando gráfico de pizza explodido](/images/pie-chart-exploded.png "Salvar documento modificado com fatias de gráfico de pizza explodidas e rótulos de porcentagem")

*A captura de tela ilustra o resultado final após o documento ser salvo.*

## Exemplo completo e executável

Juntando as peças, aqui está o programa completo que você pode copiar‑colar em um projeto de console:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Resultado esperado

Abrir `output.docx` exibirá um gráfico de pizza onde:

- Cada fatia está ligeiramente separada (**fatias de gráfico de pizza explodidas**)
- A primeira fatia começa com um deslocamento de 30 graus (**alterar primeira fatia**)
- Cada fatia mostra sua contribuição como porcentagem (**exibir rótulos de porcentagem**, **exibir porcentagens no gráfico de pizza**)
- O arquivo foi **salvo documento modificado** sem alterar o original.

## Perguntas comuns e casos de borda

| Pergunta | Resposta |
|----------|----------|
| **E se o documento não tiver gráfico?** | O código verifica se há `null` após `GetChild`. Se nenhum gráfico existir, você pode adicioná‑lo programaticamente ou abortar com uma mensagem clara. |
| **Posso explodir apenas uma única fatia?** | Sim. Use `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` onde `i` é o índice da fatia. |
| **Como altero o formato do rótulo (ex.: exibir valor + %)?** | Defina `chart.PieChart.DataLabel.ShowValue = true;` e, opcionalmente, `chart.PieChart.DataLabel.ShowPercentage = true;` para combinar ambos. |
| **O estilo do gráfico é preservado após salvar?** | Aspose.Words mantém toda a formatação, incluindo cores e fontes, quando você **salva documento modificado**. |
| **Posso processar vários gráficos no mesmo arquivo?** | Percorra todos os nós `Shape` com `NodeType.Shape` e filtre por `shape.HasChart`. Aplique as mesmas etapas a cada gráfico. |

## Conclusão

Agora você sabe como **salvar documento modificado** após personalizar programaticamente um gráfico de pizza no Word. O guia abordou a explosão de fatias de gráfico de pizza, a alteração do ângulo da primeira fatia e a exibição de rótulos de porcentagem — atendendo aos requisitos de **exibir rótulos de porcentagem**, **explodir fatias de gráfico de pizza**, **exibir porcentagens no gráfico de pizza** e **alterar primeira fatia**.

Em seguida, considere explorar:

- Adicionar séries de dados dinamicamente (`chart.Series.Add(...)`)  
- Personalizar a posição da legenda e os títulos dos gráficos  
- Converter o DOCX para PDF mantendo a formatação do gráfico  

Sinta-se à vontade para experimentar diferentes ângulos, configurações de explosão ou formatos de rótulo para atender às suas necessidades de relatório. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Como salvar documento editado em C# com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Atualizar dados da série de gráfico em um documento Word usando Aspose.Words para .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Inserir gráfico de colunas em um documento Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}