---
title: Definir rótulos de dados uniformes em um gráfico de colunas usando Aspose.Words for .NET
weight: 110
limit:
description: Aprenda a criar um gráfico de colunas Word e aplicar tamanho de fonte e cor uniformes aos rótulos de dados de todas as séries com Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aprenda a criar um gráfico de colunas Word e aplicar tamanho de fonte
    e cor uniformes aos rótulos de dados de todas as séries com Aspose.Words for .NET.
  headline: Definir rótulos de dados uniformes em um gráfico de colunas usando Aspose.Words
    for .NET
  type: TechArticle
- description: Aprenda a criar um gráfico de colunas Word e aplicar tamanho de fonte
    e cor uniformes aos rótulos de dados de todas as séries com Aspose.Words for .NET.
  name: Definir rótulos de dados uniformes em um gráfico de colunas usando Aspose.Words
    for .NET
  steps:
  - name: Crie um novo documento Word vazio e um DocumentBuilder para editá-lo.
    text: Crie um novo documento Word vazio e um DocumentBuilder para editá-lo.
  - name: Inserir um gráfico de colunas de 500×300 no documento e obter seu objeto
      Chart.
    text: Inserir um gráfico de colunas de 500×300 no documento e obter seu objeto
      Chart.
  - name: Remova a série de exemplo padrão que o Aspose.Words adiciona a um novo gráfico.
    text: Remova a série de exemplo padrão que o Aspose.Words adiciona a um novo gráfico.
  - name: Defina os rótulos de categoria e adicione duas séries de dados (Item Alpha
      e Item Beta) com seus valores ao gráfico.
    text: Defina os rótulos de categoria e adicione duas séries de dados (Item Alpha
      e Item Beta) com seus valores ao gráfico.
  - name: Defina o tamanho de fonte e a cor de base que serão aplicados a todos os
      rótulos de dados.
    text: Defina o tamanho de fonte e a cor de base que serão aplicados a todos os
      rótulos de dados.
  - name: Habilite os rótulos de dados para cada série, exiba o valor numérico e aplique
      o tamanho de fonte e a cor predefinidos.
    text: Habilite os rótulos de dados para cada série, exiba o valor numérico e aplique
      o tamanho de fonte e a cor predefinidos.
  - name: Salve o documento em um arquivo .docx.
    text: Salve o documento em um arquivo .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` cria um gráfico com uma série de exemplo padrão; limpá‑la
      remove esse espaço reservado, de modo que o gráfico exiba apenas as séries que
      você adiciona (`Item Alpha` e `Item Beta`).'
    question: Por que preciso chamar `chart.Series.Clear()` antes de adicionar minhas
      próprias séries?
  - answer: Substitua `Color.White` por qualquer valor `System.Drawing.Color`, por
      exemplo, `Color.Black` ou `Color.FromArgb(255, 30, 144, 255)`; a nova cor é
      aplicada via `series.DataLabels.Font.Color` dentro do loop.
    question: Como posso mudar a cor do rótulo de dados para algo diferente de branco?
  - answer: Os rótulos de dados ficarão ocultos, portanto as configurações de fonte
      que você aplicou se tornarão invisíveis; você deve manter `HasDataLabels` definido
      como `true` para que os rótulos (e seu estilo) apareçam.
    question: O que acontece se eu definir `series.HasDataLabels = false` depois de
      configurar o tamanho de fonte e a cor?
  - answer: Sim — cada `ChartSeries` tem seu próprio objeto `DataLabels`, portanto
      qualquer série adicionada após o loop inicial também deve ter `HasDataLabels`,
      `ShowValue` e as propriedades de fonte definidas, seja percorrendo novamente
      ou extraindo o estilo para um método auxiliar.
    question: Preciso percorrer as séries novamente se eu adicionar outra série mais
      tarde no código?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Aplicar rótulos de dados uniformes a um gráfico Word
og_description: Rapidamente dê a todos os rótulos do gráfico o mesmo tamanho de fonte e cor com Aspose.Words for .NET.
og_image_alt: Guia que mostra um documento Word com um gráfico de colunas onde todos os rótulos de dados compartilham o mesmo tamanho de fonte e cor, criado usando Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Definir rótulos de dados uniformes em um gráfico de colunas usando Aspose.Words
Este tutorial mostra como gerar um documento Word, inserir um gráfico de colunas e adicionar séries de dados personalizadas com Aspose.Words for .NET. Em seguida, demonstra como definir o tamanho de fonte e a cor padrão dos rótulos de dados para que cada série no gráfico exiba rótulos idênticos. Ao aplicar um único estilo, você garante uma aparência visual consistente em todo o gráfico.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: Por que preciso chamar `chart.Series.Clear()` antes de adicionar minhas próprias séries?**  
A: `InsertChart` cria um gráfico com uma série de exemplo padrão; limpá‑la remove esse espaço reservado, de modo que o gráfico exiba apenas as séries que você adiciona (`Item Alpha` e `Item Beta`).

**Q: Como posso mudar a cor do rótulo de dados para algo diferente de branco?**  
A: Substitua `Color.White` por qualquer valor `System.Drawing.Color`, por exemplo, `Color.Black` ou `Color.FromArgb(255, 30, 144, 255)`; a nova cor é aplicada via `series.DataLabels.Font.Color` dentro do loop.

**Q: O que acontece se eu definir `series.HasDataLabels = false` depois de configurar o tamanho de fonte e a cor?**  
A: Os rótulos de dados ficarão ocultos, portanto as configurações de fonte que você aplicou se tornarão invisíveis; você deve manter `HasDataLabels` definido como `true` para que os rótulos (e seu estilo) apareçam.

**Q: Preciso percorrer as séries novamente se eu adicionar outra série mais tarde no código?**  
A: Sim — cada `ChartSeries` tem seu próprio objeto `DataLabels`, portanto qualquer série adicionada após o loop inicial também deve ter `HasDataLabels`, `ShowValue` e as propriedades de fonte definidas, seja percorrendo novamente ou extraindo o estilo para um método auxiliar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}