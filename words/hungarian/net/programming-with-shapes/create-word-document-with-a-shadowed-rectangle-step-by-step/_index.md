---
category: general
date: 2026-01-13
description: Word dokumentum létrehozása az Aspose.Words segítségével, és megtanulni,
  hogyan szúrjunk be téglalap alakzatot, hogyan adjunk hozzá árnyékot, illetve hogyan
  alkalmazzunk alakzatárnyékot C#-ban. Teljes példát tartalmaz.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: hu
og_description: Hozzon létre Word-dokumentumot az Aspose.Words segítségével, tekintse
  meg, hogyan szúrjon be téglalap alakzatot és hogyan adjon hozzá árnyékot. Kövesse
  a teljes C# példát.
og_title: Word-dokumentum létrehozása árnyékolt téglalappal – Teljes útmutató
tags:
- Aspose.Words
- C#
- Document Automation
title: Word-dokumentum létrehozása árnyékolt téglalappal – Lépésről lépésre útmutató
url: /hu/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása árnyékolt téglalappal – Lépésről‑lépésre útmutató

Valaha szükséged volt már **create word document**-ra, amely egy szép árnyékolt téglalapot tartalmaz, de nem tudtad, hol kezdj? Nem vagy egyedül – sok fejlesztő ugyanabba a helyzetbe ütközik, amikor először dolgozik az Aspose.Words-szal.  

Ebben az útmutatóban végigvezetünk minden szükséges lépésen, hogy programozottan **create word document**-ot készíts, **insert rectangle shape**-t helyezz el, és megmutassuk, **how to add shadow**, hogy a forma igazán kiemelkedjen. A végére egy azonnal futtatható C# kódrészletet kapsz, amelyet bármely .NET projektbe beilleszthetsz.

## Mit fogsz megtanulni

- A pontos kód a **how to insert shape** (egy téglalap) egy Word fájlba történő beillesztéséhez.
- Azok a tulajdonságok, amelyeket módosítanod kell a **add shape shadow** hozzáadásához és a megjelenés szabályozásához.
- Hogyan mentsd el az eredményt, és ellenőrizd, hogy az árnyék látható-e.
- Néhány gyakorlati tipp és széljegyzet, amelyek később fejfájást takarítanak meg.

Nem szükséges külső dokumentáció – minden itt található.

## Előfeltételek

Mielőtt belemerülnénk, győződj meg róla, hogy rendelkezel:

1. **.NET 6.0** (vagy bármely friss .NET verzió) telepítve.  
2. Egy **license** az Aspose.Words for .NET-hez, vagy a teszteléshez használhatod az ingyenes értékelő módot.  
3. Fejlesztői környezet – a Visual Studio 2022 remekül működik, de bármely szerkesztő, amely képes C#-t fordítani, megfelel.

Ennyi. Nem szükséges további NuGet csomag a `Aspose.Words`-en kívül.

## 1. lépés – A projekt beállítása és az Aspose.Words hivatkozása

Először hozz létre egy új konzolos alkalmazást, és add hozzá az Aspose.Words csomagot:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Ha a ingyenes próbaverziót használod, ne felejtsd el meghívni a `License.SetLicense`-t a licencfájloddal; különben a könyvtár vízjelet ad hozzá.

## 2. lépés – A Document Builder inicializálása

Most elkezdjük a tényleges **create word document** folyamatot. A `Document` osztály egy üres vásznat ad, a `DocumentBuilder` pedig lehetővé teszi, hogy rajzoljunk rajta.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Miért van szükségünk egy builderre? Elrejti az alacsony szintű OpenXML részleteket, így a *mit* szeretnél, nem a *hogyan* struktúrája miatt kell aggódnod. Ez a **how to insert shape** gyors megvalósításának alapja.

## 3. lépés – Téglalap alakzat beillesztése

Itt történik a tényleges **insert rectangle shape**. A téglalap 150 × 100 pont lesz (kb. 2 h × 1,3 h).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

Az `InsertShape` metódus egy `Shape` objektumot ad vissza, amelyet tovább testreszabhatunk. Ezen a ponton a téglalap csak egy szilárd fehér doboz – még nincs árnyék.

## 4. lépés – Árnyék hozzáadása (Add Shape Shadow)

