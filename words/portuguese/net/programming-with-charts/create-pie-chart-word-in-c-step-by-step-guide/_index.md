---
category: general
date: 2026-08-07
description: Crie rapidamente um gráfico de pizza em C#. Aprenda como inserir um gráfico
  de pizza, adicionar rótulos de dados ao gráfico de pizza, exibir a porcentagem no
  gráfico e personalizar os rótulos de dados do gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: pt
lastmod: 2026-08-07
og_description: Crie um gráfico de pizza no Word em C# com Aspose.Words. Este tutorial
  mostra como inserir um gráfico de pizza, adicionar rótulos de dados ao pizza e exibir
  o percentual no gráfico ao personalizar os rótulos de dados.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Criar gráfico de pizza em C# – tutorial completo
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Criar gráfico de pizza em C# – guia passo a passo
url: /pt/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar gráfico de pizza no Word em C# – guia passo a passo

Se você precisa **criar gráficos de pizza no Word** em C#, este guia fornece uma solução completa, pronta‑para‑executar. Você verá como **inserir gráfico de pizza**, **adicionar rótulos de dados ao pizza**, e **exibir gráfico de porcentagem** enquanto **personaliza os rótulos de dados do gráfico** para um visual refinado.

Gerar gráficos programaticamente economiza tempo de edição manual, especialmente quando relatórios ou painéis precisam ser produzidos automaticamente. Nas seções abaixo, você aprenderá tudo o que é necessário para incorporar um gráfico de pizza totalmente rotulado em um arquivo Word usando Aspose.Words para .NET.

## Pré-requisitos e configuração

* .NET 6.0 SDK ou posterior instalado.  
* Uma licença válida do Aspose.Words para .NET (ou uma chave de avaliação temporária).  
* Visual Studio 2022 (ou qualquer IDE que suporte C#).  

Add the Aspose.Words NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

> **Dica profissional:** Se você planeja gerar muitos gráficos, habilite o modo **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) para melhor desempenho.

## Criar gráfico de pizza no Word com Aspose.Words

O primeiro passo importante é criar um documento Word em branco e um `DocumentBuilder`. Este objeto controla todas as inserções subsequentes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa*: `Document` representa o arquivo `.docx` completo, enquanto `DocumentBuilder` fornece uma API fluente para adicionar parágrafos, tabelas e gráficos. Começar com um documento limpo garante que nenhuma formatação oculta interfira no layout do gráfico.

## Inserir gráfico de pizza no documento

Agora colocamos um gráfico de pizza do tamanho desejado. O método `InsertChart` retorna um objeto `Chart` que podemos configurar ainda mais.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Por que isso importa*: A flag `ChartType.Pie` indica ao Aspose.Words que deve gerar um gráfico circular. A largura (`400`) e a altura (`300`) são expressas em pontos, proporcionando controle preciso sobre o espaço visual.

## Preencher o gráfico com dados

Um gráfico de pizza precisa de pelo menos uma série de valores numéricos. Aqui adicionamos três categorias: “Apples”, “Bananas” e “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Por que isso importa*: Cada chamada `AddCategory` cria uma fatia. O valor numérico determina o tamanho da fatia, enquanto o rótulo se torna o nome da categoria exibido quando os rótulos de dados são ativados.

## Adicionar rótulos de dados ao pizza e exibir gráfico de porcentagem

Para tornar o gráfico informativo, habilitamos os rótulos de dados, posicionamos eles fora das fatias e solicitamos ao Aspose.Words que exiba tanto o nome da categoria quanto a porcentagem.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Por que isso importa*: Definir `Position` como `OutsideEnd` melhora a legibilidade, especialmente quando as fatias são pequenas. Habilitar `ShowCategoryName` e `ShowPercentage` cumpre o requisito de **exibir gráfico de porcentagem** e satisfaz o objetivo de **adicionar rótulos de dados ao pizza**.

## Personalizar ainda mais os rótulos de dados do gráfico (opcional)

