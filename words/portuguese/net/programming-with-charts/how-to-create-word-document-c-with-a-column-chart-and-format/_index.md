---
category: general
date: 2026-09-21
description: Aprenda a criar um documento Word em C# e inserir um gráfico de colunas,
  definir a posição dos rótulos e exibir os valores usando Aspose.Words em um guia
  passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: pt
lastmod: 2026-09-21
og_description: Criar documento Word C# com Aspose.Words. Este tutorial mostra como
  inserir um gráfico de colunas, definir a posição do rótulo e exibir os valores.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Criar documento Word em C# – inserir gráfico de colunas, definir rótulo,
  exibir valores
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Como criar um documento Word em C# com um gráfico de colunas e rótulos formatados
url: /pt/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word C# com um gráfico de colunas e rótulos formatados

Se você precisa **criar documento Word C#** que inclua um gráfico, este guia mostra exatamente como fazer isso. Você aprenderá a inserir um gráfico de colunas, posicionar seu rótulo de dados e exibir os valores do rótulo — tudo com Aspose.Words for .NET.

Gerar um arquivo Word com gráfico costumava exigir trabalho manual no Microsoft Word. Com as etapas de **how to insert chart** descritas aqui, você pode automatizar todo o processo a partir do código, tornando a geração de relatórios rápida e repetível. O tutorial também aborda **how to set label** e **how to display values** para que o gráfico esteja pronto para os usuários finais.

Ao final deste artigo você terá um programa C# completo e executável que cria um arquivo `.docx` contendo um gráfico de colunas cujos rótulos de dados aparecem dentro de cada coluna e mostram seus valores numéricos.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 SDK ou posterior instalado  
* Uma cópia licenciada do **Aspose.Words for .NET** (a versão de avaliação gratuita funciona para testes)  
* Uma IDE como Visual Studio 2022 ou Visual Studio Code  

Nenhum pacote NuGet adicional é necessário além do `Aspose.Words`.

## Etapa 1: Configurar o projeto e adicionar Aspose.Words

Crie um novo projeto de console e adicione o pacote Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

O comando `dotnet add package` obtém a versão estável mais recente do **Aspose.Words**, que inclui a API de gráficos usada no exemplo de **insert column chart word**.

## Etapa 2: Criar um novo documento Word em branco

O primeiro trecho de código cria um documento vazio e um `DocumentBuilder` que permite inserir conteúdo. Esta é a base para **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa todo o arquivo `.docx`, enquanto `DocumentBuilder` fornece métodos como `InsertParagraph`, `InsertImage` e, crucialmente para este tutorial, `InsertChart`.

## Etapa 3: Inserir um gráfico de colunas (how to insert chart)

Agora inserimos um **column chart**. O método `InsertChart` recebe o tipo de gráfico, a largura e a altura em pontos.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

Neste ponto o gráfico contém uma série de dados padrão com valores de espaço reservado. Você pode substituir os dados da série se precisar de números personalizados, mas para demonstrar **how to set label** e **how to display values**, os dados padrão são suficientes.

## Etapa 4: Posicionar o rótulo de dados dentro de cada coluna (how to set label)

Rótulos de dados são o texto que aparece em cada coluna. Para tornar o gráfico mais fácil de ler, movemos o rótulo para dentro da coluna e habilitamos seu valor numérico.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` coloca o rótulo no topo da coluna, mas ainda dentro da forma da coluna, o que é um estilo visual comum em relatórios. Definir `ShowValue` como `true` atende ao requisito de **how to display values**.

## Etapa 5: Salvar o documento

Por fim, grave o documento no disco. O arquivo pode ser aberto com Microsoft Word, LibreOffice ou qualquer visualizador que suporte o formato Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Executar o programa gera `output.docx` que contém um gráfico de colunas com rótulos de dados posicionados dentro de cada coluna e exibindo seus valores.

### Resultado esperado

Ao abrir `output.docx`, você deverá ver um único gráfico de colunas semelhante à imagem abaixo. Cada coluna tem um rótulo numérico no topo, dentro da coluna, exibindo o valor da série.

![Chart in a Word document created with C#](/images/word-chart-example.png "Chart in a Word document created with C# – create word document C#")

*Alt text:* *Gráfico em um documento Word criado com C# que demonstra como inserir column chart word e exibir valores.*

## Variações comuns e casos de borda

### Adicionando dados personalizados ao gráfico

Se precisar substituir os dados de espaço reservado, você pode modificar a coleção `Series` do gráfico:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Alterando fonte e cor do rótulo

Você pode personalizar ainda mais a aparência do rótulo:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Inserindo múltiplos gráficos

O `DocumentBuilder` pode inserir quantos gráficos forem necessários. Basta chamar `InsertChart` novamente após mover o cursor com `builder.Writeln()` ou `builder.InsertParagraph()`.

## Dicas avançadas

* **Dica avançada:** Defina `chart.HasTitle = true` e atribua `chart.Title.Text` para dar ao gráfico um título descritivo. Isso melhora a acessibilidade para leitores de tela.  
* **Atenção:** Ao salvar em um compartilhamento de rede, garanta que a aplicação tenha permissões de gravação; caso contrário, `doc.Save` lançará uma `UnauthorizedAccessException`.  
* **Dica de desempenho:** Reutilize uma única instância de `DocumentBuilder` para múltiplas inserções; criar um novo builder para cada operação adiciona sobrecarga desnecessária.

## Conclusão

Agora você sabe como **criar documento Word C#** que contém um gráfico de colunas, como **insert chart** elementos, **set label** posições e **display values** dentro de cada coluna. O exemplo de código completo acima está pronto para ser executado, e você pode estendê‑lo com dados personalizados, estilos ou gráficos adicionais.

Em seguida, explore tópicos relacionados como **how to insert picture**, **how to generate tables** ou **how to apply document themes** para tornar seus relatórios automatizados ainda mais ricos. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}