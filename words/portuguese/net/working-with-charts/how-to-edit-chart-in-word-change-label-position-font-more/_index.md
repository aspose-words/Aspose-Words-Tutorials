---
category: general
date: 2026-07-29
description: Como editar gráfico em um documento do Word — aprenda a mudar a posição
  do rótulo do gráfico, ajustar os rótulos de gráfico de barras, modificar os rótulos
  de dados do gráfico e mudar a fonte do rótulo do gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: pt
lastmod: 2026-07-29
og_description: Como editar gráficos no Word rapidamente. Domine a alteração da posição
  dos rótulos do gráfico, ajuste dos rótulos de gráficos de barras, modificação dos
  rótulos de dados do gráfico e mudança da fonte dos rótulos do gráfico.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Como editar gráfico no Word – Alterar rótulos e fonte
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Como editar gráfico no Word: alterar posição do rótulo, fonte e mais'
url: /pt/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Editar Gráficos no Word: Alterar Posição do Rótulo, Fonte e Mais

Editar um gráfico em um documento Word é uma necessidade comum quando você deseja que seus relatórios tenham um visual polido. Já teve dificuldade em **alterar a posição do rótulo do gráfico** ou tornar os rótulos legíveis sem vasculhar menus intermináveis? Você não está sozinho — a maioria dos desenvolvedores encontra esse obstáculo ao automatizar a geração de relatórios. Neste guia, percorreremos um exemplo completo e executável que mostra exatamente como **ajustar rótulos de gráficos de barras**, **modificar rótulos de dados do gráfico** e **alterar a fonte dos rótulos do gráfico** usando C# e a biblioteca Aspose.Words.

## O que você aprenderá

- Carregar um arquivo .docx que já contém um gráfico de barras.  
- Recuperar a primeira forma de gráfico e acessar sua coleção de rótulos de dados.  
- **Alterar a posição do rótulo do gráfico** para que as barras pareçam mais limpas.  
- **Ajustar o tamanho da fonte dos rótulos do gráfico de barras** para melhor legibilidade.  
- Salvar o documento modificado de volta ao disco.  

Sem ferramentas externas, sem etapas manuais na UI — apenas código puro que você pode inserir em qualquer projeto .NET. Ao final, você terá uma solução autônoma que pode reutilizar em dezenas de documentos.

> **Pré‑requisitos**  
> - .NET 6.0 ou superior (o código também funciona no .NET Framework 4.7+).  
> - Aspose.Words para .NET (disponível via NuGet).  
> - Um arquivo Word (`BarChart.docx`) que já contém um gráfico de barras.  

Se estiver faltando algum desses itens, obtenha agora o pacote mais recente do Aspose.Words:

```bash
dotnet add package Aspose.Words
```

---

## Como Editar Gráfico: Recuperar o Gráfico do Documento Word

O primeiro passo em **como editar gráfico** é carregar o documento e localizar a forma do gráfico. Aspose.Words trata gráficos como nós `Shape`, então podemos usar `GetChild` com `NodeType.Shape` para obter o primeiro gráfico encontrado.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Por que isso importa:**  
> Ao acessar diretamente o objeto `Chart`, você evita o overhead de abrir o arquivo no Word e ajustar manualmente cada rótulo. Esse é o alicerce de qualquer automação de **modificar rótulos de dados do gráfico**.

## Ajustar Rótulos de Gráfico de Barras: Alterar Posição do Rótulo do Gráfico

Agora que temos a instância `Chart`, vamos iterar sobre sua `DataLabelCollection`. O objetivo é **alterar a posição do rótulo do gráfico** para que cada rótulo fique bem dentro da base da barra, em vez de flutuar de forma estranha acima dela.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Dica de especialista:**  
> `InsideBase` funciona bem para gráficos de barras verticais. Se estiver lidando com um gráfico de barras horizontal, experimente `InsideEnd`. Experimentar posições é barato — basta reexecutar o código e abrir o documento salvo.

