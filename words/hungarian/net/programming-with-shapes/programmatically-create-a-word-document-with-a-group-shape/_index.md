---
category: general
date: 2026-09-27
description: Programozott módon hozza létre a Word dokumentumot egy csoportos alakzattal
  az Aspose.Words C# használatával. Kövesse ezt a lépésről‑lépésre útmutatót a fájl
  létrehozásához, és tanuljon hasznos tippeket.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: hu
lastmod: 2026-09-27
og_description: Programozott módon hozd létre a Word dokumentumot egy csoportos alakzattal
  az Aspose.Words segítségével. Ez az útmutató végigvezet a teljes C# kódban, lépésről
  lépésre magyarázza, és bemutatja a végső eredményt.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Programozott módon Word-dokumentum létrehozása csoportos alakzattal – C#
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Programozottan létrehozni egy Word-dokumentumot csoportos alakzattal
url: /hu/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programozottan Word dokumentum létrehozása csoport alakzattal

Ha **programozottan Word dokumentumot létrehozni** kell, amely csoportosított rajzot tartalmaz, ez az útmutató pontosan megmutatja, hogyan teheted meg az Aspose.Words for .NET segítségével. Akár szerződésgenerátort, jelentéskészítőt vagy űrlapkitöltő eszközt építesz, megtanulod a teljes C# kódot, hogy miért fontos minden API hívás, és hogyan kezeld a gyakori széljegyeket.

Csoportos alakzat létrehozása Wordben trükkösnek tűnhet, mert a Word objektummodell a csoport alakzatokat más rajzobjektumok tárolóiként kezeli. Ez az útmutató nem csak azt válaszolja meg, **hogyan kell csoport alakzatot létrehozni Wordben**, hanem bemutatja, hogyan ágyazzunk be egy egyszerű szöveges StructuredDocumentTag (SDT) elemet a csoportba, hogy az alakzat szerkeszthető tartalmat tartalmazzon.

## Amit el fogsz érni

- Új üres Word dokumentum inicializálása a `Document` és `DocumentBuilder` segítségével.
- Egy `GroupShape` beszúrása az aktuális kurzorpozícióba.
- Egy egyszerű szöveges `StructuredDocumentTag` (SDT) hozzáadása a csoport alakzathoz.
- A fájl mentése `.docx` formátumban, amely megnyitható a Microsoft Wordben.
- A `GroupShape` és `StructuredDocumentTag` kulcsfontosságú tulajdonságainak megértése a jövőbeli bővítésekhez.

### Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7+ esetén is működik).
- Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`).
- C# IDE, például Visual Studio 2022 vagy VS Code a C# kiegészítővel.

---

## Programozottan Word dokumentum létrehozása – a projekt beállítása

1. **Új konzolos projekt létrehozása**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Nyisd meg a projektet az IDE-ben** és cseréld le a `Program.cs` tartalmát a következő szakaszokban látható kóddal.

> **Pro tipp:** Tartsd tisztán a projekt mappáját; az Aspose.Words a kimeneti fájlt a munkakönyvtárba írja, hacsak nem adsz meg abszolút elérési utat.

## 1. lépés: Dokumentum és builder inicializálása

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Miért fontos:**  
`Document` a teljes Word fájlt képviseli, míg a `DocumentBuilder` lehetővé teszi új elemek elhelyezését anélkül, hogy manuálisan navigálnál a csomópontfában. Az oldal méreteinek korai beállítása biztosítja, hogy a csoport alakzat ne lógjon ki az oldalról.

## 2. lépés: GroupShape beszúrása az aktuális kurzorpozícióba

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Magyarázat:**  
A `GroupShape` egy rajzobjektum, amely más alakzatokat, képeket vagy szövegdobozokat tartalmazhat. A `Width`, `Height`, `Left` és `Top` beállításával pontosan meghatározhatod a helyét az oldalon. Az `InsertNode` metódus a alakzatot a fő dokumentumáramlásba helyezi, lebegő objektumként viselkedve.

## 3. lépés: Egyszerű szöveges StructuredDocumentTag (SDT) hozzáadása a csoportba

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Miért használjunk SDT-t?**  
A StructuredDocumentTag-ek a Word natív tartalomvezérlői. Lehetővé teszik a felhasználók számára, hogy a mentett dokumentumban közvetlenül szerkesszék a szöveget, és programozottan hozzáférhetnek később az adatkinyeréshez. Egy SDT elhelyezése egy csoport alakzatban lehetővé teszi a vizuális csoportosítás és a szerkeszthető tartalom kombinálását.

## 4. lépés: Dokumentum mentése

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Eredmény:**  
A `GroupShapeDemo.docx` megnyitása a Microsoft Wordben egy lebegő téglalapot (a csoport alakzatot) mutat, amely egy szöveghelyőrzőt tartalmaz, amely a „Enter text here” szöveget jeleníti meg. A felhasználók a alakzaton belül kattintva közvetlenül gépelhetnek.

### Várható kimeneti képernyőkép (konceptuális)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

A külső doboz a `GroupShape`; a belső szürke terület a `StructuredDocumentTag`.

---

## Hogyan hozzunk létre csoport alakzatot Wordben – további megfontolások

### További gyermek alakzatok hozzáadása

A csoportot további rajzobjektumokkal, például képekkel vagy szövegdobozokkal gazdagíthatod:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Befoglalási stílus vezérlése

Ha azt szeretnéd, hogy a csoport alakzat a szöveg mögött maradjon vagy szoros beágyazást kapjon, állítsd be a `WrapType` tulajdonságot:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Széljegy: Üres csoport alakzat

A gyermekek nélküli `GroupShape` láthatatlan helyőrzőként jelenik meg. Mindig ellenőrizd, hogy legalább egy gyermek (például egy SDT vagy egy kép) hozzá legyen adva; különben a Word a mentés során eldobhatja a csoportot.

### Kompatibilitási megjegyzés

Az Aspose.Words 23.10+ teljes mértékben támogatja a `GroupShape` és a `StructuredDocumentTag` elemeket. Ha régebbi verziókat célozol, az `AppendChild` metódus másképp viselkedhet, és a mentés után szükség lehet az `UpdatePageLayout` meghívására.

---

## Teljesen futtatható példa

Másold az alábbi teljes kódrészletet a `Program.cs` fájlba, és futtasd a projektet. A kód tartalmazza a fenti összes lépést egyetlen, önálló programban.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## Mit érdemes következőként megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Téglalap alakzat létrehozása Wordben C#‑vel – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Üres Word dokumentum létrehozása az Aspose.Words‑szel – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}