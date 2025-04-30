---
"description": "Aprenda a personalizar rótulos de dados de gráficos usando o Aspose.Words para .NET em um guia passo a passo. Perfeito para desenvolvedores .NET."
"linktitle": "Personalizar rótulo de dados do gráfico"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Personalizar rótulo de dados do gráfico"
"url": "/pt/net/programming-with-charts/chart-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Personalizar rótulo de dados do gráfico

## Introdução

Deseja aprimorar seus aplicativos .NET com recursos dinâmicos e personalizados de processamento de documentos? O Aspose.Words para .NET pode ser a solução! Neste guia, vamos nos aprofundar na personalização de rótulos de dados de gráficos usando o Aspose.Words para .NET, uma biblioteca poderosa para criar, modificar e converter documentos do Word. Seja você um desenvolvedor experiente ou iniciante, este tutorial o guiará por cada etapa, garantindo que você entenda como utilizar esta ferramenta de forma eficaz.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1. Visual Studio: Instale o Visual Studio 2019 ou posterior.
2. .NET Framework: certifique-se de ter o .NET Framework 4.0 ou posterior.
3. Aspose.Words para .NET: Baixe e instale o Aspose.Words para .NET do [link para download](https://releases.aspose.com/words/net/).
4. Conhecimento básico de C#: familiaridade com programação em C# é essencial.
5. Uma licença válida: obtenha uma [licença temporária](https://purchase.aspose.com/temporary-license/) ou compre um no [link de compra](https://purchase.aspose.com/buy).

## Importar namespaces

Para começar, você precisa importar os namespaces necessários para o seu projeto C#. Esta etapa é crucial, pois garante que você tenha acesso a todas as classes e métodos fornecidos pelo Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## Etapa 1: inicializar o documento e o DocumentBuilder

Para criar e manipular documentos do Word, primeiro precisamos inicializar uma instância do `Document` classe e uma `DocumentBuilder` objeto.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Explicação

- Documento doc: Cria uma nova instância da classe Documento.
- Construtor DocumentBuilder: O DocumentBuilder auxilia na inserção de conteúdo no objeto Document.

## Etapa 2: inserir um gráfico

Em seguida, inseriremos um gráfico de barras no documento usando o `DocumentBuilder` objeto.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Explicação

- Forma forma: representa o gráfico como uma forma no documento.
- builder.InsertChart(ChartType.Bar, 432, 252): Insere um gráfico de barras com dimensões especificadas.

## Etapa 3: Acesse a série de gráficos

Para personalizar os rótulos de dados, primeiro precisamos acessar as séries no gráfico.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Explicação

- ChartSeries series0: Recupera a primeira série do gráfico, que iremos personalizar.

## Etapa 4: personalizar rótulos de dados

Os rótulos de dados podem ser personalizados para exibir diversas informações. Configuraremos os rótulos para mostrar a legenda, o nome da série e o valor, enquanto ocultaremos o nome da categoria e a porcentagem.

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### Explicação

- Rótulos ChartDataLabelCollection: acessa os rótulos de dados da série.
- labels.ShowLegendKey: Exibe a legenda.
- labels.ShowLeaderLines: Mostra linhas de liderança para rótulos de dados posicionados bem fora dos pontos de dados.
- labels.ShowCategoryName: Oculta o nome da categoria.
- labels.ShowPercentage: Oculta o valor percentual.
- labels.ShowSeriesName: Exibe o nome da série.
- labels.ShowValue: Exibe o valor dos pontos de dados.
- labels.Separator: define o separador para os rótulos de dados.

## Etapa 5: Salve o documento

Por fim, salve o documento no diretório especificado.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Explicação

- doc.Save: Salva o documento com o nome especificado no diretório fornecido.

## Conclusão

Parabéns! Você personalizou com sucesso os rótulos de dados do gráfico usando o Aspose.Words para .NET. Esta biblioteca oferece uma solução robusta para o processamento programático de documentos do Word, facilitando a criação de aplicativos de processamento de documentos sofisticados e dinâmicos para desenvolvedores. Mergulhe no [documentação](https://reference.aspose.com/words/net/) para explorar mais recursos e capacidades.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma poderosa biblioteca de processamento de documentos que permite aos desenvolvedores criar, modificar e converter documentos do Word programaticamente.

### Como instalo o Aspose.Words para .NET?
Você pode baixá-lo e instalá-lo a partir do [link para download](https://releases.aspose.com/words/net/). Siga as instruções de instalação fornecidas.

### Posso testar o Aspose.Words para .NET gratuitamente?
Sim, você pode obter um [teste gratuito](https://releases.aspose.com/) ou um [licença temporária](https://purchase.aspose.com/temporary-license/) para avaliar o produto.

### Aspose.Words para .NET é compatível com o .NET Core?
Sim, o Aspose.Words para .NET é compatível com .NET Core, .NET Standard e .NET Framework.

### Onde posso obter suporte para o Aspose.Words para .NET?
Você pode visitar o [fórum de suporte](https://forum.aspose.com/c/words/8) para obter ajuda e assistência da comunidade e especialistas da Aspose.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}