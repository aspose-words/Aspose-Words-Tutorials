---
category: general
date: 2026-03-04
description: Learn how to create rectangle shape, add shadow to shape and apply shadow
  effect in a Word document, then save Word document automatically.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: hu
og_description: Hozzon létre egy téglalap alakzatot, adjon hozzá árnyékot az alakzathoz,
  és alkalmazza az árnyékhatást egy Word dokumentumban C#-val. Kövesse ezt az útmutatót
  a Word dokumentum könnyed mentéséhez.
og_title: Téglalap alakzat létrehozása Wordben – Teljes C# oktatóanyag
tags:
- C#
- Aspose.Words
- Document Automation
title: Create rectangle shape in Word with C# – Step‑by‑Step Guide
url: /hu/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Word-ben C#-al – Teljes programozási útmutató

Szükséged volt már **téglalap alakzat létrehozása** egy Word fájlban, de nem tudtad, hol kezdjed? Nem vagy egyedül – sok fejlesztő szembesül ezzel a problémával, amikor először merül el a programozott dokumentumgenerálásban. A jó hír, hogy néhány C# sorral beilleszthetsz egy téglalapot, **árnyékot adhatsz az alakzathoz**, és **árnyékhatást alkalmazhatsz**, anélkül, hogy magad nyitnád meg a Wordöt. Ebben az útmutatóban végigvezetünk a teljes folyamaton, egy friss **üres dokumentum létrehozása**-től a végső **Word dokumentum mentése**-ig a lemezen.

Mindent lefedünk, amire szükséged van: a szükséges NuGet csomagot, a pontos API-kat, hogy miért fontos minden tulajdonság, és néhány tippet a leggyakoribb hibák elkerüléséhez. A végére egy teljesen futtatható példát kapsz, amelyet bármely .NET projektbe beilleszthetsz.

## Előfeltételek

- .NET 6.0 vagy újabb (a kód a .NET Framework 4.7+‑vel is működik)
- Visual Studio 2022 vagy bármely kedvelt IDE
- **Aspose.Words for .NET** telepítve a NuGet-en keresztül (`Install-Package Aspose.Words`)
- Alapvető ismeretek a C# szintaxisról

Nem szükségesek további Word interop könyvtárak – az Aspose.Words mindent memóriában kezel.

## 1. lépés – Üres dokumentum létrehozása

Az első dolog, amit csinálunk, az **üres dokumentum létrehozása**. Gondolj rá úgy, mint egy üres vászonra, amelyre később **téglalap alakzatot hozunk létre**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Miért fontos ez:** Egy tiszta `Document` objektummal kezdve garantálja, hogy semmilyen rejtett stílus vagy szakasz ne zavarja a későbbi alakzat elhelyezését.

## 2. lépés – Téglalap alakzat beszúrása a dokumentumba

Most ténylegesen **téglalap alakzatot hozunk létre**. Beállítjuk a méretét, a pozícióját, és azt mondjuk a Wordnek, hogy ne tördelje körül a szöveget.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Pro tipp:** Ha a téglalapot egy táblázat cellájában szeretnéd elhelyezni, változtasd a `WrapType` értékét `WrapType.Inline`‑ra. A legtöbb jelentésnél a `None` azt eredményezi, hogy az alakzat a szöveg felett lebeg.

## 3. lépés – Árnyék hozzáadása az alakzathoz és megjelenésének beállítása

Itt történik a varázslat: **árnyékot adunk az alakzathoz** és **árnyékhatást alkalmazunk**. Az árnyék kiemeli a téglalapot az oldalon, különösen nyomtatáskor.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Miért ezek az értékek?**  
> - **BlurRadius** szabályozza, mennyire homályosak a szélek; egy `5` körüli érték finom, professzionális megjelenést kölcsönöz.  
> - **Transparency** lehetővé teszi, hogy az alatta lévő szöveg olvasható maradjon.  
> - **OffsetX/Y** eltolja az árnyékot az alakzattól, mélységet teremtve.  
> - A **kék** színárnyalat csak példa – bármely `System.Drawing.Color` működik.

## 4. lépés – A konfigurált alakzat hozzáadása a dokumentum törzséhez

Miután a téglalap teljesen stilizálva van, most **hozzáadjuk a téglalap alakzatot** a dokumentum első szakaszához. Ez a lépés ténylegesen elhelyezi az alakzatot a fájlban.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Szélsőséges eset:** Ha a dokumentum már tartalmaz szakaszokat, előfordulhat, hogy egy konkrét szakaszt kell megcéloznod (például `doc.Sections[2]`). A fenti kód egyetlen szakaszos dokumentumra működik, ami gyakori a gyors jelentések esetén.

## 5. lépés – Word dokumentum mentése

