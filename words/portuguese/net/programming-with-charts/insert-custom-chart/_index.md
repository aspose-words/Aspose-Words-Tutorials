---
title: Inserir Gráfico de Colunas Personalizado em Documento Word Usando Aspose.Words for .NET
weight: 310
limit:
description: Crie um arquivo Word, insira um gráfico de colunas, substitua seus dados por uma matriz personalizada, adicione um título e salve—tudo com Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Crie um arquivo Word, insira um gráfico de colunas, substitua seus
    dados por uma matriz personalizada, adicione um título e salve—tudo com Aspose.Words
    for .NET.
  headline: Inserir Gráfico de Colunas Personalizado em Documento Word Usando Aspose.Words
    for .NET
  type: TechArticle
- description: Crie um arquivo Word, insira um gráfico de colunas, substitua seus
    dados por uma matriz personalizada, adicione um título e salve—tudo com Aspose.Words
    for .NET.
  name: Inserir Gráfico de Colunas Personalizado em Documento Word Usando Aspose.Words
    for .NET
  steps:
  - name: Crie um novo Document e um DocumentBuilder associado a ele.
    text: Crie um novo Document e um DocumentBuilder associado a ele.
  - name: Insira um gráfico de colunas com tamanho de 432x252 pontos no documento
      e obtenha seu objeto Chart.
    text: Insira um gráfico de colunas com tamanho de 432x252 pontos no documento
      e obtenha seu objeto Chart.
  - name: Remova a série de exemplo gerada automaticamente do gráfico.
    text: Remova a série de exemplo gerada automaticamente do gráfico.
  - name: Defina os rótulos de categoria do eixo X e as entradas da legenda para cada
      série.
    text: Defina os rótulos de categoria do eixo X e as entradas da legenda para cada
      série.
  - name: Crie uma matriz bidimensional onde cada linha contém os valores de uma série.
    text: Crie uma matriz bidimensional onde cada linha contém os valores de uma série.
  - name: Itere sobre cada série, extraia os valores da linha correspondente da matriz
      e adicione a série ao gráfico com a entrada de legenda correspondente e os rótulos
      do eixo X.
    text: Itere sobre cada série, extraia os valores da linha correspondente da matriz
      e adicione a série ao gráfico com a entrada de legenda correspondente e os rótulos
      do eixo X.
  - name: Defina o texto do título do gráfico como 'Half‑Yearly Revenue' e torne-o
      visível.
    text: Defina o texto do título do gráfico como 'Half‑Yearly Revenue' e torne-o
      visível.
  - name: Salve o documento que contém o gráfico personalizado em um arquivo .docx.
    text: Salve o documento que contém o gráfico personalizado em um arquivo .docx.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` espera que o comprimento da matriz de valores seja
      igual ao número de rótulos do eixo X, e você deve adicionar exatamente uma série
      por entrada de legenda; uma incompatibilidade lançará uma `ArgumentException`
      em tempo de execução.'
    question: E se as linhas ou colunas em `dataMatrix` não corresponderem aos comprimentos
      de `legendEntries` ou `xLabels`?
  - answer: Sim—substitua `ChartType.Column` em `docBuilder.InsertChart` por qualquer
      outro `ChartType` (por exemplo, `ChartType.Line`) e as chamadas subsequentes
      de `Series.Add` preencherão o novo gráfico da mesma forma.
    question: Posso usar um tipo de gráfico diferente, como um gráfico de linhas,
      com a mesma lógica de preenchimento de dados?
  - answer: Ajuste as propriedades `Width` e `Height` do `Shape` retornado por `InsertChart`
      (por exemplo, `chartContainer.Width = 500; chartContainer.Height = 300;`).
    question: Como altero o tamanho do gráfico depois que ele foi inserido?
  - answer: Defina `chartObj.Series[i].HasDataLabel = true;` para cada série após
      adicioná‑la, ou percorra `chartObj.Series` e habilite `HasDataLabel` para exibir
      os valores no gráfico.
    question: Existe uma maneira rápida de exibir rótulos de dados em cada coluna
      do gráfico?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Adicionar um Gráfico de Colunas Personalizado a um Documento Word
og_description: Troque os dados padrão de um gráfico pela sua própria matriz e defina um título em segundos.
og_image_alt: Captura de tela mostrando um documento Word com um gráfico de colunas personalizado criado usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir Gráfico de Colunas Personalizado em Documento Word Usando Aspose.Words
Este tutorial orienta você na criação de um documento Word, inserção de um gráfico de colunas, limpeza de seus dados padrão e preenchimento do gráfico com valores personalizados de uma matriz bidimensional—mapeando cada linha para uma série e cada coluna para uma categoria. Você também verá como adicionar um título ao gráfico antes de salvar o arquivo. Siga os passos para produzir um gráfico totalmente personalizado diretamente no seu arquivo Word.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: E se as linhas ou colunas em `dataMatrix` não corresponderem aos comprimentos de `legendEntries` ou `xLabels`?**  
A: `Chart.Series.Add` espera que o comprimento da matriz de valores seja igual ao número de rótulos do eixo X, e você deve adicionar exatamente uma série por entrada de legenda; uma incompatibilidade lançará uma `ArgumentException` em tempo de execução.

**Q: Posso usar um tipo de gráfico diferente, como um gráfico de linhas, com a mesma lógica de preenchimento de dados?**  
A: Sim—substitua `ChartType.Column` em `docBuilder.InsertChart` por qualquer outro `ChartType` (por exemplo, `ChartType.Line`) e as chamadas subsequentes de `Series.Add` preencherão o novo gráfico da mesma forma.

**Q: Como altero o tamanho do gráfico depois que ele foi inserido?**  
A: Ajuste as propriedades `Width` e `Height` do `Shape` retornado por `InsertChart` (por exemplo, `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Existe uma maneira rápida de exibir rótulos de dados em cada coluna do gráfico?**  
A: Defina `chartObj.Series[i].HasDataLabel = true;` para cada série após adicioná‑la, ou percorra `chartObj.Series` e habilite `HasDataLabel` para exibir os valores no gráfico.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}