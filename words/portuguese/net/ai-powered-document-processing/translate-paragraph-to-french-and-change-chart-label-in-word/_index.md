---
category: general
date: 2026-10-10
description: Traduzir o parágrafo para o francês e aprender como mudar o rótulo de
  dados do gráfico, personalizar o rótulo de dados do gráfico e salvar o arquivo DOCX
  editado usando o Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: pt
lastmod: 2026-10-10
og_description: Traduzir parágrafo para francês e aprender como alterar o rótulo de
  dados do gráfico, personalizar o rótulo de dados do gráfico e salvar o arquivo DOCX
  editado usando o Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Traduzir parágrafo para francês e mudar rótulo do gráfico no Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Traduzir parágrafo para o francês e alterar rótulo do gráfico no Word
url: /pt/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Traduzir parágrafo para francês e alterar rótulo do gráfico no Word

Se você precisa **traduzir parágrafo para francês** enquanto também atualiza um gráfico dentro do mesmo documento Word, este guia mostra exatamente como fazer. Usando Aspose.Words AI você pode traduzir o texto automaticamente, depois modificar o rótulo de dados de um gráfico e, finalmente, salvar o arquivo `.docx` editado — tudo em alguns passos simples.

O tutorial cobre tudo, desde o carregamento do arquivo fonte até a persistência das alterações. Ao final, você será capaz de traduzir qualquer parágrafo, personalizar o rótulo de dados de um gráfico e gerar um novo arquivo Word pronto para distribuição. Nenhum script externo é necessário; todo o fluxo de trabalho vive em um único programa C#.

## Pré-requisitos

- .NET 6.0 ou superior (o código também funciona com .NET Framework 4.7+)
- Uma licença do Aspose.Words for .NET (ou uma chave de avaliação gratuita)
- Acesso à internet para o tradutor Google AI (a classe `Translator` usa a API do Google nos bastidores)
- Um documento Word (`input.docx`) que contenha ao menos um parágrafo e um gráfico

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo aplicativo de console e adicione o pacote NuGet Aspose.Words:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Agora inclua os namespaces necessários no topo de `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Essas importações dão acesso ao carregamento de documentos, tradução AI e funcionalidade de edição de gráficos.

## Etapa 2: Carregar o documento Word fonte

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Carregar o arquivo cria uma representação em memória que pode ser consultada e modificada sem tocar no arquivo original no disco.

## Etapa 3: Traduzir o primeiro parágrafo para francês

O primeiro parágrafo costuma ser um título ou frase introdutória, tornando‑o um bom candidato à tradução. A classe `Translator` abstrai a chamada ao modelo AI do Google.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Por que isso funciona:**  
`paragraph.Runs.Clear()` remove todas as execuções de texto existentes, garantindo que a nova tradução não seja concatenada com o conteúdo antigo. `new Run(document, translatedText)` cria uma nova execução que herda a formatação do parágrafo.

## Etapa 4: Localizar o primeiro gráfico e personalizar seu rótulo de dados

Gráficos são armazenados como nós `Shape` do tipo `NodeType.Shape`. O primeiro gráfico pode ser obtido com `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Explicação das etapas principais:**

- `GetChild(NodeType.Shape, 0, true)` realiza uma busca em profundidade e retorna a primeira forma, que no nosso caso é um gráfico.
- `ChartSeries` representa uma coleção de pontos de dados; a primeira série (`Series[0]`) normalmente corresponde ao conjunto de dados principal.
- `ChartDataLabelPosition.OutsideEnd` move o rótulo para fora da extremidade da barra, melhorando a legibilidade.
- Definir `dataLabel.Text` para uma string em francês alinha o rótulo ao parágrafo traduzido.

## Etapa 5: Salvar o documento com o parágrafo traduzido

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

Neste ponto o documento contém o parágrafo em francês, mas ainda mantém a configuração original do gráfico.

## Etapa 6: Salvar o documento com o gráfico atualizado

Você pode reutilizar a mesma instância `Document` — não há necessidade de recarregá‑la — porque as modificações do gráfico já estão em memória.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Ambos os arquivos agora estão prontos para distribuição:

- **`translated.docx`** – contém o parágrafo em francês.
- **`chart-updated.docx`** – contém o parágrafo em francês *e* o rótulo do gráfico personalizado.

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar‑colar em `Program.cs`. Ele compila e executa como está, supondo que você tenha substituído `YOUR_DIRECTORY` por um caminho de pasta real.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Personalizar rótulo de dados do gráfico](/words/english/net/programming-with-charts/chart-data-label/)
- [Formatar número de rótulo de dados em um gráfico](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Rótulo de dados do gráfico](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}