Végül **Word dokumentumot mentünk** a lemezre. A fájl tartalmazni fogja a téglalapot az árnyékával, készen állva a Microsoft Wordben való megnyitásra.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Tipp:** Használd a `doc.Save(outputPath, SaveFormat.Docx)`‑t, ha egyértelműen meg akarod adni a formátumot. A `Save` metódus automatikusan felismeri a kiterjesztést, de az egyértelműség elkerülheti a félreértéseket, ha az útvonal programból generálódik.

## Teljes, futtatható példa

Az alábbiakban a teljes program látható, amelyet beilleszthetsz egy konzolalkalmazásba. Tartalmazza az összes `using` utasítást és a `Main` metódust, így azonnal futtatható.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Várható eredmény

Amikor megnyitod a *shadowed_rectangle.docx* fájlt a Microsoft Wordben, egy kék szegéllyel rendelkező téglalapot látsz, amely az első oldal teteje közelében lebeg, egy lágy kék árnyékkal, amely 8 pt‑vel jobbra és lefelé van eltolva. Nem körülveszi semmilyen extra szöveg, mivel a `WrapType.None`‑t állítottuk be.

## Gyakran Ismételt Kérdések és Variációk

| Kérdés | Válasz |
|----------|--------|
| **Át tudom-e változtatni az alakzatot ellipszissé?** | Igen – cseréld le a `ShapeType.Rectangle`‑t `ShapeType.Ellipse`‑re. Az összes árnyék tulajdonság változatlan marad. |
| **Mi van, ha több alakzatra van szükségem?** | Egyszerűen ismételd meg a 2‑4. lépéseket minden új `Shape` példányhoz, és állítsd be az `OffsetX/Y` vagy a `Left/Top` értékeket, hogy elkerüld az átfedést. |
| **Van mód arra, hogy az árnyék színe megegyezzen az alakzat kitöltésével?** | Természetesen. Először állítsd be a `rectangle.FillColor`‑t, majd rendeld hozzá a `rectangle.ShadowFormat.Color = rectangle.FillColor;` értéket. |
| **Hogyan illeszthetem be az alakzatot egy táblázat cellájába?** | Használd a `cell.FirstParagraph.AppendChild(rectangle);` kódot, miután megtaláltad a kívánt `Cell` objektumot. |
| **Működik ez .NET Core‑on?** | Igen – az Aspose.Words platformfüggetlen. Csak győződj meg róla, hogy a megfelelő NuGet csomagverziót hivatkozod .NET Core/5/6‑hoz. |

## Gyakori Hibák és Pro Tippek

- **Hiba:** Elfelejted beállítani a `ShadowFormat.Visible = true`‑t. Az árnyék tulajdonságok csendben figyelmen kívül maradnak.  
  **Megoldás:** Mindig engedélyezd a láthatóságot, mielőtt módosítanád a többi árnyék paramétert.

- **Hiba:** Nagyon nagy `BlurRadius` (pl. 20) használata elmosódott és amatőr hatású árnyékot eredményezhet.  
  **Megoldás:** Tartsd a `3` és `8` közötti értékeknél a legtöbb üzleti dokumentum esetén.

- **Pro tipp:** Ha később (pl. végfelhasználói szerkesztéshez) szeretnéd, hogy az alakzat kiválasztható legyen, kerüld a `WrapType.Inline` beállítását. A lebegő alakzatok (`WrapType.None`) programból könnyebben mozgathatók.

- **Pro tipp:** Sok dokumentum ciklikus generálásakor használd újra ugyanazt a `Document` példányt, és minden iterációhoz hívd a `doc.Clone(true)`‑t a teljesítmény javítása érdekében.

## Kapcsolódó Témák, Amiket Érdemes Felfedezni

- **Szöveg hozzáadása egy téglalap alakzathoz** – tanuld meg, hogyan használhatod a `Shape.TextPath`‑t címkékhez.  
- **Komplex diagramok létrehozása** – kombinálj több alakzatot, összekötőket és csoportosítást.  
- **Exportálás PDF-be** – konvertáld ugyanazt a dokumentumot PDF-be egyetlen `doc.Save("output.pdf")` hívással.  
- **Különböző kitöltési stílusok alkalmazása** – színátmenetek, textúrák vagy akár képek az alakzatokban.

## Következtetés

Most **téglalap alakzatot hoztunk létre**, **árnyékot adtunk az alakzathoz**, és **árnyékhatást alkalmaztunk** egy Word fájlban C# használatával. Az öt tömör lépés követésével most már van egy újrahasználható minta bármilyen dokumentum‑automatizálási helyzethez, és tudod, hogyan **mentheted a Word dokumentumot** megbízhatóan. Nyugodtan módosítsd a méreteket, színeket, vagy cseréld le a téglalapot egy másik geometriai alakra – az Aspose.Words mindezt egyszerűvé teszi.

Ha hasznosnak találtad ezt az útmutatót, adj egy csillagot a GitHubon, vagy oszd meg saját variációidat a megjegyzésekben. Boldog kódolást, és legyenek a dokumentumaid mindig olyan kifinomultak, mint ez az árnyékolt téglalap!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}