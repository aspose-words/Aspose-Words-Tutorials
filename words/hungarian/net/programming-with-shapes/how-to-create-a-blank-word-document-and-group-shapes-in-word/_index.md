---
category: general
date: 2026-10-20
description: Ismerje meg, hogyan hozhat létre egy üres Word-dokumentumot, csoportosíthat
  alakzatokat a Wordben, beállíthatja az alakzat kitöltőszínét, és használhatja az
  inline körbefuttatási típust egy teljes C# példával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: hu
lastmod: 2026-10-20
og_description: Hozzon létre egy üres Word-dokumentumot, csoportosítsa a formákat
  a Wordben, és állítsa be a forma kitöltőszínét beágyazott körbefuttatási típussal
  az Aspose.Words és C# használatával. Kövesse a teljes útmutatót.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Üres Word-dokumentum létrehozása és alakzatok csoportosítása a Wordben –
  lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Üres Word-dokumentum létrehozása és alakzatok csoportosítása Wordben az Aspose.Words
  használatával
url: /hu/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre egy üres Word-dokumentumot és csoportosítsunk alakzatokat a Wordben

Ha **üres Word-dokumentumot** kell létrehoznod, amely több alakzatot tartalmaz, amelyek egy egységként viselkednek, ez az útmutató pontosan megmutatja, hogyan. Meg fogod látni, hogyan **csoportosíthatók alakzatok a Wordben**, hogyan állítható be egy alakzat kitöltőszíne, és hogyan alkalmazható a **wrap type inline** – mindezt egy tömör, futtatható C# programmal.

Az útmutató minden kódsort végigvezet, elmagyarázza, miért fontos az egyes lépések, és kiemeli a gyakori buktatókat. A végére egy .docx fájlod lesz, amely egy téglalapot és egy szövegdobozt jelenít meg csoportosítva, készen állva a további automatizálásra.

## Mit fogsz megtanulni

* Hogyan inicializálj egy üres Word-fájlt az Aspose.Words segítségével.
* A helyes módja egy **GroupShape** létrehozásának és gyermekalakzatok hozzáadásának.
* Technikák a **set shape fill color** beállításához és a pozicionálás vezérléséhez.
* **wrap type inline** használata, hogy a csoport egyetlen inline objektumként viselkedjen.
* Hogyan mentsd el és ellenőrizd az eredményt.

Az Aspose.Words használatában nincs szükség előzetes tapasztalatra, de kényelmesen kell tudnod a C# alap szintaxisát, és telepítve kell legyen a Visual Studio (vagy egy másik IDE).

## Előfeltételek

| Követelmény | Indoklás |
|-------------|----------|
| .NET 6.0 vagy újabb | Biztosítja a futtatókörnyezetet a C# projekthez. |
| Aspose.Words for .NET (legújabb verzió) | `Document`, `DocumentBuilder` és a példában használt shape osztályokat biztosítja. |
| Írható mappa útvonal | A `doc.Save` hívásnak érvényes könyvtárra van szüksége a kimeneti fájl írásához. |
| Alap C# ismeretek | Lehetővé teszi a kód követését és módosítását a saját forgatókönyveidhez. |

Install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## 1. lépés: Üres Word-dokumentum létrehozása

Az első művelet a **üres Word-dokumentum** létrehozása. Az Aspose.Words `Document` osztálya egy memóriában lévő Word-fájlt képvisel, a `DocumentBuilder` pedig kényelmes API-t biztosít a szerkesztéshez.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Miért fontos*: Egy tiszta dokumentummal kezdve garantált, hogy a hozzáadott csoportos alakzat lesz az egyetlen tartalom, ami egyszerűvé teszi az ellenőrzést.

## 2. lépés: Csoportos alakzat definiálása wrap type inline beállítással

A **GroupShape** egy tárolóként működik más alakzatok számára. A `WrapType` `Inline` értékre állítása biztosítja, hogy a csoport egyetlen inline objektumként viselkedjen a bekezdés folyamatában.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Miért fontos*: A **wrap type inline** használata megakadályozza, hogy a csoport elszabaduljon a környező szövegtől, ami elengedhetetlen, ha a csoportot egységként szeretnéd mozgatni.

## 3. lépés: Téglalap hozzáadása és alakzat kitöltőszín beállítása

Egy téglalap gyakori vizuális elem. A `Shape` konstruktor egy `ShapeType`-ot vesz fel; ezután megadjuk a méreteket és a kitöltőszínt.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Miért fontos*: A `FillColor` tulajdonság a **set shape fill color** gyakorlati bemutatása, amely a téglalapnak világoskék hátteret ad, kiemelkedően a végső dokumentumban.

## 4. lépés: Szövegdoboz hozzáadása – hogyan csoportosítsunk alakzatokat hatékonyan

Egy szövegdoboz szerkeszthető szöveget biztosít a csoporton belül. A csoport koordináta-rendszeréhez viszonyítva helyezd el a `Top` tulajdonság módosításával.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Miért fontos*: Ez a lépés megválaszolja a **how to group shapes** kérdést – minden gyermek alakzatot ugyanahhoz a `GroupShape` példányhoz adva. A `Top` eltolás biztosítja, hogy a szövegdoboz a téglalap alatt jelenjen meg, demonstrálva a pontos elrendezésvezérlést.

