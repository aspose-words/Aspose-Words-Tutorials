---
"description": "Aprenda a inserir um gráfico de dispersão no Word com o Aspose.Words para .NET. Etapas simples para integrar representações visuais de dados aos seus documentos."
"linktitle": "Inserir gráfico de dispersão em documento do Word"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Inserir gráfico de dispersão em documento do Word"
"url": "/pt/net/programming-with-charts/insert-scatter-chart/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir gráfico de dispersão em documento do Word

## Introdução

Neste tutorial, você aprenderá a utilizar o Aspose.Words para .NET para inserir um gráfico de dispersão em seu documento do Word. Gráficos de dispersão são ferramentas visuais poderosas que podem exibir pontos de dados com base em duas variáveis, tornando seus documentos mais envolventes e informativos.

## Pré-requisitos

Antes de começarmos a criar gráficos de dispersão com o Aspose.Words para .NET, certifique-se de ter os seguintes pré-requisitos:

1. Instalação do Aspose.Words para .NET: Baixe e instale o Aspose.Words para .NET em [aqui](https://releases.aspose.com/words/net/).
   
2. Conhecimento básico de C#: familiaridade com a linguagem de programação C# e o .NET framework será benéfico.

## Importar namespaces

Para começar, você precisa importar os namespaces necessários no seu projeto C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Agora, vamos detalhar o processo de inserção de um gráfico de dispersão em seu documento do Word usando o Aspose.Words para .NET:

## Etapa 1: inicializar o documento e o DocumentBuilder

Primeiro, inicialize uma nova instância do `Document` classe e `DocumentBuilder` classe para começar a construir seu documento.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: Insira o gráfico de dispersão

Use o `InsertChart` método do `DocumentBuilder` classe para inserir um gráfico de dispersão no documento.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Etapa 3: adicionar séries de dados ao gráfico

Agora, adicione séries de dados ao seu gráfico de dispersão. Este exemplo demonstra como adicionar uma série com pontos de dados específicos.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Etapa 4: Salve o documento

Por fim, salve o documento modificado no local desejado usando o `Save` método do `Document` aula.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Conclusão

Parabéns! Você aprendeu com sucesso a inserir um gráfico de dispersão em seu documento do Word usando o Aspose.Words para .NET. Gráficos de dispersão são excelentes ferramentas para visualizar relacionamentos de dados e, com o Aspose.Words, você pode integrá-los facilmente aos seus documentos para aumentar a clareza e a compreensão.

## Perguntas frequentes

### Posso personalizar a aparência do gráfico de dispersão usando o Aspose.Words?
Sim, o Aspose.Words permite ampla personalização de propriedades de gráficos, como cores, eixos e rótulos.

### Aspose.Words é compatível com diferentes versões do Microsoft Word?
O Aspose.Words suporta várias versões do Microsoft Word, garantindo compatibilidade entre plataformas.

### O Aspose.Words oferece suporte para outros tipos de gráficos?
Sim, o Aspose.Words suporta uma ampla variedade de tipos de gráficos, incluindo gráficos de barras, gráficos de linhas e gráficos de pizza.

### Posso atualizar dinamicamente os dados no gráfico de dispersão programadamente?
Com certeza, você pode atualizar dados do gráfico dinamicamente usando chamadas de API do Aspose.Words.

### Onde posso obter mais assistência ou suporte para o Aspose.Words?
Para obter mais assistência, visite o [Fórum de suporte Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}