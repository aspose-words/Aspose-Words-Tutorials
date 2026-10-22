---
category: general
date: 2026-04-21
description: Hozzon létre Word-dokumentumot egy stílusos téglalappal és árnyékkal.
  Ismerje meg, hogyan adhat árnyékot, szúrhat be téglalap alakzatot, állíthatja be
  az árnyék színét, és még sok mást C#‑ban.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: hu
og_description: Hozzon létre Word-dokumentumot, és adjon hozzá egy árnyékolt téglalap
  alakzatot C#-ban. Kövesse ezt az útmutatót az árnyék színének, elmosódásának és
  eltolásainak egyszerű beállításához.
og_title: Word-dokumentum létrehozása árnyékolt téglalappal – lépésről lépésre
tags:
- Aspose.Words
- C#
- Document Automation
title: Word-dokumentum létrehozása árnyékolt téglalappal – Teljes útmutató
url: /hu/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása árnyékolt téglalappal – Teljes útmutató

Szükséged volt már **word dokumentum** létrehozására, ami egy kicsit kifinomultabb, mint egy egyszerű szöveges oldal? Lehet, hogy egy jelentés sablont vagy egy szórólapot készítesz, és egy egyszerű téglalap finom árnyékkal pont megfelelne. Ebben az útmutatóban lépésről‑lépésre bemutatjuk, hogyan szúrj be egy téglalap alakzatot, kapcsolj be árnyékot, és testre szabhatod a színét, elmosódását és eltolásait – mindezt C#‑ban és az Aspose.Words‑ben.

Megmutatjuk, **hogyan adjunk árnyékot** úgy, hogy az működjön Word 2016, 2019 vagy a legújabb Office 365 verzióval is. A végére egy menthető *.docx* fájlt kapsz, amely egy szép árnyékolt téglalapot tartalmaz, és megérted, miért kell minden egyes tulajdonságot beállítani.

## Előfeltételek

