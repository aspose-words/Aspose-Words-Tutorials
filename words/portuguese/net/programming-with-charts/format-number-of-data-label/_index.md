---
"description": "Aprenda a formatar rótulos de dados em gráficos usando o Aspose.Words para .NET com este guia passo a passo. Aprimore seus documentos do Word sem esforço."
"linktitle": "Formato Número de Rótulo de Dados em um Gráfico"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Formato Número de Rótulo de Dados em um Gráfico"
"url": "/pt/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formato Número de Rótulo de Dados em um Gráfico

## Introdução

A criação de documentos envolventes e informativos geralmente envolve a inclusão de gráficos com rótulos de dados bem formatados. Se você é um desenvolvedor .NET e busca aprimorar seus documentos do Word com gráficos sofisticados, o Aspose.Words para .NET é uma biblioteca fantástica para ajudar você a conseguir isso. Este tutorial guiará você pelo processo de formatação de rótulos numéricos em um gráfico usando o Aspose.Words para .NET, passo a passo.

## Pré-requisitos

Antes de mergulhar no código, há alguns pré-requisitos que você precisa ter em mente:

- Aspose.Words para .NET: Certifique-se de ter a biblioteca Aspose.Words para .NET instalada. Se ainda não a instalou, você pode [baixe aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: Você deve ter um ambiente de desenvolvimento .NET configurado. O Visual Studio é altamente recomendado.
- Conhecimento básico de C#: familiaridade com programação em C# é essencial, pois este tutorial envolve escrever e entender código C#.
- Licença temporária: Para usar o Aspose.Words sem quaisquer limitações, você pode obter uma [licença temporária](https://purchase.aspose.com/temporary-license/).

Agora, vamos mergulhar no processo passo a passo de formatação de rótulos numéricos em um gráfico.

## Importar namespaces

Antes de mais nada, precisamos importar os namespaces necessários para trabalhar com o Aspose.Words para .NET. Adicione as seguintes linhas no início do seu arquivo C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Etapa 1: configure seu diretório de documentos

Antes de começar a manipular seu documento do Word, você precisa especificar o diretório onde o documento será salvo. Isso é essencial para a operação de salvamento posterior.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Substituir `"YOUR DOCUMENT DIRECTORY"` com o caminho real para o diretório do seu documento.

## Etapa 2: Inicializar o documento e o DocumentBuilder

O próximo passo é inicializar um novo `Document` e um `DocumentBuilder`. O `DocumentBuilder` é uma classe auxiliar que nos permite construir o conteúdo do documento.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 3: Insira um gráfico no documento

Agora, vamos inserir um gráfico no documento usando o `DocumentBuilder`. Neste tutorial, usaremos um gráfico de linhas como exemplo.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Aqui, inserimos um gráfico de linhas com largura e altura específicas e definimos o título do gráfico.

## Etapa 4: limpar séries padrão e adicionar novas séries

Por padrão, o gráfico terá algumas séries pré-geradas. Precisamos limpá-las e adicionar nossas próprias séries com pontos de dados específicos.

```csharp
// Excluir série gerada padrão.
chart.Series.Clear();

// Adicione novas séries com pontos de dados personalizados.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Etapa 5: Habilitar rótulos de dados

Para exibir os rótulos de dados no gráfico, precisamos habilitá-los para nossa série.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Etapa 6: Formatar rótulos de dados

O foco deste tutorial é a formatação dos rótulos de dados. Podemos aplicar diferentes formatos numéricos a cada rótulo de dados individualmente.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Formato de moeda
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Formato de data
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Formato percentual
```

Além disso, você pode vincular o formato de um rótulo de dados a uma célula de origem. Quando vinculado, o `NumberFormat` será redefinido para geral e herdado da célula de origem.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Etapa 7: Salve o documento

Por fim, salve o documento no diretório especificado.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Isso salva seu documento com o nome especificado e garante que seu gráfico com rótulos de dados formatados seja preservado.

## Conclusão

Formatar rótulos de dados em um gráfico usando o Aspose.Words para .NET pode melhorar significativamente a legibilidade e o profissionalismo dos seus documentos do Word. Seguindo este guia passo a passo, você agora poderá criar um gráfico, adicionar séries de dados e formatar os rótulos de dados de acordo com suas necessidades. O Aspose.Words para .NET é uma ferramenta poderosa que permite ampla personalização e automação de documentos do Word, tornando-se um recurso inestimável para desenvolvedores .NET.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca poderosa para criar, manipular e converter documentos do Word programaticamente usando C#.

### Posso formatar outros tipos de gráficos com o Aspose.Words para .NET?
Sim, o Aspose.Words para .NET suporta uma variedade de tipos de gráficos, incluindo barras, colunas, pizza e muito mais.

### Como obtenho uma licença temporária para o Aspose.Words para .NET?
Você pode obter uma licença temporária [aqui](https://purchase.aspose.com/temporary-license/).

### É possível vincular rótulos de dados a células de origem no Excel?
Sim, você pode vincular rótulos de dados às células de origem, permitindo que o formato numérico seja herdado da célula de origem.

### Onde posso encontrar documentação mais detalhada do Aspose.Words para .NET?
Você pode encontrar documentação abrangente [aqui](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}