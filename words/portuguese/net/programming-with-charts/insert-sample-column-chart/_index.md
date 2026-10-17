---
title: Inserir Gráfico de Colunas de Exemplo em Documento Word Usando Aspose.Words for .NET
weight: 410
limit:
description: Guia passo a passo para criar um arquivo Word, inserir um gráfico de colunas padrão com DocumentBuilder.InsertChart, acessar o objeto do gráfico e salvar como .docx.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Guia passo a passo para criar um arquivo Word, inserir um gráfico de
    colunas padrão com DocumentBuilder.InsertChart, acessar o objeto do gráfico e
    salvar como .docx.
  headline: Inserir Gráfico de Colunas de Exemplo em Documento Word Usando Aspose.Words
    for .NET
  type: TechArticle
- description: Guia passo a passo para criar um arquivo Word, inserir um gráfico de
    colunas padrão com DocumentBuilder.InsertChart, acessar o objeto do gráfico e
    salvar como .docx.
  name: Inserir Gráfico de Colunas de Exemplo em Documento Word Usando Aspose.Words
    for .NET
  steps:
  - name: Crie um documento Word vazio e um DocumentBuilder para editá-lo.
    text: Crie um documento Word vazio e um DocumentBuilder para editá-lo.
  - name: Inserir um gráfico de colunas com tamanho de 432 × 252 pontos no documento.
    text: Inserir um gráfico de colunas com tamanho de 432 × 252 pontos no documento.
  - name: Recupere o objeto Chart da forma inserida para personalização adicional,
      se necessário.
    text: Recupere o objeto Chart da forma inserida para personalização adicional,
      se necessário.
  - name: Salve o documento, que agora contém o gráfico de colunas inserido, em um
      arquivo .docx.
    text: Salve o documento, que agora contém o gráfico de colunas inserido, em um
      arquivo .docx.
  type: HowTo
- questions:
  - answer: As dimensões são especificadas em pontos (1 ponto = 1/72 polegada), portanto
      432 pt ≈ 6 pol. e 252 pt ≈ 3,5 pol.
    question: Quais unidades são usadas para os parâmetros de largura e altura (432,
      252) em InsertChart?
  - answer: Sim—após a inserção você tem o objeto Chart via `chartContainer.Chart`;
      pode modificar sua SeriesCollection, Categories e Values para substituir os
      dados de exemplo.
    question: Posso alterar os dados do gráfico após chamar InsertChart com o conjunto
      de dados padrão?
  - answer: Basta substituir `ChartType.Column` por outro valor enum, como `ChartType.Line`,
      na chamada `InsertChart`.
    question: É possível inserir um tipo de gráfico diferente (por exemplo, um gráfico
      de linhas) usando o mesmo código?
  - answer: Não—`docBuilder.InsertChart` incorpora automaticamente o gráfico em um
      `Shape`; chamar `wordDoc.Save` grava o gráfico junto com o documento.
    question: Preciso chamar algum método adicional para incorporar o gráfico antes
      de salvar o documento?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Inserir um Gráfico de Colunas de Exemplo em um Documento Word
og_description: Adicione um gráfico de colunas pronto a um documento Word com Aspose.Words for .NET em minutos.
og_image_alt: Captura de tela mostrando um documento Word com um gráfico de colunas de exemplo inserido usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir Gráfico de Colunas de Exemplo em Documento Word Usando Aspose.Words
Este tutorial orienta você na criação de um novo documento Word e na inserção de um gráfico de colunas padrão com DocumentBuilder.InsertChart. Você também verá como recuperar o objeto Chart incorporado para manipulação adicional. Por fim, o guia mostra como salvar o documento como um arquivo .docx.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: Quais unidades são usadas para os parâmetros de largura e altura (432, 252) em InsertChart?**  
A: As dimensões são especificadas em pontos (1 ponto = 1/72 polegada), portanto 432 pt ≈ 6 pol. e 252 pt ≈ 3,5 pol.

**Q: Posso alterar os dados do gráfico após chamar InsertChart com o conjunto de dados padrão?**  
A: Sim—após a inserção você tem o objeto Chart via `chartContainer.Chart`; pode modificar sua SeriesCollection, Categories e Values para substituir os dados de exemplo.

**Q: É possível inserir um tipo de gráfico diferente (por exemplo, um gráfico de linhas) usando o mesmo código?**  
A: Basta substituir `ChartType.Column` por outro valor enum, como `ChartType.Line`, na chamada `InsertChart`.

**Q: Preciso chamar algum método adicional para incorporar o gráfico antes de salvar o documento?**  
A: Não—`docBuilder.InsertChart` incorpora automaticamente o gráfico em um `Shape`; chamar `wordDoc.Save` grava o gráfico junto com o documento.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}