## Alterar Fonte do Rótulo do Gráfico: Ajustar Tamanho da Fonte para Legibilidade

Uma fonte pequena é o assassino silencioso da clareza dos relatórios. Para **alterar a fonte do rótulo do gráfico**, basta definir a propriedade `Font.Size` em cada `ChartDataLabel`. Vamos aumentá‑la para 9 pt, que é um ponto ideal para a maioria dos relatórios impressos.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Por que fazemos isso:**  
> Ajustar o tamanho da fonte faz parte das boas práticas de **modificar rótulos de dados do gráfico**. Fontes maiores melhoram a acessibilidade e reduzem a necessidade de pós‑processamento manual.

## Salvar o Documento Atualizado

Depois de ajustar posições e fontes, o passo final em **como editar gráfico** é persistir as alterações. Aspose.Words torna isso uma única linha de código.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Abra `BarChartCustomLabels.docx` no Word e você verá os rótulos encaixados dentro das barras, renderizados com uma fonte clara de 9 pt. Chega de forçar a vista em números minúsculos.

---

## Exemplo Completo Funcional (Todas as Etapas em Um Arquivo)

Abaixo está um programa console completo, pronto para execução, que demonstra todo o fluxo — desde o carregamento do documento até a gravação da versão atualizada. Copie‑e‑cole em um novo projeto console .NET e pressione **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Saída esperada** ao executar o programa:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Abra o arquivo resultante e você verá os **rótulos de gráfico de barras ajustados** posicionados dentro das barras com um tamanho de fonte confortável.

---

## Perguntas Frequentes & Casos de Borda

### E se o documento contiver vários gráficos?

O código acima captura o *primeiro* gráfico (`GetChild(NodeType.Shape, 0, true)`). Para editar todos os gráficos, substitua a recuperação única por um loop:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Como **alterar a fonte do rótulo do gráfico** apenas para uma série específica?

Cada `ChartSeries` possui sua própria `DataLabelCollection`. Direcione uma série pelo índice:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Isso funciona com gráficos de pizza ou de linha?

Sim — `ChartDataLabelPosition` aceita valores como `InsideEnd`, `OutsideEnd` e `BestFit`. Para um gráfico de pizza, você pode preferir `OutsideEnd` para manter os rótulos legíveis.

### E quanto à localização (por exemplo, diferentes separadores decimais)?

Aspose.Words respeita as configurações de localidade do documento. Se precisar impor um formato específico, ajuste `label.NumberFormat` antes de salvar.

---

## Recapitulação & Próximos Passos

Cobremos **como editar gráfico** em um documento Word do início ao fim: carregar o arquivo, recuperar o gráfico, **alterar a posição do rótulo do gráfico**, **ajustar rótulos de gráfico de barras**, **modificar rótulos de dados do gráfico** e, finalmente, **alterar a fonte do rótulo do gráfico** antes de salvar. O exemplo completo está pronto para produção e pode ser inserido em qualquer pipeline de automação.

Pronto para evoluir? Considere estas ideias de continuação:

- **Adicionar cores aos rótulos de dados** (`dataLabel.Font.Color = Color.Blue;`).  
- **Mostrar valores como porcentagens** (`dataLabel.NumberFormat = "0%";`).  
- **Criar gráficos programaticamente** em vez de carregar os existentes.  

Todas essas extensões utilizam a mesma superfície de API que usamos hoje, então você se sentirá em casa.

Se encontrou algum obstáculo, deixe um comentário abaixo ou consulte a documentação do Aspose.Words para opções avançadas de personalização de gráficos. Boa codificação e aproveite esses gráficos belamente rotulados!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Personalizar Rótulo de Dados do Gráfico](/words/english/net/programming-with-charts/chart-data-label/)
- [Formatar Número de Rótulo de Dados em um Gráfico](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Rótulo de Dados do Gráfico](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}