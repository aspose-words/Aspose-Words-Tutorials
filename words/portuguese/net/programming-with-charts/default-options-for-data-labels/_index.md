---
title: Definir opções padrão para rótulos de dados em um gráfico
linktitle: Definir opções padrão para rótulos de dados em um gráfico
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como definir opções padrão para rótulos de dados em um gráfico usando Aspose.Words para .NET. Siga nosso guia passo a passo para criar e personalizar gráficos sem esforço.
weight: 10
url: /pt/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir opções padrão para rótulos de dados em um gráfico

## Introdução

Olá! Você está animado para mergulhar no mundo da automação de documentos? Hoje, vamos explorar como usar o Aspose.Words para .NET para criar documentos impressionantes programaticamente. O Aspose.Words é uma biblioteca poderosa que permite manipular documentos do Word com facilidade e, neste tutorial, vamos nos concentrar em definir opções padrão para rótulos de dados em um gráfico. Seja você um desenvolvedor experiente ou um novato, este guia o guiará por cada etapa para que você comece a trabalhar rapidamente.

## Pré-requisitos

Antes de começarmos, vamos garantir que você tenha tudo o que precisa para seguir este tutorial. Aqui está uma lista de verificação rápida:

- Visual Studio ou qualquer outro IDE compatível com .NET: É aqui que você escreverá e executará seu código.
-  Aspose.Words para .NET: Você pode[baixe a última versão](https://releases.aspose.com/words/net/) e instale-o em seu projeto.
- Conhecimento básico de programação em C#: embora este guia seja adequado para iniciantes, um pouco de familiaridade com C# será útil.
- .NET Framework instalado: certifique-se de ter o .NET Framework configurado na sua máquina.
-  Uma licença temporária para Aspose.Words: Obtenha uma[aqui](https://purchase.aspose.com/temporary-license/) para desbloquear a funcionalidade completa.

Depois de resolver esses pré-requisitos, estamos prontos para começar!

## Importar namespaces

Primeiro, vamos configurar nosso projeto e importar os namespaces necessários. Esses namespaces são cruciais para acessar a funcionalidade Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Etapa 1: Crie um novo documento


 A jornada começa com a criação de um novo documento e a inicialização de um`DocumentBuilder` . O`DocumentBuilder` A classe fornece um conjunto de métodos para manipular o conteúdo do documento facilmente.

```csharp
// Caminho para o diretório do seu documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Criar um novo documento
Document doc = new Document();

// Inicializar DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Explicação

 Nesta etapa, configuramos o documento e o construtor que usaremos para inserir e formatar nosso conteúdo. O`dataDir` variável contém o caminho onde salvaremos nosso documento final.

## Etapa 2: Insira um gráfico

 Em seguida, adicionaremos um gráfico de pizza ao nosso documento. O`InsertChart` método do`DocumentBuilder` a aula torna isso super fácil.

```csharp
// Inserir um gráfico de pizza
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Acesse o objeto gráfico
Chart chart = shape.Chart;
```

### Explicação

Aqui, estamos inserindo um gráfico de pizza em nosso documento. O`InsertChart` O método requer o tipo de gráfico, largura e altura como parâmetros. Após inserir o gráfico, acessamos o objeto gráfico para manipulá-lo ainda mais.

## Etapa 3: Personalize a série de gráficos

Agora, limparemos qualquer série existente no gráfico e adicionaremos nossa série personalizada. Esta série representará nossos pontos de dados.

```csharp
// Limpar séries de gráficos existentes
chart.Series.Clear();

// Adicionar nova série ao gráfico
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Explicação

Nesta etapa, estamos nos certificando de que nosso gráfico esteja vazio limpando qualquer série pré-existente. Então, adicionamos uma nova série com categorias e valores personalizados, que serão exibidos em nosso gráfico de pizza.

## Etapa 4: definir opções padrão para rótulos de dados

Os rótulos de dados são cruciais para tornar seu gráfico informativo. Definiremos opções para mostrar porcentagem, valor e personalizar o separador.

```csharp
// Acesse a coleção de rótulos de dados
ChartDataLabelCollection labels = series.DataLabels;

// Definir opções de rótulo de dados
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Explicação

 Aqui, estamos acessando o`DataLabels`propriedade da nossa série para personalizar a aparência e as informações exibidas em cada rótulo de dados. Escolhemos mostrar a porcentagem e o valor, ocultar linhas de liderança e definir um separador personalizado.

## Etapa 5: Salve o documento

Por fim, salvaremos nosso documento no diretório especificado. Este passo garante que todas as nossas alterações sejam gravadas em um arquivo.

```csharp
// Salvar o documento
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Explicação

 Nesta última etapa, salvamos nosso documento usando o`Save` método. O documento será salvo no diretório especificado por`dataDir`, com o nome "WorkingWithCharts.DefaultOptionsForDataLabels.docx".

## Conclusão

E aí está! Você criou com sucesso um documento do Word com um gráfico de pizza personalizado usando o Aspose.Words para .NET. Esta biblioteca poderosa facilita a automatização da criação e manipulação de documentos, economizando tempo e esforço. Não importa se você está gerando relatórios, faturas ou qualquer outro tipo de documento, o Aspose.Words tem tudo o que você precisa.

 Sinta-se à vontade para explorar o[Documentação do Aspose.Words](https://reference.aspose.com/words/net/) para mais recursos e exemplos. Boa codificação!

## Perguntas frequentes

### Posso usar o Aspose.Words gratuitamente?
Você pode usar o Aspose.Words gratuitamente com um[licença temporária](https://purchase.aspose.com/temporary-license/) ou explore seus recursos usando o[teste gratuito](https://releases.aspose.com/).

### Como obtenho suporte para o Aspose.Words?
 Você pode obter suporte através do[Fórum de suporte Aspose.Words](https://forum.aspose.com/c/words/8).

### Posso adicionar outros tipos de gráficos?
 Sim, o Aspose.Words suporta vários tipos de gráficos, como gráficos de barras, linhas e colunas. Verifique o[documentação](https://reference.aspose.com/words/net/) para mais detalhes.

### O Aspose.Words é compatível com o .NET Core?
 Sim, Aspose.Words é compatível com .NET Core. Você pode encontrar mais informações no[documentação](https://reference.aspose.com/words/net/).

### Como posso comprar uma licença para o Aspose.Words?
 Você pode comprar uma licença do[Loja Aspose](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
