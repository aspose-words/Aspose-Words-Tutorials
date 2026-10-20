---
title: Remover uma Série de Gráfico de um Documento Word usando Aspose.Words for .NET
weight: 510
limit:
description: Aprenda como excluir uma série de dados específica de um gráfico de colunas em um documento Word com Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda como excluir uma série de dados específica de um gráfico de
    colunas em um documento Word com Aspose.Words for .NET.
  headline: Remover uma Série de Gráfico de um Documento Word usando Aspose.Words
    for .NET
  type: TechArticle
- description: Aprenda como excluir uma série de dados específica de um gráfico de
    colunas em um documento Word com Aspose.Words for .NET.
  name: Remover uma Série de Gráfico de um Documento Word usando Aspose.Words for
    .NET
  steps:
  - name: Crie um novo Document do Word e um DocumentBuilder vinculado a ele.
    text: Crie um novo Document do Word e um DocumentBuilder vinculado a ele.
  - name: Insira um gráfico de colunas com tamanho de 432×252 pontos e obtenha o objeto
      Chart para manipulação adicional.
    text: Insira um gráfico de colunas com tamanho de 432×252 pontos e obtenha o objeto
      Chart para manipulação adicional.
  - name: Defina o índice baseado em zero da série que deve ser removida (a segunda
      série).
    text: Defina o índice baseado em zero da série que deve ser removida (a segunda
      série).
  - name: Se o índice for válido, chame RemoveAt na coleção Series do chart para excluir
      essa série.
    text: Se o índice for válido, chame RemoveAt na coleção Series do chart para excluir
      essa série.
  - name: Salve o documento atualizado em um arquivo .docx.
    text: Salve o documento atualizado em um arquivo .docx.
  type: HowTo
- questions:
  - answer: A verificação `if` (`targetSeriesIdx < columnChart.Series.Count`) falhará,
      portanto `RemoveAt` nunca será chamado e o gráfico permanecerá inalterado.
    question: O que acontece se eu passar um índice que é igual ao número de séries
      no gráfico?
  - answer: Sim, após `columnChart.Series.RemoveAt` a legenda é regenerada para refletir
      as séries restantes, de modo que a entrada removida desaparece da legenda.
    question: Remover uma série atualiza automaticamente a legenda do gráfico?
  - answer: O código funciona para qualquer tipo de gráfico que suporte uma coleção
      `Series`; basta alterar `ChartType.Column` para o tipo desejado ao inserir o
      gráfico.
    question: Posso usar o mesmo código para excluir uma série de um gráfico de linhas
      ou de pizza?
  - answer: Um gráfico com zero séries ainda é um `Shape` válido e será salvo, mas
      aparecerá vazio no documento resultante.
    question: Se eu remover a única série de um gráfico, o gráfico ainda será salvo
      corretamente?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Excluir uma Série de Gráfico em um Documento Word
og_description: Guia passo a passo para remover uma série de dados de um gráfico Word usando Aspose.Words for .NET.
og_image_alt: Guia que mostra como excluir uma série de dados específica de um gráfico de colunas em um documento Word usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Remover uma Série de Gráfico de um Documento Word usando Aspose.Words
Este tutorial mostra como criar um documento Word, adicionar um gráfico de colunas com DocumentBuilder e, em seguida, excluir uma série de dados específica desse gráfico usando o método ChartSeriesCollection.RemoveAt. Ao final, você terá um documento salvo com a série indesejada removida, proporcionando controle preciso sobre o conteúdo do gráfico diretamente a partir do código .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: O que acontece se eu passar um índice que é igual ao número de séries no gráfico?**  
A: A verificação `if` (`targetSeriesIdx < columnChart.Series.Count`) falhará, portanto `RemoveAt` nunca será chamado e o gráfico permanecerá inalterado.

**Q: Remover uma série atualiza automaticamente a legenda do gráfico?**  
A: Sim, após `columnChart.Series.RemoveAt` a legenda é regenerada para refletir as séries restantes, de modo que a entrada removida desaparece da legenda.

**Q: Posso usar o mesmo código para excluir uma série de um gráfico de linhas ou de pizza?**  
A: O código funciona para qualquer tipo de gráfico que suporte uma coleção `Series`; basta alterar `ChartType.Column` para o tipo desejado ao inserir o gráfico.

**Q: Se eu remover a única série de um gráfico, o gráfico ainda será salvo corretamente?**  
A: Um gráfico com zero séries ainda é um `Shape` válido e será salvo, mas aparecerá vazio no documento resultante.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}