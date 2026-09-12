---
category: general
date: 2026-09-11
description: Tanulja meg, hogyan hozhat létre Word-dokumentumot, adjon hozzá téglalap
  alakzatot, és állítsa be az alakzat méreteit az Aspose.Words segítségével. Lépésről
  lépésre C# útmutató a pontos alakzatmértezéshez.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: hu
lastmod: 2026-09-11
og_description: Készítsen Word-dokumentumot az Aspose.Words segítségével C#-ban. Ez
  az útmutató bemutatja, hogyan adjon hozzá téglalap alakzatot, állítsa be az alakzat
  méretét, és kezelje programozottan az alakzat dimenzióit.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Word dokumentum létrehozása alakzatokkal – Aspose.Words C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Hogyan készítsünk Word-dokumentumot alakzatokkal az Aspose.Words segítségével
  C#-ban
url: /hu/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre Word dokumentumot alakzatokkal az Aspose.Words használatával C#-ban

Ha **Word dokumentumot** kell létrehoznod, amely egyedi grafikákat tartalmaz, ezt teljesen kódból megteheted. Ez az útmutató végigvezet a Word fájl létrehozásán, egy téglalap alakzat hozzáadásán, és az alakzat minden dimenziójának vezérlésén. A végére egy újrahasználható kódrészletet kapsz, amelyet bármely .NET projektbe beilleszthetsz.

Megtanulod, hogyan **adj hozzá téglalap alakzatot**, **állítsd be az alakzat méretét**, és **állítsd be az alakzat dimenzióit** egy csoportosított konténeren belül. A példa az Aspose.Words 13.9-et használja, de a koncepciók későbbi verziókra is érvényesek. Nem szükséges előzetes tapasztalat az Aspose rajzoló API-val – elegendő az alap C# tudás.

## Előkövetelmények

- .NET 6.0 vagy újabb telepítve  
- Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`)  
- IDE, például Visual Studio 2022 (bármely C#-ot támogató szerkesztő megfelelő)  

Ezeknek az eszközöknek a rendelkezésre állása lehetővé teszi, hogy a kódot azonnal futtasd további konfiguráció nélkül.

## 1. lépés: A dokumentum és a builder inicializálása – a Word dokumentum alapjai

Az első művelet egy `Document` objektum és egy `DocumentBuilder` példányosítása. A `Document` maga a fájlt képviseli, míg a `DocumentBuilder` egy folyékony API-t biztosít a tartalom beszúrásához.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Miért fontos:**  
A dokumentum előzetes létrehozása tiszta vásznat biztosít. A builder kurzora az első bekezdésnél kezdődik, ahol később **alakzatokat hozunk létre Word-ben**.

## 2. lépés: GroupShape létrehozása több grafika tárolására

A `GroupShape` egy konténerként működik; a teljes csoportot egy egységként mozgathatod, elforgathatod vagy átméretezheted. Itt definiáljuk a konténer szélességét és magasságát pontban (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Miért fontos:**  
Az alakzatok csoportosítása egyszerűsíti az elrendezés kezelését. Ha később további alakzatokat kell hozzáadni (pl. körök vagy szövegdobozok), azok öröklik a csoport pozícióját és méretezését.

## 3. lépés: Téglalap alakzat létrehozása és dimenzióinak beállítása

Most hozzáadjuk a tényleges téglalapot. A `Shape` konstruktor a dokumentum hivatkozását és az alakzat típusát igényli. Létrehozás után kifejezetten **beállítjuk az alakzat méretét** és **az alakzat dimenzióit**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Miért fontos:**  
A szélesség, magasság, bal és felső koordináták megadása pixel‑pontos irányítást biztosít az alakzat felett. Ez elengedhetetlen, ha a dokumentumnak meg kell felelnie egy tervezési specifikációnak vagy nyomtatott űrlapnak.

## 4. lépés: A csoport összeállítása a téglalap hozzáfűzésével

A téglalap `GroupShape`-hez való hozzáfűzése gyermekcsomóponttá teszi. A csoport dokumentumba való beszúrása előtt annyi gyermeket adhatunk hozzá, amennyire szükség van.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tipp:**  
Ha második alakzatot szeretnél hozzáadni, hozd létre ugyanolyan módon, és hívd meg a `group.AppendChild(secondShape)` metódust. Minden gyermek a csoport koordináta‑rendszerét használja.

## 5. lépés: A csoportosított alakzat beszúrása a dokumentumba és mentése

Miután a csoport teljesen felépült, a jelenlegi bekezdésbe helyezzük. A builder `CurrentParagraph` tulajdonsága közvetlen hozzáférést biztosít az alatta lévő csomópontfához.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Miért fontos:**  
A csoport bekezdéshez való hozzáfűzése biztosítja, hogy az alakzat a szövegfolyammal együtt jelenjen meg. A dokumentum mentése befejezi a **Word dokumentum létrehozása** műveletet.

## Gyakori variációk és szélhelyzetek

| Szenárió | Módosítás |
|----------|------------|
| **Eltérő oldalorientáció** | Set `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` before creating the group. |
| **Több téglalap** | Create additional `Shape` objects and call `group.AppendChild(newRect)` for each. |
| **Dinamikus méret a tartalom alapján** | Compute width/height from image dimensions or text metrics, then assign to `rectangle.Width` / `rectangle.Height`. |
| **Exportálás PDF-be** | After `doc.Save`, call `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Kompatibilitás régebbi Word verziókkal** | Save using `SaveFormat.Doc` instead of `Docx` for Word 97‑2003 compatibility. |

## Teljes, futtatható példa

Az alábbiakban a teljes programot találod, amelyet másolhatsz, beilleszthetsz és futtathatsz. Tartalmazza az összes `using` direktívát, egy `Main` belépési pontot, és megjegyzéseket, amelyek minden sort magyaráznak.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Várható kimenet:**  
Amikor megnyitod a *GroupShape.docx*-t, az első oldal egy szürke keretű téglalapot mutat, amely 50 pt-re helyezkedik el a bal/felső margótól, a téglalap maga pedig 10 pt-rel van eltolva a csoporton belül. A dimenziók megegyeznek a kódban beállított értékekkel.

## Következtetés

Most már tudod, hogyan **hozz létre Word dokumentumot**, **adj hozzá téglalap alakzatot**, és pontosan **állítsd be az alakzat méretét** és **az alakzat dimenzióit** az Aspose.Words használatával. A csoportos alakzat megközelítés rugalmasan tartja az elrendezést, és készen áll a jövőbeli kiegészítésekre, például további grafikákra vagy szövegdobozokra.

Ezután fedezd fel a kapcsolódó témákat, például a **alakzatok létrehozása Word-ben** körök, nyilak vagy egyedi SVG útvonalak esetén, és tanuld meg, hogyan **állítsd be az alakzat kitöltőszínét** vagy **alkalmazz forgatást**. Kísérletezz különböző mértékegységekkel, hogy lásd, hogyan jeleníti meg a Word a pontokat a centiméterekhez képest, és integráld a kódot nagyobb dokumentum‑generálási folyamatokba.

Boldog kódolást, és nyugodtan adaptáld ezt a mintát bármely automatizált jelentés- vagy űrlapkitöltési szituációra, amellyel találkozol!

## Mit tanulj meg legközelebb?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Téglalap alakzat létrehozása Word-ben C#-al – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Üres Word dokumentum létrehozása árnyékolt téglalap alakzattal – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words alakzat árnyék tutorial – Árnyék hozzáadása Word alakzathoz C#-ban](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}