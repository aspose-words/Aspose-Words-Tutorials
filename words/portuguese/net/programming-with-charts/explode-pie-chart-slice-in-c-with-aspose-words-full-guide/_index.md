---
category: general
date: 2026-07-19
description: Exploda a fatia de gráfico de pizza usando Aspose.Words para C#. Aprenda
  como explodir a fatia de pizza, ajustar o tamanho do buraco do donut e alterar rapidamente
  os pontos de dados do gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: pt
lastmod: 2026-07-19
og_description: Exploda a fatia de gráfico de pizza com Aspose.Words para C#. Este
  guia mostra como explodir a fatia da pizza, ajustar o tamanho do buraco da rosca
  e alterar os pontos de dados do gráfico de forma eficiente.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Explodir Fatia de Gráfico de Pizza em C# – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Explodir Fatia de Gráfico de Pizza em C# com Aspose.Words – Guia Completo
url: /pt/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Explodir Fatia de Gráfico de Pizza em C# com Aspose.Words – Guia Completo

Já se perguntou como **explodir a fatia de um gráfico de pizza** em um documento Word usando C#? Você não está sozinho. Seja preparando uma apresentação de vendas ou visualizando resultados de pesquisa, uma fatia explodida pode chamar a atenção exatamente onde você deseja. Neste tutorial vamos percorrer todo o processo — carregar um documento, obter o gráfico, explodir a primeira fatia, ajustar o buraco do donut e até mudar os pontos de dados do gráfico.

Também vamos abordar os conceitos secundários que você pode estar procurando: **como explodir a fatia da pizza**, **ajustar o tamanho do buraco do donut** e **alterar pontos de dados do gráfico**. Sem enrolação, apenas uma solução completa pronta para copiar e colar.

---

## O que Você Precisa

Antes de mergulharmos, certifique‑se de que você tem:

- **Aspose.Words for .NET** (a versão mais recente em 2026‑07‑19). Você pode obtê‑la via NuGet com `Install-Package Aspose.Words`.
- Um projeto **.NET 6+** (ou .NET Framework 4.7.2+ se ainda estiver usando a versão legada).
- Um arquivo Word (`Chart.docx`) que já contenha um gráfico de pizza ou donut. Se não tiver um, crie um gráfico rápido no Word e salve‑o.

É só isso — sem bibliotecas extras, sem interop COM, apenas código gerenciado puro.

---

## Explodir Fatia de Gráfico de Pizza – Implementação Passo a Passo

A seguir dividimos a tarefa em etapas pequenas. Cada seção tem um título claro, um trecho de código e uma breve explicação do *porquê* da ação.

### Etapa 1: Instalar e Referenciar Aspose.Words

Primeiro de tudo, adicione o pacote Aspose.Words ao seu projeto. No Console do Gerenciador de Pacotes:

```powershell
Install-Package Aspose.Words
```

> **Dica:** Se você estiver usando a UI de NuGet integrada ao Visual Studio, procure por “Aspose.Words” e clique em Instalar. Isso garante que você obtenha as correções de bugs mais recentes e a capacidade de trabalhar com gráficos imediatamente.

### Etapa 2: Carregar o Documento Word que Contém o Gráfico

Precisamos de um objeto `Document` que aponte para o `.docx` com o gráfico que você deseja modificar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Por que isso importa:** `Document` é o ponto de entrada para toda operação no Aspose.Words. Ao verificar a existência de gráficos logo no início, evitamos uma referência nula mais tarde quando tentarmos explodir uma fatia.

### Etapa 3: Recuperar o Primeiro Nó de Gráfico

A maioria dos exemplos assume um único gráfico, então vamos pegar o primeiro. Se houver vários gráficos, ajuste o índice conforme necessário.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Observação:** O cast para `Chart` é seguro depois de confirmarmos que um gráfico existe. Esse objeto nos dá acesso às séries, pontos de dados e configurações específicas do tipo de gráfico.

### Etapa 4: Explodir a Primeira Fatia de um Gráfico de Pizza

Agora a estrela do show — **como explodir a fatia da pizza**. Definiremos a propriedade `Exploded` do primeiro ponto de dados.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Por que isso funciona:** `Exploded` indica ao Word para puxar essa fatia para fora do centro, criando o clássico efeito “pizza explodida”. A propriedade é booleana, então definir como `true` resolve o problema.

