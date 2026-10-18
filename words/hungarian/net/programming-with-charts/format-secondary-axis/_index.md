---
title: Másodlagos X‑tengely formázása és a megjelenítési egységek ezrekre állítása Word vonaldiagramokban az Aspose.Words for .NET használatával
weight: 710
limit:
description: Hozzon létre egy Word vonaldiagramot, adjon hozzá egy másodlagos X‑tengelyt, állítsa be a megjelenítési egységet ezrekre, és alkalmazzon egy egyéni numerikus formátumot az Aspose.Words for .NET segítségével.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Hozzon létre egy Word vonaldiagramot, adjon hozzá egy másodlagos X‑tengelyt,
    állítsa be a megjelenítési egységet ezrekre, és alkalmazzon egy egyéni numerikus
    formátumot az Aspose.Words for .NET segítségével.
  headline: Másodlagos X‑tengely formázása és a megjelenítési egységek ezrekre állítása
    Word vonaldiagramokban az Aspose.Words for .NET használatával
  type: TechArticle
- description: Hozzon létre egy Word vonaldiagramot, adjon hozzá egy másodlagos X‑tengelyt,
    állítsa be a megjelenítési egységet ezrekre, és alkalmazzon egy egyéni numerikus
    formátumot az Aspose.Words for .NET segítségével.
  name: Másodlagos X‑tengely formázása és a megjelenítési egységek ezrekre állítása
    Word vonaldiagramokban az Aspose.Words for .NET használatával
  steps:
  - name: Hozzon létre egy új Document objektumot és egy DocumentBuilder-t a Word
      fájl építésének megkezdéséhez.
    text: Hozzon létre egy új Document objektumot és egy DocumentBuilder-t a Word
      fájl építésének megkezdéséhez.
  - name: Illesszen be egy 500×300 méretű vonaldiagramot a dokumentumba, és szerezze
      meg a Chart objektumot.
    text: Illesszen be egy 500×300 méretű vonaldiagramot a dokumentumba, és szerezze
      meg a Chart objektumot.
  - name: Távolítsa el az alapértelmezett demo sorozatot, amelyet az Aspose.Words
      automatikusan hozzáad.
    text: Távolítsa el az alapértelmezett demo sorozatot, amelyet az Aspose.Words
      automatikusan hozzáad.
  - name: Definiáljon egy tömböt a kategória címkékkel, amelyeket az X‑tengelyhez
      használ.
    text: Definiáljon egy tömböt a kategória címkékkel, amelyeket az X‑tengelyhez
      használ.
  - name: Adja hozzá az elsődleges adat sorozatot "Main Data" névvel a címkék és értékek
      felhasználásával.
    text: Adja hozzá az elsődleges adat sorozatot "Main Data" névvel a címkék és értékek
      felhasználásával.
  - name: Hozzon létre egy másodlagos sorozatcsoportot Line típusúként, és rendelje
      hozzá a másodlagos tengelycsoporthoz.
    text: Hozzon létre egy másodlagos sorozatcsoportot Line típusúként, és rendelje
      hozzá a másodlagos tengelycsoporthoz.
  - name: Állítsa be a másodlagos X‑tengely megjelenítési egységét ezrekre, hogy az
      értékek K‑ban jelenjenek meg.
    text: Állítsa be a másodlagos X‑tengely megjelenítési egységét ezrekre, hogy az
      értékek K‑ban jelenjenek meg.
  - name: Alkalmazzon egy egyéni numerikus formátumot "#,##0.0" a másodlagos X‑tengely
      jelölőcímkéire.
    text: Alkalmazzon egy egyéni numerikus formátumot "#,##0.0" a másodlagos X‑tengely
      jelölőcímkéire.
  - name: Opcionálisan adjon hozzá egy segéd adat sorozatot a másodlagos csoporthoz.
    text: Opcionálisan adjon hozzá egy segéd adat sorozatot a másodlagos csoporthoz.
  - name: Mentse a dokumentumot .docx fájlba.
    text: Mentse a dokumentumot .docx fájlba.
  type: HowTo
