---
category: general
date: 2026-03-06
description: Hozzon létre téglalap alakzatot a Wordben, és adjon hozzá árnyékot az
  Aspose.Words segítségével. Tanulja meg, hogyan szúrjon be téglalapot a Wordbe, és
  hogyan adjon árnyékot az alakzathoz C#-ban.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: hu
og_description: Hozzon létre téglalap alakzatot a Wordben, és adjon hozzá árnyékot
  az Aspose.Words segítségével. Lépésről‑lépésre útmutató arról, hogyan illessze be
  a téglalapot a Wordbe, és hogyan adjon árnyékot az alakzathoz.
og_title: Téglalap alakzat létrehozása árnyékkal a Wordben az Aspose.Words segítségével
tags:
- Aspose.Words
- C#
- Word Automation
title: Téglalap alakzat létrehozása árnyékkal a Wordben az Aspose.Words segítségével
url: /hu/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alak létrehozása árnyékkal Word-ben az Aspose.Words használatával

Valaha is szükséged volt **téglalap alak** létrehozására egy Word dokumentumban, de nem tudtad, hogyan adj neki egy kifinomult megjelenést? Nem vagy egyedül – a legtöbb fejlesztő ugyanazzal a problémával szembesül, amikor először próbál vizuális csavart adni az automatizált dokumentumoknak. A jó hír? Az Aspose.Words for .NET segítségével mind **téglalap alak** létrehozható, mind **alak árnyék** hozzáadható néhány C# sorral.

Ebben az útmutatóban pontosan végigvezetünk a **téglalap beszúrásának Word-be** folyamatán, majd megmutatjuk, **hogyan adjunk árnyékot az alakhoz**, hogy kiemelkedjen a lapról. A végére egy mentésre kész `Shadow.docx` fájlod lesz, amelyet megnyithatsz Wordben, és láthatod a szürke árnyalatú téglalapot egy lágy vetett árnyékkal. Nincs szükség extra képfájlokra, nincs kézi finomhangolás – csak kód.

## Mit fogsz megtanulni

- A pontos C# utasítások, amelyek szükségesek a **téglalap alak** létrehozásához az Aspose.Words segítségével.  
- Hogy engedélyezzünk és konfiguráljunk egy árnyékot a `Shadow` objektum használatával.  
- Miért fontos minden egyes tulajdonság (pl. `Transparency`, `Blur`, `Angle`).  
- Gyakori buktatók (egységek, verziókompatibilitás) és gyors megoldások.  
- Egy teljes, másolás‑beillesztésre kész program, amelyet már ma futtathatsz.  

### Előfeltételek

- .NET 6+ (vagy .NET Framework 4.7+).  
- Aspose.Words for .NET 23.10 vagy újabb (a NuGet csomag neve `Aspose.Words`).  
- Alapvető C# és Visual Studio (vagy bármely kedvelt IDE) ismeretek.  

Ha már megvannak ezek, ugorjunk egyenesen bele.

---

## 1. lépés: A projekt beállítása és a névterek importálása

Először hozz létre egy új konzolos alkalmazást (vagy használj egy meglévőt), és add hozzá az Aspose.Words NuGet csomagot:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Ezután hozd be a szükséges névtereket a `Program.cs` fájlodba:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tipp:** Ha .NET 6+ célplatformot használsz, engedélyezheted a globális `using` direktívákat, hogy elkerüld ezen sorok ismétlését minden fájlban.

---

## 2. lépés: **Téglalap alak** létrehozása egy üres Word dokumentumban

Kezdünk egy új `Document` objektummal és egy `DocumentBuilder`-rel, amellyel manipulálhatjuk azt. A builder `InsertShape` metódusa az, ahol a varázslat történik.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Miért 200 × 100 pont? Wordben egy pont 1/72 hüvelyknek felel meg, így a téglalap körülbelül 2,8 × 1,4 hüvelyk lesz – elég nagy ahhoz, hogy észrevegyék, de nem túlzott. A számokat módosíthatod a saját elrendezésedhez; csak ne feledd, hogy **pontban** mérnek, nem pixelekben.

---

## 3. lépés: **Árnyék hozzáadása az alakhoz** – a megjelenés beállítása

