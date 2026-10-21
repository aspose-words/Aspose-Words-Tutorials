---
category: general
date: 2026-10-13
description: Aprenda a ajustar programaticamente os rótulos de gráficos em um documento
  Word usando C#. Este guia aborda a manipulação de gráficos do Aspose.Words e o alinhamento
  de rótulos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: pt
lastmod: 2026-10-13
og_description: Ajuste programaticamente os rótulos de gráfico em um documento Word
  usando C#. Siga este tutorial completo para mudar a posição dos rótulos, o alinhamento
  e muito mais.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Ajuste programático de rótulos de gráfico no Word – Guia passo a passo em
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Ajustar programaticamente os rótulos do gráfico em um documento Word com C#
url: /pt/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajustar programaticamente rótulos de gráfico em um documento Word com C#

Se você precisa **ajustar programaticamente rótulos de gráfico** em um documento Word, este guia mostra exatamente como fazer isso com C#. Seja gerando relatórios, automatizando dashboards ou personalizando modelos, você verá um exemplo completo e executável que altera a posição e o alinhamento dos rótulos de um gráfico dentro de um arquivo .docx.

Você também aprenderá a usar as técnicas de **manipulação de gráficos do Aspose.Words**, lidar com múltiplas séries e evitar armadilhas comuns ao trabalhar com objetos **C# chart data label**.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 (ou superior) instalado  
* Visual Studio 2022 (ou qualquer IDE C#)  
* O pacote NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Um documento Word (`input.docx`) que contenha ao menos um gráfico  

Esses itens são necessários para o **exemplo de gráfico em documento Word** que iremos modificar.

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo projeto de console e adicione as diretivas `using` necessárias. Isso prepara o ambiente para **ajustar programaticamente rótulos de gráfico**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Por que esta etapa?*  
Carregar o documento lhe dá acesso à árvore interna do **exemplo de gráfico em documento Word**, onde os gráficos são armazenados como nós de forma.

## Etapa 2: Localizar a primeira forma de gráfico

Os gráficos são armazenados como nós `Shape`. O código a seguir recupera o primeiro gráfico no documento, que será o alvo dos nossos ajustes de rótulo.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Por que esta etapa?*  
O método `GetChild` pesquisa recursivamente (`true`) e retorna o primeiro nó do tipo `Shape`. Fazer o cast para `Chart` permite trabalhar com a API específica de gráficos.

## Etapa 3: Acessar o rótulo de dados que você deseja modificar

Cada série em um gráfico possui uma coleção de rótulos de dados. Para um gráfico simples, o primeiro rótulo costuma ser suficiente. O código abaixo mostra como alcançá‑lo.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Por que esta etapa?*  
`ChartSeries` representa uma série de pontos. `DataLabelCollection` contém os rótulos dessa série, permitindo controle preciso sobre posição e alinhamento.

## Etapa 4: Alterar a posição e o alinhamento do rótulo

Agora nós **ajustamos programaticamente rótulos de gráfico** definindo a posição, o alinhamento horizontal e o alinhamento vertical. Essas propriedades correspondem às opções que você vê na interface do Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Por que essas configurações?*  

* `OutsideEnd` coloca o rótulo logo fora da extremidade de cada barra ou coluna, melhorando a legibilidade.  
* `HorizontalAlignment.Center` mantém o texto centralizado sobre o ponto, enquanto `VerticalAlignment.Top` alinha a borda superior do rótulo ao ponto de dados, evitando sobreposição com outros elementos.

### Dica profissional
Se um gráfico possui várias séries, percorra `chart.Series` e aplique as mesmas configurações a cada `DataLabelCollection`. Isso garante uma aparência consistente em todo o gráfico.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Etapa 5: Salvar o documento modificado

Depois de ajustar os rótulos, persista as alterações em um novo arquivo. Isso completa o processo de **modificar a posição do rótulo do gráfico**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Ao abrir `output.docx`, você verá que cada rótulo de gráfico foi movido para o final externo do seu ponto de dados, centralizado horizontalmente e alinhado ao topo verticalmente.

## Casos limites e variações

| Situação | O que observar | Abordagem recomendada |
|-----------|-------------------|----------------------|
| **Múltiplos gráficos** no mesmo documento | `GetChild` retorna apenas o primeiro gráfico. | Use `doc.GetChildNodes(NodeType.Shape, true)` para iterar sobre todas as formas de gráfico. |
| **Séries sem rótulos de dados** | `DataLabelCollection` pode estar vazia. | Verifique `series.HasDataLabels` antes de acessar a coleção. |
| **Tipos de gráfico diferentes** (pizza, linha, dispersão) | Nem todos os valores de `DataLabelPosition` são válidos. | Use `DataLabelPosition.Auto` para gráficos que decidem a melhor posição automaticamente. |
| **Localização** | Constantes de alinhamento são independentes de idioma, mas o texto renderizado pode precisar de suporte bidirecional. | Defina `dataLabel.TextDirection` se precisar de idiomas RTL. |

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar, colar e executar. Substitua `YOUR_DIRECTORY` por um caminho de pasta real.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Resultado esperado:** Ao abrir `output.docx`, cada rótulo de gráfico estará posicionado fora do ponto de dados, centralizado horizontalmente e alinhado ao topo — exatamente o efeito de **ajustar programaticamente rótulos de gráfico** que você programou.

## Conclusão

Agora você sabe como **ajustar programaticamente rótulos de gráfico** em um documento Word usando C#. O tutorial abordou:

* Carregar um documento com **manipulação de gráficos do Aspose.Words**  
* Acessar um **C# chart data label**  
* Alterar a **posição do rótulo do gráfico** e o alinhamento  
* Salvar o arquivo e lidar com casos limites comuns  

A partir daqui, você pode explorar cenários mais avançados, como personalizar fontes dos rótulos, adicionar formatação condicional ou atualizar vários gráficos em um processo em lote. Experimente as diferentes opções de `DataLabelPosition` para encontrar o estilo que melhor se adapta aos seus relatórios.

---

*Pronto para aprimorar seu pipeline de relatórios automatizados? Experimente adicionar formatos numéricos personalizados aos rótulos ou exportar o gráfico como imagem para uso em PDFs.*


## O que você deve aprender a seguir?


Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}