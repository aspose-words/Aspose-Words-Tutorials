---
title: Formate o eixo X secundário e defina unidades de exibição para milhares em gráficos de linhas do Word usando Aspose.Words para .NET
weight: 710
limit:
description: Crie um gráfico de linhas Word, adicione um eixo X secundário, defina sua unidade de exibição para milhares e aplique um formato numérico personalizado com Aspose.Words para .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Crie um gráfico de linhas Word, adicione um eixo X secundário, defina
    sua unidade de exibição para milhares e aplique um formato numérico personalizado
    com Aspose.Words para .NET.
  headline: Formate o eixo X secundário e defina unidades de exibição para milhares
    em gráficos de linhas do Word usando Aspose.Words para .NET
  type: TechArticle
- description: Crie um gráfico de linhas Word, adicione um eixo X secundário, defina
    sua unidade de exibição para milhares e aplique um formato numérico personalizado
    com Aspose.Words para .NET.
  name: Formate o eixo X secundário e defina unidades de exibição para milhares em
    gráficos de linhas do Word usando Aspose.Words para .NET
  steps:
  - name: Crie um novo Document e um DocumentBuilder para começar a construir o arquivo
      Word.
    text: Crie um novo Document e um DocumentBuilder para começar a construir o arquivo
      Word.
  - name: Insira um gráfico de linhas com tamanho 500×300 no documento e obtenha o
      objeto Chart.
    text: Insira um gráfico de linhas com tamanho 500×300 no documento e obtenha o
      objeto Chart.
  - name: Remova a série de demonstração padrão que o Aspose.Words adiciona automaticamente.
    text: Remova a série de demonstração padrão que o Aspose.Words adiciona automaticamente.
  - name: Defina um array de rótulos de categoria que será usado para o eixo X.
    text: Defina um array de rótulos de categoria que será usado para o eixo X.
  - name: Adicione a série de dados primária chamada "Main Data" usando os rótulos
      e valores.
    text: Adicione a série de dados primária chamada "Main Data" usando os rótulos
      e valores.
  - name: Crie um grupo de séries secundário do tipo Line e atribua-o ao grupo de
      eixo secundário.
    text: Crie um grupo de séries secundário do tipo Line e atribua-o ao grupo de
      eixo secundário.
  - name: Defina a unidade de exibição do eixo X secundário para milhares, de modo
      que os valores sejam mostrados em K.
    text: Defina a unidade de exibição do eixo X secundário para milhares, de modo
      que os valores sejam mostrados em K.
  - name: Aplique o formato numérico personalizado "#,##0.0" aos rótulos de marcação
      do eixo X secundário.
    text: Aplique o formato numérico personalizado "#,##0.0" aos rótulos de marcação
      do eixo X secundário.
  - name: Opcionalmente, adicione uma série de dados auxiliar ao grupo secundário.
    text: Opcionalmente, adicione uma série de dados auxiliar ao grupo secundário.
  - name: Salve o documento em um arquivo .docx.
    text: Salve o documento em um arquivo .docx.
  type: HowTo
- questions:
  - answer: Não – as configurações de `AxisX` pertencem ao `ChartSeriesGroup`, portanto
      você pode definir `secondaryGroup.AxisX.DisplayUnit.Unit` e `secondaryGroup.AxisX.NumberFormat.FormatCode`
      antes ou depois de adicionar as séries; a configuração será aplicada ao eixo
      do grupo de qualquer forma.
    question: Preciso adicionar a série secundária antes de definir a unidade de exibição
      e o formato numérico no eixo X secundário?
  - answer: Sim – atribua qualquer valor de `AxisBuiltInUnit`, por exemplo `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` para exibir os valores do eixo em milhões em vez
      de milhares.
    question: Posso usar uma unidade interna diferente, como milhões, para o eixo
      X secundário?
  - answer: Não – o código de formato é aplicado apenas ao eixo que você modifica
      (`secondaryGroup.AxisX.NumberFormat.FormatCode`), portanto o eixo X primário
      mantém sua formatação padrão.
    question: O formato personalizado "#,##0.0" afetará os rótulos do eixo X primário?
  - answer: O gráfico conterá a série de demonstração padrão além das que você adicionou,
      o que pode gerar linhas extras e categorias incompatíveis; limpar a coleção
      garante que apareçam apenas os dados pretendidos.
    question: O que acontece se eu esquecer de limpar a série de demonstração com
      `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formate o eixo X secundário e defina unidades para milhares
og_description: Adicione um eixo X secundário a um gráfico de linhas Word e formate seus rótulos em milhares com um padrão personalizado.
og_image_alt: Guia que mostra como adicionar um eixo X secundário a um gráfico de linhas Word e formatar seus rótulos para exibir unidades em milhares usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formate o eixo X secundário e defina unidades de exibição para milhares em gráficos de linhas do Word usando Aspose.Words para .NET
Este tutorial orienta você na criação de um documento Word que contém um gráfico de linhas, na adição de um eixo X secundário e na configuração desse eixo para exibir valores em milhares. Você também aprenderá a aplicar um formato numérico personalizado aos rótulos do eixo secundário, proporcionando controle preciso sobre como os dados são apresentados. Siga os passos para melhorar a legibilidade de gráficos com múltiplos eixos em seus relatórios Word.

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

**Q: Preciso adicionar a série secundária antes de definir a unidade de exibição e o formato numérico no eixo X secundário?**  
A: Não – as configurações de `AxisX` pertencem ao `ChartSeriesGroup`, portanto você pode definir `secondaryGroup.AxisX.DisplayUnit.Unit` e `secondaryGroup.AxisX.NumberFormat.FormatCode` antes ou depois de adicionar as séries; a configuração será aplicada ao eixo do grupo de qualquer forma.

**Q: Posso usar uma unidade interna diferente, como milhões, para o eixo X secundário?**  
A: Sim – atribua qualquer valor de `AxisBuiltInUnit`, por exemplo `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` para exibir os valores do eixo em milhões em vez de milhares.

**Q: O formato personalizado "#,##0.0" afetará os rótulos do eixo X primário?**  
A: Não – o código de formato é aplicado apenas ao eixo que você modifica (`secondaryGroup.AxisX.NumberFormat.FormatCode`), portanto o eixo X primário mantém sua formatação padrão.

**Q: O que acontece se eu esquecer de limpar a série de demonstração com `lineChart.Series.Clear();`?**  
A: O gráfico conterá a série de demonstração padrão além das que você adicionou, o que pode gerar linhas extras e categorias incompatíveis; limpar a coleção garante que apareçam apenas os dados pretendidos.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}