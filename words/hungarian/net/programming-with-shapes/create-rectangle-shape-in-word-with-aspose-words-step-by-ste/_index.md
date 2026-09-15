---
category: general
date: 2025-12-29
description: Hozzon létre téglalap alakzatot egy Word dokumentumban az Aspose.Words
  C# segítségével. Tanulja meg, hogyan állíthatja be az alakzat átlátszóságát, az
  árnyék színét, és mentse el a Word dokumentumot könnyedén.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: hu
og_description: Hozzon létre téglalap alakzatot egy Word dokumentumban az Aspose.Words
  C#-val. Ez az útmutató bemutatja, hogyan állítható be az alakzat átlátszósága, az
  árnyék színe, és hogyan menthető a Word dokumentum.
og_title: Téglalap alakzat létrehozása Wordben – Teljes Aspose.Words útmutató
tags:
- Aspose.Words
- C#
- Word Automation
title: Téglalap alakzat létrehozása Wordben az Aspose.Words segítségével – Lépésről
  lépésre útmutató
url: /hu/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Word-ben – Teljes Aspose.Words útmutató

Valaha is szükséged volt **téglalap alakzat** létrehozására egy Word dokumentumban, de nem tudtad, hol kezdj? Nem vagy egyedül; sok fejlesztő szembesül ezzel a problémával jelentések vagy számlák automatizálásakor. Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan hozhatsz létre téglalap alakzatot, állíthatod be az alakzat átlátszóságát, a árnyék színét, és végül **word dokumentumot menthetsz** az Aspose.Words for .NET használatával.

