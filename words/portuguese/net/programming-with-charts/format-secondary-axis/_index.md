---
title: Formatar o eixo Y secundário como moeda em um gráfico Word usando Aspose.Words for .NET
weight: 710
limit:
description: Aprenda a adicionar e formatar um eixo Y secundário como moeda em um gráfico de linhas Word com Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a adicionar e formatar um eixo Y secundário como moeda em um
    gráfico de linhas Word com Aspose.Words for .NET.
  headline: Formatar o eixo Y secundário como moeda em um gráfico Word usando Aspose.Words
    for .NET
  type: TechArticle
- description: Aprenda a adicionar e formatar um eixo Y secundário como moeda em um
    gráfico de linhas Word com Aspose.Words for .NET.
  name: Formatar o eixo Y secundário como moeda em um gráfico Word usando Aspose.Words
    for .NET
  steps:
  - name: Crie um novo documento Word vazio e um DocumentBuilder para editá-lo.
    text: Crie um novo documento Word vazio e um DocumentBuilder para editá-lo.
  - name: Inserir um gráfico de linhas com tamanho de 450×250 pontos no documento
      e obter seu objeto Chart.
    text: Inserir um gráfico de linhas com tamanho de 450×250 pontos no documento
      e obter seu objeto Chart.
  - name: Remova a série de espaço reservado padrão que o Aspose adiciona a um novo
      gráfico.
    text: Remova a série de espaço reservado padrão que o Aspose adiciona a um novo
      gráfico.
  - name: Defina rótulos de trimestre e adicione uma série de dados primária com valores
      de exemplo ao gráfico.
    text: Defina rótulos de trimestre e adicione uma série de dados primária com valores
      de exemplo ao gráfico.
  - name: Crie um grupo de séries secundário do tipo Line e atribua‑o ao grupo de
      eixo secundário.
    text: Crie um grupo de séries secundário do tipo Line e atribua‑o ao grupo de
      eixo secundário.
  - name: Oculte o eixo X secundário para que apenas o eixo Y secundário fique visível.
    text: Oculte o eixo X secundário para que apenas o eixo Y secundário fique visível.
  - name: Exiba o título do eixo Y secundário e defina seu texto como "Sales (USD)".
    text: Exiba o título do eixo Y secundário e defina seu texto como "Sales (USD)".
  - name: Defina o formato numérico do eixo Y secundário como um padrão de moeda com
      duas casas decimais e desvincule‑lo da formatação de origem.
    text: Defina o formato numérico do eixo Y secundário como um padrão de moeda com
      duas casas decimais e desvincule‑lo da formatação de origem.
  - name: Adicione uma série auxiliar ao grupo secundário, fornecendo dados que serão
      plotados contra o eixo Y secundário.
    text: Adicione uma série auxiliar ao grupo secundário, fornecendo dados que serão
      plotados contra o eixo Y secundário.
  - name: Salve o documento finalizado em um arquivo chamado ProfitChart.docx no diretório
      atual.
    text: Salve o documento finalizado em um arquivo chamado ProfitChart.docx no diretório
      atual.
  type: HowTo
- questions:
  - answer: O gráfico manterá a série de espaço reservado padrão que o Aspose.Words
      insere, de modo que sua "Main Series" personalizada aparecerá junto a pontos
      de dados indesejados.
    question: O que acontece se eu omitir a chamada `lineChart.Series.Clear()`?
  - answer: Defina `secondarySeriesGroup.AxisX.Hidden = false;` (ou simplesmente omita
      a linha que o define como `true`).
    question: Como posso exibir o eixo X secundário em vez de ocultá‑lo?
  - answer: Sim – altere a string de formato, por exemplo `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = "\\\"€\\\"#,##0.00";` para euros ou ajuste o padrão para atender ao seu locale.
    question: Posso usar um símbolo de moeda ou formato diferente para o eixo Y secundário?
  - answer: Quando `IsLinkedToSource` está true, o eixo herda o formato numérico da
      fonte de dados subjacente, sobrescrevendo qualquer `FormatCode` personalizado;
      defini‑lo como false força o gráfico a usar o formato que você especificar.
    question: Por que preciso definir `IsLinkedToSource = false` ao aplicar um formato
      numérico personalizado?
  - answer: Sim, atribua `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (ou `Right` para o padrão) para controlar em qual lado o eixo é desenhado.
    question: É possível mover o eixo Y secundário para o lado esquerdo do gráfico?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatar o eixo secundário de um Chart como moeda
og_description: Aprenda a adicionar um eixo Y secundário a um gráfico de linhas Word e estilizar‑lo como moeda com duas casas decimais.
og_image_alt: Captura de tela mostrando um gráfico de linhas Word com um eixo Y secundário formatado como moeda usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatar o eixo Y secundário como moeda em um gráfico Word usando Aspose.Words
Neste tutorial você verá como criar um documento Word, inserir um gráfico de linhas, adicionar um eixo Y secundário, formatar esse eixo como moeda com duas casas decimais e vincular a ele uma série de dados secundária usando Aspose.Words for .NET. Formatar o eixo secundário como moeda permite apresentar claramente dados financeiros ao lado da série primária. Siga o código passo a passo para ver o gráfico renderizado diretamente no documento gerado.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: O que acontece se eu omitir a chamada `lineChart.Series.Clear()`?**  
A: O gráfico manterá a série de espaço reservado padrão que o Aspose.Words insere, de modo que sua "Main Series" personalizada aparecerá junto a pontos de dados indesejados.

**Q: Como posso exibir o eixo X secundário em vez de ocultá‑lo?**  
A: Defina `secondarySeriesGroup.AxisX.Hidden = false;` (ou simplesmente omita a linha que o define como `true`).

**Q: Posso usar um símbolo de moeda ou formato diferente para o eixo Y secundário?**  
A: Sim – altere a string de formato, por exemplo `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = "\\\"€\\\"#,##0.00";` para euros ou ajuste o padrão para atender ao seu locale.

**Q: Por que preciso definir `IsLinkedToSource = false` ao aplicar um formato numérico personalizado?**  
A: Quando `IsLinkedToSource` está true, o eixo herda o formato numérico da fonte de dados subjacente, sobrescrevendo qualquer `FormatCode` personalizado; defini‑lo como false força o gráfico a usar o formato que você especificar.

**Q: É possível mover o eixo Y secundário para o lado esquerdo do gráfico?**  
A: Sim, atribua `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (ou `Right` para o padrão) para controlar em qual lado o eixo é desenhado.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}