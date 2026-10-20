---
title: Minta oszlopdiagram beszúrása Word dokumentumba az Aspose.Words for .NET használatával
weight: 410
limit:
description: Lépésről lépésre útmutató egy Word fájl létrehozásához, alapértelmezett oszlopdiagram beszúrásához a DocumentBuilder.InsertChart segítségével, a diagram objektum eléréséhez és .docx formátumban való mentéshez.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lépésről lépésre útmutató egy Word fájl létrehozásához, alapértelmezett
    oszlopdiagram beszúrásához a DocumentBuilder.InsertChart segítségével, a diagram
    objektum eléréséhez és .docx formátumban való mentéshez.
  headline: Minta oszlopdiagram beszúrása Word dokumentumba az Aspose.Words for .NET
    használatával
  type: TechArticle
- description: Lépésről lépésre útmutató egy Word fájl létrehozásához, alapértelmezett
    oszlopdiagram beszúrásához a DocumentBuilder.InsertChart segítségével, a diagram
    objektum eléréséhez és .docx formátumban való mentéshez.
  name: Minta oszlopdiagram beszúrása Word dokumentumba az Aspose.Words for .NET használatával
  steps:
  - name: Hozzon létre egy üres Word dokumentumot és egy DocumentBuilder objektumot
      a szerkesztéshez.
    text: Hozzon létre egy üres Word dokumentumot és egy DocumentBuilder objektumot
      a szerkesztéshez.
  - name: Szúrjon be egy 432 × 252 pont méretű oszlopdiagramot a dokumentumba.
    text: Szúrjon be egy 432 × 252 pont méretű oszlopdiagramot a dokumentumba.
  - name: A beillesztett alakzatból szerezze meg a Chart objektumot a további testreszabáshoz,
      ha szükséges.
    text: A beillesztett alakzatból szerezze meg a Chart objektumot a további testreszabáshoz,
      ha szükséges.
  - name: Mentse a dokumentumot, amely most már tartalmazza a beillesztett oszlopdiagramot,
      .docx fájlba.
    text: Mentse a dokumentumot, amely most már tartalmazza a beillesztett oszlopdiagramot,
      .docx fájlba.
  type: HowTo
- questions:
  - answer: A méretek pontban vannak megadva (1 pont = 1/72 hüvelyk), így 432 pt ≈
      6 hüvelyk és 252 pt ≈ 3,5 hüvelyk.
    question: Milyen mértékegységet használnak a szélesség és magasság paraméterek
      (432, 252) az InsertChart esetén?
  - answer: Igen – a beillesztés után a Chart objektum a `chartContainer.Chart` segítségével
      elérhető; módosíthatja a SeriesCollection, Categories és Values részeket a mintaadatok
      cseréjéhez.
    question: Módosíthatom a diagram adatait az InsertChart alapértelmezett adatkészletével
      való meghívása után?
  - answer: Egyszerűen cserélje le a `ChartType.Column` értéket egy másik enum értékre,
      például `ChartType.Line`-ra az `InsertChart` hívásban.
    question: Lehetséges-e más típusú diagramot (például vonaldiagramot) beszúrni
      ugyanazzal a kóddal?
  - answer: Nem – a `docBuilder.InsertChart` automatikusan beágyazza a diagramot egy
      `Shape`-be; a `wordDoc.Save` hívás a diagramot a dokumentummal együtt menti.
    question: Kell-e további metódust meghívni a diagram beágyazásához a dokumentum
      mentése előtt?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Minta oszlopdiagram beszúrása Word dokumentumba
og_description: Pár percen belül adjon hozzá egy kész oszlopdiagramot egy Word dokumentumhoz az Aspose.Words for .NET segítségével.
og_image_alt: Képernyőkép, amely egy Aspose.Words for .NET használatával beillesztett minta oszlopdiagramot tartalmazó Word dokumentumot mutat.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Minta oszlopdiagram beszúrása Word dokumentumba az Aspose.Words for .NET használatával
Ez az útmutató végigvezet a új Word dokumentum létrehozásán és egy alapértelmezett oszlopdiagram beszúrásán a DocumentBuilder.InsertChart segítségével. Megmutatja, hogyan szerezhető meg a beágyazott Chart objektum a további manipulációhoz. Végül a leírás bemutatja, hogyan menthető a dokumentum .docx fájlként.

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

**Q: Milyen mértékegységet használnak a szélesség és magasság paraméterek (432, 252) az InsertChart esetén?**  
A: A méretek pontban vannak megadva (1 pont = 1/72 hüvelyk), így 432 pt ≈ 6 hüvelyk és 252 pt ≈ 3,5 hüvelyk.

**Q: Módosíthatom a diagram adatait az InsertChart alapértelmezett adatkészletével való meghívása után?**  
A: Igen – a beillesztés után a Chart objektum a `chartContainer.Chart` segítségével elérhető; módosíthatja a SeriesCollection, Categories és Values részeket a mintaadatok cseréjéhez.

**Q: Lehetséges-e más típusú diagramot (például vonaldiagramot) beszúrni ugyanazzal a kóddal?**  
A: Egyszerűen cserélje le a `ChartType.Column` értéket egy másik enum értékre, például `ChartType.Line`-ra az `InsertChart` hívásban.

**Q: Kell-e további metódust meghívni a diagram beágyazásához a dokumentum mentése előtt?**  
A: Nem – a `docBuilder.InsertChart` automatikusan beágyazza a diagramot egy `Shape`-be; a `wordDoc.Save` hívás a diagramot a dokumentummal együtt menti.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}