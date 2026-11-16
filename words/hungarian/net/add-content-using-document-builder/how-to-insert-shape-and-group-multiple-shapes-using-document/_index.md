---
category: general
date: 2026-11-15
description: Tanulja meg, hogyan szúrjon be alakzatot egy Word dokumentumba, és hogyan
  csoportosítson több alakzatot az Aspose.Words DocumentBuilder segítségével. Tartalmazza
  a téglalap alakzat beszúrását és több alakzat beszúrásának példáit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: hu
lastmod: 2026-11-15
og_description: Hogyan szúrjunk be alakzatot egy Word-fájlba az Aspose.Words segítségével.
  Ez az útmutató bemutatja több alakzat csoportosítását, téglalap alakzat beszúrását,
  és a több alakzat hatékony hozzáadását.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Hogyan szúrjunk be alakzatot, és csoportosítsunk több alakzatot a DocumentBuilderrel
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Hogyan szúrjunk be alakzatot, és csoportosítsunk több alakzatot a DocumentBuilder
  használatával C#‑ban
url: /hu/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan szúrjunk be alakzatot és csoportosítsunk több alakzatot a DocumentBuilder segítségével C#-ban

Ha tudni szeretnéd, **hogyan szúrjunk be alakzatot** egy Word dokumentumba az Aspose.Words segítségével, ez az útmutató pontos lépéseket mutat. Emellett megtanulod, hogyan **csoportosíts több alakzatot**, hogy egyetlen objektumként viselkedjenek, és hogyan **szúrj be téglalap alakzatot** más grafikák mellett.

A dokumentumautomatizálás gyakran igényel több grafika – diagramok, logók, felhívások – hozzáadását, miközben rendezett marad. A tutorial végére képes leszel **több alakzat beillesztésére**, azok csoportba helyezésére, és egy tiszta, újrahasználható elrendezés mentésére.

## Előkövetelmények

