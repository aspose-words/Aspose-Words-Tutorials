---
"description": "Aprenda como adicionar valores de data e hora ao eixo de um gráfico usando o Aspose.Words para .NET neste guia passo a passo abrangente."
"linktitle": "Adicionar valores de data e hora ao eixo de um gráfico"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Adicionar valores de data e hora ao eixo de um gráfico"
"url": "/pt/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar valores de data e hora ao eixo de um gráfico

## Introdução

Criar gráficos em documentos pode ser uma maneira poderosa de visualizar dados. Ao lidar com dados de séries temporais, adicionar valores de data e hora ao eixo de um gráfico é crucial para maior clareza. Neste tutorial, mostraremos o processo de adição de valores de data e hora ao eixo de um gráfico usando o Aspose.Words para .NET. Este guia passo a passo ajudará você a configurar seu ambiente, escrever o código e entender cada parte do processo. Vamos lá!

## Pré-requisitos

Antes de começar, certifique-se de que você tenha os seguintes pré-requisitos:

1. Visual Studio ou qualquer IDE .NET: você precisa de um ambiente de desenvolvimento para escrever e executar seu código .NET.
2. Aspose.Words para .NET: Você deve ter a biblioteca Aspose.Words para .NET instalada. Você pode baixá-la em [aqui](https://releases.aspose.com/words/net/).
3. Conhecimento básico de C#: Este tutorial pressupõe que você tenha um conhecimento básico de programação em C#.
4. Uma licença Aspose válida: Você pode obter uma licença temporária em [aqui](https://purchase.aspose.com/temporary-license/).

## Importar namespaces

Para começar, certifique-se de ter os namespaces necessários importados para o seu projeto. Esta etapa é crucial para acessar as classes e métodos do Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Etapa 1: configure seu diretório de documentos

Primeiro, você precisa definir o diretório onde seu documento será salvo. Isso é importante para organizar seus arquivos e garantir que seu código seja executado corretamente.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Criar um novo documento e DocumentBuilder

Em seguida, crie uma nova instância do `Document` classe e uma `DocumentBuilder` objeto. Esses objetos ajudarão você a construir e manipular seu documento.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 3: Insira um gráfico no documento

Agora, insira um gráfico em seu documento usando o `DocumentBuilder` objeto. Neste exemplo, estamos usando um gráfico de colunas, mas você também pode escolher outros tipos.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Etapa 4: Limpar séries existentes

Limpe todas as séries existentes no gráfico para garantir que você esteja começando do zero. Esta etapa é essencial para dados personalizados.

```csharp
chart.Series.Clear();
```

## Etapa 5: adicionar valores de data e hora à série

Adicione seus valores de data e hora à série do gráfico. Esta etapa envolve a criação de matrizes para datas e valores correspondentes.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Etapa 6: Configurar o eixo X

Defina a escala e as marcas de escala para o eixo X. Isso garante que suas datas sejam exibidas corretamente e em intervalos apropriados.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Etapa 7: Salve o documento

Por fim, salve o documento no diretório especificado. Esta etapa conclui o processo, e seu documento deverá conter um gráfico com valores de data e hora no eixo X.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Conclusão

Adicionar valores de data e hora ao eixo de um gráfico em um documento é um processo simples com o Aspose.Words para .NET. Seguindo os passos descritos neste tutorial, você pode criar gráficos claros e informativos que visualizam dados de séries temporais de forma eficaz. Seja para preparar relatórios, apresentações ou qualquer documento que exija representação detalhada de dados, o Aspose.Words oferece as ferramentas necessárias para o sucesso.

## Perguntas frequentes

### Posso usar outros tipos de gráficos com o Aspose.Words para .NET?

Sim, o Aspose.Words suporta vários tipos de gráficos, incluindo linhas, barras, pizza e muito mais.

### Como posso personalizar a aparência do meu gráfico?

Você pode personalizar a aparência acessando as propriedades do gráfico e definindo estilos, cores e muito mais.

### É possível adicionar várias séries a um gráfico?

Com certeza! Você pode adicionar várias séries ao seu gráfico chamando o `Series.Add` método várias vezes com dados diferentes.

### E se eu precisar atualizar os dados do gráfico dinamicamente?

Você pode atualizar os dados do gráfico dinamicamente manipulando as propriedades da série e do eixo programaticamente com base em suas necessidades.

### Onde posso encontrar documentação mais detalhada do Aspose.Words para .NET?

Você pode encontrar documentação mais detalhada [aqui](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}