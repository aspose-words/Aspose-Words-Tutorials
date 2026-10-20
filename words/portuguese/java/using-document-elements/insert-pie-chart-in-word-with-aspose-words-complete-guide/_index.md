---
category: general
date: 2026-07-26
description: Insira um gráfico de pizza em um documento Word usando Aspose.Words.
  Aprenda a adicionar o gráfico, destacar fatias e exibir porcentagens em apenas alguns
  passos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: pt
lastmod: 2026-07-26
og_description: Insira um gráfico de pizza em um arquivo Word com Aspose.Words. Siga
  este guia para aprender como adicionar o gráfico, destacar fatias e exibir porcentagens
  rapidamente.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Inserir Gráfico de Pizza no Word – Tutorial Aspose.Words Passo a Passo
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Inserir Gráfico de Pizza no Word com Aspose.Words – Guia Completo
url: /pt/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir Gráfico de Pizza no Word com Aspose.Words – Guia Completo

Já precisou **inserir gráfico de pizza** em um relatório Word, mas não sabia por onde começar? Você não está sozinho. Em muitos aplicativos empresariais, o impacto visual de um gráfico de pizza torna os dados instantaneamente digeríveis, e o Aspose.Words torna isso possível com apenas algumas linhas de código.

Neste tutorial, percorreremos os passos exatos para **adicionar gráfico ao Word**, explodir uma fatia para ênfase e mostrar porcentagens nos rótulos de dados. Ao final, você terá um exemplo pronto‑para‑executar que pode ser inserido em qualquer projeto .NET.

---

## Pré-requisitos

- .NET 6.0 ou posterior (o código funciona tanto com .NET Core quanto com .NET Framework)
- O pacote NuGet Aspose.Words for .NET instalado  
  ```bash
  dotnet add package Aspose.Words
  ```
- Um entendimento básico da sintaxe C# — nada sofisticado é necessário
- Uma IDE de sua escolha (Visual Studio, Rider ou VS Code)

É isso. Vamos colocar a mão na massa.

---

## Inserir Gráfico de Pizza em um Documento Word

A primeira coisa que precisamos é um novo objeto `Document` e um `DocumentBuilder`. Pense no builder como uma caneta que escreve diretamente na tela do Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por que isso importa:** O `Document` representa o arquivo .docx completo, enquanto o `DocumentBuilder` nos fornece uma API conveniente para inserir elementos como gráficos, tabelas e texto. Esta é a base para toda operação de **como adicionar gráfico**.

---

## Como Adicionar Gráfico ao Word

Agora que temos um builder, podemos realmente **inserir gráfico de pizza**. O método `insertChart` recebe o tipo de gráfico e as dimensões desejadas em pontos (1 ponto = 1/72 polegada).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Dica:** Se precisar de um tamanho diferente, basta ajustar os valores de largura e altura. O gráfico será dimensionado automaticamente para se ajustar às margens da página.

---

## Como Explodir uma Fatia para Ênfase

Um ajuste visual comum é “explodir” uma fatia para que ela se destaque do círculo. Isso atrai o olhar do leitor para o segmento mais importante.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Por que explodir uma fatia?** Quando você deseja destacar uma categoria específica — por exemplo, “receita do Q1” em um relatório financeiro — explodir a fatia a torna instantaneamente perceptível sem texto adicional.

---

## Como Mostrar Percentuais nos Rótulos de Dados

A maioria dos gráficos de pizza fica melhor quando cada fatia exibe sua porcentagem. O Aspose.Words permite ativar isso com uma única propriedade.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Nota rápida:** O sinalizador `ShowPercentage` funciona para todos os pontos da série, portanto não é necessário configurá‑lo por fatia.

---

## Salvar o Documento que Contém o Gráfico

Finalmente, gravamos o documento no disco. Escolha qualquer pasta que desejar; apenas certifique‑se de que o caminho exista.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Ao abrir `PieChart.docx` no Microsoft Word, você verá um gráfico de pizza perfeitamente renderizado com a primeira fatia explodida e as porcentagens exibidas — exatamente o que se espera de um relatório empresarial bem elaborado.

---

## Exemplo Completo Funcional

Abaixo está o programa completo, pronto para copiar e colar. Execute‑o como um aplicativo de console e verifique o arquivo de saída.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Resultado esperado:** Abra o `PieChart.docx` gerado. Você verá um gráfico de pizza de três fatias intitulado “Sales Q1”, com a primeira fatia destacada e cada fatia rotulada como “30 %”, “45 %” e “25 %”. O visual corresponde aos dados que inserimos.

---

## Perguntas Frequentes & Casos Limite

- **E se eu precisar de mais de uma série?**  
  Basta adicionar objetos `ChartSeries` adicionais a `chart.Series`. Cada série pode ter seu próprio conjunto de dados, cores e configurações de explosão.

- **Posso mudar as cores do gráfico?**  
  Sim. Cada `ChartPoint` possui a propriedade `Format.Fill.ForeColor` que pode ser definida para qualquer `System.Drawing.Color`.

- **E quanto a diferentes tipos de gráfico?**  
  O enum `ChartType` inclui barra, linha, rosquinha e muitos outros. Troque `ChartType.Pie` pelo visual que precisar.

- **O gráfico é editável no Word após a inserção?**  
  Absolutamente. O Word trata o gráfico como um gráfico nativo do Office, permitindo que os usuários dêem duplo‑clique para abrir o editor de gráficos incorporado.

---

## Conclusão

Agora você sabe exatamente como **inserir gráfico de pizza** em um documento Word usando Aspose.Words, **como adicionar gráfico ao Word**, **como explodir uma fatia**, e **como mostrar percentuais** nos rótulos de dados. O exemplo completo acima está pronto para ser executado, e você pode estendê‑lo com dados personalizados, estilos ou séries adicionais.

Pronto para o próximo passo? Experimente substituir a pizza por um gráfico de rosquinha, ou gere um lote de relatórios com diferentes conjuntos de dados automaticamente. Se estiver curioso sobre outras visualizações, confira nossos guias sobre **como adicionar gráfico** para gráficos de barra e linha, ou explore a referência da API **add chart to word** para personalizações mais avançadas.

Feliz codificação, e que seus documentos sejam sempre tão claros quanto uma pizza perfeitamente fatiada!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir Gráfico de Colunas no Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Inserir Gráfico de Área em Documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Criar Gráfico de Dispersão no Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}