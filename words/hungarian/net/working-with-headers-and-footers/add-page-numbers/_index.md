---
title: Oldalszámok hozzáadása egy Word dokumentum láblécéhez az Aspose.Words for .NET használatával
weight: 210
limit:
description: Automatikusan frissülő oldalszámok hozzáadása egy Word dokumentum elsődleges láblécéhez az Aspose.Words for .NET használatával.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Automatikusan frissülő oldalszámok hozzáadása egy Word dokumentum elsődleges
    láblécéhez az Aspose.Words for .NET használatával.
  headline: Oldalszámok hozzáadása egy Word dokumentum láblécéhez az Aspose.Words
    for .NET használatával
  type: TechArticle
- description: Automatikusan frissülő oldalszámok hozzáadása egy Word dokumentum elsődleges
    láblécéhez az Aspose.Words for .NET használatával.
  name: Oldalszámok hozzáadása egy Word dokumentum láblécéhez az Aspose.Words for
    .NET használatával
  steps:
  - name: Hozzon létre egy új Document objektumot és egy hozzá kapcsolódó DocumentBuilder‑t.
    text: Hozzon létre egy új Document objektumot és egy hozzá kapcsolódó DocumentBuilder‑t.
  - name: Mozgassa a builder kurzorát az első szakasz elsődleges láblécéhez.
    text: Mozgassa a builder kurzorát az első szakasz elsődleges láblécéhez.
  - name: Állítsa be a bekezdés igazítását középre, hogy a lábléc szövege középre
      legyen igazítva.
    text: Állítsa be a bekezdés igazítását középre, hogy a lábléc szövege középre
      legyen igazítva.
  - name: Írja ki a "Page " feliratot, és szúrjon be egy PAGE mezőt, amely a jelenlegi
      oldalszámot jeleníti meg.
    text: Írja ki a "Page " feliratot, és szúrjon be egy PAGE mezőt, amely a jelenlegi
      oldalszámot jeleníti meg.
  - name: Írja ki a " of " szöveget, és szúrjon be egy NUMPAGES mezőt, amely a teljes
      oldalszámot mutatja.
    text: Írja ki a " of " szöveget, és szúrjon be egy NUMPAGES mezőt, amely a teljes
      oldalszámot mutatja.
  - name: Mentse a dokumentumot .docx fájlba.
    text: Mentse a dokumentumot .docx fájlba.
  type: HowTo
- questions:
  - answer: Nem. A `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` a buildert
      csak az *első* szakasz elsődleges láblécéhez viszi, így a mezők csak oda kerülnek
      beszúrásra.
    question: Ha a dokumentumnak egynél több szakasza van, ez a kód minden szakasz
      láblécéhez hozzáadja az oldalszámokat?
  - answer: Állítsa a `builder.ParagraphFormat.Alignment` értékét egy másik `ParagraphAlignment`
      értékre (például `ParagraphAlignment.Right`), mielőtt a mezőket írná.
    question: Hogyan változtathatom meg az oldalszám bekezdés igazítását a láblécben?
  - answer: Az `InsertField` a mezőkódot és egy opcionális mezőeredményt vár; a `null`
      átadása azt jelzi az Aspose.Words számára, hogy a Word számítsa ki az eredményt
      futásidőben.
    question: Mit jelent a `null` argumentum a `InsertField("PAGE", null)` hívásban?
  - answer: Igen – cserélje a `HeaderFooterType.FooterPrimary`-t `HeaderFooterType.HeaderPrimary`-ra
      (vagy egy másik fejléc típusra) a mezők beszúrása előtt.
    question: Elhelyezhetem ugyanazt a "Page X of Y" mezőt a fejlécben a lábléc helyett?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Automatikus oldalszámok beszúrása a Word láblécébe
og_description: Lépésről‑lépésre kód a Word láblécébe élő oldalszámok hozzáadásához az Aspose.Words for .NET segítségével.
og_image_alt: Útmutató, amely bemutatja, hogyan adhat hozzá automatikus oldalszámokat egy Word dokumentum láblécéhez az Aspose.Words for .NET használatával
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Oldalszámok hozzáadása egy Word dokumentum láblécéhez az Aspose.Words for .NET használatával
Ez a bemutató azt mutatja be, hogyan használhatja az Aspose.Words Document és DocumentBuilder osztályokat automatikusan frissülő oldalszámok beszúrásához a Word dokumentum elsődleges láblécébe. Az oldalszámok programozott hozzáadásával biztosíthatja a következetes oldalszámozást a teljes fájlban manuális szerkesztés nélkül. A példakód készen áll a .NET környezetben való futtatásra.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Ha a dokumentumnak egynél több szakasza van, ez a kód minden szakasz láblécéhez hozzáadja az oldalszámokat?**  
A: Nem. A `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` a buildert csak az *első* szakasz elsődleges láblécéhez viszi, így a mezők csak oda kerülnek beszúrásra.

**Q: Hogyan változtathatom meg az oldalszám bekezdés igazítását a láblécben?**  
A: Állítsa a `builder.ParagraphFormat.Alignment` értékét egy másik `ParagraphAlignment` értékre (például `ParagraphAlignment.Right`), mielőtt a mezőket írná.

**Q: Mit jelent a `null` argumentum a `InsertField("PAGE", null)` hívásban?**  
A: Az `InsertField` a mezőkódot és egy opcionális mezőeredményt vár; a `null` átadása azt jelzi az Aspose.Words számára, hogy a Word számítsa ki az eredményt futásidőben.

**Q: Elhelyezhetem ugyanazt a "Page X of Y" mezőt a fejlécben a lábléc helyett?**  
A: Igen – cserélje a `HeaderFooterType.FooterPrimary`-t `HeaderFooterType.HeaderPrimary`-ra (vagy egy másik fejléc típusra) a mezők beszúrása előtt.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}