## 5. lépés: A kész csoportos alakzat beillesztése a dokumentumba

Miután a csoport mindkét gyermek alakzatot tartalmazza, illeszd be a jelenlegi builder pozícióba.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Miért fontos*: A csoport egyetlen csomópontként való beillesztése garantálja, hogy a Word a téglalapot és a szövegdobozt egy logikai objektumként kezelje, megőrizve relatív pozícióikat a szerkesztés során.

## 6. lépés: Dokumentum mentése és az eredmény ellenőrzése

Végül írd a dokumentumot a lemezre. Cseréld le a `YOUR_DIRECTORY`-t egy valós útvonalra a gépeden.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Amikor megnyitod a `GroupShape.docx` fájlt a Microsoft Wordben, egy világoskék téglalapot kell látnod egy „Grouped text” feliratú szövegdobozzal, amely közvetlenül alatta helyezkedik el. Bármelyik alakzat kiválasztása az egész csoportot kijelöli, megerősítve, hogy a **group shapes in Word** a kívánt módon működik.

### Várt eredmény

* Egy .docx fájl, amely egyetlen bekezdést tartalmaz.
* A bekezdésen belül egy inline csoport, amely egyetlen összetett objektumnak tűnik.
* A téglalap világoskék kitöltéssel rendelkezik, a szövegdoboz pedig a „Grouped text” feliratot jeleníti meg.

![A generált Word-dokumentum képernyőképe](grouped_shapes.png){.center width=600 alt="Egy üres Word-dokumentum képernyőképe, amelyben csoportosított téglalap és szövegdoboz van, az Aspose.Words segítségével létrehozva"}

## Gyakori kérdések és szélsőséges esetek kezelése

### Mi van, ha a csoportnak lebegőnek kell lennie az inline helyett?

Cseréld le a `WrapType.Inline`-t `WrapType.TopBottom`-ra (vagy bármely más `WrapType` enum értékre). A lebegő csoportok függetlenül helyezhetők el a bekezdés folyamatától, de elveszítik az automatikus inline igazítást.

### Hozzáadhatok további alakzatokat, például köröket vagy képeket?

Igen. Hozz létre további `Shape` objektumokat `ShapeType.Ellipse` vagy `ShapeType.Image` segítségével, állítsd be a tulajdonságaikat, és hívd a `group.AppendChild(newShape)`-t. A csoport automatikusan kibővül, hogy befogadja az új határokat, ha ennek megfelelően frissíted a `group.Bounds`-t.

### Hogyan változtathatom meg a csoport teljes méretét a gyermekek hozzáadása után?

Állítsd be a `group.Bounds`-t, miután az összes gyermek hozzá lett adva, vagy programozottan számold ki a gyermekek határainak egyesítését. Ez biztosítja, hogy a csoport találat‑teszt területe megegyezzen a vizuális tartalommal.

### Mi van, ha a kimeneti mappa nem létezik?

Aspose.Words `DirectoryNotFoundException`-t dob. Hozd létre a könyvtárat előbb:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Működik ez .NET Framework alatt a .NET Core helyett?

Az összes használt API (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) elérhető az Aspose.Words .NET Framework változatában is, így ugyanaz a kód változtatás nélkül működik.

## Profi tippek

* **Teljesítmény tipp** – Használj egyetlen `DocumentBuilder` példányt sok csoport beillesztésekor; minden csoporthoz új builder létrehozása plusz terhet jelent.
* **Vizuális konzisztencia** – Állítsd be a `rectangle.StrokeColor`-t, hogy megegyezzen a `FillColor`-ral a zökkenőmentes megjelenésért, vagy állítsd `rectangle.LineWidth = 0`-ra a keret elrejtéséhez.
* **Hibakeresés** – Hívd meg a `doc.UpdatePageLayout()`-ot a mentés előtt, ha sok alakzatot módosítasz; ez arra kényszeríti a Word-öt, hogy újraszámolja az elrendezést, és megelőzheti a váratlan vágásokat.

## Következtetés

Most már tudod, hogyan **hozz létre egy üres Word-dokumentumot**, **csoportosíts alakzatokat a Wordben**, **állíts be alakzat kitöltőszínt**, és alkalmazd a **wrap type inline**-t az Aspose.Words for .NET segítségével. A teljes példa bemutatja a szabványos megközelítést összetett grafikák építéséhez, amelyek egyetlen objektumként viselkednek a Wordben.

Innen tovább felfedezheted:

* További alakzatok hozzáadása, például képek vagy diagramok.
* Különböző `WrapType` értékek kipróbálása lebegő csoportokhoz.
* Csoportos diagramok kötegelt generálásának automatizálása több dokumentumban.

Nyugodtan adaptáld a kódot a saját automatizálási forgatókönyveidhez, és oszd meg az eredményeidet a megjegyzésekben!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Csoportos alakzat létrehozása Word-dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Üres Word-dokumentum létrehozása Aspose.Words segítségével – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Hogyan mentsünk PDF-et Wordből inline alakzatokkal – Teljes útmutató](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}