---
title: Formátování sekundární osy X a nastavení zobrazovacích jednotek na tisíce v čárových grafech Word pomocí Aspose.Words pro .NET
weight: 710
limit:
description: Vytvořte čárový graf Word, přidejte sekundární osu X, nastavte její zobrazovací jednotku na tisíce a použijte vlastní číselný formát pomocí Aspose.Words pro .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Vytvořte čárový graf Word, přidejte sekundární osu X, nastavte její
    zobrazovací jednotku na tisíce a použijte vlastní číselný formát pomocí Aspose.Words
    pro .NET.
  headline: Formátování sekundární osy X a nastavení zobrazovacích jednotek na tisíce
    v čárových grafech Word pomocí Aspose.Words pro .NET
  type: TechArticle
- description: Vytvořte čárový graf Word, přidejte sekundární osu X, nastavte její
    zobrazovací jednotku na tisíce a použijte vlastní číselný formát pomocí Aspose.Words
    pro .NET.
  name: Formátování sekundární osy X a nastavení zobrazovacích jednotek na tisíce
    v čárových grafech Word pomocí Aspose.Words pro .NET
  steps:
  - name: Vytvořte nový Document a DocumentBuilder pro zahájení tvorby souboru Word.
    text: Vytvořte nový Document a DocumentBuilder pro zahájení tvorby souboru Word.
  - name: Vložte do dokumentu čárový graf o rozměrech 500 × 300 a získejte objekt
      Chart.
    text: Vložte do dokumentu čárový graf o rozměrech 500 × 300 a získejte objekt
      Chart.
  - name: Odstraňte výchozí demonstrační sérii, kterou Aspose.Words přidává automaticky.
    text: Odstraňte výchozí demonstrační sérii, kterou Aspose.Words přidává automaticky.
  - name: Definujte pole štítků kategorií, které budou použity pro osu X.
    text: Definujte pole štítků kategorií, které budou použity pro osu X.
  - name: Přidejte primární datovou sérii pojmenovanou „Main Data“ pomocí štítků a
      hodnot.
    text: Přidejte primární datovou sérii pojmenovanou „Main Data“ pomocí štítků a
      hodnot.
  - name: Vytvořte sekundární skupinu sérií typu Line a přiřaďte ji ke skupině sekundární
      osy.
    text: Vytvořte sekundární skupinu sérií typu Line a přiřaďte ji ke skupině sekundární
      osy.
  - name: Nastavte zobrazovací jednotku sekundární osy X na tisíce, aby se hodnoty
      zobrazovaly v K.
    text: Nastavte zobrazovací jednotku sekundární osy X na tisíce, aby se hodnoty
      zobrazovaly v K.
  - name: Použijte vlastní číselný formát "#,##0.0" na popisky značek sekundární osy
      X.
    text: Použijte vlastní číselný formát "#,##0.0" na popisky značek sekundární osy
      X.
  - name: Volitelně přidejte pomocnou datovou sérii do sekundární skupiny.
    text: Volitelně přidejte pomocnou datovou sérii do sekundární skupiny.
  - name: Uložte dokument do souboru .docx.
    text: Uložte dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: Ne – nastavení `AxisX` patří k `ChartSeriesGroup`, takže můžete nastavit
      `secondaryGroup.AxisX.DisplayUnit.Unit` a `secondaryGroup.AxisX.NumberFormat.FormatCode`
      před nebo po přidání sérií; konfigurace se použije na osu skupiny v obou případech.
    question: Musím přidat sekundární sérii před nastavením zobrazovací jednotky a
      číselného formátu na sekundární osu X?
  - answer: Ano – přiřaďte libovolnou hodnotu `AxisBuiltInUnit`, např. `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` a tím zobrazíte hodnoty osy v milionech místo tisíců.
    question: Mohu pro sekundární osu X použít jinou vestavěnou jednotku, například
      miliony?
  - answer: Ne – kód formátu se použije pouze na osu, kterou upravujete (`secondaryGroup.AxisX.NumberFormat.FormatCode`),
      takže primární osa X si zachová výchozí formátování.
    question: Ovlivní vlastní formát `"#,##0.0"` popisky primární osy X?
  - answer: Graf bude obsahovat výchozí demonstrační sérii vedle těch, které přidáte,
      což může vést k nadbytečným čarám a nesouladu kategorií; vymazání kolekce zajistí,
      že se zobrazí pouze zamýšlená data.
    question: Co se stane, pokud zapomenu vymazat demonstrační sérii pomocí `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formátování sekundární osy X a nastavení jednotek na tisíce
og_description: Přidejte sekundární osu X do čárového grafu Word a naformátujte její popisky v tisících pomocí vlastního vzoru.
og_image_alt: Průvodce ukazující, jak přidat sekundární osu X do čárového grafu Word a naformátovat její popisky tak, aby zobrazovaly jednotky v tisících pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formátování sekundární osy X a nastavení zobrazovacích jednotek na tisíce v čárových grafech Word pomocí Aspose.Words pro .NET
Tento tutoriál vás provede vytvořením dokumentu Word, který obsahuje čárový graf, přidáním sekundární osy X a nastavením této osy tak, aby zobrazovala hodnoty v tisících. Také se naučíte, jak použít vlastní číselný formát na popisky sekundární osy, což vám poskytne přesnou kontrolu nad tím, jak jsou data prezentována. Postupujte podle kroků a zlepšete čitelnost víceosých grafů ve svých Word zprávách.

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

**Q: Musím přidat sekundární sérii před nastavením zobrazovací jednotky a číselného formátu na sekundární osu X?**  
A: Ne – nastavení `AxisX` patří k `ChartSeriesGroup`, takže můžete nastavit `secondaryGroup.AxisX.DisplayUnit.Unit` a `secondaryGroup.AxisX.NumberFormat.FormatCode` před nebo po přidání sérií; konfigurace se použije na osu skupiny v obou případech.

**Q: Mohu pro sekundární osu X použít jinou vestavěnou jednotku, například miliony?**  
A: Ano – přiřaďte libovolnou hodnotu `AxisBuiltInUnit`, např. `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` a tím zobrazíte hodnoty osy v milionech místo tisíců.

**Q: Ovlivní vlastní formát `"#,##0.0"` popisky primární osy X?**  
A: Ne – kód formátu se použije pouze na osu, kterou upravujete (`secondaryGroup.AxisX.NumberFormat.FormatCode`), takže primární osa X si zachová výchozí formátování.

**Q: Co se stane, pokud zapomenu vymazat demonstrační sérii pomocí `lineChart.Series.Clear();`?**  
A: Graf bude obsahovat výchozí demonstrační sérii vedle těch, které přidáte, což může vést k nadbytečným čarám a nesouladu kategorií; vymazání kolekce zajistí, že se zobrazí pouze zamýšlená data.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}