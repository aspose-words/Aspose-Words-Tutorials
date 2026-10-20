---
title: Vložte ukázkový sloupcový graf do dokumentu Word pomocí Aspose.Words pro .NET
weight: 410
limit:
description: Postupný návod, jak vytvořit soubor Word, vložit výchozí sloupcový graf pomocí DocumentBuilder.InsertChart, získat přístup k objektu grafu a uložit jako .docx.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Postupný návod, jak vytvořit soubor Word, vložit výchozí sloupcový
    graf pomocí DocumentBuilder.InsertChart, získat přístup k objektu grafu a uložit
    jako .docx.
  headline: Vložte ukázkový sloupcový graf do dokumentu Word pomocí Aspose.Words pro
    .NET
  type: TechArticle
- description: Postupný návod, jak vytvořit soubor Word, vložit výchozí sloupcový
    graf pomocí DocumentBuilder.InsertChart, získat přístup k objektu grafu a uložit
    jako .docx.
  name: Vložte ukázkový sloupcový graf do dokumentu Word pomocí Aspose.Words pro .NET
  steps:
  - name: Vytvořte prázdný dokument Word a DocumentBuilder pro jeho úpravu.
    text: Vytvořte prázdný dokument Word a DocumentBuilder pro jeho úpravu.
  - name: Vložte sloupcový graf o rozměrech 432 × 252 bodů do dokumentu.
    text: Vložte sloupcový graf o rozměrech 432 × 252 bodů do dokumentu.
  - name: Získáte objekt Chart z vloženého tvaru pro další úpravy, pokud je to potřeba.
    text: Získáte objekt Chart z vloženého tvaru pro další úpravy, pokud je to potřeba.
  - name: Uložte dokument, který nyní obsahuje vložený sloupcový graf, do souboru
      .docx.
    text: Uložte dokument, který nyní obsahuje vložený sloupcový graf, do souboru
      .docx.
  type: HowTo
- questions:
  - answer: Rozměry jsou zadány v bodech (1 bod = 1/72 palce), takže 432 pt ≈ 6 palců
      a 252 pt ≈ 3,5 palce.
    question: Jaké jednotky jsou použity pro parametry šířky a výšky (432, 252) v
      InsertChart?
  - answer: Ano—po vložení máte objekt Chart přes `chartContainer.Chart`; můžete upravit
      jeho SeriesCollection, Categories a Values a nahradit tak ukázková data.
    question: Mohu změnit data grafu po zavolání InsertChart s výchozím datasetem?
  - answer: Jednoduše nahraďte `ChartType.Column` jinou hodnotou výčtu, například
      `ChartType.Line`, ve volání `InsertChart`.
    question: Je možné vložit jiný typ grafu (např. čárový graf) pomocí stejného kódu?
  - answer: Ne—`docBuilder.InsertChart` automaticky vloží graf do `Shape`; volání
      `wordDoc.Save` zapíše graf spolu s dokumentem.
    question: Musím před uložením dokumentu zavolat nějakou další metodu pro vložení
      grafu?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Vložte ukázkový sloupcový graf do dokumentu Word
og_description: Přidejte hotový sloupcový graf do dokumentu Word během několika minut pomocí Aspose.Words pro .NET.
og_image_alt: Snímek obrazovky ukazující dokument Word s vloženým ukázkovým sloupcovým grafem pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložte ukázkový sloupcový graf do dokumentu Word pomocí Aspose.Words pro .NET
Tento tutoriál vás provede vytvořením nového dokumentu Word a vložením výchozího sloupcového grafu pomocí DocumentBuilder.InsertChart. Také uvidíte, jak získat vložený objekt Chart pro další manipulaci. Nakonec průvodce ukazuje, jak uložit dokument jako soubor .docx.

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

**Q: Jaké jednotky jsou použity pro parametry šířky a výšky (432, 252) v InsertChart?**  
A: Rozměry jsou zadány v bodech (1 bod = 1/72 palce), takže 432 pt ≈ 6 palců a 252 pt ≈ 3,5 palce.

**Q: Mohu změnit data grafu po zavolání InsertChart s výchozím datasetem?**  
A: Ano—po vložení máte objekt Chart přes `chartContainer.Chart`; můžete upravit jeho SeriesCollection, Categories a Values a nahradit tak ukázková data.

**Q: Je možné vložit jiný typ grafu (např. čárový graf) pomocí stejného kódu?**  
A: Jednoduše nahraďte `ChartType.Column` jinou hodnotou výčtu, například `ChartType.Line`, ve volání `InsertChart`.

**Q: Musím před uložením dokumentu zavolat nějakou další metodu pro vložení grafu?**  
A: Ne—`docBuilder.InsertChart` automaticky vloží graf do `Shape`; volání `wordDoc.Save` zapíše graf spolu s dokumentem.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}