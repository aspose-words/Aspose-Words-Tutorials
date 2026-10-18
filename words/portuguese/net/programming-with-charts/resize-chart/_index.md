---
title: Redimensionar Gráfico Proporcionalmente ao Alterar o Tamanho da Página no Word Usando Aspose.Words for .NET
weight: 210
limit:
description: Aprenda a redimensionar automaticamente um gráfico de colunas do Word ao mudar o documento para A4 usando Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a redimensionar automaticamente um gráfico de colunas do Word
    ao mudar o documento para A4 usando Aspose.Words for .NET.
  headline: Redimensionar Gráfico Proporcionalmente ao Alterar o Tamanho da Página
    no Word Usando Aspose.Words for .NET
  type: TechArticle
- description: Aprenda a redimensionar automaticamente um gráfico de colunas do Word
    ao mudar o documento para A4 usando Aspose.Words for .NET.
  name: Redimensionar Gráfico Proporcionalmente ao Alterar o Tamanho da Página no
    Word Usando Aspose.Words for .NET
  steps:
  - name: Crie um novo objeto Document e um DocumentBuilder para editá‑lo.
    text: Crie um novo objeto Document e um DocumentBuilder para editá‑lo.
  - name: Insira um gráfico de colunas com tamanho de 432×252 pontos e obtenha seu
      objeto Chart.
    text: Insira um gráfico de colunas com tamanho de 432×252 pontos e obtenha seu
      objeto Chart.
  - name: Defina o texto do título do gráfico como "Quarterly Revenue" e torne‑lo
      visível.
    text: Defina o texto do título do gráfico como "Quarterly Revenue" e torne‑lo
      visível.
  - name: Salve o documento em um arquivo exibindo o tamanho original do gráfico.
    text: Salve o documento em um arquivo exibindo o tamanho original do gráfico.
  - name: Altere o tamanho do papel do documento para A4 e atualize o layout.
    text: Altere o tamanho do papel do documento para A4 e atualize o layout.
  - name: Calcule uma nova largura para o gráfico equivalente a 80 % da largura da
      página, preservando a proporção original.
    text: Calcule uma nova largura para o gráfico equivalente a 80 % da largura da
      página, preservando a proporção original.
  - name: Se a forma contiver um gráfico, aplique a largura e a altura calculadas
      para redimensioná‑lo.
    text: Se a forma contiver um gráfico, aplique a largura e a altura calculadas
      para redimensioná‑lo.
  - name: Salve o documento após o gráfico ser redimensionado para refletir o novo
      tamanho da página.
    text: Salve o documento após o gráfico ser redimensionado para refletir o novo
      tamanho da página.
  type: HowTo
- questions:
  - answer: Sim. Alterar `docBuilder.PageSetup.PaperSize` não ajusta automaticamente
      as formas existentes, portanto você deve recalcular e atribuir `chartContainer.Width`
      e `Height` manualmente, conforme mostrado.
    question: Preciso redimensionar manualmente o gráfico após mudar o tamanho do
      papel do documento?
  - answer: Ele armazena `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      e então calcula `newChartHeight = newChartWidth * originalAspectRatio` após
      determinar a nova largura.
    question: Como o código mantém a proporção original de largura‑para‑altura do
      gráfico ao redimensionar?
  - answer: '`UpdatePageLayout()` força o mecanismo de layout a reavaliar as dimensões
      da página, garantindo que `docBuilder.PageSetup.PageWidth` reflita a nova largura
      A4 antes que o tamanho do gráfico seja recalculado.'
    question: Por que `myDoc.UpdatePageLayout()` é chamado após definir o tamanho
      do papel para A4?
  - answer: A verificação `if (chartContainer.HasChart)` impede que o código atribua
      `Width` e `Height` quando não há gráfico, evitando uma exceção em tempo de execução.
    question: O que acontece se a forma inserida não contiver realmente um gráfico?
  - answer: Com certeza—substitua o multiplicador `0.8` por qualquer proporção que
      desejar; o restante da lógica de redimensionamento ainda preservará a proporção
      original.
    question: Posso alterar o fator de escala de 80 % para outro valor?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Redimensionar um Gráfico do Word ao Mudar para A4
og_description: Mantenha seu gráfico proporcional redimensionando‑lo automaticamente após mudar o documento para A4.
og_image_alt: Captura de tela mostrando um gráfico de colunas redimensionado automaticamente para caber em um documento Word tamanho A4 usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Redimensionar Gráfico Proporcionalmente ao Alterar o Tamanho da Página no Word Usando Aspose.Words
Este tutorial mostra como inserir um gráfico de colunas em um documento Word, mudar o tamanho da página do documento para A4 e fazer com que o gráfico seja redimensionado automaticamente para que permaneça proporcional à nova largura da página. Ao seguir os passos, você verá o gráfico ajustar suas dimensões sem escalonamento manual, garantindo um layout consistente em diferentes formatos de página.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Preciso redimensionar manualmente o gráfico após mudar o tamanho do papel do documento?**  
A: Sim. Alterar `docBuilder.PageSetup.PaperSize` não ajusta automaticamente as formas existentes, portanto você deve recalcular e atribuir `chartContainer.Width` e `Height` manualmente, conforme mostrado.

**Q: Como o código mantém a proporção original de largura‑para‑altura do gráfico ao redimensionar?**  
A: Ele armazena `originalAspectRatio = chartContainer.Height / chartContainer.Width` e então calcula `newChartHeight = newChartWidth * originalAspectRatio` após determinar a nova largura.

**Q: Por que `myDoc.UpdatePageLayout()` é chamado após definir o tamanho do papel para A4?**  
A: `UpdatePageLayout()` força o mecanismo de layout a reavaliar as dimensões da página, garantindo que `docBuilder.PageSetup.PageWidth` reflita a nova largura A4 antes que o tamanho do gráfico seja recalculado.

**Q: O que acontece se a forma inserida não contiver realmente um gráfico?**  
A: A verificação `if (chartContainer.HasChart)` impede que o código atribua `Width` e `Height` quando não há gráfico, evitando uma exceção em tempo de execução.

**Q: Posso alterar o fator de escala de 80 % para outro valor?**  
A: Com certeza—substitua o multiplicador `0.8` por qualquer proporção que desejar; o restante da lógica de redimensionamento ainda preservará a proporção original.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}