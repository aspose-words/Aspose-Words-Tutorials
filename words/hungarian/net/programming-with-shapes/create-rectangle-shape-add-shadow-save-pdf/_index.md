---
category: general
date: 2026-02-24
description: Hozzon létre téglalap alakzatot C#-ban az Aspose.Words használatával,
  adjon árnyékot az alakzathoz, és mentse a dokumentumot PDF-ként. Tanulja meg, hogyan
  adjon árnyékot, és hogyan mentse PDF-be néhány perc alatt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: hu
og_description: Hozzon létre téglalap alakzatot C#‑ban az Aspose.Words segítségével,
  majd adjon árnyékot az alakzathoz, és mentse a dokumentumot PDF‑ként – egy teljes,
  lépésről‑lépésre útmutató.
og_title: Hozzon létre téglalap alakzatot, adjon árnyékot és mentse PDF‑ként
tags:
- Aspose.Words
- C#
- PDF generation
title: Téglalap alakzat létrehozása, árnyék hozzáadása és PDF mentése
url: /hu/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása, árnyék hozzáadása és PDF mentése

Szükséged volt már **téglalap alakzat** létrehozására egy Word‑dokumentumban, de emellett egy szép vetett árnyékra és PDF‑kimenetre is? Nem vagy egyedül. Sok jelentés‑ vagy számlagenerálási projektben a vizuális kifinomultság – például egy finom árnyék – döntő lehet a „csak egy újabb fájl” és a „professzionális szintű dokumentum” között.  

Ebben az útmutatóban pontosan ezt mutatjuk be: hogyan használjuk az **Aspose.Words for .NET**‑et téglalap alakzat létrehozásához, árnyék hozzáadásához, majd **a dokumentum PDF‑ként mentéséhez**. A végére egy futtatható C# konzolalkalmazást kapsz, amely PDF‑et generál egy árnyékolt téglalappal, és megérted, hogyan lehet finomhangolni az árnyékot vagy módosítani az export beállításait.

## Amire szükséged lesz

- .NET 6 SDK (vagy bármely friss .NET verzió) – az API ugyanúgy működik a .NET Framework 4.x‑en is.  
- Aspose.Words for .NET NuGet csomag (`Aspose.Words`) – telepítheted a `dotnet add package Aspose.Words` paranccsal.  
- Kódszerkesztő – Visual Studio, VS Code vagy Rider megfelel.  

Ehhez a példához nincs extra licencelési lépés; a ingyenes értékelő mód elegendő a PDF‑kimenet megtekintéséhez.

## 1. lépés: Projekt létrehozása és névterek importálása

Először is hozzunk létre egy konzolprojektet, és importáljuk a szükséges osztályokat.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Miért fontos:* A `Document` és a `DocumentBuilder` biztosítja a vásznat, míg a `Shape` és a `ShadowFormat` lehetővé teszi a téglalap rajzolását és formázását. Az előzetes importálás tisztábbá teszi a későbbi kódot.

## 2. lépés: **Téglalap alakzat** létrehozása a kívánt méretekkel

Most már létrehozzuk az üres dokumentumot, és beszúrunk egy téglalapot. Figyeld meg, hogy az `InsertShape` metódus egy `Shape` objektumot ad vissza, amelyet azonnal formázhatunk.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Magyarázat*: A méret pontban van megadva (1 pt = 1/72 in). A számokat a saját elrendezésedhez igazíthatod. Emellett a téglalapnak világoskék kitöltést adunk, hogy az árnyék jobban kiemelkedjen.

## 3. lépés: **Árnyék hozzáadása a alakzathoz** – a hatás finomhangolása

Az árnyék nem csak „be/ki”. Szabályozhatod a színét, elmosódását, távolságát, irányát és akár az átlátszóságát is. Íme egy gyakorlati konfiguráció, amely a legtöbb jelentésnél jól működik.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Miért érdemes ezeket az értékeket módosítani:*  
- **BlurRadius** – növeld egy álomszerű hatáshoz, csökkentsd egy éles élhez.  
- **Direction** – 0° jobbra mutat, 90° lefelé, 180° balra stb. Forgasd a lap elrendezéséhez illeszkedően.  
- **Transparency** – állítsd `0`‑ra egy szilárd árnyékhoz, `0.5`‑re félig átlátszóhoz, stb.

### Árnyék hozzáadása – alternatív megközelítések

Ha **többrétegű árnyékra** (például egy sötétebb külső árnyék és egy világosabb belső árnyék) van szükséged, létrehozhatsz egy második alakzatot, eltolhatod, és másik `ShadowFormat`‑ot állíthatsz be. Vagy egy gyors „nincs elmosódás” hatáshoz állítsd `BlurRadius = 0`‑t.

