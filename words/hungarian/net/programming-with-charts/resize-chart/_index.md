---
title: Diagram arányos átméretezése Wordben oldalméret változtatásakor az Aspose.Words for .NET használatával
weight: 210
limit:
description: Tanulja meg, hogyan automatikusan átméretezhető egy Word oszlopdiagram, amikor a dokumentumot A4-re változtatja az Aspose.Words for .NET használatával.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Tanulja meg, hogyan automatikusan átméretezhető egy Word oszlopdiagram,
    amikor a dokumentumot A4-re változtatja az Aspose.Words for .NET használatával.
  headline: Diagram arányos átméretezése Wordben oldalméret változtatásakor az Aspose.Words
    for .NET használatával
  type: TechArticle
- description: Tanulja meg, hogyan automatikusan átméretezhető egy Word oszlopdiagram,
    amikor a dokumentumot A4-re változtatja az Aspose.Words for .NET használatával.
  name: Diagram arányos átméretezése Wordben oldalméret változtatásakor az Aspose.Words
    for .NET használatával
  steps:
  - name: Hozzon létre egy új Document objektumot és egy DocumentBuilder‑t a szerkesztéshez.
    text: Hozzon létre egy új Document objektumot és egy DocumentBuilder‑t a szerkesztéshez.
  - name: Szúrjon be egy 432×252 pont méretű oszlopdiagramot, és szerezze meg a hozzá
      tartozó Chart objektumot.
    text: Szúrjon be egy 432×252 pont méretű oszlopdiagramot, és szerezze meg a hozzá
      tartozó Chart objektumot.
  - name: Állítsa be a diagram címét "Quarterly Revenue" szövegre, és tegye láthatóvá.
    text: Állítsa be a diagram címét "Quarterly Revenue" szövegre, és tegye láthatóvá.
  - name: Mentse a dokumentumot egy fájlba, amely az eredeti diagramméretet mutatja.
    text: Mentse a dokumentumot egy fájlba, amely az eredeti diagramméretet mutatja.
  - name: Módosítsa a dokumentum papírméretét A4-re, és frissítse az elrendezést.
    text: Módosítsa a dokumentum papírméretét A4-re, és frissítse az elrendezést.
  - name: Számolja ki az új diagram szélességét, amely az oldal szélességének 80 %-a,
      miközben megőrzi az eredeti képarányt.
    text: Számolja ki az új diagram szélességét, amely az oldal szélességének 80 %-a,
      miközben megőrzi az eredeti képarányt.
  - name: Ha az alakzat tartalmaz diagramot, alkalmazza a kiszámított szélességet
      és magasságot a méretezéshez.
    text: Ha az alakzat tartalmaz diagramot, alkalmazza a kiszámított szélességet
      és magasságot a méretezéshez.
  - name: Mentse a dokumentumot a diagram átméretezése után, hogy tükrözze az új oldalméretet.
    text: Mentse a dokumentumot a diagram átméretezése után, hogy tükrözze az új oldalméretet.
  type: HowTo
- questions:
  - answer: Igen. A `docBuilder.PageSetup.PaperSize` módosítása nem méretezi át automatikusan
      a meglévő alakzatokat, ezért újra kell számolni és saját kezűleg hozzárendelni
      a `chartContainer.Width` és `Height` értékeket, ahogy a példában látható.
    question: Kézzel kell-e átméretezni a diagramot a dokumentum papírméretének módosítása
      után?
  - answer: A kód a `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      értéket tárolja, majd az új szélesség meghatározása után kiszámítja a `newChartHeight
      = newChartWidth * originalAspectRatio` értéket.
    question: Hogyan tartja a kód a diagram eredeti szélesség‑magasság arányát átméretezéskor?
  - answer: Az `UpdatePageLayout()` arra kényszeríti az elrendező motorját, hogy újraértékelje
      az oldal méreteit, biztosítva, hogy a `docBuilder.PageSetup.PageWidth` tükrözze
      az új A4 szélességet, mielőtt a diagram mérete újraszámításra kerül.
    question: Miért hívják meg a `myDoc.UpdatePageLayout()` metódust a papírméret
      A4-re állítása után?
  - answer: Az `if (chartContainer.HasChart)` ellenőrzés megakadályozza, hogy a kód
      `Width` és `Height` értékeket állítson be, ha nincs diagram, ezáltal elkerülve
      a futásidejű kivételt.
    question: Mi történik, ha a beszúrt alakzat valójában nem tartalmaz diagramot?
  - answer: Természetesen—cserélje le a `0.8` szorzót bármelyik kívánt arányra; a
      többi átméretezési logika továbbra is megőrzi az eredeti képarányt.
    question: Megváltoztathatom a 80 %-os skálázási tényezőt egy másik értékre?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Word diagram átméretezése A4-re váltáskor
og_description: Tartsa diagramját arányosnak az automatikus átméretezéssel a dokumentum A4-re változtatása után.
og_image_alt: Képernyőkép, amely egy oszlopdiagramot mutat, amely automatikusan átméretezve van, hogy illeszkedjen egy A4 méretű Word dokumentumba az Aspose.Words for .NET használatával
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Diagram arányos átméretezése Wordben oldalméret változtatásakor az Aspose.Words for .NET használatával
Ez a bemutató azt mutatja be, hogyan lehet oszlopdiagramot beszúrni egy Word dokumentumba, a dokumentum oldalméretét A4-re váltani, és a diagramot automatikusan átméretezni, hogy arányos maradjon az új oldal szélességével. A lépések követésével láthatja, hogy a diagram a méreteit kézi skálázás nélkül módosítja, ezáltal konzisztens elrendezést biztosítva a különböző oldalformátumok között.

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

**Q: Kézzel kell-e átméretezni a diagramot a dokumentum papírméretének módosítása után?**  
A: Igen. A `docBuilder.PageSetup.PaperSize` módosítása nem méretezi át automatikusan a meglévő alakzatokat, ezért újra kell számolni és saját kezűleg hozzárendelni a `chartContainer.Width` és `Height` értékeket, ahogy a példában látható.

**Q: Hogyan tartja a kód a diagram eredeti szélesség‑magasság arányát átméretezéskor?**  
A: A kód a `originalAspectRatio = chartContainer.Height / chartContainer.Width` értéket tárolja, majd az új szélesség meghatározása után kiszámítja a `newChartHeight = newChartWidth * originalAspectRatio` értéket.

**Q: Miért hívják meg a `myDoc.UpdatePageLayout()` metódust a papírméret A4-re állítása után?**  
A: Az `UpdatePageLayout()` arra kényszeríti az elrendező motorját, hogy újraértékelje az oldal méreteit, biztosítva, hogy a `docBuilder.PageSetup.PageWidth` tükrözze az új A4 szélességet, mielőtt a diagram mérete újraszámításra kerül.

**Q: Mi történik, ha a beszúrt alakzat valójában nem tartalmaz diagramot?**  
A: Az `if (chartContainer.HasChart)` ellenőrzés megakadályozza, hogy a kód `Width` és `Height` értékeket állítson be, ha nincs diagram, ezáltal elkerülve a futásidejű kivételt.

**Q: Megváltoztathatom a 80 %-os skálázási tényezőt egy másik értékre?**  
A: Természetesen—cserélje le a `0.8` szorzót bármelyik kívánt arányra; a többi átméretezési logika továbbra is megőrzi az eredeti képarányt.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}