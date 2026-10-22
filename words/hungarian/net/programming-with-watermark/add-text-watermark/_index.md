---
title: Piros átlós szöveges vízjel hozzáadása Word-dokumentumokhoz az Aspose.Words for .NET használatával
weight: 110
limit:
description: Automatikusan alkalmazzon piros átlós szöveges vízjelet minden, kötegben generált Word-fájlra az Aspose.Words for .NET használatával.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Automatikusan alkalmazzon piros átlós szöveges vízjelet minden, kötegben
    generált Word-fájlra az Aspose.Words for .NET használatával.
  headline: Piros átlós szöveges vízjel hozzáadása Word-dokumentumokhoz az Aspose.Words
    for .NET használatával
  type: TechArticle
- description: Automatikusan alkalmazzon piros átlós szöveges vízjelet minden, kötegben
    generált Word-fájlra az Aspose.Words for .NET használatával.
  name: Piros átlós szöveges vízjel hozzáadása Word-dokumentumokhoz az Aspose.Words
    for .NET használatával
  steps:
  - name: Hozza létre a \"GeneratedReports\" mappát, ahová a kimeneti fájlok mentésre
      kerülnek.
    text: Hozza létre a \"GeneratedReports\" mappát, ahová a kimeneti fájlok mentésre
      kerülnek.
  - name: Indítson egy ciklust, amely három különálló dokumentumot generál.
    text: Indítson egy ciklust, amely három különálló dokumentumot generál.
  - name: Hozzon létre egy új, üres Word-dokumentum objektumot.
    text: Hozzon létre egy új, üres Word-dokumentum objektumot.
  - name: Használja a DocumentBuilder-t, hogy egy címsort és egy leírást írjon a dokumentumba.
    text: Használja a DocumentBuilder-t, hogy egy címsort és egy leírást írjon a dokumentumba.
  - name: Határozza meg a vízjel megjelenését, beleértve a betűtípust, méretet, színt
      és az átlós elrendezést.
    text: Határozza meg a vízjel megjelenését, beleértve a betűtípust, méretet, színt
      és az átlós elrendezést.
  - name: Alkalmazza a beállított piros átlós vízjelet a \"PROTECTED\" szöveggel a
      dokumentumra.
    text: Alkalmazza a beállított piros átlós vízjelet a \"PROTECTED\" szöveggel a
      dokumentumra.
  - name: Mentse a vízjelezett dokumentumot a \"GeneratedReports\" mappába egy egyedi
      fájlnévvel.
    text: Mentse a vízjelezett dokumentumot a \"GeneratedReports\" mappába egy egyedi
      fájlnévvel.
  - name: Zárja le a ciklust a jelenlegi dokumentum feldolgozása után.
    text: Zárja le a ciklust a jelenlegi dokumentum feldolgozása után.
  type: HowTo
- questions:
  - answer: Az IsSemitrasparent meghatározza, hogy a vízjel részben átlátszó módon
      jelenik-e meg; **true**‑ra állítva a szöveg félig átlátszó lesz, így az alatta
      lévő tartalom jobban olvasható marad.
    question: Mit szabályoz a **IsSemitrasparent** beállítás, és milyen hatása van,
      ha **true**‑ra állítjuk?
  - answer: Igen – állítsa a **Layout** tulajdonságot **WatermarkLayout.Horizontal**‑ra
      a **TextWatermarkOptions**‑ban, mielőtt meghívná a **document.Watermark.SetText**‑t.
    question: Megváltoztathatom a vízjel tájolását átlós helyett vízszintesre?
  - answer: A kódrészlet egy új **Document** példányt hoz létre, de bármely meglévő
      fájlt megnyithat (pl. `new Document(\"Existing.docx\")`), majd meghívhatja a
      **document.Watermark.SetText**‑t a ugyanazon vízjel alkalmazásához.
    question: Ez a kód vízjelet ad hozzá egy meglévő Word-fájlhoz, vagy csak az újonnan
      létrehozott dokumentumokhoz?
  - answer: Rendeljen egy egyedi színt a **Color.FromArgb(red, green, blue)** segítségével
      a **TextWatermarkOptions** **Color** tulajdonságához, például `Color = Color.FromArgb(128,
      0, 128)` a lila színhez.
    question: Hogyan használhatok egy egyedi RGB színt a vízjelhez a beépített **Color.Red**
      helyett?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Piros átlós szöveges vízjel hozzáadása Word-dokumentumokhoz
og_description: Tekintse meg, hogyan lehet automatikusan alkalmazni egy piros átlós vízjelet minden Word-dokumentumra egy kötegben az Aspose.Words segítségével.
og_image_alt: Útmutató, amely bemutatja, hogyan adjon hozzá piros átlós szöveges vízjelet Word-dokumentumokhoz az Aspose.Words for .NET használatával
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Piros átlós szöveges vízjel hozzáadása Word-dokumentumokhoz az Aspose.Words for .NET használatával
Ez az útmutató bemutatja, hogyan lehet automatikusan beágyazni egy piros átlós szöveges vízjelet minden, a kötegelt jelentéskészítés során létrehozott Word-dokumentumba. Az Aspose.Words for .NET Document és DocumentBuilder osztályainak használatával a vízjelet programozottan alkalmazzák a fájlok létrehozásakor, biztosítva, hogy minden dokumentum ugyanazt a márkát vagy titoktartási megjegyzést tartalmazza manuális beavatkozás nélkül.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Mit szabályoz a **IsSemitrasparent** beállítás, és milyen hatása van, ha **true**‑ra állítjuk?**  
A: Az IsSemitrasparent meghatározza, hogy a vízjel részben átlátszó módon jelenik-e meg; **true**‑ra állítva a szöveg félig átlátszó lesz, így az alatta lévő tartalom jobban olvasható marad.

**Q: Megváltoztathatom a vízjel tájolását átlós helyett vízszintesre?**  
A: Igen – állítsa a **Layout** tulajdonságot **WatermarkLayout.Horizontal**‑ra a **TextWatermarkOptions**‑ban, mielőtt meghívná a **document.Watermark.SetText**‑t.

**Q: Ez a kód vízjelet ad hozzá egy meglévő Word-fájlhoz, vagy csak az újonnan létrehozott dokumentumokhoz?**  
A: A kódrészlet egy új **Document** példányt hoz létre, de bármely meglévő fájlt megnyithat (pl. `new Document(\"Existing.docx\")`), majd meghívhatja a **document.Watermark.SetText**‑t a ugyanazon vízjel alkalmazásához.

**Q: Hogyan használhatok egy egyedi RGB színt a vízjelhez a beépített **Color.Red** helyett?**  
A: Rendeljen egy egyedi színt a **Color.FromArgb(red, green, blue)** segítségével a **TextWatermarkOptions** **Color** tulajdonságához, például `Color = Color.FromArgb(128, 0, 128)` a lila színhez.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}