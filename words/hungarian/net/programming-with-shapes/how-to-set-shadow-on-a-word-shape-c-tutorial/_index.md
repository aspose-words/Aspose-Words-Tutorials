---
category: general
date: 2026-03-30
description: Tanulja meg, hogyan állíthat be árnyékot egy Word alakzatra C#-ban. Ez
  az útmutató azt is bemutatja, hogyan adhat hozzá alakzatárnyékot, állíthatja az
  alakzat átlátszóságát, és hogyan adhat hozzá téglalap árnyékot.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: hu
og_description: Hogyan állítsunk be árnyékot egy Word alakzatra C#‑ban? Kövesse ezt
  a lépésről‑lépésre útmutatót az alakzat árnyékának hozzáadásához, az alakzat átlátszóságának
  beállításához és a téglalap árnyékának hozzáadásához.
og_title: Hogyan állíts be árnyékot egy Word alakzatra – C# oktató
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Hogyan állítsunk be árnyékot egy Word alakzatra – C# útmutató
url: /hu/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan állítsunk be árnyékot egy Word alakzatra – C# oktatóanyag

Gondolkodtál már azon, **hogyan állítsunk be árnyékot** egy alakzaton belül egy Word dokumentumban anélkül, hogy a felhasználói felületet kellene manipulálni? Nem vagy egyedül. Sok jelentésben vagy marketing anyagban egy finom drop‑shadow kiemeli a téglalapot, és programozott módon megoldva órákat takaríthat meg.

Ebben az útmutatóban egy teljes, azonnal futtatható példán keresztül mutatjuk be, amely nem csak **hogyan állítsunk be árnyékot**, hanem lefedi a **add shape shadow**, **adjust shape transparency**, és még a **add rectangle shadow** használatát is azokhoz a klasszikus felhívó dobozokhoz. A végére egy Word fájlt (`output.docx`) kapsz, amely kifinomult megjelenésű, és megérted, miért fontos minden egyes tulajdonság.

## Előfeltételek

