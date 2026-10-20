---
title: Atualizar o Título do Gráfico e Alternar a Visibilidade da Legenda no Word usando Aspose.Words for .NET
weight: 810
limit:
description: Aprenda a alterar o título de um gráfico e controlar a visibilidade da legenda em um documento Word com Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a alterar o título de um gráfico e controlar a visibilidade
    da legenda em um documento Word com Aspose.Words for .NET.
  headline: Atualizar o Título do Gráfico e Alternar a Visibilidade da Legenda no
    Word usando Aspose.Words for .NET
  type: TechArticle
- description: Aprenda a alterar o título de um gráfico e controlar a visibilidade
    da legenda em um documento Word com Aspose.Words for .NET.
  name: Atualizar o Título do Gráfico e Alternar a Visibilidade da Legenda no Word
    usando Aspose.Words for .NET
  steps:
  - name: Defina o título do gráfico fornecido pelo usuário e se a legenda deve ser
      exibida.
    text: Defina o título do gráfico fornecido pelo usuário e se a legenda deve ser
      exibida.
  - name: Crie um novo documento Word e um DocumentBuilder para adicionar conteúdo.
    text: Crie um novo documento Word e um DocumentBuilder para adicionar conteúdo.
  - name: Insira um gráfico de colunas de 432 × 252 pt no documento e verifique se
      a forma realmente contém um gráfico.
    text: Insira um gráfico de colunas de 432 × 252 pt no documento e verifique se
      a forma realmente contém um gráfico.
  - name: Recupere o objeto Chart, defina o texto do título com o valor fornecido
      pelo usuário e garanta que o título seja exibido.
    text: Recupere o objeto Chart, defina o texto do título com o valor fornecido
      pelo usuário e garanta que o título seja exibido.
  - name: 'Configure a legenda: exiba-a à direita se solicitado, caso contrário oculte-a,
      e permita que ela sobreponha a área do gráfico.'
    text: 'Configure a legenda: exiba-a à direita se solicitado, caso contrário oculte-a,
      e permita que ela sobreponha a área do gráfico.'
  - name: Salve o documento modificado no disco como CustomChart.docx.
    text: Salve o documento modificado no disco como CustomChart.docx.
  type: HowTo
- questions:
  - answer: Quando `displayLegend` é `true`, o código define `chartLegend.Position`
      como `LegendPosition.Right`, tornando a legenda visível no lado direito da área
      do gráfico; a propriedade `Overlay` permanece `true`, permitindo que a legenda
      se sobreponha ao gráfico para economizar espaço.
    question: O que mudar ao definir `displayLegend` como `true` no gráfico gerado?
  - answer: Defina `chartTitle.Show = false` (ou simplesmente não defina `Show` como
      `true`) após atribuir `chartTitle.Text`; o título não será renderizado no documento
      Word.
    question: Como posso ocultar o título do gráfico se o usuário não fornecer um?
  - answer: Sim—`InsertChart` retorna um `Shape` que deve conter um gráfico, mas verificar
      `HasChart` garante que a forma realmente contém um objeto `Chart`; caso contrário,
      o código lança uma `InvalidOperationException`.
    question: É necessário verificar `chartContainer.HasChart` após chamar `InsertChart`?
  - answer: Com certeza; atribua qualquer valor do enum `LegendPosition` (por exemplo,
      `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) a `chartLegend.Position`
      para reposicionar a legenda conforme necessário.
    question: Posso posicionar a legenda em outro lugar que não o lado direito?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Alterar Título e Legenda do Gráfico no Word
og_description: Aprenda a definir um título de gráfico personalizado e controlar a exibição da legenda em um documento Word com Aspose.Words for .NET.
og_image_alt: Guia que mostra código que atualiza o título de um gráfico e alterna a legenda em um documento Word usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Atualizar o Título do Gráfico e Alternar a Visibilidade da Legenda no Word usando Aspose.Words
Este tutorial mostra como modificar programaticamente um gráfico dentro de um documento Word com Aspose.Words for .NET. Você aprenderá a inserir um gráfico de colunas, substituir seu título por texto fornecido pelo usuário e controlar a visibilidade e a sobreposição da legenda com base nas preferências do usuário. Essas etapas permitem personalizar a apresentação do gráfico dinamicamente, sem edição manual.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: O que mudar ao definir `displayLegend` como `true` no gráfico gerado?**  
A: Quando `displayLegend` é `true`, o código define `chartLegend.Position` como `LegendPosition.Right`, tornando a legenda visível no lado direito da área do gráfico; a propriedade `Overlay` permanece `true`, permitindo que a legenda se sobreponha ao gráfico para economizar espaço.

**Q: Como posso ocultar o título do gráfico se o usuário não fornecer um?**  
A: Defina `chartTitle.Show = false` (ou simplesmente não defina `Show` como `true`) após atribuir `chartTitle.Text`; o título não será renderizado no documento Word.

**Q: É necessário verificar `chartContainer.HasChart` após chamar `InsertChart`?**  
A: Sim—`InsertChart` retorna um `Shape` que deve conter um gráfico, mas verificar `HasChart` garante que a forma realmente contém um objeto `Chart`; caso contrário, o código lança uma `InvalidOperationException`.

**Q: Posso posicionar a legenda em outro lugar que não o lado direito?**  
A: Com certeza; atribua qualquer valor do enum `LegendPosition` (por exemplo, `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) a `chartLegend.Position` para reposicionar a legenda conforme necessário.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}