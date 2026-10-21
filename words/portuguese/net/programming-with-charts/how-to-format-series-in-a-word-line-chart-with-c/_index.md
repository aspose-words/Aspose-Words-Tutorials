---
category: general
date: 2026-09-21
description: Como formatar séries em um gráfico de linhas do Word usando C#. Aprenda
  a criar um documento do Word, inserir um gráfico de linhas e aplicar um formato
  numérico personalizado.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: pt
lastmod: 2026-09-21
og_description: Como formatar séries em um gráfico de linhas do Word usando C#. Este
  tutorial mostra como criar um documento do Word, inserir um gráfico de linhas e
  aplicar um formato numérico personalizado.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Como formatar séries em um gráfico de linhas do Word com C# – guia passo
  a passo
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Como formatar séries em um gráfico de linhas do Word com C#
url: /pt/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como formatar séries em um gráfico de linhas do Word com C#

Se você precisa **formatar séries** em um gráfico de linhas do Word, este guia fornece uma solução completa e pronta‑para‑executar. Você verá como **criar um documento Word**, **inserir um gráfico de linhas** e **aplicar um formato numérico personalizado** aos valores do eixo Y — tudo com Aspose.Words para .NET.

A automação do Word torna‑se simples quando você entende o modelo de objetos do gráfico. Ao final deste tutorial você terá um arquivo Word que contém um gráfico de linhas cujas séries de dados são exibidas como porcentagens com duas casas decimais.

## O que você vai conseguir

* Gerar programaticamente um arquivo `.docx` em branco.  
* Adicionar um gráfico de linhas com tamanho 400 × 300 pontos.  
* Acessar a primeira série de dados do gráfico.  
* Aplicar o código de formato `#,##0.00%` para que os valores do eixo Y apareçam como porcentagens.  

Nenhuma ferramenta externa é necessária além do pacote NuGet Aspose.Words.

## Pré‑requisitos

* .NET 6.0 SDK ou superior.  
* Visual Studio 2022 (ou qualquer IDE C#).  
* Aspose.Words para .NET 23.10 ou mais recente – instale via `dotnet add package Aspose.Words`.  

O código funciona no Windows, Linux e macOS porque o Aspose.Words é independente de plataforma.

## Criar um documento Word com Aspose.Words

O primeiro passo é instanciar um objeto `Document`. Esse objeto representa todo o arquivo Word na memória.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Por que isso importa*: `Document` é o ponto de entrada para todas as operações de processamento de Word. Sem ele você não pode adicionar parágrafos, tabelas ou gráficos.

## Inserir um gráfico de linhas no documento

Um `DocumentBuilder` grava conteúdo no `Document`. Chamar `InsertChart` cria uma forma de gráfico na página atual.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Por que isso importa*: `InsertChart` devolve um objeto `Chart` que lhe dá controle total sobre séries, eixos e formatação. Os parâmetros de tamanho são expressos em pontos (1 ponto = 1/72 polegada).

## Acessar a primeira série de dados

Todo gráfico contém uma ou mais `ChartSeries`. A primeira série está no índice 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Por que isso importa*: O objeto `ChartSeries` contém os valores Y, valores X e opções de formatação para uma única linha em um gráfico de linhas. Modificar esse objeto altera a representação visual dos dados.

## Aplicar um formato numérico personalizado à série

A propriedade `FormatCode` controla como os valores numéricos são exibidos. Definir `#,##0.00%` indica ao Word que trate os valores como porcentagens com duas casas decimais.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Por que isso importa*: Sem um formato personalizado, o Word mostra números decimais brutos (por exemplo, `0.15`). O código de formato converte‑os para `15.00%`, que é o que a maioria dos relatórios de negócios exige.

## Salvar o documento e verificar o resultado

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ao abrir `FormattedSeriesLineChart.docx` no Microsoft Word, você verá um gráfico de linhas onde os rótulos do eixo Y exibem `15.00%`, `30.00%`, `45.00%` e `60.00%`. O tamanho do gráfico corresponde às dimensões fornecidas em `InsertChart`.

### Captura de tela esperada

> *Imagem: Uma página de documento Word mostrando um gráfico de linhas com valores do eixo Y formatados em porcentagem.*  
> *(Texto alternativo: Captura de tela de um documento Word exibindo um gráfico de linhas com valores do eixo Y formatados em porcentagem)*

## Variações comuns e casos de borda

| Situação | Ajuste |
|-----------|------------|
| **Múltiplas séries** | Percorra `chart.Series` e defina `FormatCode` para cada série. |
| **Tipo de gráfico diferente** | Substitua `ChartType.Line` por `ChartType.Column`, `ChartType.Pie` etc. |
| **Separadores específicos de localidade** | Use strings de formato sensíveis a `CultureInfo`, por exemplo, `"# ##0,00 %"` para localidades francesas. |
| **Fonte de dados dinâmica** | Preencha `series.YValues` a partir de um banco de dados ou arquivo CSV antes de aplicar o formato. |

**Dica profissional:** Sempre aplique o formato **depois** de ter adicionado os valores Y. Alterar o formato primeiro e depois inserir os valores também funciona, mas aplicá‑lo posteriormente garante que o formato seja usado no conjunto de dados final.

## Recapitulação

Agora você sabe **como formatar séries** em um gráfico de linhas do Word usando C#. O tutorial abordou:

* Criação de um documento Word (`create word document`).  
* Inserção de um gráfico de linhas (`insert line chart`, `add chart to word`).  
* Acesso à primeira série do gráfico.  
* Aplicação de um formato numérico personalizado (`apply custom number format`) para exibir porcentagens.

## Próximos passos

* Experimente diferentes valores de `ChartType` para ver como outras visualizações se comportam.  
* Adicione títulos, rótulos de eixo e legendas usando `chart.Title`, `chart.AxisX.Title` e `chart.AxisY.Title`.  
* Exporte o gráfico como imagem (`chart.Save` com `SaveFormat.Png`) para uso em relatórios web.

Sinta‑se à vontade para adaptar esse padrão para gerar dashboards, relatórios financeiros ou qualquer documento que precise de gráficos programáticos. Boa codificação!


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}