### Etapa 5: Ajustar o Tamanho do Buraco do Donut (Se for um Gráfico Donut)

Se o seu gráfico for um donut, talvez queira **ajustar o tamanho do buraco do donut**. O tamanho do buraco é uma porcentagem do raio do gráfico.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **O que o número significa:** Um valor de `30` indica que o círculo interno ocupará 30 % do raio total, deixando um anel externo mais espesso.

### Etapa 6: Alterar Pontos de Dados do Gráfico (Opcional)

Às vezes é necessário **alterar pontos de dados do gráfico** — talvez você tenha atualizado os números subjacentes e queira que a visualização reflita isso.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Por que fazer isso:** Alterar o valor de um ponto de dados recalcula automaticamente as porcentagens das fatias, mantendo o gráfico preciso sem edição manual no Word.

### Etapa 7: Salvar o Documento Modificado

Por fim, grave as alterações no disco. Você pode sobrescrever o arquivo original ou criar um novo — como preferir.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Dica:** Use `SaveFormat.Docx` se precisar ser explícito, mas `Save(string)` detecta automaticamente o formato a partir da extensão do arquivo.

---

## Resultado Esperado

Ao abrir `FormattedChart.docx` no Microsoft Word, você deverá ver:

- A primeira fatia de um gráfico de pizza **explodida** para fora.
- Se o gráfico for um donut, o buraco central agora ocupa **30 %** do raio.
- Qualquer ponto de dado modificado reflete os novos valores que você definiu.

Abaixo está uma ilustração de como a fatia explodida se parece (imagem apenas para demonstração).

![Fatia de gráfico de pizza explodida criada com Aspose.Words em C#](exploded-pie-slice.png)

*Texto alternativo:* **fatia de gráfico de pizza explodida** mostrando um segmento afastado em um documento Word.

---

## Perguntas Frequentes & Casos de Borda

**E se o gráfico não for de pizza ou donut?**  
O código verifica `ChartType` antes de aplicar `Exploded` ou `HoleSize`. Para gráficos de barra, linha ou área essas propriedades simplesmente não existem, então a lógica as ignora com segurança.

**Posso explodir várias fatias?**  
Com certeza. Percorra `chart.PieChartData.Series[0].DataPoints` e defina `Exploded = true` em qualquer índice que desejar.

**Preciso me preocupar com formatos numéricos específicos de cultura?**  
Aspose.Words armazena valores numéricos como doubles, independente da localidade, então você está protegido contra problemas de vírgula vs ponto.

**E quanto a gráficos incorporados em cabeçalhos/rodapés?**  
Use `doc.GetChildNodes(NodeType.Chart, true)` para recuperar todos os gráficos, depois inspecione `ParentNode` de cada nó para ver onde ele está. A mesma lógica de explosão se aplica.

---

## Conclusão

Agora você tem uma solução completa, pronta para copiar e colar, de como **explodir a fatia de um gráfico de pizza** usando Aspose.Words em C#. Cobriram‑se todo o fluxo de trabalho — desde o carregamento do documento, obtenção do gráfico, explosão da fatia, **ajuste do tamanho do buraco do donut**, até **alteração de pontos de dados do gráfico** e, finalmente, a gravação do arquivo.

Sinta‑se à vontade para experimentar: tente explodir outra fatia, ajuste o tamanho do buraco para 45 %, ou atualize vários pontos de dados de uma vez. A API Aspose.Words torna esses ajustes simples, e as mudanças aparecem instantaneamente ao abrir o arquivo Word.

---

### O que vem a seguir?

- **Estilizar a fatia explodida** (alterar cor de preenchimento, borda ou adicionar rótulo de dados). Pesquise por “Aspose.Words chart formatting”.
- **Automatizar processamento em lote** de múltiplos documentos — percorrer uma pasta, explodir fatias e salvar novas versões.
- **Combinar com Aspose.Slides** se precisar do mesmo gráfico em uma apresentação PowerPoint.

Tem mais perguntas sobre manipulação de gráficos, ou quer aprofundar em outros tipos de gráfico? Deixe um comentário abaixo, e feliz codificação!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Inserir Gráfico de Colunas no Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Inserir um Gráfico de Colunas Simples no Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Inserir Gráfico de Área em Documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}