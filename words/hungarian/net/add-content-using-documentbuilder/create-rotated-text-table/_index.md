---
title: Forgatott szöveges táblázat létrehozása Word dokumentumban az Aspose.Words for .NET használatával
weight: 110
limit:
description: Tanulja meg, hogyan építsen Word táblázatot rögzített oszlopszélességekkel, elforgatott szöveggel, pontos sormagasságokkal és feltöltött cellákkal az Aspose.Words for .NET használatával.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Tanulja meg, hogyan építsen Word táblázatot rögzített oszlopszélességekkel,
    elforgatott szöveggel, pontos sormagasságokkal és feltöltött cellákkal az Aspose.Words
    for .NET használatával.
  headline: Forgatott szöveges táblázat létrehozása Word dokumentumban az Aspose.Words
    for .NET használatával
  type: TechArticle
- description: Tanulja meg, hogyan építsen Word táblázatot rögzített oszlopszélességekkel,
    elforgatott szöveggel, pontos sormagasságokkal és feltöltött cellákkal az Aspose.Words
    for .NET használatával.
  name: Forgatott szöveges táblázat létrehozása Word dokumentumban az Aspose.Words
    for .NET használatával
  steps:
  - name: Hozzon létre egy új Document példányt és egy DocumentBuilder‑t, amelyet
      a táblázat felépítéséhez használunk.
    text: Hozzon létre egy új Document példányt és egy DocumentBuilder‑t, amelyet
      a táblázat felépítéséhez használunk.
  - name: Kezdjen el egy új táblázatot, szúrja be az első cellát, és rögzítse az oszlopszélességeket,
      hogy ne automatikusan igazodjanak.
    text: Kezdjen el egy új táblázatot, szúrja be az első cellát, és rögzítse az oszlopszélességeket,
      hogy ne automatikusan igazodjanak.
  - name: Igazítsa középre függőlegesen a tartalmat az aktuális cellában, és írja
      be az első sor első cellájának szövegét.
    text: Igazítsa középre függőlegesen a tartalmat az aktuális cellában, és írja
      be az első sor első cellájának szövegét.
  - name: Szúrja be az első sor második celláját, és írja be annak szövegét.
    text: Szúrja be az első sor második celláját, és írja be annak szövegét.
  - name: Zárja le az első sort, ezzel befejezve annak elrendezését.
    text: Zárja le az első sort, ezzel befejezve annak elrendezését.
  - name: Kezdje el a második sor első celláját, állítsa be a sormagasságot pontosan
      100 pontra, forgassa a szöveget felfelé, és írja be a cella szövegét.
    text: Kezdje el a második sor első celláját, állítsa be a sormagasságot pontosan
      100 pontra, forgassa a szöveget felfelé, és írja be a cella szövegét.
  - name: Szúrja be a második sor második celláját, forgassa a szöveget lefelé, és
      írja be a cella szövegét.
    text: Szúrja be a második sor második celláját, forgassa a szöveget lefelé, és
      írja be a cella szövegét.
  - name: Zárja le a második sort, ezzel befejezve a táblázat második sorát.
    text: Zárja le a második sort, ezzel befejezve a táblázat második sorát.
  - name: Fejezze be a táblázat építését, lezárva a táblázat szerkezetét.
    text: Fejezze be a táblázat építését, lezárva a táblázat szerkezetét.
  - name: Mentse a kész dokumentumot .docx fájlba.
    text: Mentse a kész dokumentumot .docx fájlba.
  type: HowTo
- questions:
  - answer: Az oszlopszélességek rögzítése után adjon meg szélességet minden cellának
      a `builder.CellFormat.Width = <valueInPoints>;` használatával a következő cella
      beszúrása előtt; a táblázat megtartja ezeket a pontos szélességeket.
    question: Hogyan állíthatok be konkrét oszlopszélességeket a `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`
      hívása után?
  - answer: A `builder.CellFormat.VerticalAlignment` egy cellaszintű beállítás, ezért
      újra be kell állítania a második sor celláiban (pl. `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) a tartalom írása előtt.
    question: Miért csak az első sorra van hatással a függőleges igazítás, és nem
      a második sorra?
  - answer: Igen – állítsa be a `builder.RowFormat.Height` és a `builder.RowFormat.HeightRule
      = HeightRule.Exactly` értékeket minden `builder.EndRow();` hívás előtt; a következő
      sor más magasságértékkel rendelkezhet.
    question: Lehet-e minden sorhoz különböző pontos magasságot adni, és ha igen,
      hogyan?
  - answer: Állítsa vissza az orientációt a `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      hozzárendelésével a következő cellába írás előtt.
    question: Hogyan állíthatom vissza a szövegorientációt az alapértelmezettre a
      `TextOrientation.Upward` vagy `Downward` használata után?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Forgatott szöveges táblázat létrehozása Wordben az Aspose.Words segítségével
og_description: Lépésről‑lépésre kód egy rögzített szélességű táblázat felépítéséhez, függőlegesen elforgatott szöveggel és pontos sormagasságokkal.
og_image_alt: Képernyőfelvétel, amely egy Word dokumentumot mutat egy táblázattal, amelynek rögzített oszlopszélességei, a cellákban elforgatott szövege és meghatározott sormagasságai vannak, az Aspose.Words for .NET használatával létrehozva
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Forgatott szöveges táblázat létrehozása Word dokumentumban az Aspose.Words for .NET használatával
Ez a bemutató azt mutatja be, hogyan lehet Word dokumentumot generálni és egy táblázatot hozzáadni, amelynek oszlopai rögzített szélességűek, sorai pontos magasságúak, és a cellák szövege függőlegesen van elforgatva. Megtanulja, hogyan állítsa be a függőleges igazítást, alkalmazza a szövegorientációt, töltsön fel minden cellát tartalommal, és végül mentse a dokumentumot – mindezt az Aspose.Words for .NET segítségével.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Hogyan állíthatok be konkrét oszlopszélességeket a `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` hívása után?**  
A: Az oszlopszélességek rögzítése után adjon meg szélességet minden cellának a `builder.CellFormat.Width = <valueInPoints>;` használatával a következő cella beszúrása előtt; a táblázat megtartja ezeket a pontos szélességeket.

**Q: Miért csak az első sorra van hatással a függőleges igazítás, és nem a második sorra?**  
A: A `builder.CellFormat.VerticalAlignment` egy cellaszintű beállítás, ezért újra be kell állítania a második sor celláiban (pl. `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) a tartalom írása előtt.

**Q: Lehet-e minden sorhoz különböző pontos magasságot adni, és ha igen, hogyan?**  
A: Igen – állítsa be a `builder.RowFormat.Height` és a `builder.RowFormat.HeightRule = HeightRule.Exactly` értékeket minden `builder.EndRow();` hívás előtt; a következő sor más magasságértékkel rendelkezhet.

**Q: Hogyan állíthatom vissza a szövegorientációt az alapértelmezettre a `TextOrientation.Upward` vagy `Downward` használata után?**  
A: Állítsa vissza az orientációt a `builder.CellFormat.Orientation = TextOrientation.Horizontal;` hozzárendelésével a következő cellába írás előtt.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}