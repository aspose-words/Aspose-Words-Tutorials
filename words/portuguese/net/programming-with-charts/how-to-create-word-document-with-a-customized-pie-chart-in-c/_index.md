---
category: general
date: 2026-10-07
description: Aprenda como criar um documento Word e inserir um gráfico de pizza usando
  Aspose.Words em C#. O guia também mostra como gerar um arquivo Word com rótulos
  de gráfico personalizados.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: pt
lastmod: 2026-10-07
og_description: Crie um documento Word e insira um gráfico de pizza em C#. Siga este
  guia passo a passo para gerar um arquivo Word com rótulos de gráfico totalmente
  personalizados.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Crie um documento Word com um gráfico de pizza personalizado em C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Como criar um documento Word com um gráfico de pizza personalizado em C#
url: /pt/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento Word com um gráfico de pizza personalizado em C#

Se você precisa **criar documento Word** programaticamente, este tutorial mostra como **inserir gráfico de pizza** e personalizar seus rótulos de dados usando Aspose.Words for .NET. Você também aprenderá como **gerar arquivo Word** que contém um gráfico totalmente estilizado, cobrindo tudo, desde a configuração do projeto até a gravação do documento final.

O guia percorre cada passo necessário para adicionar um gráfico, ajustar as posições dos rótulos, habilitar linhas de ligação e, finalmente, salvar o resultado como um arquivo `.docx`. Nenhuma ferramenta externa é necessária além da biblioteca Aspose.Words, e o código-fonte completo é fornecido para que você possa copiar, colar e executá‑lo imediatamente.

## Pré-requisitos

* .NET 6.0 SDK ou posterior instalado  
* Uma licença válida do Aspose.Words for .NET (ou uma chave de avaliação gratuita)  
* Uma IDE como Visual Studio 2022 ou Visual Studio Code  

Você também precisará adicionar os seguintes pacotes NuGet ao seu projeto:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Esses pacotes expõem as classes `Document`, `DocumentBuilder` e relacionadas a gráficos usadas nos exemplos abaixo.

## Criar documento Word e adicionar um gráfico

O primeiro passo é **criar documento Word** e obter um `DocumentBuilder` que permite inserir conteúdo. O builder funciona como um cursor posicionado dentro do documento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

O objeto `Document` representa todo o arquivo Word, enquanto o `DocumentBuilder` fornece métodos como `InsertChart` que inserem objetos diretamente no fluxo do documento.

## Inserir gráfico de pizza no documento

Agora que o builder está pronto, você pode **inserir gráfico de pizza** com um tamanho específico. O gráfico é adicionado na posição atual do builder.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` retorna um objeto `Chart` que você pode manipular ainda mais. Os dados de exemplo criam quatro fatias representando as vendas trimestrais.

## Personalizar rótulos de dados do gráfico de pizza

Para tornar o gráfico mais legível, muitas vezes é necessário **personalizar os rótulos do gráfico de pizza** — posicioná‑los fora das fatias e exibir linhas de ligação. É aqui que a `ChartDataLabelCollection` entra em ação.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Definir `Position` como `OutsideEnd` move cada rótulo além da borda da fatia, enquanto `ShowLeaderLines` desenha uma linha que conecta o rótulo à sua fatia. As flags opcionais `ShowValue` e `ShowPercentage` fornecem aos leitores tanto os números brutos quanto as porcentagens relativas.

**Dica profissional:** Se precisar formatar a fonte do rótulo, use `dataLabels.Font` para definir tamanho, cor e estilo. Isso garante que o gráfico corresponda à identidade visual da sua empresa.

## Salvar e gerar arquivo Word

Depois que o gráfico estiver totalmente configurado, você pode **gerar arquivo Word** salvando a instância `Document` no disco. Escolha o formato `.docx` para máxima compatibilidade com as versões modernas do Word.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ao abrir `CustomPieChart.docx`, você verá um gráfico de pizza com quatro fatias, cada uma rotulada fora da fatia, conectada por linhas de ligação e exibindo tanto o valor quanto a porcentagem.

![Captura de tela de um documento Word que contém um gráfico de pizza personalizado criado com C#](image-placeholder.png)

*A imagem mostra o resultado final do tutorial de **criar documento Word**.*

## Variações comuns e casos extremos

| Cenário | Como adaptar o código |
|----------|----------------------|
| **Múltiplas séries** | Adicione objetos `ChartSeries` adicionais a `pieChart.Series`. Cada série pode ter sua própria coleção `DataLabels` para estilização independente. |
| **Tamanho de gráfico diferente** | Altere os parâmetros de largura e altura em `InsertChart(width, height)`. Os valores estão em pontos (1 pt ≈ 1/72 pol). |
| **Título do gráfico** | Use `pieChart.Title.Text = "Quarterly Sales"` para adicionar um título descritivo. |
| **Exportar para PDF** | Chame `document.Save("Report.pdf", SaveFormat.Pdf);` após o gráfico ser construído. |
| **Manipulação de licença** | Coloque seu arquivo de licença (`Aspose.Words.lic`) na pasta da aplicação e carregue‑lo com `new License().SetLicense("Aspose.Words.lic");` antes de criar o documento. |

Essas variações permitem responder à pergunta **como adicionar gráfico de pizza** em muitos cenários reais, desde relatórios simples até dashboards complexos.

## Conclusão

Agora você sabe como **criar documento Word**, **inserir gráfico de pizza** e **personalizar os rótulos do gráfico de pizza** usando Aspose.Words for .NET. O exemplo completo demonstra um fluxo de trabalho limpo: inicializar o documento, adicionar um gráfico, ajustar o posicionamento dos rótulos de dados, habilitar linhas de ligação e, finalmente, **gerar arquivo Word** que pode ser compartilhado com qualquer pessoa.

Tente expandir este tutorial experimentando diferentes tipos de gráficos (`ChartType.Column`, `ChartType.Line`) ou aplicando paletas de cores personalizadas para combinar com sua marca. Se encontrar problemas, consulte a documentação do Aspose.Words ou explore tópicos relacionados, como “como adicionar gráfico de pizza” com múltiplas séries e fontes de dados dinâmicas.

Feliz codificação, e sinta‑se à vontade para compartilhar seus resultados ou fazer perguntas de follow‑up nos comentários!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir Gráfico de Colunas em um Documento Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Inserir Gráfico de Área em um Documento Word](/words/english/net/programming-with-charts/insert-area-chart/)
- [Inserir Gráfico de Dispersão em Documento Word](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}