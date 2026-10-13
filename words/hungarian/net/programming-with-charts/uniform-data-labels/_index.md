---
title: Egységes adatcímkék beállítása oszlopdiagramon az Aspose.Words for .NET használatával
weight: 110
limit:
description: Tanulja meg, hogyan hozhat létre Word oszlopdiagramot, és alkalmazzon egységes adatcímke betűméretet és színt az összes sorozatra az Aspose.Words for .NET segítségével.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Tanulja meg, hogyan hozhat létre Word oszlopdiagramot, és alkalmazzon
    egységes adatcímke betűméretet és színt az összes sorozatra az Aspose.Words for
    .NET segítségével.
  headline: Egységes adatcímkék beállítása oszlopdiagramon az Aspose.Words for .NET
    használatával
  type: TechArticle
- description: Tanulja meg, hogyan hozhat létre Word oszlopdiagramot, és alkalmazzon
    egységes adatcímke betűméretet és színt az összes sorozatra az Aspose.Words for
    .NET segítségével.
  name: Egységes adatcímkék beállítása oszlopdiagramon az Aspose.Words for .NET használatával
  steps:
  - name: Hozzon létre egy új üres Word dokumentumot és egy DocumentBuilder objektumot
      a szerkesztéséhez.
    text: Hozzon létre egy új üres Word dokumentumot és egy DocumentBuilder objektumot
      a szerkesztéséhez.
  - name: Szúrjon be egy 500×300 méretű oszlopdiagramot a dokumentumba, és szerezze
      meg a hozzá tartozó Chart objektumot.
    text: Szúrjon be egy 500×300 méretű oszlopdiagramot a dokumentumba, és szerezze
      meg a hozzá tartozó Chart objektumot.
  - name: Távolítsa el az alapértelmezett minta sorozatot, amelyet az Aspose.Words
      egy új diagramhoz ad.
    text: Távolítsa el az alapértelmezett minta sorozatot, amelyet az Aspose.Words
      egy új diagramhoz ad.
  - name: Határozza meg a kategória címkéket, és adjon hozzá két adat sorozatot (Item
      Alpha és Item Beta) a diagramhoz a megfelelő értékekkel.
    text: Határozza meg a kategória címkéket, és adjon hozzá két adat sorozatot (Item
      Alpha és Item Beta) a diagramhoz a megfelelő értékekkel.
  - name: Állítsa be az alap betűméretet és színt, amely az összes adatcímkére alkalmazásra
      kerül.
    text: Állítsa be az alap betűméretet és színt, amely az összes adatcímkére alkalmazásra
      kerül.
  - name: Engedélyezze az adatcímkéket minden sorozathoz, jelenítse meg a numerikus
      értéket, és alkalmazza az előre definiált betűméretet és színt.
    text: Engedélyezze az adatcímkéket minden sorozathoz, jelenítse meg a numerikus
      értéket, és alkalmazza az előre definiált betűméretet és színt.
  - name: Mentse a dokumentumot .docx fájlba.
    text: Mentse a dokumentumot .docx fájlba.
  type: HowTo
- questions:
  - answer: Az `InsertChart` egy diagramot hoz létre alapértelmezett minta sorozattal;
      annak törlése eltávolítja ezt a helyőrzőt, így a diagram csak az általad hozzáadott
      sorozatokat (`Item Alpha` és `Item Beta`) jeleníti meg.
    question: Miért kell meghívnom a `chart.Series.Clear()` metódust, mielőtt saját
      sorozatot adok hozzá?
  - answer: Cserélje le a `Color.White` értéket bármely `System.Drawing.Color` értékre,
      például `Color.Black` vagy `Color.FromArgb(255, 30, 144, 255)`; az új szín a
      `series.DataLabels.Font.Color` segítségével kerül alkalmazásra a cikluson belül.
    question: Hogyan változtathatom meg az adatcímke színét a fehér helyett másra?
  - answer: Az adatcímkék el lesznek rejtve, így a beállított betűstílus láthatatlanná
      válik; a címkék (és a stílusuk) megjelenítéséhez a `HasDataLabels` értékét `true`-ra
      kell hagyni.
    question: Mi történik, ha a betűméret és szín beállítása után a `series.HasDataLabels
      = false` értéket adom meg?
  - answer: Igen – minden `ChartSeries` saját `DataLabels` objektummal rendelkezik,
      ezért az első ciklus után hozzáadott sorozatoknak is be kell állítani a `HasDataLabels`,
      `ShowValue` és a betűstílus tulajdonságokat, akár újra végigmenve a sorozatokon,
      akár a stílusokat egy segédmetódusba kiszervezve.
    question: Újra kell-e végigmenni a sorozatokon, ha később a kódban egy további
      sorozatot adok hozzá?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Egységes adatcímkék alkalmazása Word diagramra
og_description: Az Aspose.Words for .NET segítségével gyorsan adjon minden diagramcímkének azonos betűméretet és színt.
og_image_alt: Útmutató, amely egy Word dokumentumot mutat be oszlopdiagrammal, ahol az összes adatcímke ugyanazt a betűméretet és színt használja, az Aspose.Words for .NET használatával létrehozva.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Egységes adatcímkék beállítása oszlopdiagramon az Aspose.Words for .NET használatával
Ez a bemutató azt mutatja be, hogyan generálhatunk Word dokumentumot, szúrhatunk be oszlopdiagramot, és adhatunk hozzá egyéni adat sorozatokat az Aspose.Words for .NET segítségével. Ezután bemutatja az alapértelmezett adatcímke betűméret és szín definiálását, hogy a diagram minden sorozata azonos címkéket jelenítsen meg. Egyetlen stílus alkalmazásával biztosítható a következetes megjelenés az egész diagramon.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: Miért kell meghívnom a `chart.Series.Clear()` metódust, mielőtt saját sorozatot adok hozzá?**  
A: Az `InsertChart` egy diagramot hoz létre alapértelmezett minta sorozattal; annak törlése eltávolítja ezt a helyőrzőt, így a diagram csak az általad hozzáadott sorozatokat (`Item Alpha` és `Item Beta`) jeleníti meg.

**Q: Hogyan változtathatom meg az adatcímke színét a fehér helyett másra?**  
A: Cserélje le a `Color.White` értéket bármely `System.Drawing.Color` értékre, például `Color.Black` vagy `Color.FromArgb(255, 30, 144, 255)`; az új szín a `series.DataLabels.Font.Color` segítségével kerül alkalmazásra a cikluson belül.

**Q: Mi történik, ha a betűméret és szín beállítása után a `series.HasDataLabels = false` értéket adom meg?**  
A: Az adatcímkék el lesznek rejtve, így a beállított betűstílus láthatatlanná válik; a címkék (és a stílusuk) megjelenítéséhez a `HasDataLabels` értékét `true`-ra kell hagyni.

**Q: Újra kell-e végigmenni a sorozatokon, ha később a kódban egy további sorozatot adok hozzá?**  
A: Igen – minden `ChartSeries` saját `DataLabels` objektummal rendelkezik, ezért az első ciklus után hozzáadott sorozatoknak is be kell állítani a `HasDataLabels`, `ShowValue` és a betűstílus tulajdonságokat, akár újra végigmenve a sorozatokon, akár a stílusokat egy segédmetódusba kiszervezve.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}