- .NET 6 (vagy bármely friss .NET Framework verzió)  
- Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`)  
- Alapvető C# szintaxis ismeret  
- IDE, például Visual Studio (bár bármely szerkesztő megfelel)

További könyvtárak nem szükségesek; minden más az Aspose.Words‑ben található.

## 1. lépés – Dokumentum és Builder inicializálása (Create Word Document)

A **word dokumentum** programozott létrehozásához a `Document` osztállyal kezdünk. A `DocumentBuilder` a festőecseted; lehetővé teszi szöveg, alakzat és egyéb elemek hozzáadását.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Miért fontos:* A `Document` objektum képviseli a teljes .docx fájlt. Nélküle nincs hova csatolni a téglalapot vagy az árnyékát.

## 2. lépés – Téglalap alakzat beszúrása (Insert Rectangle Shape)

Most **beszúrjuk a téglalap alakzatot**. Az `InsertShape` metódus egy `ShapeType` enumot, valamint a szélességet és magasságot pontban várja.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Pro tipp:* 1 pont ≈ 1/72 hüvelyk, tehát a 200 pt körülbelül 2,78 hüvelyk széles. Igazítsd ezeket a számokat a saját elrendezésedhez.

## 3. lépés – Árnyék engedélyezése (How to Add Shadow)

Az árnyékok alapértelmezés szerint le vannak tiltva. Kapcsold be a `Visible` jelzőt.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Mi történik?* Amikor a `Visible` igaz, a Word megjeleníti a vetett árnyékot a következő tulajdonságok alapján.

## 4. lépés – Árnyék megjelenésének testreszabása (Set Shadow Color, Blur, Offsets)

Itt **állítod be az árnyék színét**, elmosódási sugarát és az X/Y eltolásokat. Kísérletezz nyugodtan – különböző értékek lágy fényt, mély vetést vagy akár „lebegő” hatást eredményeznek.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Miért ezek a számok?* Az 5 pt elmosódás lágy, szőtt szélű árnyékot ad, míg a 4 pt eltolás jobbra‑lefelé mozgatja, mintha a fényforrás a bal‑felső sarokból jönne. A `Color`-t állítsd `Color.Black`‑ra erősebb kontraszthoz, vagy használj `Color.FromArgb(128, 0, 0, 0)`‑t félig átlátszó fekete árnyékhoz.

### Szélsőséges esetek és variációk

- **Nincs elmosódás:** Állítsd `Blur = 0`‑ra, ha éles, kemény szélű árnyékot szeretnél.  
- **Negatív eltolások:** Használd `OffsetX = -4`‑et, hogy az árnyék balra tolódjon.  
- **Különböző alakzatok:** Ugyanazok az árnyék tulajdonságok működnek körök, háromszögek vagy akár szabadkézi alakzatok esetén – csak változtasd meg a `ShapeType`‑ot a 2. lépésben.  
- **Kompatibilitás:** Az Aspose.Words az árnyék adatot Office Open XML formátumban írja, ami a Word 2010‑2021 és Office 365 között is működik.

## 5. lépés – Dokumentum mentése (Create Word Document)

Végül írd ki a fájlt a lemezre. Bármely támogatott formátum (`.docx`, `.pdf`, `.odt`, …) választható, de ebben az útmutatóban a klasszikus Word formátumot használjuk.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Amikor megnyitod a **ShadowRectangle.docx**‑t a Microsoft Word‑ben, egy szürke téglalapot látsz egy finom, elmosódott árnyékkal, amely a jobb‑alsó sarok felé van eltolva – pontosan úgy, ahogy kódoltuk.

### Várt kimenet

- Egyoldalas *.docx* fájl.  
- Egy 200 pt × 100 pt méretű téglalap, amely a kurzor helyén középre kerül, amikor az `InsertShape`‑t meghívod.  
- Egy szürke árnyék, amely 4 pt‑rel jobbra és 4 pt‑rel lejjebb helyezkedik el, 5 pt elmosódással.

Ha az alakzat nem középen jelenik meg, a `builder.MoveTo`‑val mozgathatod a kurzort a beszúrás előtt, vagy a beszúrás után módosíthatod a `Left` és `Top` tulajdonságokat.

## Gyakori kérdések és hibaelhárítás

**Q: Az árnyék nem jelenik meg Word‑ben.**  
A: Győződj meg róla, hogy a `ShadowFormat.Visible` **true**. Ellenőrizd továbbá, hogy a legfrissebb Aspose.Words verziót használod (az árnyék funkció a 20.3‑as verzióban került be).

**Q: Alkalmazhatok‑e fokozatot az árnyékra?**  
A: Közvetlenül a `ShadowFormat`‑on keresztül nem. A Word felhasználói felülete támogat fokozatos árnyékot, de az Open XML séma (amelyet az Aspose.Words követ) csak egyszínű árnyékot tesz elérhetővé. Ehhez manuálisan kell szerkeszteni az alapszintű XML‑t – ez egy haladóbb feladat.

**Q: Mit tehetek, ha átlátszó téglalapot szeretnék, csak árnyékkal?**  
A: A beszúrás után állítsd be `rectangle.FillColor = Color.Transparent;`. Az árnyék továbbra is megjelenik, mivel független a kitöltéstől.

## Profi tippek a produkciós kódhoz

- **A builder újrahasználata:** Ha több alakzatot adsz hozzá, tartsd meg ugyanazt a `DocumentBuilder` példányt – minden alakzathoz új példány létrehozása felesleges terhelést jelent.  
- **Kötegelt mentés:** Ments egyszer a módosítások után; a gyakori I/O lassítja a nagy dokumentumok generálását.  
- **Hibakezelés:** Csomagold be a teljes blokkot egy `try / catch`‑be, és logold az `Aspose.Words` kivételeket; ezek gyakran tartalmaznak hasznos sor‑számokat, ha a sablon sérült.

## Következő lépések (Related Topics)

- **How to add shadow** képekhez vagy szövegdobozokhoz (hasonló `ShadowFormat` használat).  
- **Insert rectangle shape** táblázatcellába egyedi cellastílushoz.  
- **Create rectangle in Word** a Word natív XML‑jével (azoknak, akik a nyers Open XML‑et részesítik előnyben).  
- **Set shadow color** dinamikusan felhasználói bemenet vagy téma színek alapján.

Kísérletezz különböző színekkel, elmosódási sugarakkal és eltolásokkal – például egy lágy kék fény a vállalati jelentéshez, vagy egy mély fekete árnyék a drámai szórólaphoz. A lehetőségek végtelenek, a kódbeli változtatások pedig minimálisak.

---

### Gyors összefoglaló

- **Létrehoztuk** egy word dokumentumot a semmiből.  
- **Beszúrtunk** egy téglalap alakzatot, és bekapcsoltuk az árnyékát.  
- **Beállítottuk** az árnyék színét, elmosódását és eltolásait, hogy professzionális hatást érjünk el.  
- **Elmentettük** a fájlt, készen a terjesztésre.

Most már szilárd alapod van a vizuális elemek hozzáadásához bármely Word automatizálási projekthez. Van még ötleted? Hagyj egy megjegyzést, és folytassuk a beszélgetést. Boldog kódolást!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}