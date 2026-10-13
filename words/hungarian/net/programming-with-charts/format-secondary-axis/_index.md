---
title: Másodlagos Y‑tengely formázása pénznemként Word diagramon az Aspose.Words for .NET használatával
weight: 710
limit:
description: Tanulja meg, hogyan adjon hozzá és formázzon egy másodlagos Y‑tengelyt pénznemként egy Word vonaldiagramon az Aspose.Words for .NET segítségével.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Tanulja meg, hogyan adjon hozzá és formázzon egy másodlagos Y‑tengelyt
    pénznemként egy Word vonaldiagramon az Aspose.Words for .NET segítségével.
  headline: Másodlagos Y‑tengely formázása pénznemként Word diagramon az Aspose.Words
    for .NET használatával
  type: TechArticle
- description: Tanulja meg, hogyan adjon hozzá és formázzon egy másodlagos Y‑tengelyt
    pénznemként egy Word vonaldiagramon az Aspose.Words for .NET segítségével.
  name: Másodlagos Y‑tengely formázása pénznemként Word diagramon az Aspose.Words
    for .NET használatával
  steps:
  - name: Hozzon létre egy új, üres Word dokumentumot és egy DocumentBuilder‑t a szerkesztéséhez.
    text: Hozzon létre egy új, üres Word dokumentumot és egy DocumentBuilder‑t a szerkesztéséhez.
  - name: Szúrjon be egy 450×250 pont méretű vonaldiagramot a dokumentumba, és szerezze
      meg a hozzá tartozó Chart objektumot.
    text: Szúrjon be egy 450×250 pont méretű vonaldiagramot a dokumentumba, és szerezze
      meg a hozzá tartozó Chart objektumot.
  - name: Távolítsa el az alapértelmezett helyőrző sorozatot, amelyet az Aspose egy
      új diagramhoz ad.
    text: Távolítsa el az alapértelmezett helyőrző sorozatot, amelyet az Aspose egy
      új diagramhoz ad.
  - name: Határozza meg a negyedéves címkéket, és adjon hozzá egy elsődleges adat
      sorozatot mintaértékekkel a diagramhoz.
    text: Határozza meg a negyedéves címkéket, és adjon hozzá egy elsődleges adat
      sorozatot mintaértékekkel a diagramhoz.
  - name: Hozzon létre egy Line típusú másodlagos sorozatcsoportot, és rendelje hozzá
      a másodlagos tengelycsoporthoz.
    text: Hozzon létre egy Line típusú másodlagos sorozatcsoportot, és rendelje hozzá
      a másodlagos tengelycsoporthoz.
  - name: Rejtse el a másodlagos X‑tengelyt, hogy csak a másodlagos Y‑tengely legyen
      látható.
    text: Rejtse el a másodlagos X‑tengelyt, hogy csak a másodlagos Y‑tengely legyen
      látható.
  - name: Jelenítse meg a másodlagos Y‑tengely címét, és állítsa be a szövegét \"Sales
      (USD)\"-re.
    text: Jelenítse meg a másodlagos Y‑tengely címét, és állítsa be a szövegét \"Sales
      (USD)\"-re.
  - name: Állítsa be a másodlagos Y‑tengely számformátumát egy két tizedesjegyű pénznem
      mintára, és válassza le a forrásformázástól.
    text: Állítsa be a másodlagos Y‑tengely számformátumát egy két tizedesjegyű pénznem
      mintára, és válassza le a forrásformázástól.
  - name: Adjon egy segéd sorozatot a másodlagos csoporthoz, amely adatokat biztosít
      a másodlagos Y‑tengelyhez.
    text: Adjon egy segéd sorozatot a másodlagos csoporthoz, amely adatokat biztosít
      a másodlagos Y‑tengelyhez.
  - name: Mentse el a kész dokumentumot a ProfitChart.docx nevű fájlba az aktuális
      könyvtárban.
    text: Mentse el a kész dokumentumot a ProfitChart.docx nevű fájlba az aktuális
      könyvtárban.
  type: HowTo
