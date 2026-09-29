---
title: Átlós szöveges vízjel létrehozása egyedi betűtípussal Word dokumentumban az Aspose.Words for .NET használatával
weight: 210
limit:
description: Lépésről‑lépésre kód egy átlós szöveges vízjel egyedi betűtípussal egy Word .docx fájlhoz az Aspose.Words for .NET használatával.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Lépésről‑lépésre kód egy átlós szöveges vízjel egyedi betűtípussal
    egy Word .docx fájlhoz az Aspose.Words for .NET használatával.
  headline: Átlós szöveges vízjel létrehozása egyedi betűtípussal Word dokumentumban
    az Aspose.Words for .NET használatával
  type: TechArticle
- description: Lépésről‑lépésre kód egy átlós szöveges vízjel egyedi betűtípussal
    egy Word .docx fájlhoz az Aspose.Words for .NET használatával.
  name: Átlós szöveges vízjel létrehozása egyedi betűtípussal Word dokumentumban az
    Aspose.Words for .NET használatával
  steps:
  - name: Hozzon létre egy új, üres Word dokumentum példányt `document` néven.
    text: Hozzon létre egy új, üres Word dokumentum példányt `document` néven.
  - name: Állítsa be a `watermarkSettings`-et Arial 48‑pontos szürke betűtípussal,
      átlós elrendezéssel és átlátszatlan megjelenítéssel.
    text: Állítsa be a `watermarkSettings`-et Arial 48‑pontos szürke betűtípussal,
      átlós elrendezéssel és átlátszatlan megjelenítéssel.
  - name: Alkalmazza a "Private" szöveges vízjelet a `document`-re a korábban definiált
      beállításokkal.
    text: Alkalmazza a "Private" szöveges vízjelet a `document`-re a korábban definiált
      beállításokkal.
  - name: Határozza meg a fájl útvonalát, ahová a vízjelezett dokumentumot menteni
      kívánja.
    text: Határozza meg a fájl útvonalát, ahová a vízjelezett dokumentumot menteni
      kívánja.
  - name: Mentse a módosított `document`-et a megadott útvonalra .docx fájlként.
    text: Mentse a módosított `document`-et a megadott útvonalra .docx fájlként.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` meghatározza, hogy a vízjel részlegesen átlátszó módon
      jelenik‑e meg; `false` értékre állítva a vízjel teljesen átlátszatlan lesz,
      míg `true` esetén az alapértelmezett félig átlátszó hatást alkalmazza.'
    question: Mit szabályoz a **IsSemitrasparent** jelző a `TextWatermarkOptions`-ban?
  - answer: Igen — állítsa a `Layout` tulajdonságot `WatermarkLayout.Horizontal`‑ra
      (vagy egy másik enum értékre) a `document.Watermark.SetText` meghívása előtt.
    question: Módosíthatom a vízjel tájolását átlós helyett vízszintesre?
  - answer: A Word a vízjelhez az alapértelmezett betűtípust fogja használni, így
      a szöveg megjelenik, de eltérhet a kívánt stílustól.
    question: Mi történik, ha a megadott `FontFamily` (például "Arial") nincs telepítve
      a célgépen?
  - answer: Töltse be a meglévő fájlt a `Document document = new Document(\"Existing.docx\");`
      kóddal, majd állítsa be a `TextWatermarkOptions`-t és hívja meg a `document.Watermark.SetText`-et
      a példában látható módon.
    question: Lehetséges-e egy meglévő `.docx` fájlhoz hozzáadni a vízjelet egy új
      létrehozása helyett?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Átlós szöveges vízjel hozzáadása egyedi betűtípussal
og_description: Tanulja meg, hogyan ágyazhat be ferde szöveges vízjelet saját betűtípusával egy Word fájlba percek alatt.
og_image_alt: Útmutató, amely bemutatja, hogyan adhat hozzá átlós szöveges vízjelet egyedi betűtípussal egy Word dokumentumhoz az Aspose.Words for .NET használatával
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Átlós szöveges vízjel létrehozása egyedi betűtípussal Word dokumentumban az Aspose.Words for .NET használatával
Ez a bemutató végigvezeti Önt egy új Word dokumentum létrehozásán, egy átlós szöveges vízjel beállításán a kívánt betűtípus-beállításokkal, annak alkalmazásán a Document.Watermark.SetText API-n keresztül, és az eredmény .docx fájlként történő mentésén. A végére egy professzionálisan vízjelezett dokumentumot kap, amely bemutatja márkáját vagy tulajdonjogát. A lépésről‑lépésre kód készen áll a másolásra bármely .NET projektbe.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Mit szabályoz a **IsSemitrasparent** jelző a `TextWatermarkOptions`-ban?**  
A: `IsSemitrasparent` meghatározza, hogy a vízjel részlegesen átlátszó módon jelenik‑e meg; `false` értékre állítva a vízjel teljesen átlátszatlan lesz, míg `true` esetén az alapértelmezett félig átlátszó hatást alkalmazza.

**Q: Módosíthatom a vízjel tájolását átlós helyett vízszintesre?**  
A: Igen — állítsa a `Layout` tulajdonságot `WatermarkLayout.Horizontal`‑ra (vagy egy másik enum értékre) a `document.Watermark.SetText` meghívása előtt.

**Q: Mi történik, ha a megadott `FontFamily` (például "Arial") nincs telepítve a célgépen?**  
A: A Word a vízjelhez az alapértelmezett betűtípust fogja használni, így a szöveg megjelenik, de eltérhet a kívánt stílustól.

**Q: Lehetséges-e egy meglévő `.docx` fájlhoz hozzáadni a vízjelet egy új létrehozása helyett?**  
A: Töltse be a meglévő fájlt a `Document document = new Document(\"Existing.docx\");` kóddal, majd állítsa be a `TextWatermarkOptions`-t és hívja meg a `document.Watermark.SetText`-et a példában látható módon.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}