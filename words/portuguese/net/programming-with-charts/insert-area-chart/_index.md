---
title: Inserir gráfico de área em um documento do Word
linktitle: Inserir gráfico de área em um documento do Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como inserir um gráfico de área em um documento usando o Aspose.Words para .NET. Adicione dados de série e salve o documento com o gráfico.
weight: 10
url: /pt/net/programming-with-charts/insert-area-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir gráfico de área em um documento do Word

## Introdução

Bem-vindo a este guia passo a passo sobre como inserir um gráfico de área em um documento do Word usando o Aspose.Words para .NET. Seja você um desenvolvedor experiente ou apenas começando, este tutorial o guiará por tudo o que você precisa saber para criar gráficos de área impressionantes e informativos em seus documentos do Word. Abordaremos os pré-requisitos, mostraremos como importar os namespaces necessários e o guiaremos por cada etapa do processo com instruções claras e fáceis de seguir.

## Pré-requisitos

Antes de começarmos, vamos garantir que você tenha tudo o que precisa para começar:

1.  Aspose.Words para .NET: Certifique-se de ter o Aspose.Words para .NET instalado. Você pode baixá-lo[aqui](https://releases.aspose.com/words/net/).
2. .NET Framework: certifique-se de ter o .NET Framework instalado na sua máquina.
3. IDE: Um ambiente de desenvolvimento integrado (IDE) como o Visual Studio para escrever e executar seu código.
4. Conhecimento básico de C#: Um conhecimento básico de programação em C# será útil.

Depois de cumprir esses pré-requisitos, você estará pronto para começar a criar belos gráficos de área em seus documentos do Word.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Esses namespaces fornecem as classes e métodos necessários para trabalhar com documentos e gráficos do Word no Aspose.Words para .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

Agora que importamos os namespaces essenciais, vamos criar nosso documento e inserir um gráfico de área passo a passo.

## Etapa 1: Crie um novo documento do Word

Vamos começar criando um novo documento do Word. Esta será a base onde inseriremos nosso gráfico de área.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

 Nesta etapa, inicializamos um novo`Document` objeto que representa nosso documento do Word.

## Etapa 2: use o DocumentBuilder para inserir um gráfico

 Em seguida, usaremos o`DocumentBuilder` classe para inserir um gráfico de área em nosso documento.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

 Aqui, criamos um`DocumentBuilder` objeto e usá-lo para inserir um gráfico de área de dimensões específicas (432x252) em nosso documento.

## Etapa 3: Acesse o objeto Chart

 Após inserir o gráfico, precisamos acessar o`Chart` objeto para personalizar nosso gráfico de área.

```csharp
Chart chart = shape.Chart;
```

 Esta linha de código recupera o`Chart` objeto da forma que acabamos de inserir.

## Etapa 4: Adicionar dados de série ao gráfico

Agora, é hora de adicionar alguns dados ao nosso gráfico. Adicionaremos uma série com datas e valores correspondentes.

```csharp
chart.Series.Add("Aspose Series 1", new []
{
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)
}, 
new double[] { 32, 32, 28, 12, 15 });
```

Nesta etapa, adicionamos uma série chamada "Aspose Series 1" com um conjunto de datas e valores correspondentes.

## Etapa 5: Salve o documento

Por fim, salvaremos nosso documento com o gráfico de área inserido.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

Esta linha de código salva o documento no diretório especificado com o nome de arquivo fornecido.

## Conclusão

Parabéns! Você inseriu com sucesso um gráfico de área em um documento do Word usando o Aspose.Words para .NET. Este guia o levou por cada etapa, desde a configuração do seu ambiente até o salvamento do documento final. Com o Aspose.Words para .NET, você pode criar uma grande variedade de gráficos e outros elementos complexos em seus documentos do Word, tornando seus relatórios e apresentações mais dinâmicos e informativos.

## Perguntas frequentes

### Posso usar o Aspose.Words para .NET com outras linguagens .NET?
Sim, o Aspose.Words para .NET oferece suporte a outras linguagens .NET, como VB.NET.

### É possível personalizar a aparência do gráfico?
Absolutamente! O Aspose.Words for .NET fornece opções extensivas para personalizar a aparência dos seus gráficos.

### Posso adicionar vários gráficos a um único documento do Word?
Sim, você pode inserir quantos gráficos precisar em um único documento do Word.

### O Aspose.Words para .NET oferece suporte a outros tipos de gráficos?
Sim, o Aspose.Words para .NET suporta vários tipos de gráficos, incluindo barras, linhas, pizza e muito mais.

### Onde posso obter uma licença temporária para o Aspose.Words para .NET?
 Você pode obter uma licença temporária em[aqui](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
