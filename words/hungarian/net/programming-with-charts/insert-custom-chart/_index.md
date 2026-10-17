---
title: Egyéni oszlopdiagram beszúrása Word dokumentumba az Aspose.Words for .NET használatával
weight: 310
limit:
description: Hozzon létre egy Word fájlt, szúrjon be egy oszlopdiagramot, cserélje le az adatokat egy egyéni tömbre, adjon hozzá címet, és mentse – mindezt az Aspose.Words for .NET segítségével.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Hozzon létre egy Word fájlt, szúrjon be egy oszlopdiagramot, cserélje
    le az adatokat egy egyéni tömbre, adjon hozzá címet, és mentse – mindezt az Aspose.Words
    for .NET segítségével.
  headline: Egyéni oszlopdiagram beszúrása Word dokumentumba az Aspose.Words for .NET
    használatával
  type: TechArticle
- description: Hozzon létre egy Word fájlt, szúrjon be egy oszlopdiagramot, cserélje
    le az adatokat egy egyéni tömbre, adjon hozzá címet, és mentse – mindezt az Aspose.Words
    for .NET segítségével.
  name: Egyéni oszlopdiagram beszúrása Word dokumentumba az Aspose.Words for .NET
    használatával
  steps:
  - name: Hozzon létre egy új Document objektumot és egy hozzá kapcsolt DocumentBuilder-t.
    text: Hozzon létre egy új Document objektumot és egy hozzá kapcsolt DocumentBuilder-t.
  - name: Szúrjon be egy 432×252 pont méretű oszlopdiagramot a dokumentumba, és szerezze
      meg a hozzá tartozó Chart objektumot.
    text: Szúrjon be egy 432×252 pont méretű oszlopdiagramot a dokumentumba, és szerezze
      meg a hozzá tartozó Chart objektumot.
  - name: Távolítsa el a diagram automatikusan generált minta sorozatát.
    text: Távolítsa el a diagram automatikusan generált minta sorozatát.
  - name: Határozza meg az X‑tengely kategória címkéit és a legendabejegyzéseket minden
      sorozathoz.
    text: Határozza meg az X‑tengely kategória címkéit és a legendabejegyzéseket minden
      sorozathoz.
  - name: Hozzon létre egy kétdimenziós tömböt, ahol minden sor egy sorozat értékeit
      tartalmazza.
    text: Hozzon létre egy kétdimenziós tömböt, ahol minden sor egy sorozat értékeit
      tartalmazza.
  - name: Iteráljon minden sorozaton, nyerje ki a sor értékeit a mátrixból, és adja
      hozzá a sorozatot a diagramhoz a megfelelő legendabejegyzéssel és X‑tengely
      címkékkel.
    text: Iteráljon minden sorozaton, nyerje ki a sor értékeit a mátrixból, és adja
      hozzá a sorozatot a diagramhoz a megfelelő legendabejegyzéssel és X‑tengely
      címkékkel.
  - name: Állítsa be a diagram címét 'Half‑Yearly Revenue' szövegre, és tegye láthatóvá.
    text: Állítsa be a diagram címét 'Half‑Yearly Revenue' szövegre, és tegye láthatóvá.
  - name: Mentse a testreszabott diagramot tartalmazó dokumentumot .docx fájlba.
    text: Mentse a testreszabott diagramot tartalmazó dokumentumot .docx fájlba.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` azt várja, hogy az értéktömb hossza megegyezzen az
      X‑tengely címkéinek számával, és minden legendabejegyzéshez pontosan egy sorozatot
      kell hozzáadni; ha nem egyezik, futásidőben `ArgumentException` kivételt dob.'
    question: Mi van, ha a `dataMatrix` sorai vagy oszlopai nem egyeznek a `legendEntries`
      vagy `xLabels` hosszával?
  - answer: Igen – cserélje le a `ChartType.Column` értéket a `docBuilder.InsertChart`‑ben
      bármely más `ChartType`‑ra (például `ChartType.Line`), és a későbbi `Series.Add`
      hívások ugyanúgy feltöltik az új diagramot.
    question: Használhatok másik diagramtípust, például vonaldiagramot, ugyanazzal
      az adatfeltöltési logikával?
  - answer: Állítsa be az `InsertChart` által visszaadott `Shape` `Width` és `Height`
      tulajdonságait (például `chartContainer.Width = 500; chartContainer.Height =
      300;`).
    question: Hogyan változtathatom meg a diagram méretét a beszúrás után?
  - answer: Állítsa be minden sorozatnál a `chartObj.Series[i].HasDataLabel = true;`
      értéket a hozzáadás után, vagy iteráljon a `chartObj.Series` elemein, és engedélyezze
      a `HasDataLabel` tulajdonságot az értékek megjelenítéséhez a diagramon.
    question: Van gyors módja annak, hogy adatcímkéket jelenítsen meg a diagram minden
      oszlopán?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Egyéni oszlopdiagram hozzáadása Word dokumentumhoz
og_description: Cserélje le a diagram alapértelmezett adatait a saját tömbjére, és állítson be címet pillanatok alatt.
og_image_alt: Képernyőkép, amely egy Aspose.Words for .NET használatával létrehozott egyéni oszlopdiagramot tartalmazó Word dokumentumot mutat
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Egyéni oszlopdiagram beszúrása Word dokumentumba az Aspose.Words for .NET használatával
Ez a bemutató végigvezet a Word dokumentum létrehozásán, egy oszlopdiagram beszúrásán, az alapértelmezett adatok törlésén, és a diagram testreszabott értékekkel való feltöltésén egy kétdimenziós tömbből – minden sort egy sorozathoz, minden oszlopot egy kategóriához rendelve. Megmutatja továbbá, hogyan adhat hozzá diagramcímet a fájl mentése előtt. Kövesse a lépéseket, hogy teljesen testreszabott diagramot hozzon létre közvetlenül a Word fájljában.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: Mi van, ha a `dataMatrix` sorai vagy oszlopai nem egyeznek a `legendEntries` vagy `xLabels` hosszával?**  
A: `Chart.Series.Add` azt várja, hogy az értéktömb hossza megegyezzen az X‑tengely címkéinek számával, és minden legendabejegyzéshez pontosan egy sorozatot kell hozzáadni; ha nem egyezik, futásidőben `ArgumentException` kivételt dob.

**Q: Használhatok másik diagramtípust, például vonaldiagramot, ugyanazzal az adatfeltöltési logikával?**  
A: Igen – cserélje le a `ChartType.Column` értéket a `docBuilder.InsertChart`‑ben bármely más `ChartType`‑ra (például `ChartType.Line`), és a későbbi `Series.Add` hívások ugyanúgy feltöltik az új diagramot.

**Q: Hogyan változtathatom meg a diagram méretét a beszúrás után?**  
A: Állítsa be az `InsertChart` által visszaadott `Shape` `Width` és `Height` tulajdonságait (például `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Van gyors módja annak, hogy adatcímkéket jelenítsen meg a diagram minden oszlopán?**  
A: Állítsa be minden sorozatnál a `chartObj.Series[i].HasDataLabel = true;` értéket a hozzáadás után, vagy iteráljon a `chartObj.Series` elemein, és engedélyezze a `HasDataLabel` tulajdonságot az értékek megjelenítéséhez a diagramon.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}