- questions:
  - answer: Nem – az `AxisX` beállítások a `ChartSeriesGroup`-hoz tartoznak, így a
      `secondaryGroup.AxisX.DisplayUnit.Unit` és a `secondaryGroup.AxisX.NumberFormat.FormatCode`
      értékeket sorozat hozzáadása előtt vagy után is beállíthatja; a konfiguráció
      mindenképpen a csoport tengelyére lesz alkalmazva.
    question: Kell-e a másodlagos sorozatot hozzáadni, mielőtt beállítanám a megjelenítési
      egységet és a számformátumot a másodlagos X‑tengelyen?
  - answer: Igen – rendelj hozzá bármely `AxisBuiltInUnit` értéket, például `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` a tengely értékeinek millióban való megjelenítéséhez
      ezrek helyett.
    question: Használhatok más beépített egységet, például milliót, a másodlagos X‑tengelyhez?
  - answer: Nem – a formátumkód csak arra a tengelyre kerül alkalmazásra, amelyet
      módosít (`secondaryGroup.AxisX.NumberFormat.FormatCode`), így az elsődleges
      X‑tengely megőrzi az alapértelmezett formázását.
    question: A `"#,##0.0"` egyéni formátum hatással lesz az elsődleges X‑tengely
      címkéire?
  - answer: A diagram a hozzáadott sorozatok mellett az alapértelmezett demo sorozatot
      is tartalmazni fogja, ami felesleges vonalakhoz és nem egyező kategóriákhoz
      vezethet; a gyűjtemény törlése biztosítja, hogy csak a kívánt adatok jelenjenek
      meg.
    question: Mi történik, ha elfelejtem törölni a demo sorozatot a `lineChart.Series.Clear();`
      paranccsal?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Másodlagos X‑tengely formázása és az egységek ezrekre állítása
og_description: Adjon egy másodlagos X‑tengelyt egy Word vonaldiagramhoz, és formázza a címkéket ezrekben egy egyéni mintával.
og_image_alt: Útmutató, amely bemutatja, hogyan adjon hozzá egy másodlagos X‑tengelyt egy Word vonaldiagramhoz, és hogyan formázza a címkéket ezrekben megjelenő egységekkel az Aspose.Words for .NET használatával
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Másodlagos X‑tengely formázása és a megjelenítési egységek ezrekre állítása Word vonaldiagramokban az Aspose.Words for .NET használatával
Ez a bemutató végigvezet a Word dokumentum létrehozásán, amely vonaldiagramot tartalmaz, a másodlagos X‑tengely hozzáadásán és annak beállításán, hogy ezrekben jelenítse meg az értékeket. Megtanulja, hogyan alkalmazzon egy egyéni numerikus formátumot a másodlagos tengelycímkékre, így pontosan szabályozhatja az adatok megjelenítését. Kövesse a lépéseket a többtengelyes diagramok olvashatóságának javításához a Word jelentéseiben.

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

**Q: Kell-e a másodlagos sorozatot hozzáadni, mielőtt beállítanám a megjelenítési egységet és a számformátumot a másodlagos X‑tengelyen?**  
A: Nem – az `AxisX` beállítások a `ChartSeriesGroup`-hoz tartoznak, így a `secondaryGroup.AxisX.DisplayUnit.Unit` és a `secondaryGroup.AxisX.NumberFormat.FormatCode` értékeket sorozat hozzáadása előtt vagy után is beállíthatja; a konfiguráció mindenképpen a csoport tengelyére lesz alkalmazva.

**Q: Használhatok más beépített egységet, például milliót, a másodlagos X‑tengelyhez?**  
A: Igen – rendelj hozzá bármely `AxisBuiltInUnit` értéket, például `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` a tengely értékeinek millióban való megjelenítéséhez ezrek helyett.

**Q: A `"#,##0.0"` egyéni formátum hatással lesz az elsődleges X‑tengely címkéire?**  
A: Nem – a formátumkód csak arra a tengelyre kerül alkalmazásra, amelyet módosít (`secondaryGroup.AxisX.NumberFormat.FormatCode`), így az elsődleges X‑tengely megőrzi az alapértelmezett formázását.

**Q: Mi történik, ha elfelejtem törölni a demo sorozatot a `lineChart.Series.Clear();` paranccsal?**  
A: A diagram a hozzáadott sorozatok mellett az alapértelmezett demo sorozatot is tartalmazni fogja, ami felesleges vonalakhoz és nem egyező kategóriákhoz vezethet; a gyűjtemény törlése biztosítja, hogy csak a kívánt adatok jelenjenek meg.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}