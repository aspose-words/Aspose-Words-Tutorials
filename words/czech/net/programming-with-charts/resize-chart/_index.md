---
title: Proporcionální změna velikosti grafu při změně velikosti stránky ve Wordu pomocí Aspose.Words pro .NET
weight: 210
limit:
description: Naučte se automaticky měnit velikost sloupcového grafu ve Wordu při změně dokumentu na A4 pomocí Aspose.Words pro .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se automaticky měnit velikost sloupcového grafu ve Wordu při
    změně dokumentu na A4 pomocí Aspose.Words pro .NET.
  headline: Proporcionální změna velikosti grafu při změně velikosti stránky ve Wordu
    pomocí Aspose.Words pro .NET
  type: TechArticle
- description: Naučte se automaticky měnit velikost sloupcového grafu ve Wordu při
    změně dokumentu na A4 pomocí Aspose.Words pro .NET.
  name: Proporcionální změna velikosti grafu při změně velikosti stránky ve Wordu
    pomocí Aspose.Words pro .NET
  steps:
  - name: Vytvořte nový objekt Document a DocumentBuilder pro jeho úpravu.
    text: Vytvořte nový objekt Document a DocumentBuilder pro jeho úpravu.
  - name: Vložte sloupcový graf o rozměrech 432 × 252 bodů a získejte jeho objekt
      Chart.
    text: Vložte sloupcový graf o rozměrech 432 × 252 bodů a získejte jeho objekt
      Chart.
  - name: Nastavte text titulku grafu na "Quarterly Revenue" a zobrazte jej.
    text: Nastavte text titulku grafu na "Quarterly Revenue" a zobrazte jej.
  - name: Uložte dokument do souboru, který zachovává původní velikost grafu.
    text: Uložte dokument do souboru, který zachovává původní velikost grafu.
  - name: Změňte velikost papíru dokumentu na A4 a obnovte rozvržení.
    text: Změňte velikost papíru dokumentu na A4 a obnovte rozvržení.
  - name: Vypočítejte novou šířku grafu rovnou 80 % šířky stránky při zachování původního
      poměru stran.
    text: Vypočítejte novou šířku grafu rovnou 80 % šířky stránky při zachování původního
      poměru stran.
  - name: Pokud tvar obsahuje graf, použijte vypočtenou šířku a výšku k jeho změně
      velikosti.
    text: Pokud tvar obsahuje graf, použijte vypočtenou šířku a výšku k jeho změně
      velikosti.
  - name: Uložte dokument po změně velikosti grafu, aby odrážel novou velikost stránky.
    text: Uložte dokument po změně velikosti grafu, aby odrážel novou velikost stránky.
  type: HowTo
- questions:
  - answer: Ano. Změna `docBuilder.PageSetup.PaperSize` automaticky neúpravu existujících
      tvarů, takže musíte sami přepočítat a přiřadit `chartContainer.Width` a `Height`,
      jak je uvedeno.
    question: Musím po změně velikosti papíru dokumentu ručně měnit velikost grafu?
  - answer: Ukládá `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      a poté po určení nové šířky vypočítá `newChartHeight = newChartWidth * originalAspectRatio`.
    question: Jak kód zachovává původní poměr šířky a výšky grafu při změně velikosti?
  - answer: '`UpdatePageLayout()` nutí engine rozvržení znovu vyhodnotit rozměry stránky,
      čímž zajišťuje, že `docBuilder.PageSetup.PageWidth` odráží novou šířku A4 před
      přepočítáním velikosti grafu.'
    question: Proč je po nastavení velikosti papíru na A4 voláno `myDoc.UpdatePageLayout()`?
  - answer: Podmínka `if (chartContainer.HasChart)` zabraňuje kódu přiřazovat `Width`
      a `Height`, když graf není přítomen, čímž se vyhne výjimce za běhu.
    question: Co se stane, pokud vložený tvar ve skutečnosti neobsahuje graf?
  - answer: Určitě — nahraďte násobitel `0.8` libovolnou poměrovou hodnotou, kterou
      preferujete; zbytek logiky změny velikosti i nadále zachová původní poměr stran.
    question: Mohu změnit faktor škálování 80 % na jinou hodnotu?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Změna velikosti grafu ve Wordu při přepnutí na A4
og_description: Udržte graf úměrný automatickým změněním jeho velikosti po přepnutí dokumentu na A4.
og_image_alt: Snímek obrazovky ukazující sloupcový graf automaticky přizpůsobený tak, aby se vešel do dokumentu Word formátu A4 pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Proporcionální změna velikosti grafu při změně velikosti stránky ve Wordu pomocí Aspose.Words pro .NET
Tento tutoriál ukazuje, jak vložit sloupcový graf do dokumentu Word, přepnout velikost stránky dokumentu na A4 a nechat graf automaticky změnit velikost tak, aby zůstal úměrný nové šířce stránky. Po provedení kroků uvidíte, jak se graf přizpůsobí svým rozměrům bez ručního škálování, což zajišťuje konzistentní rozvržení napříč různými formáty stránek.

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

**Q: Musím po změně velikosti papíru dokumentu ručně měnit velikost grafu?**  
A: Ano. Změna `docBuilder.PageSetup.PaperSize` automaticky neúpravu existujících tvarů, takže musíte sami přepočítat a přiřadit `chartContainer.Width` a `Height`, jak je uvedeno.

**Q: Jak kód zachovává původní poměr šířky a výšky grafu při změně velikosti?**  
A: Ukládá `originalAspectRatio = chartContainer.Height / chartContainer.Width` a poté po určení nové šířky vypočítá `newChartHeight = newChartWidth * originalAspectRatio`.

**Q: Proč je po nastavení velikosti papíru na A4 voláno `myDoc.UpdatePageLayout()`?**  
A: `UpdatePageLayout()` nutí engine rozvržení znovu vyhodnotit rozměry stránky, čímž zajišťuje, že `docBuilder.PageSetup.PageWidth` odráží novou šířku A4 před přepočítáním velikosti grafu.

**Q: Co se stane, pokud vložený tvar ve skutečnosti neobsahuje graf?**  
A: Podmínka `if (chartContainer.HasChart)` zabraňuje kódu přiřazovat `Width` a `Height`, když graf není přítomen, čímž se vyhne výjimce za běhu.

**Q: Mohu změnit faktor škálování 80 % na jinou hodnotu?**  
A: Určitě — nahraďte násobitel `0.8` libovolnou poměrovou hodnotou, kterou preferujete; zbytek logiky změny velikosti i nadále zachová původní poměr stran.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}