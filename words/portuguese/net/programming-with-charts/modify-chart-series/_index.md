---
title: Atualizar Dados de Séries de Gráfico em um Documento Word Usando Aspose.Words for .NET
weight: 610
limit:
description: Aprenda a modificar os pontos de dados das séries de um gráfico em um documento Word e atualizar o gráfico usando Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a modificar os pontos de dados das séries de um gráfico em
    um documento Word e atualizar o gráfico usando Aspose.Words for .NET.
  headline: Atualizar Dados de Séries de Gráfico em um Documento Word Usando Aspose.Words
    for .NET
  type: TechArticle
- description: Aprenda a modificar os pontos de dados das séries de um gráfico em
    um documento Word e atualizar o gráfico usando Aspose.Words for .NET.
  name: Atualizar Dados de Séries de Gráfico em um Documento Word Usando Aspose.Words
    for .NET
  steps:
  - name: Crie um novo Document, insira um gráfico de colunas com um DocumentBuilder
      e salve-o como o arquivo inicial.
    text: Crie um novo Document, insira um gráfico de colunas com um DocumentBuilder
      e salve-o como o arquivo inicial.
  - name: Abra o arquivo salvo e localize a forma de gráfico para obter o objeto Chart
      existente.
    text: Abra o arquivo salvo e localize a forma de gráfico para obter o objeto Chart
      existente.
  - name: Limpe os valores da primeira série e adicione novos pontos, depois ajuste
      a segunda série removendo seu primeiro ponto e adicionando um novo.
    text: Limpe os valores da primeira série e adicione novos pontos, depois ajuste
      a segunda série removendo seu primeiro ponto e adicionando um novo.
  - name: Salve o documento modificado em um novo arquivo contendo o gráfico atualizado.
    text: Salve o documento modificado em um novo arquivo contendo o gráfico atualizado.
  type: HowTo
- questions:
  - answer: Use `document.GetChildNodes(NodeType.Shape, true)` para obter todas as
      formas, depois filtre com `s.HasChart` e escolha a primeira (ou a que você precisar)
      – isso evita selecionar imagens ou caixas de texto não relacionadas.
    question: Como posso localizar de forma confiável a forma de gráfico em um documento
      que pode conter outras formas?
  - answer: '`ClearValues()` remove os pontos de dados existentes; sem ele, os novos
      pontos são acrescentados aos antigos, o que pode gerar categorias duplicadas
      ou totais incorretos.'
    question: Por que preciso chamar `ClearValues()` antes de adicionar novos pontos
      a uma série?
  - answer: Use `FromString` quando as categorias do eixo X do gráfico são textuais
      (por exemplo, "Group A"), e `FromDouble` quando o eixo espera valores numéricos,
      como datas ou medições.
    question: Quando devo usar `ChartXValue.FromString` em vez de `ChartXValue.FromDouble`
      para os valores do eixo X?
  - answer: Tentar acessar uma série inexistente lança uma `ArgumentOutOfRangeException`;
      sempre verifique `existingChart.Series.Count` antes de referenciar um índice
      específico.
    question: O que acontece se o gráfico tiver apenas uma série e eu tentar acessar
      `existingChart.Series[1]`?
  - answer: Salvar `openedDoc` é suficiente porque ele é a instância do documento
      que contém o gráfico modificado; o `document` original foi usado apenas para
      criar o arquivo inicial.
    question: Preciso salvar novamente o `document` original após modificar o gráfico,
      ou salvar `openedDoc` é suficiente?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Editar Dados de Séries de Gráfico no Word
og_description: Guia passo a passo para alterar os valores das séries de um gráfico em um arquivo Word com Aspose.Words for .NET.
og_image_alt: Guia que mostra um documento Word com um gráfico de colunas antes e depois de atualizar os dados das séries usando Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Atualizar Dados de Séries de Gráfico em um Documento Word Usando Aspose.Words
Este tutorial mostra como criar um documento Word contendo um gráfico de colunas, depois reabrir o arquivo, recuperar as séries de gráfico existentes, modificar seus pontos de dados e salvar o documento para que o gráfico exiba os novos valores. Siga o código passo a passo para ver como é simples ajustar programaticamente os dados do gráfico com Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Como posso localizar de forma confiável a forma de gráfico em um documento que pode conter outras formas?**  
A: Use `document.GetChildNodes(NodeType.Shape, true)` para obter todas as formas, depois filtre com `s.HasChart` e escolha a primeira (ou a que você precisar) – isso evita selecionar imagens ou caixas de texto não relacionadas.

**Q: Por que preciso chamar `ClearValues()` antes de adicionar novos pontos a uma série?**  
A: `ClearValues()` remove os pontos de dados existentes; sem ele, os novos pontos são acrescentados aos antigos, o que pode gerar categorias duplicadas ou totais incorretos.

**Q: Quando devo usar `ChartXValue.FromString` em vez de `ChartXValue.FromDouble` para os valores do eixo X?**  
A: Use `FromString` quando as categorias do eixo X do gráfico são textuais (por exemplo, "Group A"), e `FromDouble` quando o eixo espera valores numéricos, como datas ou medições.

**Q: O que acontece se o gráfico tiver apenas uma série e eu tentar acessar `existingChart.Series[1]`?**  
A: Tentar acessar uma série inexistente lança uma `ArgumentOutOfRangeException`; sempre verifique `existingChart.Series.Count` antes de referenciar um índice específico.

**Q: Preciso salvar novamente o `document` original após modificar o gráfico, ou salvar `openedDoc` é suficiente?**  
A: Salvar `openedDoc` é suficiente porque ele é a instância do documento que contém o gráfico modificado; o `document` original foi usado apenas para criar o arquivo inicial.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}