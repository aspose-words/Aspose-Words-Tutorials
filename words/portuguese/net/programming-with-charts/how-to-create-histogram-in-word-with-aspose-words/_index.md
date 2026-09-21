---
category: general
date: 2026-09-21
description: Como criar um histograma no Word com Aspose.Words. Aprenda a definir
  intervalos do histograma e a configurá‑los para uma visualização precisa dos dados.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create histogram in word
- how to set histogram bins
- configure histogram bins
language: pt
lastmod: 2026-09-21
og_description: Como criar um histograma no Word com Aspose.Words. Este tutorial mostra
  como definir intervalos do histograma e configurá-los para gráficos precisos.
og_image_alt: Screenshot of a Word document showing a histogram chart created with
  Aspose.Words
og_title: Crie um histograma no Word com Aspose.Words – guia completo
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  headline: How to create histogram in Word with Aspose.Words
  type: TechArticle
- description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  name: How to create histogram in Word with Aspose.Words
  steps:
  - name: Prepare the development environment.
    text: Prepare the development environment.
  - name: Build a blank Word document and obtain a `DocumentBuilder`.
    text: Build a blank Word document and obtain a `DocumentBuilder`.
  - name: Insert a histogram chart and adjust its properties.
    text: Insert a histogram chart and adjust its properties.
  - name: Save the document and verify the result.
    text: Save the document and verify the result.
  type: HowTo
tags:
- histogram
- Aspose.Words
- C#
- Word automation
title: Como criar histograma no Word com Aspose.Words
url: /pt/net/programming-with-charts/how-to-create-histogram-in-word-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um histograma no Word com Aspose.Words

Se você precisa criar um histograma no Word, o Aspose.Words torna o processo simples. Este guia orienta você em cada passo, desde a configuração do projeto até a configuração dos intervalos do histograma para uma apresentação clara dos dados. Você também verá como definir os intervalos do histograma e configurá‑los para atender aos requisitos de relatório.

## Como criar um histograma no Word – fluxo de trabalho geral

O fluxo de trabalho geral consiste em quatro fases lógicas:

1. Prepare o ambiente de desenvolvimento.  
2. Crie um documento Word em branco e obtenha um `DocumentBuilder`.  
3. Insira um gráfico de histograma e ajuste suas propriedades.  
4. Salve o documento e verifique o resultado.

Cada fase é detalhada abaixo, e o código‑fonte completo é fornecido ao final do artigo.

## Configurar o ambiente de desenvolvimento

Antes de escrever qualquer código, certifique‑se de que você possui os seguintes pré‑requisitos:

| Pré‑requisito | Motivo |
|--------------|--------|
| .NET 6.0 or later | Fornece o runtime para projetos C#. |
| Visual Studio 2022 (or any IDE that supports .NET) | Permite compilar e depurar o exemplo. |
| Aspose.Words for .NET NuGet package | Fornece as classes `Document`, `DocumentBuilder` e de gráficos. |

Você pode adicionar o pacote Aspose.Words com a NuGet CLI:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Use uma versão fixa (por exemplo, `23.9.0`) em produção para evitar alterações inesperadas que quebrem a funcionalidade.

## Inserir um gráfico de histograma

Com o ambiente pronto, crie um novo projeto de console e abra o arquivo `Program.cs`. As duas primeiras linhas de código instanciam um documento em branco e um `DocumentBuilder` que permite manipular o documento:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank document and a DocumentBuilder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Em seguida, chame `InsertChart` para adicionar um histograma. O método requer o tipo de gráfico, a largura e a altura em pontos:

```csharp
// Insert a histogram chart with a specific size (400x300 points)
Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);
```

Neste ponto, o documento contém um espaço reservado para o histograma vazio. Quando você abrir o arquivo *.docx* gerado, verá uma área de gráfico cinza pronta para receber dados.

![Histogram placeholder in Word document](/images/histogram-placeholder.png){: .img-fluid alt="Captura de tela de um documento Word mostrando um espaço reservado para um gráfico de histograma criado com Aspose.Words"}

## Como definir intervalos do histograma

Um histograma visualiza a distribuição de dados numéricos agrupando valores em *bins* (intervalos). A propriedade `HistogramBins` controla quantos intervalos o gráfico exibe. Definir essa propriedade antes de adicionar dados garante que o gráfico reserve o número correto de barras.

```csharp
// Set the number of bins (bars) in the histogram
histogram.HistogramBins = 10;
```

Você pode ajustar a contagem de intervalos para corresponder à granularidade do seu conjunto de dados. Por exemplo, um conjunto de dados que varia de 0 a 100 com uma contagem de intervalos de 10 cria intervalos de 10 unidades cada (0‑9, 10‑19, …, 90‑100).

> **Why it matters:** Escolher poucos intervalos pode ocultar padrões importantes, enquanto muitos intervalos podem gerar um gráfico ruidoso. Teste alguns valores para encontrar o ponto ideal para seus dados específicos.

## Configurar intervalos do histograma para melhor legibilidade

