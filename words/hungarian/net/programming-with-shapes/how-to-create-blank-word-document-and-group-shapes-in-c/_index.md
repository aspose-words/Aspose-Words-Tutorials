---
category: general
date: 2026-10-07
description: Üres Word-dokumentum létrehozása C#-ban, és megtanulni téglalap alakzatot
  hozzáadni, képalakzatot beszúrni, valamint több alakzatot csoportosítani dinamikus
  jelentésekhez.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: hu
lastmod: 2026-10-07
og_description: Üres Word-dokumentum létrehozása C#-ban az Aspose.Words segítségével.
  Tanulja meg, hogyan adjon hozzá téglalap alakzatot, szúrjon be képalakzatot, és
  csoportosítsa több alakzatot professzionális dokumentumokhoz.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Üres Word-dokumentum létrehozása és alakzatok csoportosítása C#-ban – lépésről
  lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan készítsünk üres Word-dokumentumot és csoportosítsuk az alakzatokat C#-ban
url: /hu/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre üres Word dokumentumot és csoportosítsunk alakzatokat C#‑ban

Ha programozott módon **üres Word dokumentumot** kell létrehoznod, ez az útmutató pontosan megmutatja, hogyan teheted. Megtanulod, hogyan **adj hozzá téglalap alakzatot**, **illessz be képalakzatot**, és **csoportosíts több alakzatot**, hogy egyetlen objektumként viselkedjenek, amikor később **képet adsz hozzá a Wordhöz**.

A Word fájlok kódból történő kezelése ijesztőnek tűnhet, de az Aspose.Words egyszerűvé teszi a folyamatot. A tutorial végére egy újrahasználható C# kódrészletet kapsz, amely egy tiszta, üres Word fájlt generál, benne egy csoportosított téglalappal és logóval. A végeredményt beágyazhatod számlákba, jelentésekbe vagy bármilyen automatizált dokumentumfolyamatba.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy rendelkezel a következőkkel:

* .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑tel is működik).  
* Érvényes Aspose.Words for .NET licenc vagy egy ingyenes értékelő kulcs.  
* Egy képfájl (például `logo.png`), amelyet a kódból elérhető mappában helyeztél el.  
* Visual Studio 2022 vagy bármely C#‑kompatibilis IDE.

Nem szükséges további NuGet csomag a `Aspose.Words`‑en kívül.

## Hogyan hozzunk létre üres Word dokumentumot az Aspose.Words‑szal

Az első lépés mindig a **üres Word dokumentum létrehozása**. Ez az objektum fogja tartalmazni az összes későbbi alakzatot.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

A `Document` képviseli a teljes `.docx` fájlt. Ebben a pontban a fájl üres, ami megfelel a *üres Word dokumentum létrehozása* követelménynek.

## Konténer létrehozása több alakzat csoportosításához

Az alakzatok csoportosítása lehetővé teszi, hogy egyszerre mozgass, forgass vagy átméretezz több elemet. Az Aspose.Words a `GroupShape` osztályt biztosítja erre a célra.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

A `Bounds` téglalap határozza meg, hogy a csoport hol jelenik meg az oldalon. Ha a csoportot az első bekezdésbe helyezzük, garantáljuk, hogy a **üres Word dokumentum létrehozása** azonnal tartalmaz egy vizuális konténert.

## Hogyan adjunk hozzá téglalap alakzatot a csoporton belül

Gyakori igény a **téglalap alakzat hozzáadása** háttérként vagy keretként. Az alábbi kód létrehoz egy téglalapot, és hozzáadja a korábban definiált csoporthoz.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Mivel a téglalap a `GroupShape`‑en belül él, együtt mozog majd a később hozzáadott egyéb alakzatokkal. Ez a **több alakzat csoportosítása** funkció központja.

## Hogyan illessz be képalakzatot a csoportba

Ezután **képalakzatot illesztesz be** (a logót), és a téglalap mellé helyezed. Ez demonstrálja a **kép hozzáadása a Wordhöz** munkafolyamatot.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

