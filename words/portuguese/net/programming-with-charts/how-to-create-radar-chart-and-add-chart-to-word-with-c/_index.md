---
category: general
date: 2026-09-05
description: Criar gráfico de radar no Word usando C#. Aprenda a gerar um documento
  Word em branco, adicionar um gráfico de radar, definir o tamanho do gráfico e habilitar
  as marcas de escala rapidamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: pt
lastmod: 2026-09-05
og_description: Criar gráfico de radar no Word usando C#. Este guia mostra como gerar
  um documento Word em branco, adicionar um gráfico de radar, definir o tamanho do
  gráfico e habilitar marcas de escala — tudo em minutos.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Criar gráfico de radar no Word – guia passo a passo em C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Como criar um gráfico de radar e adicionar o gráfico ao Word com C#
url: /pt/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um gráfico de radar e adicionar gráfico ao Word com C#

Se você precisa **criar um gráfico de radar** dentro de um arquivo Word, este guia orienta todo o processo. Você aprenderá a **gerar um documento Word em branco**, inserir um gráfico de radar, **definir o tamanho do gráfico no Word**, e habilitar as graduações do eixo — tudo com algumas linhas de código C#.

Adicionar dados visuais a relatórios é uma necessidade comum, e usar Aspose.Words torna isso simples. Nas etapas abaixo também abordamos como **adicionar gráfico ao Word** programaticamente, para que você possa automatizar dashboards, resumos financeiros ou qualquer conteúdo orientado a dados.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou superior instalado  
* Uma licença do Aspose.Words for .NET (ou um teste gratuito) – a biblioteca fornece as APIs `Document`, `DocumentBuilder` e de gráficos usadas neste tutorial  
* Visual Studio 2022 (ou qualquer IDE C#)  

> **Dica:** Se estiver testando, coloque o DLL do Aspose.Words na pasta `bin` do seu projeto e faça a referência via NuGet (`Install-Package Aspose.Words`).

## Como criar um gráfico de radar em um documento Word

A primeira etapa é **gerar um documento Word em branco** que hospedará o gráfico. Isso fornece uma tela limpa e permite controlar os metadados do documento antes que qualquer conteúdo seja adicionado.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Por que isso importa:* Um objeto `Document` vazio garante que nenhum estilo ou seção ocultos interfiram no layout do gráfico. Também permite definir propriedades do documento (autor, título) posteriormente, se necessário.

## Como adicionar gráfico ao Word usando Aspose.Words

Em seguida, crie um `DocumentBuilder`. O builder é a ferramenta principal que permite inserir texto, imagens e gráficos no documento.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Agora você pode **adicionar um gráfico de radar** diretamente onde o cursor está posicionado. O método `InsertChart` aceita um enum `ChartType`, largura e altura em pontos.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Por que 400 × 300?* Essas dimensões fornecem um gráfico claro e legível em uma página A4 padrão. Você pode ajustar o tamanho mais tarde com a etapa **definir o tamanho do gráfico no Word** se o layout exigir uma proporção diferente.

## Definindo o tamanho do gráfico no Word

Se precisar ajustar o tamanho após a inserção, pode modificar as propriedades `Width` e `Height` do gráfico. Isso é útil quando o texto ao redor ou as margens da página exigem um equilíbrio visual diferente.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Observação:** A sobrecarga de `InsertChart` já define o tamanho, portanto o código acima é opcional e mostrado para completude.

## Habilitar marcas de escala no eixo radial

Um gráfico de radar é mais útil quando o eixo radial mostra graduações claras. As configurações a seguir ativam as marcas de escala e definem o intervalo para 30 graus, o que se alinha com exibições de radar no estilo de bússola.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Por que isso importa:* As graduações ajudam os leitores a avaliar os valores em cada ângulo, melhorando a legibilidade para as partes interessadas que não estão familiarizadas com os dados.

## Salvar o documento contendo o gráfico

Por fim, grave o documento no disco. Você pode escolher qualquer pasta; apenas certifique‑se de que o caminho exista.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Ao abrir `RadialChart.docx` no Microsoft Word, você verá um gráfico de radar totalmente renderizado, centralizado na página, com o tamanho especificado e marcas de escala a cada 30 graus.

### Saída esperada

* Um arquivo `.docx` chamado **RadialChart.docx**  
* A primeira página contém um gráfico de radar com tamanho 400 × 300 pontos  
* O eixo X (eixo radial) exibe marcas de escala em 0°, 30°, 60°, …, 330°  

Agora você pode substituir a série de dados placeholder pelos seus próprios valores acessando `radarChart.Series` – mas isso está fora do escopo deste tutorial básico de **adicionar gráfico de radar**.

## Variações comuns e casos de borda

| Cenário | Ajuste |
|----------|------------|
| **Tipo de gráfico diferente** | Substitua `ChartType.Radar` por `ChartType.Column`, `ChartType.Pie`, etc. |
| **Múltiplos gráficos** | Chame `InsertChart` repetidamente; cada chamada posiciona o novo gráfico após o anterior. |
| **Conjuntos de dados grandes** | Use `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` para popular muitos pontos. |
| **Salvar como PDF** | Chame `document.Save("RadialChart.pdf", SaveFormat.Pdf);` após adicionar o gráfico. |
| **Executar no .NET Core** | Certifique‑se de referenciar o pacote `Aspose.Words.NETCore`; o uso da API é idêntico. |

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar‑colar em uma aplicação console. Ele inclui todas as etapas, ajustes opcionais de tamanho e comentários para clareza.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Execute o programa, abra o arquivo resultante e você verá o gráfico de radar exatamente como descrito.

## Conclusão

Agora você sabe como **criar um gráfico de radar** e **adicionar gráfico ao Word** usando C#. O tutorial abordou a geração de um **documento Word em branco**, a inserção de um gráfico de radar, **definir o tamanho do gráfico no Word**, e a habilitação de graduações do eixo. Com essa base, você pode expandir a solução para múltiplos gráficos, séries de dados personalizadas ou exportação para PDF.

### Próximos passos

* Explore outros tipos de gráfico com `ChartType` (por exemplo, `Bar`, `Line`) – veja a palavra‑chave **add radar chart** para exemplos relacionados.

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui código completo e exemplos passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}