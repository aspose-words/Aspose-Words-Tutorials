---
category: general
date: 2026-01-02
description: Hozzon létre Word-dokumentumot egy téglalap alakzattal, állítsa be az
  alakzat kitöltőszínét, és mentse el a docx fájlt az Aspose.Words használatával.
  Tanulja meg, hogyan készítsen téglalapot árnyékkal percek alatt.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: hu
og_description: Hozzon létre Word-dokumentumot egy egyéni téglalappal, állítsa be
  a kitöltőszínt, adjon hozzá árnyékot, és mentse DOCX formátumban. Teljes kód és
  magyarázatok.
og_title: Word-dokumentum létrehozása téglalap alakzattal – lépésről lépésre
tags:
- Aspose.Words
- C#
- Document Generation
title: Word dokumentum létrehozása téglalap alakzattal és árnyékkal – Teljes útmutató
url: /hu/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása téglalap alakzattal és árnyékkal – Teljes útmutató

Valaha is elgondolkodtál, hogyan **create word document** olyan dokumentumot, amely egy szép stílusú téglalapot tartalmaz? Lehet, hogy egy logó helyőrzőre, egy színes bannerre vagy csak egy vizuális jelzésre van szükséged egy jelentésben. Ebben az útmutatóban **add rectangle shape**, színt adunk a kitöltésnek, egy finom árnyékot alkalmazunk, és végül **save docx file** – mindezt az Aspose.Words for .NET segítségével.

Kész C# kódrészlettel, minden sor részletes magyarázatával és néhány újrahasználható tippel távozol, amelyeket saját projektjeidben alkalmazhatsz. Nincs felesleges részlet, csak egy gyakorlati megoldás, amit egyszerűen másolhatsz és beilleszthetsz.

## Amire szükséged lesz

- .NET 6 vagy újabb (a kód .NET Frameworkön is működik)  
- Visual Studio 2022 (vagy bármelyik kedvenc szerkesztő)  
- **Aspose.Words** NuGet csomag (`Install-Package Aspose.Words`)  

Ha már megvannak ezek, nagyszerű – vágjunk bele.

## 1. lépés – Új dokumentum inicializálása (How to create word document)

Az első dolog, amit tenned kell, hogy **create word document** memóriában. Gondolj rá úgy, mint egy üres vászonra, ahol később megrajzolod a téglalapot.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Miért fontos:** `Document` képviseli az egész DOCX fájlt, míg a `DocumentBuilder` egy kényelmes segédeszköz, amely lehetővé teszi szöveg, táblázatok, képek és alakzatok beszúrását anélkül, hogy manuálisan kezelnéd az alatta lévő csomópontfát.

## 2. lépés – Téglalap alakzat beszúrása (Add rectangle shape)

Most **add rectangle shape** a dokumentumba. Az `InsertShape` metódus megkapja az alakzat típusát és méreteit pontban (1 pont = 1/72 hüvelyk).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Pro tipp:** Ha valaha más geometriát (ellipszis, háromszög stb.) kell létrehoznod, egyszerűen cseréld le a `ShapeType.Rectangle`-t a kívánt enum értékre.

## 3. lépés – Árnyék beállítása (Set shape fill color & shadow)

Az árnyék egy lapos alakzatot háromdimenziósabbá tehet. Itt engedélyezzük az árnyékot és finomhangoljuk a megjelenését.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Miért ezek az értékek?** Egy szerény elmosódási sugár és egy 5‑pontos távolság megakadályozza, hogy az árnyék elnyomja az alakzatot, míg a 45° egy bal felső sarokból érkező fényforrást imitál – ez egy gyakori UI konvenció.

## 4. lépés – Dokumentum mentése (Save docx file)

Végül **save docx file** a lemezre. Igazítsd az elérési utat a környezetedhez.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Amikor megnyitod a `ShadowDemo.docx` fájlt a Wordben, egy világoskék téglalapot látsz majd egy lágy szürke árnyékkal, pontosan úgy, mint az alábbi képernyőképen.