* .NET 6.0 vagy újabb telepítve  
* Visual Studio 2022 (vagy bármely C# IDE)  
* Aspose.Words for .NET licenc vagy ingyenes értékelő kulcs  
* Alapvető ismeretek a C#-ról és az Aspose.Words `DocumentBuilder` osztályról  

Nem **szükséges** más harmadik féltől származó könyvtár; minden, amire szükség van, az Aspose.Words része.

## 1. lépés: Aspose.Words telepítése NuGet-en keresztül

Nyisd meg a projektet a Visual Studio-ban, és futtasd a következő parancsot a Package Manager Console-ban:

```powershell
Install-Package Aspose.Words
```

A csomag tartalmazza a `DocumentBuilder`, `Shape` és `GroupShape` osztályokat, amelyeket a tutorial során használunk.

## 2. lépés: DocumentBuilder példány létrehozása – az alap **hogyan szúrjunk be alakzatot**

Az első végrehajtható kódsor a `DocumentBuilder` létrehozása. Ez az objektum közvetlen hozzáférést biztosít a dokumentumfához, lehetővé téve, hogy az alakzatokat pontosan oda helyezd, ahová szeretnéd.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Miért fontos*: A `DocumentBuilder` egy kurzort (a „beszúrási pontot”) tart fenn. Minden későbbi `Insert...` hívás ezt a kurzort használja, ezért később áthelyezzük egy `GroupShape`-be, hogy az összes alakzat együtt maradjon.

## 3. lépés: **Téglalap alakzat beszúrása** – az első grafika, amelyet hozzáadsz

A téglalap gyakori helyőrző táblázatokhoz, képekhez vagy felhívásokhoz. Használd az `InsertShape`-t a `ShapeType.Rectangle`-el, és add meg a szélességet és magasságot pontban (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

A téglalap a jelenlegi kurzorhelyen jelenik meg. Szükség esetén később testreszabhatod a kitöltést, vonalstílust vagy a szöveget.

## 4. lépés: Egy másik alakzat beszúrása – ellipszis a vizuális változatosságért

Több mint egy alakzat hozzáadása bemutatja a **több alakzat beillesztését**. Az ellipszis a téglalap után helyezkedik el a dokumentum áramlásában.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Ekkor a dokumentum két független alakzatot tartalmaz. Ha a kurzort áthelyezed vagy szöveget adsz hozzá, az alakzatok ott maradnak, ahol be lettek szúrva.

## 5. lépés: **Több alakzat csoportosítása**, hogy egy egységként viselkedjenek

A csoportosítás elengedhetetlen, ha több grafikát kell együtt mozgatni, forgatni vagy formázni. Az alábbi kód létrehoz egy `GroupShape`-t, áthelyezi a builder kurzorát bele, majd újra beszúrja ugyanazokat az alakzatokat – ezúttal a csoport gyermekei lesznek.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Miért használjunk csoportot?

* **Egyetlen pontú transzformáció** – a teljes csoport forgatása vagy átméretezése egy hívással.  
* **Logikai szervezés** – a Word dokumentumfában a csoportosítás tükröződik, ami megkönnyíti a későbbi szerkesztéseket.  
* **Következetes elrendezés** – a csoport mozgatása megőrzi a gyermekek relatív pozícióit.

### További alakzatok hozzáadása – a **több alakzat beillesztésének** kiterjesztése a csoporton belül

Folyamatosan hívhatod az `InsertShape`-t, amíg a kurzor a `GroupShape`-ben marad. Például egy háromszög hozzáadásához:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

## 6. lépés: Dokumentum mentése és az eredmény ellenőrzése

Miután az összes alakzat el lett helyezve, mentsd a dokumentumot egy `.docx` fájlba. A fájl megnyitása a Microsoft Wordben (vagy bármely kompatibilis megjelenítőben) két különálló alakzatot, majd egy csoportosított halmazt kell, hogy mutasson, amely ugyanazt a téglalapot, ellipszist és háromszöget tartalmazza.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Várt kimenet

* **Az első két alakzat** – egy téglalap és egy ellipszis, amelyek függetlenül vannak elhelyezve az oldalon.  
* **Csoportosított blokk** – egy téglalap, egy ellipszis és egy háromszög, amelyek együtt mozognak, ha bármelyiket rákattintod a Wordben.

A csoportosítást tesztelheted, ha a csoport bármelyik alakzatát kiválasztod; a Word kiemeli az egész gyűjteményt, ezzel megerősítve, hogy a **több alakzat csoportosítása** művelet sikeres volt.

## Gyakori buktatók és profi tippek

| Probléma | Miért fordul elő | Megoldás |
|----------|------------------|----------|
| Az alakzatok a kívánt oldal kívül jelennek meg | A builder kurzort nem helyezték át a `GroupShape`-be a beszúrás előtt. | Mindig hívd meg a `builder.MoveTo(group)` **előtt**, minden olyan `InsertShape` hívás előtt, amely a csoporthoz tartozik. |
| A csoport eltűnik a mentés után | A csoportot úgy szúrták be, hogy nem lett hozzáadva a dokumentum csomópontgyűjteményéhez. | Használd a `builder.InsertNode(group)`-t közvetlenül a `GroupShape` létrehozása után. |
| Váratlan méret a dokumentum DPI-ja miatt | Az Aspose.Words pontokat használ; ha pixelekben gondolkodsz, eltérő méreteket kaphatsz. | Konvertáld a pixeleket pontokra (`points = pixels * 72 / 96`), vagy dolgozz közvetlenül pontokban. |
| Az alakzatok szándékos nélkül átfedik egymást | Nem lett explicit pozicionálás beállítva; a Word sorban helyezi el őket. | Állítsd be a `Shape.Left` és `Shape.Top` értékeket a beszúrás után a pontos elhelyezéshez. |

**Profi tipp:** A csoportosítás után lekérheted a csoport `Shapes` gyűjteményét (`group.Shapes`), hogy végigjárd, átnevezd vagy tömeges formázást alkalmazz.

## 7. lépés: A példa kiterjesztése – mi következik?

Most, hogy ismered a **alakzat beszúrásának módját**, a **téglalap alakzat beszúrását**, és a **több alakzat csoportosítását**, felfedezheted:

* **Csoportosított alakzatok animálása** – állíts be forgatási vagy tükrözési tulajdonságokat a csoporton.  
* **Stílusok alkalmazása** – használd a `Shape.FillColor`, `Shape.LineFormat` vagy `Shape.TextBox`-ot címkék hozzáadásához.  
* **Exportálás PDF-be** – ugyanaz a csoportosított elrendezés helyesen jelenik meg, ha meghívod a `doc.Save("output.pdf")`-t.  

Ezek a kiterjesztések mind ugyanazt a `DocumentBuilder` munkafolyamatot használják, így a kódod tiszta és karbantartható marad.

## Következtetés

Ez a tutorial bemutatta, hogyan **szúrjunk be alakzatot** egy Word dokumentumba az Aspose.Words segítségével, hogyan **szúrjunk be téglalap alakzatot**, és hogyan **csoportosítsunk több alakzatot**, hogy egyetlen objektumként viselkedjenek. A lépésről‑lépésre kód követésével megbízhatóan **több alakzatot szúrhatsz be**, szervezheted őket csoportokba, és programozottan professzionális dokumentumokat hozhatsz létre.

Nyugodtan kísérletezz különböző alakzat típusokkal, színekkel és csoporttranszformációkkal. Amikor készen állsz, integráld a mintát nagyobb jelentés- vagy sablonmegoldásokba, hogy automatizáld a komplex dokumentumelrendezéseket. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Alakzatok beszúrása Word dokumentumokba az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/insert-shape/)
- [Hogyan hozzunk létre és szúrjunk be ellipszis és téglalap alakzatokat egy csoportos alakzatba egy Word dokumentumban az Aspose.Words segítségével](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Hogyan csoportosítsunk alakzatokat egy Word dokumentumban az Aspose.Words használatával](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}