Miután megvan a téglalap, adjunk neki egy finom szürke árnyékot. A `Shadow` objektum a `Shape` része, és több hasznos tulajdonságot is elérhetővé tesz.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Mit jelent minden egyes tulajdonság

| Tulajdonság | Hatás | Tipikus értékek |
|------------|-------|-----------------|
| **Enabled** | Turns the shadow on/off | `true` or `false` |
| **Color** | Base colour of the shadow | Any `System.Drawing.Color` |
| **Transparency** | Opacity (0 = solid, 1 = invisible) | 0.0 – 1.0 |
| **Blur** | Softness of the edge | 0 – 10 (higher = softer) |
| **Distance** | Gap between shape and shadow | 0 – 20 points |
| **Angle** | Direction the light appears to come from | 0 – 360 degrees |
| **Size** | Scale of the shadow relative to the shape | 0 – 200 % |

> **Miért érdemes ezeket a beállításokat használni?**  
> Az árnyék finomhangolásával megfelelhetsz a vállalati arculati irányelveknek (pl. egy finom 20 % átlátszóság a professzionális megjelenéshez) anélkül, hogy külső képszerkesztőkhöz kellene folyamodnod.

---

## 4. lépés: A dokumentum mentése és az eredmény ellenőrzése

Végül írd a fájlt a lemezre. Bármely mappát választhatod; csak cseréld le a `YOUR_DIRECTORY`-t egy valós útvonalra.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Nyisd meg a `Shadow.docx` fájlt a Microsoft Wordben, és látnod kell egy szürke téglalapot egy enyhe vetett árnyékkal, amely 45°-os szöggel van eltolva. Ez a vizuális jelzés azt a benyomást kelti, mintha az alak a lapról „felemelkedne” – pontosan amire egy kifinomult jelentés vagy számla esetén számítanál.

## Teljes működő példa

Az alábbiakban a teljes programot találod, amelyet beilleszthetsz a `Program.cs` fájlba. Semmi hiányzik; úgy fordul és fut, ahogy van.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Várt kimenet

- **Fájl:** `Shadow.docx`, a projekt futtatási mappájában.  
- **Vizuál:** Egyetlen téglalap a lap közepén, alapértelmezett fehér kitöltéssel, és egy szürke árnyék, amely 4 ponttal a jobb alsó irányba van eltolva, enyhén elmosódva a természetes hatás érdekében.

## Gyakori kérdések és speciális esetek

### 1. Mi van, ha más egységre van szükség (pl. centiméter)?

Az Aspose.Words pontokban dolgozik, de a centimétereket egyszerű képlettel átalakíthatod pontokra:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Működik ez régebbi Aspose.Words verziókkal?

A `Shadow` API a 14.0-s verzióban került bevezetésre. Ha régebbi kiadást használsz, frissítened kell a NuGet-en keresztül. A kód többi része (alakok létrehozása) évek óta stabil, így nem fogsz töréspontokba ütközni.

### 3. Hozzáadhatok-e árnyékot más alakokhoz (pl. körök)?

Természetesen – bármely `Shape` objektum rendelkezik `Shadow` tulajdonsággal. Csak cseréld le a `ShapeType.Rectangle`-t `ShapeType.Ellipse`-re vagy `ShapeType.Cloud`-ra, majd alkalmazd ugyanazokat az árnyékbeállításokat.

### 4. Mi van, ha színes árnyékra van szükség (pl. kék a márkához)?

Cseréld le a `Color.Gray`-t bármely kívánt `Color`-ra:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Ne felejtsd el a `Transparency`-t beállítani, hogy a szín ne legyen túl domináns.

## 🎨 Vizuális összefoglaló

![téglalap alak létrehozása árnyékkal Word-ben az Aspose.Words használatával](image-placeholder.png "téglalap alak létrehozása árnyékkal Word-ben az Aspose.Words használatával")

*Alt szöveg: téglalap alak létrehozása árnyékkal Word-ben az Aspose.Words használatával*

A képernyőkép (helyőrző) a végleges dokumentumot mutatja – csak a téglalapot és annak lágy szürke árnyékát.

## Következtetés

Most már tudod, hogyan **téglalap alakot** hozz létre egy Word fájlban, **árnyékot adj az alakhoz**, és finomhangold a vizuális megjelenést az Aspose.Words for .NET segítségével. Az általunk írt rövid program lefedi a teljes munkafolyamatot – a

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}