![Create Word Document with rectangle shape and shadow](https://example.com/images/rectangle-shadow.png "Create Word Document with rectangle shape and shadow")

*Kép alt szöveg:* **Create Word Document** egy téglalap alakzatot árnyékkal mutat.

## Teljes, futtatható példa (How to create rectangle and save)

Mindent összevonva, itt a teljes program, amelyet beilleszthetsz egy konzolos alkalmazásba:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Várható eredmény

- Egy **ShadowDemo.docx** nevű fájl jelenik meg a célmappában.  
- Megnyitva a Microsoft Wordben, egyetlen oldalon a “Shadow Demo” szöveg után egy világoskék téglalap látható.  
- A téglalap egy lágy szürke árnyékot vet 45° szöggel, enyhe 3‑D hatást kölcsönözve.

## Gyakori kérdések és szélhelyzetek

### Mi van, ha más méretre van szükséged?

Egyszerűen módosítsd a `200, 100` argumentumokat az `InsertShape`‑ben. Ezek a számok a szélességet és magasságot jelölik pontban. Egy négyzethez azonos értékeket használj.

### Tudom-e erőteljesebbé tenni az árnyékot?

Növeld a `BlurRadius`‑t a simább élért, emeld a `Distance`‑t a nagyobb eltolásért, vagy csökkentsd a `Transparency`‑t (pl. `0.1`) a sötétebb árnyékért.

### Hogyan adhatok keretet a téglalap köré?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Kompatibilis-e ez az Aspose.Words régebbi verzióival?

Igen. A `ShadowFormat` osztály már a 2020-as korai kiadásoktól létezik. Ha nagyon régi verziót használsz, előfordulhat, hogy frissítened kell a teljes funkcionalitás eléréséhez.

## Tippek és buktatók

- **Pro tipp:** Mindig szabadítsd fel a nagy dokumentumokat (`doc.Dispose()`) amikor befejezted, különösen webalkalmazásokban, hogy natív erőforrásokat szabadíts fel.  
- **Vigyázz:** Relatív útvonal használata megfelelő jogosultságok nélkül `UnauthorizedAccessException`-t okozhat. Inkább abszolút útvonalakat használj vagy biztosítsd, hogy az alkalmazás pool írási jogosultsággal rendelkezzen.  
- **Ne feledd:** A `FillColor` tulajdonság bármilyen `System.Drawing.Color` értéket elfogad. Nyugodtan használhatod a `Color.FromArgb(255, 173, 216, 230)`-t egy egyedi pasztell árnyalathoz.

## Következő lépések

Most, hogy tudod, hogyan **create word document**, **add rectangle shape**, **set shape fill color**, és **save docx file**, tovább kísérletezhetsz:

- Több alakzat beszúrása és elrendezése a `RelativeHorizontalPosition` és `RelativeVerticalPosition` segítségével.  
- A téglalap kombinálása szöveggel a `Shape.TextBox` használatával feliratokhoz.  
- Ugyanazon dokumentum exportálása PDF‑be (`doc.Save("output.pdf")`) terjesztéshez.  

Ha érdekelnek a fejlettebb grafikák, nézd meg az Aspose.Words támogatását a **WordArt**, **chart** és **inline images** számára. Mindegyik ugyanazt a mintát követi: node létrehozása, tulajdonságok beállítása, majd mentés.

---

### TL;DR

- `Document` és `DocumentBuilder` használata a **create word document**-hez.  
- `InsertShape(ShapeType.Rectangle, …)` hívása a **add rectangle shape**-hez.  
- `FillColor` beállítása a kívánt háttérhez.  
- `ShadowFormat` engedélyezése és a tulajdonságok finomhangolása a kifinomult megjelenésért.  
- Befejezés a `document.Save("yourPath.docx")`-val a **save docx file**-hez.

Boldog kódolást, és élvezd, hogy Word fájljaid egy kicsit stílusosabbak lesznek!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}