- .NET 6+ (vagy .NET Framework 4.7.2) C# fordítóval  
- Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`)  
- Alapvető C# ismeretek és a Word objektummodelljának áttekintése  

További könyvtárak nem szükségesek – minden az Aspose.Words-ben található.

---

## Hogyan állítsunk be árnyékot egy Word alakzatra C#‑ben

Az alábbiakban a teljes forrásfájl látható. Mentsd `Program.cs` néven, és futtasd a kedvenc IDE‑dben vagy a `dotnet run` paranccsal. A kód betölti a meglévő `.docx` fájlt, megtalálja az első alakzatot (alapértelmezés szerint egy téglalapot), bekapcsolja az árnyékot, finomhangolja néhány vizuális paramétert, majd elmenti az eredményt.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Mit fogsz látni** – A téglalap most egy fekete drop‑shadow‑ot kap, amely 30 % átlátszó, 5 pt‑rel jobbra és lejjebb eltolódik, enyhe elmosódással. Nyisd meg az `output.docx` fájlt Wordben a ellenőrzéshez.

## Alakzat átlátszóságának beállítása – Miért fontos

Az átlátszóság nem csupán esztétikai beállítás; befolyásolja az olvashatóságot. A 0.0 érték teljesen átlátszatlan árnyékot eredményez, míg az 1.0 teljesen elrejti azt. A fenti kódrészletben `0.3`-at használtunk, hogy egy finom hatást érjünk el, amely mind világos, mind sötét háttéren jól működik. Kísérletezhetsz:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Ne feledd, a **adjust shape transparency** ugyanúgy alkalmazható az alakzat kitöltőszínére is, ha egy félig átlátszó téglalapra van szükséged.

## Árnyék hozzáadása különböző objektumokhoz

A bemutatott kód egy `Shape` objektumot céloz, de ugyanazok a `ShadowFormat` tulajdonságok elérhetők **Image**, **Chart**, és még **TextBox** objektumokon is. Íme egy gyors minta, amelyet egyszerűen másolhatsz‑beilleszthetsz:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Így akár **add shape shadow**‑t is hozzáadhatsz egy logóhoz vagy egy díszítő ikonhoz, a megközelítés változatlan marad.

## Árnyék hozzáadása bármely alakzatra – Különleges esetek

1. **Alakzat keret nélkül** – Néhány Word alakzat (például szabadkézi vonalak) nem támogatja az árnyékot. A `ShadowFormat.Visible` beállítása csendben hibát eredményez. Ellenőrizd a `shape.IsShadowSupported` értéket, ha biztonságra van szükséged.  
2. **Régebbi Word verziók** – Az árnyék tulajdonságok a Word 2007+ funkciókra épülnek. Ha Word 2003-at kell támogatni, az árnyék figyelmen kívül marad a fájl megnyitásakor.  
3. **Több árnyék** – Az Aspose.Words jelenleg egyetlen árnyékot támogat alakzatonként. Ha dupla rétegű hatást szeretnél, másold meg az alakzatot, helyezd el eltolva, és alkalmazz különböző árnyékbeállításokat.

## Téglalap árnyék hozzáadása – Valós példák

Képzeld el, hogy egy negyedéves jelentést generálsz, és minden szekciócím egy színes téglalap. Egy **add rectangle shadow** hozzáadása „kártya‑szerű” megjelenést kölcsönöz az oldalnak. A lépések megegyeznek az alappéldával; csak győződj meg róla, hogy a cél alakzat valóban téglalap (`shape.ShapeType == ShapeType.Rectangle`). Ha a téglalapot a semmiből kell létrehozni, lásd az alábbi kódrészletet:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

A teljes program ezzel a kiegészítéssel egy új téglalapot hoz létre, amely már magában foglalja a kívánt **add rectangle shadow** hatást.

---

![Word shape with shadow](placeholder-image.png){alt="hogyan állítsunk be árnyékot egy alakzatra Wordben"}

*Ábra: A téglalap az árnyékbeállítások alkalmazása után.*

## Gyors összefoglaló (Bullet‑Point Cheat Sheet)

- **Betöltés** a dokumentum `new Document(path)` segítségével.  
- **Keresés** az alakzatra a `doc.GetChild(NodeType.Shape, index, true)` metódussal.  
- **Árnyék engedélyezése**: `shape.ShadowFormat.Visible = true;`.  
- **Szín beállítása** bármely `System.Drawing.Color` értékkel.  
- **Átlátszóság** (`0.0–1.0`) szabályozása az opacitásért.  
- **OffsetX / OffsetY** eltolás vízszintesen/függőlegesen (pontokban).  
- **BlurRadius** a szélek lágyításához – nagyobb érték = homályosabb árnyék.  
- **Mentés** a fájlba, majd megnyitás Wordben a végeredmény megtekintéséhez.

## Mit próbálj ki legközelebb?

- **Dinamikus színek** – Árnyék színének lekérése egy témából vagy felhasználói bemenetből.  
- **Feltételes árnyékok** – Árnyék alkalmazása csak akkor, ha az alakzat szélessége meghalad egy küszöbértéket.  
- **Kötegelt feldolgozás** – Az összes alakzat bejárása egy dokumentumban, és **add shape shadow** automatikus hozzáadása.  

Ha végigkövetted a lépéseket, most már tudod, **hogyan állítsunk be árnyékot**, hogyan **adjust shape transparency**, és hogyan **add rectangle shadow** a professzionális megjelenésért. Kísérletezz, hibázz, majd javíts – a kódolás a legjobb tanár.

---

*Boldog kódolást! Ha ez az oktatóanyag hasznos volt, hagyj egy megjegyzést vagy oszd meg saját árnyék‑trükkjeidet. Minél többet tanulunk egymástól, annál szebbé válnak a Word dokumentumaink.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}