Az első dokumentumobjektól a lemezre írt végső `.docx` fájlig mindent lefedünk, így a végére képes leszel **word dokumentumot létrehozni** programozottan találgatás nélkül. Nincsenek külső hivatkozások, csak egy önálló megoldás, amelyet egyszerűen beilleszthetsz a projektedbe.

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑vel is működik)
- Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`)
- Alapvető ismeretek a C# szintaxisról
- A kedvenc IDE‑d (Visual Studio, Rider, VS Code, stb.)

> **Pro tipp:** Ha az Aspose.Words ingyenes próbaverzióját használod, a könyvtár vízjelet ad a kimeneti fájlhoz. Éles környezetben érvényes licencre lesz szükséged.

## 1. lépés: A dokumentum és a Builder inicializálása

Az első dolog, amit teszünk, egy friss, üres Word dokumentum és egy `DocumentBuilder` létrehozása, amely lehetővé teszi a tartalom beszúrását. Gondolj a Builderre, mint egy virtuális tollra, amely a lapra rajzol.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Miért fontos:** `DocumentBuilder` nélkül közvetlenül kellene a low‑level csomópontfát manipulálni, ami hibára hajlamos és nehezebben olvasható.

## 2. lépés: Téglalap alakzat létrehozása

Most ténylegesen **téglalap alakzatot hozunk létre**. Az `InsertShape` metódus egy `ShapeType` enumot, szélességet és magasságot (pontban) vár. A visszaadott `Shape` objektum lehetővé teszi a vizuális tulajdonságok későbbi finomhangolását.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Ebben a pontban a téglalap egy szilárd fekete doboz, amely az aktuális bekezdéshez van rögzítve. Később mozgathatod, átméretezheted, vagy akár elforgathatod is, ha szükséges.

![téglalap alakzat árnyékkal](/images/rectangle-shadow.png "Egy Word dokumentum, amely egy szürke árnyékú téglalap alakzatot mutat")

*Kép alternatív szöveg: téglalap alakzat árnyékkal egy Word dokumentumban*

## 3. lépés: Az alakzat átlátszóságának beállítása

Az átlátszóság az alakzat kitöltésének „átlátszó” szintje. Az Aspose.Words egy `Transparency` tulajdonságot használ, amely `0.0` (átlátszatlan) és `1.0` (teljesen átlátszó) között mozog. Itt **az alakzat átlátszóságát** 40 %-ra állítjuk, hogy az alatta lévő szöveg olvasható maradjon.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

**Külön eset:** Ha teljesen láthatatlan alakzatra van szükséged, de mégis szeretnéd, hogy az árnyék megjelenjen, állítsd a `Transparency` értékét `1.0`‑ra, és adj az alakzatnak nem nulla körvonalvastagságot.

## 4. lépés: Az árnyék beállítása

Egy finom vetett árnyék mélységet ad. **Az árnyék színét** közép‑szürkére állítjuk, beállítjuk a elmosódási sugarát, és néhány ponttal eltoljuk vízszintesen és függőlegesen is.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

**Miért fontos:** Egy túl éles vagy túl sötét árnyék nyomtatási hibának tűnhet. Állítsd a `Blur` és a `Transparency` értékeket, amíg természetesnek nem tűnik.

## 5. lépés: A Word dokumentum mentése

Végül **word dokumentumot mentünk** a lemezre. A `Save` metódus automatikusan a kiterjesztés alapján határozza meg a fájlformátumot; a `.docx` a modern OpenXML formátum.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Ha a mappa nem létezik, az Aspose.Words `ArgumentException`‑t dob. Győződj meg róla, hogy az útvonal érvényes, vagy hozd létre a könyvtárat előre.

## Teljes működő példa

Az alábbiakban a teljes, azonnal futtatható program látható, amely összevonja az összes lépést. Másold be egy új konzolprojektbe, és nyomd meg az **F5**‑öt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Várható eredmény

Nyisd meg a `ShadowRectangle.docx` fájlt a Microsoft Wordben. Egy világosszürke téglalapot kell látnod, amelynek lágy, enyhén eltolódó árnyéka van, mindkettő 40 % átlátszósággal jelenik meg. Az alakzat egy üres oldalon helyezkedik el, készen áll további tartalomra.

## Gyakori kérdések és variációk

**Mi van, ha más alakzatra van szükségem?**  
Cseréld le a `ShapeType.Rectangle`‑t bármely más enum értékre (`Ellipse`, `Triangle`, `Star`, stb.). A kód többi része változatlan marad.

**Megváltoztathatom a körvonal színét?**  
Igen—használd a `rectangleShape.StrokeColor = System.Drawing.Color.Blue;`‑t, és opcionálisan állítsd be a `rectangleShape.StrokeWeight = 1.5;`‑t.

**Hogyan helyezhetem el az alakzatot egy adott helyen az oldalon?**  
Állítsd be a `rectangleShape.WrapType = WrapType.None;`‑t, majd módosítsd a `rectangleShape.Left` és `rectangleShape.Top` tulajdonságokat (az értékek pontban vannak).

**Lehetőség van szöveget hozzáadni a téglalap belsejéhez?**  
Természetesen. Az alakzat létrehozása után meghívhatod a `rectangleShape.AppendChild(new Paragraph(document))`‑t, majd hozzáadhatsz egy `Run`‑t a szöveggel. Ne felejtsd el beállítani a `rectangleShape.TextBox` tulajdonságokat, ha gazdagabb formázást szeretnél.

## Pro tippek és buktatók

- **Licenc időben:** Ha elfelejted alkalmazni a licencet, az Aspose.Words vízjelet helyez el az első oldalon, ami a tesztelés során zavaró lehet.
- **Teljesítmény tipp:** Sok dokumentum generálásakor egy ciklusban újrahasználj egyetlen `Document` példányt, és minden mentés után hívd meg a `document.RemoveAllChildren();`‑t, hogy elkerüld a túlzott GC terhelést.
- **Árnyék láthatósága:** Alacsony felbontású képernyőkön egy finom árnyék láthatatlanná válhat. Növeld a `Blur` vagy `OffsetX/Y` értékét hibakereséskor, majd állítsd vissza a termeléshez.

## Következő lépések

Most, hogy tudod, hogyan **hozz létre téglalap alakzatot**, **állítsd be az alakzat átlátszóságát**, **állítsd be az árnyék színét**, és **mentsd a word dokumentumot**, gondolkodj el a tutorial kibővítésén:

- Több alakzat hozzáadása és csoportosítása.
- A téglalap beillesztése egy táblázat cellájába jelentéselrendezéshez.
- Az alakzat kombinálása a `DocumentBuilder.InsertHtml`‑val HTML‑stílusú tartalom átfedéséhez.
- Más vizuális hatások felfedezése, mint a `Glow` vagy a `Reflection`, a gazdagabb UI‑szerű dokumentumokhoz.

Kísérletezz, törj össze dolgokat, majd finomítsd – a programozott dokumentumgenerálás egy játszótér, ahol a vizuális tervezés találkozik a kóddal.

---

*Boldog kódolást! Ha bármilyen problémába ütköztél, hagyj egy megjegyzést alább, és együtt megoldjuk.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}