Az árnyék hozzáadása meglepően egyszerű, ha tudod, mely tulajdonságokat kell módosítani. A `ShadowFormat` objektum szabályozza a láthatóságot, színt, elmosódást, eltolást és méretet.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Ez a blokk egyszerűen megválaszolja a **how to add shadow** kérdést: kapcsold be, válassz színt, állítsd be az átlátszóságot, eltolást, elmosódást és méretet. Kísérletezhetsz ezekkel a számokkal, hogy erős vetésárnyékot vagy finom, szelíd árnyékot kapj.

### Gyakori variációk

- **Different colours:** Használd a `Color.Black`-ot egy klasszikus vetésárnyékhoz, vagy a `Color.BlueViolet`-ot egy stilizált hatáshoz.  
- **Zero blur:** Állítsd `BlurRadius = 0`-ra, hogy éles, tiszta él legyen.  
- **Larger offsets:** Növeld az `OffsetX`/`OffsetY` értékét, hogy az árnyék távolabb legyen az alakzattól.

## 5. lépés – Dokumentum mentése és ellenőrzése

Végül írd a dokumentumot a lemezre. A fájl egy szabványos `.docx` lesz, amelyet bármely modern szövegszerkesztő megnyithat.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Nyisd meg a keletkezett *ShadowRectangle.docx*-t a Microsoft Wordben. Egy téglalapot kell látnod egy lágy szürke árnyékkal, amely a jobb alsó sarok felé van eltolva – pontosan úgy, ahogy a kód meghatározta.

> **Expected output:** Egy egyoldalas Word fájl, amely 150 × 100 pont méretű téglalapot tartalmaz 30 % átlátszó szürke árnyékkal, 5 pt eltolással, 4 pt elmosódással, és a forma 75 %-os méretével.

## Teljes működő példa

Mindent összevonva, itt a teljes, azonnal futtatható program:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Futtasd a programot (`dotnet run`), és kapsz egy friss Word fájlt egy szép árnyékolt téglalappal – tökéletes jelentésekhez, tanúsítványokhoz vagy bármilyen vizuális jelhez, amire szükséged van.

## Gyakran Ismételt Kérdések (GYIK)

**Q: Beszúrhatok más alakzatokat (ellipszis, csillag) és továbbra is használhatom ugyanazt az árnyék kódot?**  
A: Természetesen. Az `InsertShape` metódus bármely `ShapeType` enum értéket elfogad. Miután van egy `Shape` példányod, a `ShadowFormat` tulajdonságok ugyanúgy működnek, így a **how to add shadow** alakzatra független.

**Q: Mi van, ha az árnyékra a forma mindkét oldalán szükség van?**  
A: Az Aspose.Words csak egyetlen vetésárnyékot támogat alakzatonként. Kettős oldali hatás szimulálásához duplikáld a formát, minden másolatot eltérően offseteld, és az egyik `ShadowFormat.Visible` értékét állítsd `false`-ra, miközben a másik árnyékát láthatóvá hagyod.

**Q: Működik ez a .NET Framework 4.8-on is?**  
A: Igen. Az API verziófüggetlen; csak a megfelelő Aspose.Words DLL-t hivatkozd meg a célkeretrendszeredhez.

## Tippek és buktatók

- **Ne felejtsd el beállítani a `Visible = true`-t** – különben az árnyék tulajdonságok figyelmen kívül maradnak.  
- **Az átlátszóság értékei 0.0 (átlátszatlan) és 1.0 (teljesen átlátszó) között vannak.** Gyakori hiba, hogy `30`-at használnak a `0.3` helyett.  
- **Írásvédett mappába mentés kivételt okoz.** Győződj meg róla, hogy a kimeneti könyvtár írható.

## Következő lépések

Most, hogy ismered a **how to insert shape**, **add shape shadow**, és **create word document** használatát az Aspose.Words-szal, érdemes lehet felfedezni:

- **Szöveg hozzáadása a téglalap belsejébe** a `builder.InsertParagraph()` használatával a forma beillesztése előtt.  
- **Gradient kitöltések** vagy **mintás szegélyek** alkalmazása a gazdagabb vizuális stílusért.  
- Több oldal automatikus generálása, mindegyik más árnyékolt alakzattal, dinamikus jelentések építéséhez.

Nyugodtan kísérletezz – az árnyék színének, elmosódásának vagy méretének módosítása drámaian megváltoztathatja a dokumentum kinézetét.

*Készen állsz a termelésbe helyezni? Vedd a kódot, állítsd be a paramétereket, és nézd, ahogy a Word fájljaid néhány másodperc alatt professzionális csillogást kapnak.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}