Você pode querer mudar a fonte, adicionar uma linha guia ou ocultar a legenda. O trecho a seguir demonstra personalizações comuns:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Por que isso importa*: Personalizar a aparência dos rótulos garante que o gráfico corresponda ao guia de estilo do seu documento. Remover a legenda reduz a desordem visual quando os rótulos de dados já transmitem a mesma informação.

## Salvar o documento com o gráfico personalizado

Finalmente, grave o documento no disco. Escolha um caminho ao qual você tenha permissão de gravação.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Ao abrir `ChartWithCustomLabels.docx` no Microsoft Word, você verá um gráfico de pizza onde cada fatia está rotulada com seu nome de categoria e porcentagem, posicionada fora da fatia, e estilizada com as configurações de fonte personalizadas.

### Saída esperada

| Fatia   | Valor | Porcentagem | Rótulo exibido no Word |
|---------|-------|-------------|------------------------|
| Apples  | 40    | 40 %        | Apples – 40 %          |
| Bananas | 35    | 35 %        | Bananas – 35 %         |
| Cherries| 25    | 25 %        | Cherries – 25 %        |

O gráfico deve ter aparência semelhante à ilustração abaixo:

![Documento Word exibindo um gráfico de pizza com rótulos de porcentagem fora de cada fatia](pie-chart-word.png "Exemplo de criação de gráfico de pizza no Word")

*O texto alternativo da imagem inclui a palavra‑chave principal para SEO.*

## Manipulando múltiplas séries e casos de borda

O exemplo básico usa uma única série, o que é típico para um gráfico de pizza. Se você precisar exibir múltiplas séries (por exemplo, comparando dois anos), você deve:

1. Chamar `chart.Series.Add()` para cada série adicional.  
2. Garantir que cada série use as mesmas categorias; caso contrário, o Aspose.Words lançará uma `ArgumentException`.  
3. Opcionalmente, definir `labels.ShowSeriesName = true` para diferenciar as fatias.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Quando múltiplas séries existem, o gráfico é renderizado automaticamente como um **pie agrupado** (também chamado de “pie of pies”). Revise a saída para verificar se os rótulos permanecem legíveis.

## Armadilhas comuns e como evitá‑las

| Problema | Causa | Solução |
|----------|-------|---------|
| Rótulos sobrepõem as fatias | Área do gráfico pequena ou muitas categorias | Aumente as dimensões do gráfico (`InsertChart(width, height)`) ou altere `Position` para `InsideEnd`. |
| As porcentagens não somam 100 % | Erros de arredondamento nos dados | Use `labels.ShowPercentage = true` (Aspose.Words normaliza automaticamente). |
| O gráfico aparece em branco no Word | Licença ausente ou tempo de avaliação expirado | Certifique‑se de que uma licença válida do Aspose.Words está carregada antes de criar o documento. |
| Cores da fonte diferem do tema do Word | Fonte personalizada definida no código | Remova as configurações de fonte personalizada ou combine com as cores do tema do Word (`System.Drawing.Color.Black`). |

## Código‑fonte completo (executável)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Executar o programa produz `ChartWithCustomLabels.docx`, que contém um exemplo de **criar gráfico de pizza no Word** que atende a todos os requisitos listados no tutorial.

## Conclusão

Agora você sabe como **criar gráficos de pizza no Word** em C# usando Aspose.Words. O guia abordou a inserção de um gráfico de pizza, **adicionar rótulos de dados ao pizza**, **exibir gráfico de porcentagem**, e **personalizar os rótulos de dados do gráfico** para obter um arquivo Word profissional e orientado a dados.

A partir daqui você pode explorar tópicos relacionados, como **inserir gráfico de pizza** em parágrafos existentes, gerar gráficos de **barra** ou **linha**, ou automatizar a criação em lote de relatórios com diferentes conjuntos de dados. Experimente diferentes posições de rótulos, estilos de fonte e configurações de múltiplas séries para adaptar a saída às suas necessidades específicas de relatório.

Boa criação de gráficos!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Personalizar rótulo de dados do gráfico](/words/english/net/programming-with-charts/chart-data-label/)
- [Definir opções padrão para rótulos de dados em um gráfico](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Inserir gráfico de colunas em um documento Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}