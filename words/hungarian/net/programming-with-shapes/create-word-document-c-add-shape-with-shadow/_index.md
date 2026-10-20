---
category: general
date: 2026-03-27
description: Word dokumentum létrehozása C#-ban, és megtanulni, hogyan adjon hozzá
  alakzatot, hogyan alkalmazzon árnyékot az alakzatra, és hogyan állítsa be az árnyék
  távolságát. Lépésről‑lépésre útmutató az Aspose.Words-hez.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: hu
og_description: Hozzon létre Word-dokumentumot C#-ban egy téglalap alakzattal és egyedi
  árnyékkal. Kövesse ezt a teljes útmutatót az árnyék távolságának és stílusának beállításához.
og_title: Word-dokumentum létrehozása C#‑ban – Alakzat hozzáadása árnyékkal
tags:
- Aspose.Words
- C#
- Document Automation
title: Word dokumentum létrehozása C#‑ban – Alakzat hozzáadása árnyékkal
url: /hu/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása C#‑ban – Alakzat hozzáadása árnyékkal

Szükséged volt már **create word document c#**‑ra, amely egy szép stílusú téglalapot tartalmaz? Talán egy jelentés sablont építesz, és egy finom vetett árnyékot szeretnél, hogy a megjelenés kitűnjön. Ebben az útmutatóban pontosan ezt mutatjuk be – hogyan adjunk hozzá alakzatot, alkalmazzunk árnyékot az alakzatra, és még a árnyék távolságát is finomhangoljuk az Aspose.Words segítségével.

Egy üres dokumentummal kezdünk, beillesztünk egy téglalapot, egy előre beállított árnyékot adunk neki, majd elmentjük a fájlt. A végére egy használatra kész .docx fájlod lesz, amelyet Word‑ben azonnal megnyithatsz, és láthatod a hatást. Nincs szükség külső eszközökre, csak tiszta C# kód.

## Előfeltételek

- .NET 6 (vagy bármely friss .NET Framework) telepítve.
- Visual Studio 2022 vagy VS Code C# kiegészítővel.
- Aspose.Words for .NET NuGet csomag (`Aspose.Words` 23.12 vagy újabb verzió).  
  A Package Manager Console‑ból így adhatod hozzá:

  ```powershell
  Install-Package Aspose.Words
  ```

Ennyi – nincs szükség extra DLL‑re vagy COM interopra.

## 1. lépés: Új dokumentum és builder inicializálása – *create word document c#* alapok

Először egy `Document` objektumra van szükség, amely a Word fájlt képviseli, és egy `DocumentBuilder`‑re, amellyel szerkeszthetjük.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Miért fontos ez a lépés:** A `Document` osztály a Word összes részét (oldalak, stílusok, képek) tárolja. A builder egy magas szintű API, amely elrejti az alacsony szintű csomópontkezelést, így könnyen **create word document c#**‑t készíthetsz XML‑kel való közvetlen foglalkozás nélkül.

## 2. lépés: Téglalap alakzat beszúrása – *how to create rectangle*  

