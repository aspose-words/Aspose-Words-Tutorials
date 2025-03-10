---
title: Ocultar eixo do gráfico em um documento do Word
linktitle: Ocultar eixo do gráfico em um documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como ocultar o eixo do gráfico em um documento do Word usando o Aspose.Words para .NET com nosso tutorial detalhado passo a passo.
weight: 10
url: /pt/net/programming-with-charts/hide-chart-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ocultar eixo do gráfico em um documento do Word

## Introdução

Criar documentos dinâmicos e visualmente atraentes do Word geralmente envolve incorporar tabelas e gráficos. Um cenário como esse pode exigir ocultar o eixo do gráfico para uma apresentação mais limpa. O Aspose.Words para .NET fornece uma API abrangente e fácil de usar para essas tarefas. Este tutorial o guiará pelas etapas para ocultar um eixo de gráfico em um documento do Word usando o Aspose.Words para .NET.

## Pré-requisitos

Antes de começarmos o tutorial, certifique-se de ter os seguintes pré-requisitos:

-  Aspose.Words para .NET: Você pode baixá-lo em[aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: qualquer IDE que suporte desenvolvimento .NET, como o Visual Studio.
- .NET Framework: certifique-se de ter o .NET Framework instalado na sua máquina.
- Conhecimento básico de C#: Familiaridade com a linguagem de programação C# será benéfica.

## Importar namespaces

Para começar a trabalhar com Aspose.Words para .NET, você precisa importar os namespaces necessários no seu projeto. Veja como você pode fazer isso:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Vamos dividir o processo em etapas simples e fáceis de seguir.

## Etapa 1: inicializar o documento e o DocumentBuilder

primeiro passo envolve criar um novo documento do Word e inicializar o objeto DocumentBuilder.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Nesta etapa, definimos o caminho onde o documento será salvo. Em seguida, criamos um novo`Document` objeto e um`DocumentBuilder` objeto para começar a construir nosso documento.

## Etapa 2: Insira um gráfico

 Em seguida, inseriremos um gráfico no documento usando o`DocumentBuilder` objeto.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 Aqui, inserimos um gráfico de colunas com dimensões especificadas. O`InsertChart` método retorna um`Shape` objeto que contém o gráfico.

## Etapa 3: Limpar séries existentes

Antes de adicionar novos dados ao gráfico, precisamos limpar todas as séries existentes.

```csharp
chart.Series.Clear();
```

Esta etapa garante que todos os dados padrão no gráfico sejam removidos, abrindo caminho para os novos dados que adicionaremos a seguir.

## Etapa 4: Adicionar dados de série

Agora, vamos adicionar nossa própria série de dados ao gráfico.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

Nesta etapa, adicionamos uma série intitulada "Aspose Series 1" com categorias e valores correspondentes.

## Etapa 5: Ocultar o eixo Y

 Para ocultar o eixo Y do gráfico, basta definir o`Hidden` propriedade do eixo Y para`true`.

```csharp
chart.AxisY.Hidden = true;
```

Esta linha de código oculta o eixo Y, tornando-o invisível no gráfico.

## Etapa 6: Salve o documento

Por fim, salve o documento no diretório especificado.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

Este comando salva o documento do Word com o gráfico no caminho especificado.

## Conclusão

Parabéns! Você aprendeu com sucesso como ocultar um eixo de gráfico em um documento do Word usando o Aspose.Words para .NET. Esta biblioteca poderosa facilita a manipulação de documentos do Word programaticamente. Seguindo estas etapas, você pode criar documentos personalizados e com aparência profissional com o mínimo de esforço.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma API poderosa para criar, editar, converter e manipular documentos do Word em aplicativos .NET.

### Posso ocultar os eixos X e Y em um gráfico?
 Sim, você pode ocultar ambos os eixos definindo o`Hidden` propriedade de ambos`AxisX` e`AxisY` para`true`.

### Existe uma versão de avaliação gratuita disponível para o Aspose.Words para .NET?
 Sim, você pode obter uma avaliação gratuita[aqui](https://releases.aspose.com/).

### Onde posso encontrar mais documentação?
 Você pode encontrar documentação detalhada no Aspose.Words para .NET[aqui](https://reference.aspose.com/words/net/).

### Como posso obter suporte para o Aspose.Words para .NET?
 Você pode obter suporte da comunidade Aspose[aqui](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
