---
category: general
date: 2026-08-10
description: Word dokumentum létrehozása programozottan az Aspose.Words használatával,
  megtanulni, hogyan csoportosítsunk több alakzatot a Wordben, hogyan adjunk hozzá
  téglalapot a Wordhöz, és hogyan hozzunk létre csoportos alakzatot C#-ban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: hu
lastmod: 2026-08-10
og_description: Word dokumentum létrehozása programozottan az Aspose.Words segítségével.
  Ez az útmutató megmutatja, hogyan csoportosíthat több alakzatot a Wordben, hogyan
  adhat hozzá egy téglalapot a Wordhöz, és hogyan ágyazhat be egy egyszerű szöveges
  tartalomvezérlőt, mindezt C#‑ban.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Word dokumentum létrehozása programozottan – alakzatok csoportosítása C#‑ban
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Word dokumentum létrehozása programozottan és alakzatok csoportosítása C#‑ban
url: /hu/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum programozott létrehozása és alakzatok csoportosítása C#‑ban

Ha **programozottan kell Word dokumentumot létrehozni**, ez a bemutató megmutatja, hogyan építsünk egy DOCX fájlt az Aspose.Words segítségével, és **csoportosítsuk a több alakzatot Word‑ben**. Kitérünk arra is, hogyan **adjunk hozzá téglalapot Word‑höz** és **hogyan hozzunk létre csoportos alakzatot**, amely egy téglalapot és egy ellipszist tartalmaz, valamint egy egyszerű szöveges StructuredDocumentTag‑et a felhasználói bevitelhez.

A végén egy használatra kész Word fájlt kapunk, amely egy csoportosított téglalap‑ellipszis alakzatot és egy tartalomvezérlőt tartalmaz, ahol a felhasználó beírhat egy nevet. A kód futtatása után nem szükséges kézi szerkesztés a Word‑ben.

## Amire szükséged lesz

- .NET 6.0 vagy újabb (a minta .NET 6‑ra céloz, de bármely friss .NET verzió működik)
- Aspose.Words for .NET licenc (az ingyenes próba verzió teszteléshez elegendő)
- Visual Studio 2022 vagy bármely kedvelt C# IDE
- Alapvető ismeretek a C# szintaxisáról

## Word dokumentum programozott létrehozása – általános munkafolyamat

A folyamat három logikai fázisból áll:

1. **Inicializálás** egy `Document` és egy `DocumentBuilder` objektummal – ez a bármely generált Word fájl alapja.
2. **Csoportos alakzat építése**, amely egy téglalapot és egy ellipszist tartalmaz – bemutatja a **group multiple shapes word** és a **how to create group shape** műveleteket.
3. **StructuredDocumentTag (SDT) beszúrása** – egy egyszerű szöveges tartalomvezérlő, amely lehetővé teszi a végfelhasználók számára az adatok kitöltését, illusztrálva az **add rectangle to word** lépést a dokumentum teljes elrendezésében.

Az alábbiakban a teljes, futtatható kódot, majd a lépésről‑lépésre magyarázatot találod.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### 1. lépés – A dokumentum és a builder inicializálása
A `Document` objektum a teljes DOCX fájlt képviseli, míg a `DocumentBuilder` kényelmes API‑t biztosít a tartalom hozzáadásához. Ezek inicializálása az első követelmény, amikor **programozottan kell Word dokumentumot létrehozni**.

> **Pro tipp:** Ha ugyanazt a dokumentumot több műveletben is újra felhasználod, tarts egyetlen `DocumentBuilder` példányt, hogy elkerüld a felesleges objektum‑létrehozást.

### 2. lépés – Csoportos alakzat konténer létrehozása
Egy `Shape` `ShapeType.Group` típussal egy vászonként működik, amely más alakzatokat tarthat. A `Width` és `Height` beállítása meghatározza a csoport határoló dobozát. Ez a **how to create group shape** központi eleme az Aspose.Words‑ben.

> **Szélsőséges eset:** Ha a csoport szélessége kisebb, mint a gyermekek összesített szélessége, a gyermekek levágásra kerülnek. Mindig olyan méretű csoportot állíts be, amely minden gyermek alakzatot befogad.

