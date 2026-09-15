---
category: general
date: 2026-09-14
description: Inserir gráfico de radar no Word com C#. Aprenda como definir o título
  do gráfico, adicionar várias séries e criar o gráfico programaticamente em apenas
  algumas linhas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: pt
lastmod: 2026-09-14
og_description: Inserir gráfico de radar no Word usando C#. Este tutorial mostra como
  definir o título do gráfico, adicionar várias séries e criar o gráfico programaticamente.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: Inserir gráfico de radar no Word com C# – guia rápido de programação
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: Inserir gráfico de radar no Word usando C# – guia passo a passo
url: /pt/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir gráfico radar no Word usando C# – guia passo a passo

Se você precisa **inserir um gráfico radar** em um documento Word, este guia mostra como fazer isso programaticamente com C#. Você também aprenderá a **definir o título do gráfico**, adicionar um **gráfico radar com múltiplas séries** e salvar o arquivo sem sair da sua IDE.

O tutorial cobre tudo, desde a configuração do projeto até a chamada final `doc.Save`, para que você possa copiar‑colar o exemplo completo e executá‑lo imediatamente. Não é necessário consultar documentação externa.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6 (ou superior) instalado.  
* Uma licença válida do Aspose.Words for .NET (ou uma chave de avaliação temporária).  
* Visual Studio 2022 ou qualquer IDE C# de sua preferência.

> **Dica:** Se estiver usando a versão de avaliação, lembre‑se de definir a licença antes da primeira criação de `Document` para evitar a marca d'água de avaliação.

## Etapa 1: Inserir gráfico radar em um documento Word

A primeira operação é criar um novo `Document` e um `DocumentBuilder`. O builder dá acesso ao conteúdo do documento e permite posicionar um **gráfico radar** exatamente onde você precisar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Por que esta etapa é importante:* `InsertChart` cria um objeto de gráfico que pode ser totalmente configurado antes de salvar o documento. Usar `ChartType.Radar` indica ao Word que ele deve renderizar um gráfico radial em vez de um gráfico de colunas ou linhas.

## Etapa 2: Definir título do gráfico e graduações dos eixos

Um gráfico sem título pode gerar confusão. Aqui **definimos o título do gráfico** como “Sales Radar” e habilitamos graduações em ambos os eixos (disponível a partir do Aspose.Words 24.9).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Por que esta etapa é importante:* O título fornece contexto ao leitor, e as graduações melhoram a legibilidade ao mostrar onde cada ponto de dado se posiciona na escala.

## Etapa 3: Criar múltiplas séries para o gráfico radar

Um **gráfico radar com múltiplas séries** permite comparar diferentes períodos lado a lado. Abaixo adicionamos duas séries — Q1 e Q2 — cada uma com três pontos de dado.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Por que esta etapa é importante:* Adicionar múltiplas séries demonstra como comparar conjuntos de dados no mesmo radar, uma necessidade comum para vendas, desempenho ou resultados de pesquisas.

## Etapa 4: Salvar o documento Word programaticamente

Por fim, você **cria o gráfico programaticamente** e persiste o documento no disco. O método `Save` grava um arquivo `.docx` que pode ser aberto no Microsoft Word.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

Ao abrir `RadialGraduations.docx`, você verá um gráfico radar intitulado “Sales Radar” com duas séries (Q1 e Q2) plotadas contra os meses Jan‑Mar.

### Saída esperada

![Radar chart in Word](https://example.com/radar-chart.png){: .align-center alt="Documento Word exibindo um gráfico radar com duas séries de dados"}

A captura de tela (ou o próprio arquivo) confirma que o gráfico foi inserido, recebeu título e foi preenchido corretamente.

## Exemplo completo e executável

Juntando tudo, aqui está um programa autocontido que você pode compilar e executar:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Execute o programa, abra o arquivo gerado e verifique que a operação de **inserir gráfico radar** foi bem‑sucedida.

## Perguntas comuns e casos extremos

| Pergunta | Resposta |
|----------|----------|
| **Posso mudar o tipo de gráfico após a inserção?** | Sim. Após `InsertChart`, atribua um novo `ChartType` a `chart.Type`. Contudo, criar o gráfico com o tipo correto desde o início é mais eficiente. |
| **E se eu precisar de mais de duas séries?** | Chame `chart.Series.Add` para cada série adicional. O gráfico ajustará automaticamente a legenda e as cores. |
| **Como personalizar cores ou marcadores?** | Use `chart.Series[i].Format.Fill.ForeColor` para cores de preenchimento e `chart.Series[i].Marker` para estilos de marcadores. |
| **A API é compatível com .NET Framework?** | O mesmo código funciona com .NET Framework 4.7+; basta referenciar o DLL apropriado do Aspose.Words. |
| **E se eu estiver usando uma versão mais antiga do Aspose.Words?** | As graduações (`HasGraduations`) foram introduzidas na 24.9. Em versões anteriores, você pode adicionar linhas de grade manualmente usando `chart.AxisX.MajorGridLines` e `chart.AxisY.MajorGridLines`. |

## Conclusão

Agora você sabe como **inserir um gráfico radar** em um documento Word usando C#, **definir o título do gráfico**, adicionar um **gráfico radar com múltiplas séries** e **criar o gráfico programaticamente**. Esta solução de ponta a ponta permite automatizar relatórios, dashboards ou qualquer cenário onde a comparação visual de categorias seja necessária.

Em seguida, explore tópicos relacionados como **personalização de cores de gráficos**, **exportação de gráficos como imagens** ou **incorporação de gráficos em arquivos PDF**. Experimente diferentes conjuntos de dados para ver como a visualização radar se adapta.

Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Inserir gráfico de colunas no Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Inserir um gráfico de bolhas no Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Inserir gráfico de área em documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}