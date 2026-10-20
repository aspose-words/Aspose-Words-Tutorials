---
category: general
date: 2026-10-20
description: Criar gráfico de pizza em um documento Word usando Aspose.Words – guia
  passo a passo que mostra como definir a cor, destacar uma fatia e salvar o documento
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: pt
lastmod: 2026-10-20
og_description: Crie um gráfico de pizza em um documento Word com Aspose.Words. Aprenda
  como definir a cor, destacar fatias e salvar o documento Word em um único exemplo
  executável.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Crie um gráfico de pizza em um documento Word – guia completo de C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Como criar um gráfico de pizza em um documento Word com Aspose.Words
url: /pt/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um gráfico de pizza em um documento Word com Aspose.Words

Se você precisa **criar um gráfico de pizza** dentro de um arquivo Word, este guia mostra exatamente como fazer isso. Você verá como definir uma cor personalizada, “explodir” uma fatia para destaque e, finalmente, **salvar o documento Word** com o gráfico incorporado.

Gerar gráficos programaticamente elimina as etapas manuais de abrir o Word, inserir um gráfico e ajustar sua aparência. Ao final deste tutorial você terá um aplicativo console C# completo e executável que cria um gráfico de pizza, o personaliza e grava o resultado no disco.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior instalado  
* Uma licença válida do Aspose.Words for .NET (ou uma chave de avaliação gratuita)  
* Uma IDE como Visual Studio 2022 ou VS Code  

Nenhum pacote NuGet adicional é necessário além do `Aspose.Words`.

## Como criar um gráfico de pizza em um documento Word

A primeira etapa é instanciar um `Document` e um `DocumentBuilder`. O builder fornece acesso a recursos de alto nível do Word, incluindo inserção de gráficos.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

Neste ponto o documento já contém um gráfico de pizza básico. As próximas seções explicam **como explodir uma fatia**, **como definir a cor** e **como salvar o documento Word**.

## Como explodir uma fatia para destaque

Explodir uma fatia a separa do restante da pizza, atraindo o olhar do leitor. A API Aspose.Words permite especificar uma distância de explosão em pontos.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Por que explodir a fatia? Em relatórios que destacam uma categoria específica — como “Produto mais vendido” — a separação visual torna o ponto de dados instantaneamente reconhecível.

## Como definir cor em uma fatia do gráfico

Cores personalizadas melhoram a consistência da marca e a legibilidade. Você pode atribuir qualquer `System.Drawing.Color` a um ponto de dados específico.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Você não está limitado a cores predefinidas; pode criar um valor `Color.FromArgb` para tons precisos.

## Como salvar o documento Word com o gráfico

Depois que o gráfico estiver como você deseja, persistir o arquivo é simples. O método `Document.Save` grava o documento no formato que você especificar — aqui usamos o padrão `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Executar o programa cria `PieChart.docx`. Abrir o arquivo no Microsoft Word mostra um gráfico de pizza onde a primeira fatia está explodida e colorida de vermelho, exatamente como o código especifica.

### Resultado esperado

* Um arquivo Word chamado **PieChart.docx** em `C:\Temp`.  
* O documento contém um único gráfico de pizza, com tamanho de 400 × 300 pontos.  
* A fatia 0 está deslocada em 20 pontos e preenchida de vermelho, enquanto as demais fatias mantêm a cor padrão.  

Você pode verificar a explosão e a cor selecionando o gráfico no Word e inspecionando as propriedades da fatia.

## Dicas avançadas e armadilhas comuns

* **Dica avançada:** Se precisar alterar o título ou a legenda do gráfico, use as propriedades `pieChart.Title.Text` e `pieChart.Legend` antes de salvar.  
* **Cuidado com:** Esquecer de limpar os pontos de dados padrão pode gerar fatias extras indesejadas. Sempre chame `Series[0].DataPoints.Clear()` antes de adicionar seus próprios dados.  
* **Dica de desempenho:** Para documentos grandes, reutilize uma única instância de `DocumentBuilder` em vez de criar vários builders; isso reduz a sobrecarga de memória.

## Como criar um gráfico usando Aspose.Words (contexto adicional)

O método `InsertChart` suporta muitos tipos de gráficos além de pizzas, como colunas, linhas e áreas. Para mudar para outro tipo, substitua `ChartType.Pie` pelo valor enum desejado, por exemplo, `ChartType.Column`. O restante das etapas de personalização (explodir fatias, definir cores) segue o mesmo padrão, embora nem todos os tipos de gráfico exponham a propriedade “explosion”.

## Como explodir uma fatia em outros tipos de gráfico

Apenas gráficos do tipo pizza expõem o método `SetExplosion`. Se você tentar chamá‑lo em um gráfico de barras, a API lançará uma `ArgumentException`. Nesses casos, considere usar rótulos de dados ou chamadas de atenção para destacar uma barra específica.

## Como definir cor em uma série em vez de uma única fatia

Se quiser que todas as fatias de uma série compartilhem a mesma cor, percorra os pontos de dados:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Essa abordagem é útil quando você precisa de um esquema de cores uniforme em vários gráficos.

## Como salvar o documento Word em outros formatos

Aspose.Words pode exportar para PDF, HTML e muitos outros formatos. Altere a extensão do arquivo em `Save` e, opcionalmente, passe um objeto `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

O mecanismo de renderização do gráfico converte automaticamente o gráfico para o formato de destino, preservando cores e configurações de explosão.

## Conclusão

Agora você sabe como **criar um gráfico de pizza** em um documento Word, personalizar sua aparência **explodindo uma fatia** e **definindo cor**, e finalmente **salvar o documento Word** com o gráfico incorporado. Este exemplo de ponta a ponta fornece uma base sólida para automatizar a geração de relatórios, dashboards ou qualquer cenário onde dados visuais precisem ser inseridos programaticamente.

### Próximos passos

* Explore outros tipos de gráficos (`ChartType.Column`, `ChartType.Line`) para ampliar seu conjunto de ferramentas de relatório.  
* Combine vários gráficos em um único documento para construir dashboards abrangentes.  
* Experimente `ChartDataLabel` para mostrar percentuais ou valores diretamente nas fatias.  

Sinta‑se à vontade para adaptar o código às suas próprias fontes de dados — seja extraindo valores de um banco de dados, de uma API ou de um arquivo CSV, o mesmo fluxo de trabalho do Aspose.Words se aplica. Boas criações de gráficos!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}