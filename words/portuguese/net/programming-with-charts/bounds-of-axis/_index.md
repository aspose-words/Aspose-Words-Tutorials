---
title: Limites do eixo em um gráfico
linktitle: Limites do eixo em um gráfico
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a definir os limites de um eixo em um gráfico usando o Aspose.Words para .NET controlando o intervalo de valores exibidos no eixo.
weight: 10
url: /pt/net/programming-with-charts/bounds-of-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Limites do eixo em um gráfico

## Introdução

Você está procurando criar documentos profissionais com gráficos em .NET? Você está no lugar certo! Este guia o guiará pelo processo de uso do Aspose.Words para .NET para definir os limites do eixo em um gráfico. Vamos detalhar cada etapa para garantir que você possa acompanhar facilmente, mesmo se for novo na biblioteca. Então, vamos mergulhar e começar!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

-  Aspose.Words para .NET: Você pode[download](https://releases.aspose.com/words/net/) a versão mais recente ou use um[teste gratuito](https://releases.aspose.com/).
- .NET Framework: certifique-se de ter o .NET instalado no seu sistema.
- IDE: Um ambiente de desenvolvimento como o Visual Studio.

Depois que tudo estiver pronto, podemos passar para os próximos passos.

## Importar namespaces

Para começar, você precisará importar os namespaces necessários. Eles permitirão que você acesse a biblioteca Aspose.Words e seus recursos de gráficos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Etapa 1: configure seu diretório de documentos

Primeiro, você precisa configurar o diretório onde seu documento será salvo. Este é um passo simples, mas crucial para organizar seus arquivos.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Crie um novo documento

Em seguida, crie um novo objeto de documento. Este documento servirá como o contêiner para seu gráfico.

```csharp
Document doc = new Document();
```

## Etapa 3: Inicializar o Document Builder

A classe DocumentBuilder fornece uma maneira rápida e fácil de construir documentos. Inicialize-a com seu documento.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 4: Insira um gráfico

Agora, é hora de inserir um gráfico no seu documento. Neste exemplo, usaremos um gráfico de colunas.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Etapa 5: Limpar séries existentes

Para garantir que você comece do zero, limpe qualquer série existente do gráfico.

```csharp
chart.Series.Clear();
```

## Etapa 6: Adicionar dados ao gráfico

Aqui, adicionamos dados ao gráfico. Isso inclui especificar o nome da série e os pontos de dados.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

## Etapa 7: Definir limites do eixo

Definir os limites do eixo Y garante que seu gráfico seja dimensionado corretamente.

```csharp
chart.AxisY.Scaling.Minimum = new AxisBound(0);
chart.AxisY.Scaling.Maximum = new AxisBound(6);
```

## Etapa 8: Salve o documento

Por fim, salve seu documento no diretório especificado.

```csharp
doc.Save(dataDir + "WorkingWithCharts.BoundsOfAxis.docx");
```

é isso! Você criou com sucesso um documento com um gráfico usando Aspose.Words para .NET. 

## Conclusão

Usando o Aspose.Words para .NET, você pode facilmente criar e manipular gráficos em seus documentos. Este guia passo a passo mostrou como definir os limites do eixo em um gráfico, tornando sua apresentação de dados mais precisa e profissional. Não importa se você está gerando relatórios, apresentações ou qualquer outro documento, o Aspose.Words fornece as ferramentas de que você precisa.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca que permite criar, modificar e converter documentos do Word programaticamente usando o .NET framework.

### Como configuro o Aspose.Words para .NET?
 Você pode baixá-lo em[aqui](https://releases.aspose.com/words/net/) siga as instruções de instalação fornecidas.

### Posso usar o Aspose.Words gratuitamente?
 Sim, você pode usar um[teste gratuito](https://releases.aspose.com/) ou pegue um[licença temporária](https://purchase.aspose.com/temporary-license/).

### Onde posso encontrar documentação do Aspose.Words para .NET?
 Documentação detalhada está disponível[aqui](https://reference.aspose.com/words/net/).

### Como posso obter suporte para o Aspose.Words?
 Você pode visitar o[fórum de suporte](https://forum.aspose.com/c/words/8) para obter assistência.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
