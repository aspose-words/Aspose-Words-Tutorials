---
title: Přidejte pojmenovanou datovou řadu do histogramového grafu ve Wordu pomocí Aspose.Words pro .NET
weight: 610
limit:
description: Naučte se, jak vložit histogramový graf do Word dokumentu a přidat pojmenovanou datovou řadu pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se, jak vložit histogramový graf do Word dokumentu a přidat
    pojmenovanou datovou řadu pomocí Aspose.Words pro .NET.
  headline: Přidejte pojmenovanou datovou řadu do histogramového grafu ve Wordu pomocí
    Aspose.Words pro .NET
  type: TechArticle
- description: Naučte se, jak vložit histogramový graf do Word dokumentu a přidat
    pojmenovanou datovou řadu pomocí Aspose.Words pro .NET.
  name: Přidejte pojmenovanou datovou řadu do histogramového grafu ve Wordu pomocí
    Aspose.Words pro .NET
  steps:
  - name: Vytvořte nový prázdný Word dokument a DocumentBuilder pro jeho úpravu.
    text: Vytvořte nový prázdný Word dokument a DocumentBuilder pro jeho úpravu.
  - name: Vložte do dokumentu tvar histogramového grafu o rozměrech 500×300 a získejte
      jeho objekt Chart.
    text: Vložte do dokumentu tvar histogramového grafu o rozměrech 500×300 a získejte
      jeho objekt Chart.
  - name: Odeberte výchozí zástupnou řadu, kterou Aspose.Words přidává do nových grafů.
    text: Odeberte výchozí zástupnou řadu, kterou Aspose.Words přidává do nových grafů.
  - name: Přidejte pojmenovanou řadu nazvanou "Demo Series" s určenými datovými body
      do histogramového grafu.
    text: Přidejte pojmenovanou řadu nazvanou "Demo Series" s určenými datovými body
      do histogramového grafu.
  - name: Uložte dokument do souboru .docx, který obsahuje pojmenované řady grafu.
    text: Uložte dokument do souboru .docx, který obsahuje pojmenované řady grafu.
  type: HowTo
- questions:
  - answer: '`InsertChart` vytvoří výchozí zástupnou řadu; její vymazání odstraní
      tuto prázdnou řadu, takže graf zobrazí jen data, která přidáte pomocí `Series.Add`.'
    question: Proč potřebuji zavolat `histogramChart.Series.Clear()` před přidáním
      vlastní řady?
  - answer: Ano, zavolejte `histogramChart.Series.Add` vícekrát, každou s odlišným
      názvem a hodnotami `double[]`; každá řada bude v legendě grafu uvedena s poskytnutým
      názvem.
    question: Mohu pomocí stejného přetížení přidat více než jednu řadu a bude každá
      zobrazena se svým vlastním popiskem?
  - answer: Přetížení očekává `double[]`; pokud máte `int[]` nebo jiné číselné pole,
      přetypujte nebo převedete je na `double[]` před jejich předáním.
    question: Je argument `double[]` jediným typem přijímaným pro datové body?
  - answer: Řetězec předaný jako první argument (např. "Demo Series") se použije jako
      název řady a ve výchozím nastavení se zobrazí v legendě grafu.
    question: Zobrazí se název řady, který zadám, v grafu automaticky?
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: Přidejte pojmenovanou řadu do Word histogramového grafu
og_description: Rychle označte řadu grafu ve Wordu pomocí Aspose.Words a okamžitě ji zobrazte.
og_image_alt: Snímek obrazovky zobrazující Word dokument s histogramovým grafem, který obsahuje pojmenovanou datovou řadu vytvořenou pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidejte pojmenovanou datovou řadu do histogramového grafu ve Wordu pomocí Aspose.Words pro .NET
Tento tutoriál demonstruje, jak vytvořit Word dokument pomocí Aspose.Words pro .NET, vložit histogramový graf a přidat pojmenovanou datovou řadu pomocí přetížení ChartSeriesCollection.Add, které přijímá název a hodnoty. Pojmenováním řady můžete jasně identifikovat každou datovou sadu v grafu, což usnadňuje čtení a interpretaci vizuálního výstupu.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


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

**Q: Proč potřebuji zavolat `histogramChart.Series.Clear()` před přidáním vlastní řady?**  
A: `InsertChart` vytvoří výchozí zástupnou řadu; její vymazání odstraní tuto prázdnou řadu, takže graf zobrazí jen data, která přidáte pomocí `Series.Add`.

**Q: Mohu pomocí stejného přetížení přidat více než jednu řadu a bude každá zobrazena se svým vlastním popiskem?**  
A: Ano, zavolejte `histogramChart.Series.Add` vícekrát, každou s odlišným názvem a hodnotami `double[]`; každá řada bude v legendě grafu uvedena s poskytnutým názvem.

**Q: Je argument `double[]` jediným typem přijímaným pro datové body?**  
A: Přetížení očekává `double[]`; pokud máte `int[]` nebo jiné číselné pole, přetypujte nebo převedete je na `double[]` před jejich předáním.

**Q: Zobrazí se název řady, který zadám, v grafu automaticky?**  
A: Řetězec předaný jako první argument (např. "Demo Series") se použije jako název řady a ve výchozím nastavení se zobrazí v legendě grafu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}