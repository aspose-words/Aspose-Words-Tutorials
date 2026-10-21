---
category: general
date: 2026-10-13
description: Como formatar um gráfico no Word com C# aplicando um formato numérico
  personalizado, como moeda, aos eixos do gráfico. Exemplo de código passo a passo
  incluído.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: pt
lastmod: 2026-10-13
og_description: Como formatar gráficos no Word com C# permite aplicar um formato numérico
  personalizado aos eixos do gráfico, garantindo que os valores apareçam como moeda,
  porcentagens ou qualquer padrão que você precisar. Siga o guia passo a passo.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Como formatar gráfico no Word com C# – formatos numéricos personalizados
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Como formatar gráfico no Word com C# e formatos numéricos personalizados
url: /pt/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como formatar gráfico no Word com C# e formatos numéricos personalizados

Formatar um gráfico no Word com C# é uma necessidade comum quando você precisa apresentar dados de forma profissional. Este guia mostra como aplicar um formato numérico personalizado ao eixo de um gráfico usando **Aspose.Words for .NET**, para que os valores apareçam exatamente como você espera.

Você aprenderá como carregar um arquivo DOCX, localizar o primeiro gráfico, ler o formato atual e, em seguida, definir um novo padrão, como moeda com duas casas decimais. O tutorial também aborda como alterar o formato do eixo do gráfico para séries adicionais e como redefinir o formato, se necessário.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou posterior instalado  
* Um projeto Visual Studio 2022 (ou qualquer IDE que suporte .NET)  
* O pacote NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* Um documento Word (`input.docx`) que contém ao menos um gráfico

Você pode adicionar o pacote com o seguinte comando:

```bash
dotnet add package Aspose.Words
```

## Como formatar gráfico no Word usando Aspose.Words

O programa completo a seguir demonstra cada passo necessário para **formatar** os valores do eixo de um gráfico. Salve o arquivo como `Program.cs` e execute-o a partir da linha de comando ou da sua IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Explicação de cada passo

| Etapa | Por que é importante | Código chave |
|------|----------------------|--------------|
| **Carregar o documento** | Você precisa de um objeto `Document` para trabalhar com o arquivo Word. | `new Document("input.docx")` |
| **Recuperar o gráfico** | Objetos `Chart` são armazenados como nós `Shape`; o casting permite usar APIs específicas de gráficos. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Acessar X‑values** | A formatação do eixo é aplicada à coleção de valores de uma série de dados. | `chart.ChartData.Series[0].XValues` |
| **Ler o formato atual** | Conhecer o `FormatCode` existente ajuda a decidir se deve substituí‑lo ou complementá‑lo. | `xValues.FormatCode` |
| **Definir formato personalizado** | A propriedade `FormatCode` aceita qualquer padrão compatível com Excel, permitindo moeda, porcentagens, datas, etc. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Salvar o documento** | Persistir as alterações grava o novo formato do eixo de volta no arquivo DOCX. | `doc.Save("output_formatted.docx")` |

Executar o programa gera `output_formatted.docx`. Abra-o no Word e você verá os valores do eixo X do gráfico exibidos como **$1,234.00**, **$2,345.00**, … em vez de números simples.

## Aplicar formato numérico personalizado ao eixo do gráfico

Se precisar **aplicar formato numérico personalizado** ao eixo Y ou a séries adicionais, o processo é idêntico—basta direcionar uma coleção diferente:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Dica profissional:** Use aspas duplas dentro da string de formato para inserir caracteres literais (por exemplo, `"$"` para moeda). Escape as aspas conforme mostrado acima.

## Formato numérico personalizado no Word – lidando com a localidade do Word

O Word respeita a localidade do documento ao interpretar formatos numéricos. Se o documento usar uma localidade diferente dos EUA, pode ser necessário ajustar a string de formato:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Testar o formato em um documento com configurações de idioma alemão confirma que os valores aparecem como **€ 1.234,00**.

## Como definir propriedades do gráfico programaticamente

Além da formatação dos eixos, você frequentemente quer **definir** títulos, legendas ou rótulos de dados do gráfico. Aqui está um trecho rápido que demonstra como definir o título de um gráfico após formatar o eixo:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Combinar isso com o formato numérico personalizado fornece um gráfico totalmente polido e pronto para relatórios.

## Alterar formato do eixo do gráfico dinamicamente com base na entrada do usuário

Em aplicações reais você pode permitir que os usuários escolham um formato em tempo de execução. O método a seguir encapsula a lógica de formatação:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Você pode chamar `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` para moeda ou `SetAxisFormat(chart, 0, "0%")` para porcentagens. Essa abordagem mantém seu código principal limpo e suporta extensões futuras.

## Casos extremos e armadilhas comuns

| Situação | O que observar | Correção sugerida |
|----------|----------------|-------------------|
| Documento contém **nenhum gráfico** | `GetChild` retorna `null`, causando uma exceção de cast. | Verifique se é `null` antes de fazer o cast (veja o exemplo). |
| Múltiplos gráficos no mesmo documento | O código sempre captura o primeiro gráfico (`índice 0`). | Percorra `doc.GetChildNodes(NodeType.Shape, true)` e filtre por `ShapeType.Chart`. |
| Séries **sem X‑values** (ex.: gráficos de pizza) | Acessar `XValues` pode lançar `ArgumentOutOfRangeException`. | Verifique se `Series[i].XValues` não está vazio antes de formatar. |
| Incompatibilidade de localidade | O símbolo da moeda pode aparecer incorretamente. | Defina explicitamente `xValues.FormatCode` com os símbolos de localidade apropriados. |

## Saída esperada

Depois de executar o programa de exemplo, abra **output_formatted.docx**. O eixo X do gráfico deve exibir números no formato personalizado escolhido. Para o exemplo de moeda, os rótulos do eixo ficam assim:

```
$1,000.00
$2,000.00
$3,000.00
```

Se você aplicou o formato de porcentagem aos valores Y, os rótulos do eixo Y aparecem como:

```
10%
20%
30%
```

## Conclusão

Este tutorial mostrou como **formatar gráfico** no Word com C# ao **aplicar um formato numérico personalizado** aos valores dos eixos. Agora você tem um padrão reutilizável para definir moeda, porcentagens ou qualquer outro padrão numérico, além de orientações para lidar com localidades, múltiplas séries e entrada dinâmica do usuário.

Em seguida, você pode explorar **como definir** títulos, rótulos de dados ou até exportar o gráfico como imagem usando `ChartRenderer`. Esses tópicos se baseiam diretamente nos conceitos abordados aqui e ajudarão você a criar soluções de relatório totalmente automatizadas.

---


## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Format Secondary X‑Axis and Set Display Units to Thousands in Word Line Charts Using Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}