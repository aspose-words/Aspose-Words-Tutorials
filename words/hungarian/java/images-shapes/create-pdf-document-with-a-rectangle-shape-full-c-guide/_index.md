---
category: general
date: 2026-03-25
description: PDF dokumentum létrehozása C#-ban, és tanuld meg, hogyan adhatsz hozzá
  téglalap alakzatot, állíthatsz be kitöltőszínt, módosíthatod az alakzat méretét
  és beállíthatod az átlátszóságot néhány lépésben.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: hu
og_description: Készíts PDF dokumentumot C#-ban, és nézd meg, hogyan adhatunk hozzá
  egy téglalapot, állíthatjuk be a kitöltőszínt, méretet és átlátszóságot a kifinomult
  PDF kimenethez.
og_title: PDF-dokumentum létrehozása téglalap alakzattal – C#-bemutató
tags:
- C#
- PDF
- Aspose.Words
title: PDF-dokumentum létrehozása téglalap alakzattal – Teljes C# útmutató
url: /hu/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF dokumentum létrehozása téglalap alakzattal – Teljes C# útmutató

Valaha szükséged volt **PDF dokumentum** létrehozására, amely egy egyedi stílusú alakzatot tartalmaz, de nem tudtad, hol kezdj hozzá? Nem vagy egyedül. Legyen szó jelentésgenerátorról vagy marketing szórólapról, ha programozottan tudsz téglalapot rajzolni, beállítani a kitöltő színét, finomhangolni a méretét és még az átlátszóságát is, akkor a PDF-jeid sokkal professzionálisabbak lesznek.

> **Pro tipp:** Ugyanez a megközelítés működik más alakzat típusokkal (ellipszis, vonal, stb.) – csak cseréld le a `ShapeType.RECTANGLE`-t arra, amire szükséged van.

---

## Amire szükséged lesz

| Előfeltétel | Miért fontos |
|--------------|----------------|
| **.NET 6+** (or .NET Framework 4.6+) | Az Aspose.Words könyvtár a modern futtatókörnyezeteket célozza. |
| **Aspose.Words for .NET** NuGet package | Biztosítja a `Document`, `Shape`, `ShadowEffect` és a kapcsolódó osztályokat. |
| **A C# IDE** (Visual Studio, Rider, VS Code) | Megkönnyíti a minta hibakeresését és futtatását. |
| **Basic C# knowledge** | Megérted a szintaxist anélkül, hogy mélyen belemerülnél. |

A könyvtárat a parancssorból telepítheted:

```bash
dotnet add package Aspose.Words
```

Ennyi—nincs extra DLL, nincs natív függőség. Miután a csomag telepítve van, az alábbi kód lefordul és fut.

---

## Lépésről‑lépésre megvalósítás

Az alábbiakban a folyamatot öt logikai lépésre bontjuk. Minden lépésnek van egy egyértelmű címe (így az AI modellek is indexelni tudják) és egy rövid kódrészlet, amelyet közvetlenül másolhatsz.

### ## 1. PDF dokumentum létrehozása és a vászon előkészítése

Az első dolog, amit teszünk, egy `Document` példányosítása. Tekintsd úgy, mint egy üres vászonra, amely végül a PDF fájlod lesz.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Miért?** A `Document` tartalmazza az összes szekciót, bekezdést és alakzatot. Egy tiszta objektummal kezdve garantált, hogy nincsenek rejtett maradványok az előző futtatásokból.

### ## 2. Téglalap alakzat hozzáadása – Kitöltő szín beállítása és alakzat méretének meghatározása

Most létrehozunk egy téglalapot, élénk sárga kitöltést adunk neki, és meghatározzuk a méreteit. Ez lefedi a **téglalap alakzat hozzáadását**, a **kitöltő szín beállítását**, valamint a **alakzat méretének meghatározását**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Megjegyzés:** A szélesség/magasság pontban van mérve (1 pont = 1/72 hüvelyk). Igazítsd ezeket a számokat a felépítésedhez.

### ## 3. Külső árnyék alkalmazása és alakzat átlátszóságának beállítása