Most egy téglalapot helyezünk el az oldalon. A méret pontban van megadva (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Pro tipp:** Ha másik alakzatra van szükséged, egyszerűen cseréld le a `ShapeType.Rectangle`‑t `ShapeType.Ellipse`, `ShapeType.Triangle` stb. a kód ugyanúgy működik **how to add shape** bármely típusra.

## 3. lépés: Előre beállított árnyék alkalmazása és finomhangolása – *apply shadow to shape*  

Az Aspose.Words több előre beállított árnyékformátummal érkezik. A `Preset1`‑et használjuk, majd testre szabjuk a távolságot, elmosódást, átlátszóságot és a színt.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Miért testre szabjuk az árnyékot?** A `Distance` tulajdonság határozza meg, milyen messze helyezkedik el az árnyék a téglalaptól – ez olyan, mint a “magasság”, amit egy 3‑D renderelésben látsz. A `BlurRadius` lágyítja a széleket, míg a `Transparency` lehetővé teszi egy finom, professzionális megjelenés létrehozását. Ez lefedi a **set shadow distance** követelményt, és megmutatja, hogyan **apply shadow to shape**‑t rugalmasan végezheted.

## 4. lépés: Dokumentum mentése – *create word document c#* befejezés

Végül írjuk a dokumentumot a lemezre. Állítsd be a útvonalat egy olyan mappára, amelyhez írási jogosultságod van.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Nyisd meg a keletkezett fájlt a Microsoft Wordben, és egy világoskék téglalapot látsz majd egy lágy szürke árnyékkal, amely 5 pt‑vel van eltolva. Ez a vizuális bizonyíték arra, hogy sikeresen **create word document c#**‑t készítettél egy stílusos alakzattal.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# példája, amely téglalapot mutat árnyékkal"}

## Opcionális variációk és szélhelyzetek

| Szenárió | Mit kell módosítani | Miért fontos |
|----------|--------------------|--------------|
| **Másik árnyékstílus** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Drámaibb megjelenést ad extra kód nélkül. |
| **Nincs preset – egyedi árnyék** | Hagyd el a `Format` beállítást, és állítsd be kézzel az `OffsetX`, `OffsetY` értékeket. | Teljes irány- és mélység‑vezérlés. |
| **Több alakzat** | Hívj meg újra `builder.InsertShape`‑t a mentés előtt. | Hasznos összetett sablonokhoz ikonokkal, logókkal stb. |
| **Kompatibilitás régebbi Aspose verziókkal** | Használd a `ShadowEffect` osztályt (elérhető v20.x‑ben). | Biztosítja, hogy a kód régi projektekben is fusson. |
| **Mentés PDF‑ként** | `document.Save("ShadowShape.pdf");` | Az árnyék ugyanúgy jelenik meg a PDF kimenetben. |

> **Gyakori kérdés:** *Mi van, ha az árnyék nem jelenik meg Wordben?*  
> Győződj meg róla, hogy a legújabb Aspose.Words verziót (≥ 22.9) használod. A régebbi kiadások korlátozott árnyék‑támogatással rendelkeztek. Emellett ellenőrizd, hogy a dokumentumot egy friss Word‑verzióban (2016+) nyitod meg.

## Teljes működő példa

Az alábbi program teljes, másolás‑beillesztés‑kész kódot tartalmaz. Minden `using` direktívát, megjegyzést és hibakezelést is, hogy zökkenőmentes legyen a futtatás.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Futtasd a programot, navigálj a `C:\Temp\ShadowShape.docx` helyre, és láthatod a pontosan beállított árnyékkal rendelkező téglalapot.

## Összefoglalás és következő lépések

- Most már tudod, hogyan **create word document c#**, hogyan szúrj be egy téglalapot, és hogyan **apply shadow to shape** egy egyedi **set shadow distance**‑del.  
- A példa az Aspose.Words‑t használja, amely elrejti az OpenXML bonyolultságát, és garantálja a konzisztens megjelenítést a Word verziók között.  
- Szeretnél tovább lépni? Próbáld ki több alakzat kombinálását, szöveg hozzáadását a téglalapba, vagy exportáld ugyanazt a dokumentumot PDF‑ként, hogy lásd, hogyan viselkedik az árnyék.

### Kapcsolódó témák, amelyeket érdemes felfedezni

- **How to add shape** a fejléc/láblécbe márkaépítés céljából.  
- **Aspose.Words** használata diagramok és táblázatok programozott beszúrásához.  
- **Shadow effects** testreszabása képeken vektoros alakzatok helyett.  
- Tömeges dokumentumgenerálás automatizálása számlák vagy bizonyítványok számára.

Kísérletezz, törjön el a kód, majd építsd újra – ez a leggyorsabb módja a koncepciók elsajátításának. Ha elakadsz, írj egy megjegyzést alul, vagy nézd meg az Aspose.Words hivatalos dokumentációját a mélyebb API‑részletekért.

Boldog kódolást, és élvezd, hogy a Word fájljaid egy kicsit elegánsabbak lesznek!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}