A `SetImage` metódus beolvassa a fájlt és közvetlenül beágyazza a Word dokumentumba, biztosítva, hogy a kép megmaradjon akkor is, ha a forrásfájl áthelyezésre kerül. Ezzel befejeződik a **képalakzat beillesztése** lépés, és teljesül a **kép hozzáadása a Wordhöz** követelmény.

## Dokumentum mentése

Végül írjuk a fájlt a lemezre. A mentett fájl tartalmazza az üres dokumentumot, a csoportosított téglalapot és a beágyazott logót.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Amikor megnyitod a `GroupShape.docx` fájlt a Microsoft Wordben, egyetlen csoportot látsz, amely egy világosszürke téglalapot és a logót helyezi el egymás mellett. A csoport bármely részének kiválasztása lehetővé teszi a teljes gyűjtemény mozgatását vagy átméretezését, bizonyítva, hogy az alakzatok valóban **több alakzatot csoportosítanak**.

## Teljes, futtatható példa

Az alábbi teljes programot másold, illeszd be és futtasd. Cseréld le a `YOUR_DIRECTORY`‑t egy olyan abszolút vagy relatív útvonalra, amely létezik a gépeden.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Várható kimenet

* Egy `GroupShape.docx` nevű fájl, amely a `YOUR_DIRECTORY`‑ben található.  
* A fájl megnyitása Wordben egyetlen vizuális csoportot mutat, bal oldalon egy szürke téglalappal, jobb oldalon a `logo.png`‑nel.  
* A vizuális csoport bármely részének kiválasztása lehetővé teszi a teljes gyűjtemény mozgatását vagy átméretezését, megerősítve, hogy az alakzatok helyesen **több alakzatot csoportosítanak**.

## Gyakori kérdések és speciális esetek kezelése

| Kérdés | Válasz |
|---|---|
| **Hozzáadhatok több mint két alakzatot ugyanahhoz a csoporthoz?** | Igen. Hívjuk a `group.AppendChild(yourShape)`‑t minden további `Shape` esetén. A csoport tetszőleges számú rajzobjektumot tartalmazhat. |
| **Mi történik, ha a képfájl hiányzik?** | A `SetImage` `FileNotFoundException`‑t dob. Tekerjük be a hívást try‑catch blokkba, és biztosítsunk tartalékot (például egy helyőrző alakzatot). |
| **Szükséges beállítani a `WrapType`‑ot az alakzatoknál?** | Alapértelmezés szerint az alakzatok inline‑ok. Ha lebegő viselkedésre van szükség, állítsuk be a `picture.WrapType = WrapType.Inline;`‑t vagy más wrap módot a csoporthoz adás előtt. |
| **Hogyan befolyásolja a dokumentum mérete a csoport határait?** | A `Bounds` téglalap pontokban van megadva (1 pt ≈ 1/72 in). Állítsuk a méretet, ha a csoportot másik oldalelrendezésre (pl. A4 vs. Letter) helyezzük. |
| **Újra felhasználhatom ugyanazt a csoportot egy másik dokumentumban?** | Igen. Klónozhatjuk a csoportot a `GroupShape cloned = (GroupShape)group.Clone(true);` segítségével, majd beilleszthetjük egy másik `Document`‑be. |

## Pro tippek

* **Használd újra a `DocumentBuilder`‑t** szöveg hozzáadásához a csoport előtt vagy után. Automatikusan a jelenlegi kurzorpozíciót veszi figyelembe.  
* **Állítsd be a `Shape.StrokeColor`‑t**, ha látható keretet szeretnél a téglalap köré.  
* **Használj nagy felbontású PNG‑ket** a logóhoz, hogy elkerüld a pixelesedést, amikor

## Mit érdemes még megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek az ebben az útmutatóban bemutatott technikákra épülnek. Minden forrás komplett működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}