## 4. lépés: **Dokumentum mentése PDF‑ként** – a végső export

Miután a téglalap és az árnyéka készen áll, az utolsó lépés a fájl PDF‑ként való kiírása. Az Aspose.Words belsőleg kezeli a konverziót; csak a `Save` metódust kell meghívnod a kívánt formátummal.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Tippek*: Ha PDF megfelelőséget (PDF/A, PDF/X) vagy betűtípus beágyazást kell szabályoznod, használj egy túlterhelt változatot:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Ez a **PDF mentésének** lényege röviden.

## Teljes, futtatható példa

Az alábbi kódrészlet a teljes program, amelyet beilleszthetsz a `Program.cs`‑be. Úgy van megírva, hogy azonnal lefordul és fut (csak győződj meg róla, hogy a kimeneti mappa létezik).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Várt eredmény

Nyisd meg a generált `ShadowRectangle.pdf` fájlt. Egyetlen oldalon egy világoskék téglalapot, egy lágy szürke árnyékot (45°‑os lejjebb‑jobbra eltolással) és tiszta széleket látsz majd. A PDF‑et bármely modern olvasó (Adobe Acrobat, Edge, Chrome) meg tudja jeleníteni.

![Create rectangle shape with shadow in PDF](/images/shadow-rectangle.png "Create rectangle shape with shadow in PDF")

*(A kép alternatív szövege tartalmazza a fő kulcsszót a SEO‑szempontból.)*

## Gyakori kérdések és speciális esetek kezelése

**Mi van, ha az árnyék eltűnik a PDF‑ben?**  
Győződj meg róla, hogy a legfrissebb Aspose.Words verziót (≥23.3) használod. A régebbi build‑ekben volt egy hiba, amely bizonyos árnyék‑tulajdonságokat figyelmen kívül hagyta a PDF konverzió során.

**Meg tudom változtatni az árnyék színét a márkámhoz igazítva?**  
Természetesen – cseréld ki a `System.Drawing.Color.Gray`‑t bármely `Color`‑ra, például `Color.FromArgb(128, 0, 0, 255)`‑ra egy félig átlátszó kékre.

**Hogyan adok árnyékot más alakzatokhoz (ellipszis, csillag, stb.)?**  
Ugyanaz a `ShadowFormat` működik minden `Shape` objektumnál. Miután létrehoztad az alakzatot, vedd fel a `ShadowFormat`‑ját, és állítsd be a kívánt tulajdonságokat.

**Mi a helyzet a DPI‑vel vagy a méretezési problémákkal?**  
A PDF renderelés a forma pontméretét veszi figyelembe. Ha nagyobb felbontású kimenetre (nyomtatáshoz) van szükséged, állítsd a forma méreteit ennek megfelelően, vagy használd a `PdfSaveOptions.ImageResolution`‑t.

**Exportálhatok más formátumokba, például PNG‑be?**  
Igen – egyszerűen hívd meg a `document.Save("output.png", SaveFormat.Png)` metódust. Az árnyék ugyanúgy lesz renderelve.

## Pro tippek és legjobb gyakorlatok

- **A builder újrahasználata**: Ha több alakzatot adsz hozzá, tarts egyetlen `DocumentBuilder` példányt; ez olcsóbb, mint többször újat létrehozni.  
- **Kötegelt mentés**: Sok PDF‑et generálsz egy ciklusban, akkor ismételd meg a `PdfSaveOptions` objektumot, hogy elkerüld a felesleges allokációkat.  
- **Tesztelés**: Mindig nyisd meg a PDF‑et mentés után, hogy ellenőrizd, megjelenik‑e az árnyék. Egyes PDF‑olvasók kissé eltérően renderelnek; az Adobe Acrobat a legmegbízhatóbb referencia.  
- **Teljesítmény**: Nagy dokumentumok esetén tiltsd le a `DocumentBuilder.InsertShape` automatikus oldaltöréseket a `builder.PageSetup.DifferentFirstPageHeaderFooter = false` beállítással, ha nincs rá szükséged.

## Összegzés

Mindezt áttekintettük: **téglalap alakzat** létrehozása, **árnyék hozzáadása az alakzathoz**, és **dokumentum mentése PDF‑ként** az Aspose.Words for .NET segítségével. A kód kompakt, a koncepciók érthetőek, és most már stabil alapod van más alakzatok, árnyékstílusok és export beállítások kipróbálásához.  

Mi a következő lépés? Próbáld ki a téglalap helyett egy lekerekített‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}