Além do número de intervalos, você geralmente deseja rotular cada intervalo para que os leitores vejam a contagem exata. A propriedade `ShowBinLabels` alterna a visibilidade desses rótulos:

```csharp
// Display the value of each bin on the chart
histogram.ShowBinLabels = true;
```

Quando `ShowBinLabels` está definido como `true`, o Word renderiza um rótulo numérico acima de cada barra. Essa pequena configuração melhora muito a interpretabilidade do gráfico, especialmente em relatórios onde o público pode não ter o conjunto de dados original.

Você também pode personalizar a aparência do rótulo, como tamanho da fonte ou cor, via o objeto `HistogramLabel` (disponível em versões mais recentes do Aspose.Words). O trecho a seguir demonstra um ajuste comum:

```csharp
// Optional: make bin labels bold and increase font size
histogram.HistogramLabel.Font.Size = 10;
histogram.HistogramLabel.Font.Bold = true;
```

> **Edge case:** Se você definir `HistogramBins` para um valor maior que o número de pontos de dados distintos, alguns intervalos aparecerão vazios. O gráfico ainda será renderizado corretamente, mas a visualização pode parecer esparsa. Considere reduzir a contagem de intervalos nesses cenários.

## Adicionar série de dados ao histograma

Um histograma requer uma única série de dados que represente os valores numéricos subjacentes. Você pode preencher a série usando um array, um `List<double>` ou qualquer coleção enumerável. Abaixo está um exemplo conciso que adiciona um conjunto de dados aleatório:

```csharp
// Create a data series for the histogram
ChartSeries series = histogram.Series[0];
double[] sampleData = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
series.DataPoints.AddRange(sampleData);
```

O método `AddRange` converte cada valor em um intervalo de acordo com o `HistogramBins` definido anteriormente. Após esta etapa, o gráfico exibe um histograma totalmente preenchido.

## Salvar e visualizar o documento resultante

Finalmente, grave o documento no disco. Você pode escolher qualquer local que sua aplicação possa acessar. A linha a seguir salva o arquivo como `output.docx`:

```csharp
// Save the document so you can view the chart
doc.Save("output.docx");
```

Abra `output.docx` no Microsoft Word para ver um histograma com dez intervalos, valores rotulados e os dados de exemplo que você forneceu. O gráfico terá aparência semelhante à imagem abaixo:

![Completed histogram in Word](/images/histogram-complete.png){: .img-fluid alt="Documento Word exibindo um gráfico de histograma concluído com dez intervalos e rótulos"}

## Exemplo completo e executável

Juntando todas as peças, aqui está um programa autônomo que você pode copiar, colar e executar:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a histogram chart (400×300 points)
        Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);

        // 3️⃣ Configure the histogram
        histogram.HistogramBins = 10;          // How to set histogram bins
        histogram.ShowBinLabels = true;       // Configure histogram bins to show labels
        histogram.HistogramLabel.Font.Size = 10;
        histogram.HistogramLabel.Font.Bold = true;

        // 4️⃣ Add a data series
        ChartSeries series = histogram.Series[0];
        double[] data = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
        series.DataPoints.AddRange(data);

        // 5️⃣ Save the document
        doc.Save("output.docx");
    }
}
```

**Saída esperada:** Ao abrir `output.docx` será exibido um histograma com dez barras igualmente espaçadas, cada uma rotulada com sua contagem. O gráfico reflete a distribuição do array `data`, tornando as tendências instantaneamente visíveis.

## Perguntas comuns e solução de problemas

| Pergunta | Resposta |
|----------|----------|
| *E se eu precisar de mais de uma série de dados?* | Histograms normalmente representam uma única distribuição. Se precisar de múltiplas séries, considere usar um gráfico de colunas em vez disso. |
| *Posso alterar o tamanho do gráfico após a inserção?* | Sim. Ajuste as propriedades `histogram.Width` e `histogram.Height`, ou chame `builder.InsertChart` novamente com dimensões diferentes. |
| *Isso funciona com .NET Framework 4.8?* | Absolutamente. Aspose.Words suporta .NET Framework 4.5 e posteriores, portanto o mesmo código funciona sem alterações. |
| *Como exportar o gráfico como imagem?* | Use `histogram.ToImage()` para obter um `System.Drawing.Image`, então salve‑o com `image.Save("chart.png")`. |

## Conclusão

Agora você sabe como criar um histograma no Word usando Aspose.Words, como definir intervalos do histograma e como configurá‑los para uma saída clara e rotulada. O exemplo completo demonstra uma abordagem pronta para produção que você pode adaptar a qualquer cenário de relatórios orientado por dados.  

Em seguida, explore tópicos relacionados como **como criar gráficos de pizza no Word**, **personalizar cores de gráficos** e **incorporar fontes de dados do Excel**. Cada um desses se baseia no mesmo fluxo de trabalho `DocumentBuilder`, permitindo que você estenda a solução com esforço mínimo.

Boas criações de gráficos!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [como criar pdf a partir do Word – Guia completo em C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Como carregar documentos Word usando Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}