- questions:
  - answer: A diagram megtartja az alapértelmezett helyőrző sorozatot, amelyet az
      Aspose.Words beszúr, így az egyéni \"Main Series\" a nem kívánt adatpontokkal
      együtt jelenik meg.
    question: Mi történik, ha kihagyom a `lineChart.Series.Clear()` hívást?
  - answer: Állítsa be a `secondarySeriesGroup.AxisX.Hidden = false;` értéket (vagy
      egyszerűen hagyja ki azt a sort, amely `true`‑ra állítja).
    question: Hogyan jeleníthetem meg a másodlagos X‑tengelyt a rejtés helyett?
  - answer: Igen – módosítsa a formátum karakterláncot, például `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"\\\"€\\\"#,##0.00\";` euróhoz, vagy állítsa be a mintát a saját területi
      beállításaihoz.
    question: Használhatok más pénznem szimbólumot vagy formátumot a másodlagos Y‑tengelyhez?
  - answer: Ha az `IsLinkedToSource` igaz, a tengely az alapadatforrás számformátumát
      örökli, felülbírálva minden egyéni `FormatCode`-ot; ha hamisra állítja, a diagram
      a megadott formátumot fogja használni.
    question: Miért kell beállítani az `IsLinkedToSource = false` értéket egy egyéni
      számformátum alkalmazásakor?
  - answer: Igen, állítsa be a `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      értéket (vagy a `Right`‑et az alapértelmezetthez), hogy meghatározza, melyik
      oldalra kerül a tengely.
    question: Lehetséges a másodlagos Y‑tengelyt a diagram bal oldalára helyezni?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Diagram másodlagos tengelyének formázása pénznemként
og_description: Tanulja meg, hogyan adjon egy másodlagos Y‑tengelyt egy Word vonaldiagramhoz, és formázza azt pénznemként két tizedesjeggyel.
og_image_alt: Képernyőkép, amely egy Word vonaldiagramot mutat, ahol a másodlagos Y‑tengely pénznemként van formázva az Aspose.Words for .NET használatával
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Másodlagos Y‑tengely formázása pénznemként Word diagramon az Aspose.Words for .NET használatával
Ebben a bemutatóban láthatja, hogyan építsen fel egy Word dokumentumot, szúrjon be egy vonaldiagramot, adjon hozzá egy másodlagos Y‑tengelyt, formázza azt a tengelyt pénznemként két tizedesjeggyel, és kössön hozzá egy másodlagos adat sorozatot az Aspose.Words for .NET segítségével. A másodlagos tengely pénznemként való formázása lehetővé teszi, hogy a pénzügyi adatokat egyértelműen mutassa be az elsődleges sorozattal együtt. Kövesse a lépésről‑lépésre kódot, hogy a diagram közvetlenül a generált dokumentumban jelenjen meg.

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

**Q: Mi történik, ha kihagyom a `lineChart.Series.Clear()` hívást?**  
A: A diagram megtartja az alapértelmezett helyőrző sorozatot, amelyet az Aspose.Words beszúr, így az egyéni \"Main Series\" a nem kívánt adatpontokkal együtt jelenik meg.

**Q: Hogyan jeleníthetem meg a másodlagos X‑tengelyt a rejtés helyett?**  
A: Állítsa be a `secondarySeriesGroup.AxisX.Hidden = false;` értéket (vagy egyszerűen hagyja ki azt a sort, amely `true`‑ra állítja).

**Q: Használhatok más pénznem szimbólumot vagy formátumot a másodlagos Y‑tengelyhez?**  
A: Igen – módosítsa a formátum karakterláncot, például `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";` euróhoz, vagy állítsa be a mintát a saját területi beállításaihoz.

**Q: Miért kell beállítani az `IsLinkedToSource = false` értéket egy egyéni számformátum alkalmazásakor?**  
A: Ha az `IsLinkedToSource` igaz, a tengely az alapadatforrás számformátumát örökli, felülbírálva minden egyéni `FormatCode`-ot; ha hamisra állítja, a diagram a megadott formátumot fogja használni.

**Q: Lehetséges a másodlagos Y‑tengelyt a diagram bal oldalára helyezni?**  
A: Igen, állítsa be a `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` értéket (vagy a `Right`‑et az alapértelmezetthez), hogy meghatározza, melyik oldalra kerül a tengely.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}