---
category: general
date: 2026-09-08
description: Crie um documento Word em branco e adicione um gráfico ao Word com Aspose.Words.
  Aprenda como inserir um gráfico de radar, habilitar graduações e salvar o arquivo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: pt
lastmod: 2026-09-08
og_description: Crie um documento Word em branco e adicione um gráfico ao Word usando
  Aspose.Words. Este tutorial mostra como inserir um gráfico de radar, configurar
  os eixos e salvar o documento.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Crie um documento Word em branco e adicione um gráfico de radar – guia passo
  a passo
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Como criar um documento Word em branco e adicionar um gráfico ao Word
url: /pt/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento Word em branco e adicionar um gráfico ao Word

Se você precisar **criar um documento Word em branco** para um relatório, modelo ou mesclagem de correspondência automatizada, este guia o conduzirá por todo o processo com C# e Aspose.Words. Você também aprenderá como **adicionar um gráfico ao Word**, especificamente como **inserir um gráfico de radar**, ativar as graduações e salvar o resultado como um arquivo .docx.

Este tutorial cobre tudo, desde a configuração do projeto até a etapa final de verificação. Ao final, você terá um trecho de código reutilizável que pode ser inserido em qualquer aplicação .NET. Não é necessário ter experiência prévia com Aspose.Words, mas você deve ter conhecimentos básicos de C# e um SDK .NET recente instalado.

## Pré-requisitos

- .NET 6.0 SDK ou posterior  
- Aspose.Words for .NET (pacote NuGet `Aspose.Words`)  
- Uma IDE como Visual Studio 2022 ou VS Code  
- Permissão de escrita na pasta onde o documento será salvo  

Você pode instalar a biblioteca com o seguinte comando:

```bash
dotnet add package Aspose.Words
```

## Etapa 1: Criar um documento Word em branco

O primeiro passo é **criar um documento Word em branco** na memória. A classe `Document` representa todo o arquivo, enquanto `DocumentBuilder` fornece uma API fluente para adicionar conteúdo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` começa vazio, então você tem uma tela limpa onde colocar o gráfico. Manter o documento em branco nesta fase facilita a reutilização do mesmo código para diferentes modelos.

## Etapa 2: Adicionar gráfico ao Word

Em seguida, **adicionamos um gráfico ao Word** chamando `InsertChart`. O método requer o tipo de gráfico e as dimensões desejadas em pontos (1 ponto = 1/72 polegada).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` indica ao Aspose.Words que gere um gráfico radial, que é ideal para exibir dados multivariados em um layout circular. Os valores de tamanho (400 × 300) funcionam bem para a maioria das páginas em retrato, mas você pode ajustá-los para se adequar ao seu layout.

## Etapa 3: Inserir gráfico de radar e configurar graduações

Agora **inserimos um gráfico de radar** e habilitamos as graduações (marcadores) tanto no eixo de categoria (X) quanto no eixo de valor (Y). As graduações melhoram a legibilidade ao mostrar posições exatas para cada ponto de dados.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Definir `HasGraduations` como `true` desenha marcadores nos eixos. O opcional `GraduationStep` controla o espaçamento entre os marcadores no eixo radial; um passo de 10 significa um marcador a cada 10 graus.

### Dica profissional
Se precisar exibir rótulos de dados, chame `radarChart.Series[0].HasDataLabel = true;`. Isso adiciona o valor numérico ao lado de cada ponto, o que é útil para apresentações.

## Etapa 4: Preencher o gráfico com dados de exemplo (opcional)

Um gráfico de radar sem dados é invisível. Abaixo está uma maneira rápida de adicionar uma série de valores de exemplo. Você pode substituir este bloco pela sua própria fonte de dados.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Cada chamada a `Add` insere um ponto na série. A ordem dos pontos corresponde às posições angulares ao redor do círculo.

## Etapa 5: Salvar o documento contendo o gráfico

Finalmente, armazene o documento no disco. O método `Save` grava automaticamente o arquivo .docx, preservando o gráfico e toda a formatação.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Executar o programa cria um **documento Word em branco** que agora contém um gráfico de radar totalmente funcional. Abra o arquivo no Microsoft Word para ver o resultado.

![Gráfico de radar em documento Word](radar_chart.png){alt="Gráfico de radar inserido em um documento Word em branco"}

## Variações comuns e casos extremos

| Situação | O que mudar |
|-----------|----------------|
| **Tamanho de gráfico diferente** | Ajuste os parâmetros de largura/altura de `InsertChart`. |
| **Outros tipos de gráfico** | Substitua `ChartType.Radar` por `ChartType.Column`, `ChartType.Pie`, etc., e mantenha a mesma lógica de graduação. |
| **Salvar em um stream** | Use `document.Save(Stream, SaveFormat.Docx)` |

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir gráfico de área em documento Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Criar gráfico de dispersão Word usando Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Inserir gráfico de colunas no Word usando Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}