Az árnyékok mélységet adnak, és az átlátszóságuk szabályozása a **alakzat átlátszóságának beállítása** lényege. Az alábbiakban egy szürke külső árnyékot állítunk be 30 % átlátszósággal.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Miért állítsuk be az átlátszóságot?** A 30 % átlátszó árnyék finom, megakadályozza, hogy a téglalap „lapos” legyen az oldalon.

### ## 4. Alakzat beszúrása a dokumentum törzsébe

Most a téglalapot a dokumentum első szekciójának első bekezdésébe helyezzük. Ez a lépés köti össze az egészet.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Szélsőséges eset:** Ha az alakzatot új oldalon szeretnéd, a `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` sort tedd a shape hozzáadása előtt.

### ## 5. Dokumentum mentése PDF fájlként

Végül a memória struktúrát egy fizikai PDF fájlba mentjük. A fájl a megadott mappába lesz írva.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

A program futtatásakor megjelenik egy `shadow.pdf` nevű fájl. Megnyitva egy sárga téglalapot látsz egy lágy szürke árnyékkal, amely 4 ponttal van eltolva – pontosan úgy, ahogy a kódunk leírta.

> **Várt kimenet:** Egyoldalas PDF, ahol a téglalap a lap bal‑felső sarkához közel helyezkedik el, sárgával kitöltve, 200 × 100 pont méretű, és félig átlátszó külső árnyékkal.

## Teljes működő példa (másolás‑beillesztés kész)

Az alábbiakban az egész forrásfájl látható, készen áll, hogy egy új konzol projektbe illeszd.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tipp:** Cseréld le a `YOUR_DIRECTORY`-t egy abszolút útvonalra, például `C:\\Temp`, vagy egy relatív útvonalra, mint `./output`. A program létrehozza a mappát, ha még nem létezik.

## Gyakran Ismételt Kérdések (GYIK)

**Q: Meg tudom változtatni a téglalap pozícióját az oldalon?**  
A: Természetesen. Állítsd be a `rectangle.Left` és `rectangle.Top` értékeket (mindkettő pontban van mérve), mielőtt a bekezdéshez hozzáadod.

**Q: Mi van, ha átlátszó kitöltést szeretnék az átlátszó árnyék helyett?**  
A: Használd a `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` kifejezést – az első argumentum az alfa csatorna (0‑255), ahol a 128 körülbelül 50 % átlátszóságot eredményez.

**Q: Működik ez a .NET Core‑dal?**  
A: Igen. Az Aspose.Words támogatja a .NET Standard 2.0+ verziókat, így ugyanazt a kódot futtathatod .NET 6, .NET 7 vagy .NET Framework 4.6+ környezetben.

**Q: Hogyan adhatok hozzá több alakzatot?**  
A: Egyszerűen ismételd meg a 2‑4. lépéseket minden egyes alakzatra, esetleg különböző bekezdésekbe vagy szekciókba illesztve.

## Következtetés

Most **PDF dokumentumot** hoztunk létre a semmiből, **hozzáadtunk egy téglalap alakzatot**, **beállítottuk a kitöltő színét**, **meghatároztuk a méretét**, és **beállítottuk az alakzat átlátszóságát**, hogy egy kifinomult árnyékhatást érjünk el. A minta kód önálló, egy perc alatt lefut, és bemutatja az alapvető koncepciókat, amelyekre a bonyolultabb PDF elrendezésekhez szükséged lesz.

Készen állsz a következő kihívásra? Próbáld meg a téglalapot egy lekerekített sarkú alakzattal helyettesíteni, ágyazz be egy képet az alakzatba, vagy generálj automatikusan tartalomjegyzéket. Ugyanaz az API lehetővé teszi a szöveg, képek és vektorok rétegezését – a lehetőségek határtalanok.

Ha hasznosnak találtad ezt az útmutatót, adj egy csillagot a GitHubon, oszd meg egy csapattárssal, vagy hagyj egy megjegyzést a saját változataiddal. Boldog kódolást!

---

![PDF dokumentum létrehozása téglalap alakzattal példa](/images/rectangle-shadow.png "Képernyőfelvétel, amely a sárga téglalappal és szürke külső árnyékkal létrehozott PDF-et mutatja")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}