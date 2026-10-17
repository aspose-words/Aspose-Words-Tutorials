---
title: Chart sorozat eltávolítása Word dokumentumból az Aspose.Words for .NET használatával
weight: 510
limit:
description: Tanulja meg, hogyan törölhet egy adott adat sorozatot egy oszlopdiagramból egy Word dokumentumban az Aspose.Words for .NET segítségével.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Tanulja meg, hogyan törölhet egy adott adat sorozatot egy oszlopdiagramból
    egy Word dokumentumban az Aspose.Words for .NET segítségével.
  headline: Chart sorozat eltávolítása Word dokumentumból az Aspose.Words for .NET
    használatával
  type: TechArticle
- description: Tanulja meg, hogyan törölhet egy adott adat sorozatot egy oszlopdiagramból
    egy Word dokumentumban az Aspose.Words for .NET segítségével.
  name: Chart sorozat eltávolítása Word dokumentumból az Aspose.Words for .NET használatával
  steps:
  - name: Hozzon létre egy új Word Document-et és egy hozzá kapcsolódó DocumentBuilder-t.
    text: Hozzon létre egy új Word Document-et és egy hozzá kapcsolódó DocumentBuilder-t.
  - name: Szúrjon be egy 432×252 pont méretű oszlopdiagramot, és szerezze meg a Chart
      objektumot a további módosításokhoz.
    text: Szúrjon be egy 432×252 pont méretű oszlopdiagramot, és szerezze meg a Chart
      objektumot a további módosításokhoz.
  - name: Adja meg a sorozat nulláról induló indexét, amelyet el kell távolítani (a
      második sorozat).
    text: Adja meg a sorozat nulláról induló indexét, amelyet el kell távolítani (a
      második sorozat).
  - name: Ha az index érvényes, hívja meg a RemoveAt metódust a diagram Series gyűjteményén,
      hogy törölje azt a sorozatot.
    text: Ha az index érvényes, hívja meg a RemoveAt metódust a diagram Series gyűjteményén,
      hogy törölje azt a sorozatot.
  - name: Mentse a frissített dokumentumot egy .docx fájlba.
    text: Mentse a frissített dokumentumot egy .docx fájlba.
  type: HowTo
- questions:
  - answer: Az `if` ellenőrzés (`targetSeriesIdx < columnChart.Series.Count`) hibás
      lesz, így a `RemoveAt` soha nem kerül meghívásra, és a diagram változatlan marad.
    question: Mi történik, ha olyan indexet adok meg, amely megegyezik a diagram sorozatainak
      számával?
  - answer: Igen, a `columnChart.Series.RemoveAt` után a jelmagyarázat újra generálódik,
      hogy tükrözze a megmaradt sorozatokat, így az eltávolított elem eltűnik a jelmagyarázatból.
    question: Az sorozat eltávolítása automatikusan frissíti a diagram jelmagyarázatát?
  - answer: A kód bármely olyan diagramtípusnál működik, amely támogatja a `Series`
      gyűjteményt; csak cserélje le a `ChartType.Column` értéket a kívánt típusra
      a diagram beszúrásakor.
    question: Használhatom ugyanazt a kódot egy vonal- vagy kördiagram sorozatának
      törlésére?
  - answer: A nulla sorozatú diagram továbbra is érvényes `Shape`, és mentésre kerül,
      de a végső dokumentumban üresnek fog megjelenni.
    question: Ha eltávolítom a diagram egyetlen sorozatát, a diagram továbbra is helyesen
      lesz mentve?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Chart sorozat törlése Word dokumentumban
og_description: Lépésről lépésre útmutató egy adat sorozat eltávolításához egy Word diagramról az Aspose.Words for .NET használatával.
og_image_alt: Útmutató, amely bemutatja, hogyan törölhet egy adott adat sorozatot egy oszlopdiagramból egy Word dokumentumban az Aspose.Words for .NET használatával.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chart sorozat eltávolítása Word dokumentumból az Aspose.Words for .NET használatával
Ez a bemutató megmutatja, hogyan hozhat létre egy Word dokumentumot, adjon hozzá egy oszlopdiagramot a DocumentBuilder segítségével, majd a ChartSeriesCollection.RemoveAt metódussal töröljön egy adott adat sorozatot a diagramról. A végére egy mentett dokumentumot kap, amelyből a nemkívánatos sorozat eltávolításra került, így pontosan irányíthatja a diagram tartalmát közvetlenül a .NET kódból.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Mi történik, ha olyan indexet adok meg, amely megegyezik a diagram sorozatainak számával?**  
A: Az `if` ellenőrzés (`targetSeriesIdx < columnChart.Series.Count`) hibás lesz, így a `RemoveAt` soha nem kerül meghívásra, és a diagram változatlan marad.

**Q: Az sorozat eltávolítása automatikusan frissíti a diagram jelmagyarázatát?**  
A: Igen, a `columnChart.Series.RemoveAt` után a jelmagyarázat újra generálódik, hogy tükrözze a megmaradt sorozatokat, így az eltávolított elem eltűnik a jelmagyarázatból.

**Q: Használhatom ugyanazt a kódot egy vonal- vagy kördiagram sorozatának törlésére?**  
A: A kód bármely olyan diagramtípusnál működik, amely támogatja a `Series` gyűjteményt; csak cserélje le a `ChartType.Column` értéket a kívánt típusra a diagram beszúrásakor.

**Q: Ha eltávolítom a diagram egyetlen sorozatát, a diagram továbbra is helyesen lesz mentve?**  
A: A nulla sorozatú diagram továbbra is érvényes `Shape`, és mentésre kerül, de a végső dokumentumban üresnek fog megjelenni.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}