### 3. lépés – Téglalap hozzáadása Word‑höz
A téglalap `ShapeType.Rectangle`‑el jön létre. A `Left` és `Top` tulajdonságok a csoport eredetéhez képest helyezik el. Ez a lépés demonstrálja az **add rectangle to word** műveletet, és megmutatja, hogyan irányítható a pontos pozíció.

> **Gyakori hiba:** A `Left`/`Top` elhagyása miatt a téglalap a csoport alapértelmezett origóján (0,0) jelenik meg, ami átfedhet más gyermekeket.

### 4. lépés – Ellipszis (kör) hozzáadása a csoporthoz
Az ellipszis ugyanúgy kerül hozzáadásra, mint a téglalap, csak `ShapeType.Ellipse`‑t használunk. A `Left = 210` eltolja jobbra a téglalaptól, így egy vizuálisan elkülönülő párost hozunk létre ugyanabban a csoportban.

> **Miért használjunk csoportot?** A csoportosítás lehetővé teszi, hogy később egyetlen művelettel mozgassuk, forgassuk vagy méretezzük mindkét alakzatot, megőrizve relatív elrendezésüket.

### 5. lépés – A kész csoportos alakzat beszúrása a dokumentumba
A `builder.InsertNode(groupShape)` a teljes csoportot a jelenlegi kurzorpozícióba helyezi. Mivel a csoport már tartalmazza a gyermekeket, nincs szükség további beszúrási hívásokra a téglalap vagy az ellipszis esetén.

### 6. lépés – Egyszerű szöveges StructuredDocumentTag (SDT) létrehozása
A StructuredDocumentTag egy tartalomvezérlő, amelyet a végfelhasználók kitölthetnek, amikor a dokumentumot Word‑ben megnyitják. A `Title = "CustomerName"` érték értelmes azonosítót ad a vezérlőnek, ami későbbi adatkinyerésnél hasznos.

> **Miért egyszerű szöveges SDT?** Korlátozza a bevitt adatot egyszerű szövegre, megakadályozva a véletlen formázást, amely a további feldolgozást megzavarhatja.

### 7. lépés – Dokumentum mentése
A `doc.Save("GroupAndSDT.docx")` a fájlt a lemezre írja. A keletkezett DOCX tartalmazza a csoportos alakzatokat és az SDT‑t. A fájl megnyitása a Microsoft Word‑ben egy téglalapot mutat egy kör mellett, mindkettő egyetlen objektumként kiválasztható, alatta pedig egy „Enter name here …” feliratú szürke árnyalatú tartalomvezérlő.

#### Várt kimenet
- **GroupAndSDT.docx** nevű fájl a futtatási mappában.
- Word‑ben: egy csoportos alakzat (téglalap + ellipszis), amelyet egy egységként lehet mozgatni.
- A csoport közvetlenül alatti szürke árnyalatú tartalomvezérlő, amely a felhasználót a név beírására kéri.

## További variációk és legjobb gyakorlatok

### Különböző alakzat típusok használata
A `ShapeType.Rectangle` vagy `ShapeType.Ellipse` helyett bármely más `ShapeType` (pl. `ShapeType.Polygon`, `ShapeType.Line`) használható. A csoportosítás logikája változatlan marad.

### Kitöltő szín és szegély beállítása
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
A kitöltés és a vonal hozzáadása javítja a vizuális megkülönböztethetőséget, különösen, ha a dokumentumot nem‑technikai érintettekkel osztod meg.

### A teljes csoport forgatása
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
A csoport forgatása hatékonyabb, mint az egyes gyermekek külön‑külön forgatása.

### Exportálás PDF‑be
Ha PDF‑verzióra van szükséged, egyszerűen hívd meg:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Az összes csoportos alakzat és az SDT (szövegmezőként megjelenítve) megjelenik a PDF‑ben.

## Gyakori buktatók és elkerülésük módja

| Symptom | Cause | Fix |
|---------|-------|-----|
|         |       |     |
|         |       |     |
|         |       |     |

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}