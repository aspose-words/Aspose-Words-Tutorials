---
category: general
date: 2026-10-13
description: Exemplo de gráfico radial do Aspose.Words que mostra como habilitar graduções
  em um gráfico radial usando C# e Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: pt
lastmod: 2026-10-13
og_description: Exemplo de gráfico radial Aspose.Words que demonstra como habilitar
  graduações em um gráfico radial com C# e a biblioteca mais recente 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Exemplo de gráfico radial Aspose.Words – habilitar graduações em C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Exemplo de gráfico radial Aspose.Words: habilitar graduações em C#'
url: /pt/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exemplo de gráfico radial Aspose.Words: habilitar graduações em C#

Se você está procurando um **exemplo de gráfico radial Aspose.Words**, chegou ao lugar certo. Este tutorial orienta passo a passo como ativar as graduações para um gráfico radial usando a API Aspose.Words for .NET.

Gráficos radiais são úteis para visualizar dados cíclicos, como métricas de horário do dia ou tendências sazonais. Por padrão, as graduações (as marcas de escala ao redor do eixo circular) estão ocultas, o que pode tornar o gráfico mais difícil de ler. Habilitá‑las é uma mudança de uma única linha, mas você precisa conhecer o modelo de objetos correto e a versão que oferece esse recurso.

Neste guia você aprenderá a:

* Carregar um documento Word que já contém um gráfico radial.  
* Acessar a forma do gráfico via a API de gráficos do Aspose.Words.  
* Ativar a **visibilidade das graduações** (disponível a partir da **versão 24.9 do Aspose.Words**).  
* Salvar o documento modificado e verificar o resultado.

O código completo e executável está incluído, para que você possa copiá‑lo e colá‑lo em um novo projeto de console e ver o efeito imediatamente.

![Exemplo de gráfico radial Aspose.Words com graduações](https://example.com/images/radial-chart-graduations.png "Exemplo de gráfico radial Aspose.Words mostrando graduações habilitadas")

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

| Requisito | Por que é importante |
|-----------|----------------------|
| .NET 6.0 ou posterior | Aspose.Words for .NET 24.9+ tem como alvo .NET Standard 2.0 e funciona em .NET 6+. |
| Aspose.Words for .NET **24.9** ou mais recente | A propriedade `IsGraduationsVisible` foi introduzida na versão 24.9. Versões anteriores lançarão uma `MissingMemberException`. |
| Um documento Word (`RadialChart.docx`) que contenha um gráfico radial | O exemplo manipula um gráfico existente; criar um do zero é um tópico separado. |
| Um IDE C# (Visual Studio, Rider, VS Code) | Qualquer IDE que compile projetos .NET funcionará. |
| Pacote NuGet `Aspose.Words` | Instale via `dotnet add package Aspose.Words --version 24.9.0` (ou posterior). |

> **Dica profissional:** Se você não puder atualizar para a 24.9, ainda poderá modificar outras propriedades do gráfico, mas as graduações permanecerão ocultas porque a API não expôs essa flag.

## Exemplo de gráfico radial Aspose.Words – guia passo a passo

As seções a seguir dividem o processo em etapas discretas e fáceis de seguir. Cada etapa inclui o código exato que você precisa e uma breve explicação do *porquê* da etapa existir.

### Etapa 1: Carregar o documento que contém um gráfico radial

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Por que isso importa:**  
`Document` é o ponto de entrada da **API de gráficos Aspose.Words**. Ele carrega o arquivo DOCX na memória, dando acesso a todos os nós — parágrafos, tabelas e formas de gráfico. Se o arquivo não for encontrado, `Document` lança uma `FileNotFoundException`, que você deve tratar em código de produção.

### Etapa 2: Recuperar a primeira forma de gráfico do documento

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Por que isso importa:**  
Gráficos são armazenados como nós `Shape`. O método `GetChild` com `NodeType.Shape` percorre o DOM e devolve a primeira forma correspondente. O cast para `Chart` fornece acesso a propriedades específicas do gráfico, como `RadialChart`. A verificação de nulo garante um erro claro caso o documento não contenha um gráfico, situação comum ao reutilizar modelos.

### Etapa 3: Habilitar graduações no gráfico radial

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Por que isso importa:**  
`IsGraduationsVisible` controla as marcas de escala ao redor do eixo circular. Quando definido como `true`, o gráfico renderiza as graduações, melhorando a legibilidade para quem precisa avaliar valores com precisão. A propriedade está sob `RadialChart`, que é um subtipo de `Chart`. Se você tentar isso em um gráfico que não seja radial (por exemplo, um gráfico de barras), a propriedade `RadialChart` será `null`, portanto verifique o tipo de gráfico primeiro em cenários mais complexos.

#### Tratamento de gráficos não radiais (opcional)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Essa proteção torna o código robusto quando o documento de origem pode conter diferentes tipos de gráfico.

### Etapa 4: Salvar o documento modificado

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Por que isso importa:**  
Chamar `Save` grava o DOM em memória de volta para um arquivo .docx, persistindo a alteração feita no gráfico. O arquivo de saída pode ser aberto no Microsoft Word, LibreOffice ou qualquer visualizador que suporte DOCX. Você verá o gráfico radial com graduações visíveis.

## Exemplo completo e executável

Abaixo está o programa completo que você pode colar em `Program.cs` de um projeto console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Saída esperada

Ao abrir `RadialChart_Graduations.docx` no Word, o gráfico radial exibirá marcas de escala (graduações) ao redor do eixo circular, semelhante à captura de tela mostrada anteriormente. O restante do gráfico (séries de dados, legenda, título) permanece inalterado.

## Variações comuns e casos de borda

| Situação | Solução |
|----------|---------|
| **Versão antiga do Aspose.Words (< 24.9)** | Atualize para o pacote NuGet mais recente. A propriedade `IsGraduationsVisible` não existe em versões anteriores. |
| **Múltiplos gráficos no mesmo documento** | Use `doc.GetChild(NodeType.Shape, index, true)` com o `index` apropriado ou itere sobre `doc.GetChildNodes(NodeType.Shape, true)` e filtre por `ChartType.Radial`. |
| **Gráfico criado programaticamente** | Use `DocumentBuilder` para inserir um gráfico, então defina `RadialChart.IsGraduationsVisible` no |

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Atualizar dados da série de um gráfico em um documento Word usando Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Remover uma série de gráfico de um documento Word usando Aspose.Words for .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Ocultar a borda da área de plotagem em um gráfico de colunas com Aspose.Words for .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}