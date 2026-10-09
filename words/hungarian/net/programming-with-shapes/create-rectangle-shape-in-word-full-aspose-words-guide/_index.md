---
category: general
date: 2026-02-26
description: Hozzon létre téglalap alakzatot a Wordben az Aspose.Words segítségével,
  és tanulja meg, hogyan adjon hozzá alakzatot a Wordhöz, hogyan alkalmazzon árnyékot
  az alakzatra, valamint hogyan állítsa be az alakzat átlátszóságát percek alatt.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: hu
og_description: Hozzon létre téglalap alakzatot a Wordben az Aspose.Words segítségével.
  Tanulja meg, hogyan adjon hozzá alakzatot a Wordhöz, alkalmazzon árnyékot az alakzatra,
  és állítsa be gyorsan az alakzat átlátszóságát.
og_title: Téglalap alakzat létrehozása a Wordben – Teljes Aspose.Words útmutató
tags:
- Aspose.Words
- C#
- Word Automation
title: Téglalap alakzat létrehozása Wordben – Teljes Aspose.Words útmutató
url: /hu/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Word-ben – Teljes Aspose.Words útmutató

Valaha is szükséged volt **create rectangle shape** egy Word dokumentumban, de nem tudtad, hol kezdj? Nem vagy egyedül – sok fejlesztő szembesül ezzel a problémával jelentések vagy számlák automatizálásakor. Ebben az útmutatóban egy teljes, azonnal futtatható példán keresztül mutatjuk be, hogyan **add shape to Word**, hogyan alkalmazz finom árnyékot, és hogyan szabályozd az alakzat átlátszóságát, mindezt az Aspose.Words for .NET segítségével.

A útmutató végére egy `.docx` fájlod lesz, amely egy tiszta téglalapot tartalmaz egy kifinomult árnyékkal – tökéletes a márkaépítéshez, kiemelésekhez, vagy egyszerűen csak a dokumentumod egy kicsit professzionálisabbá tételéhez. Nincs szükség külső eszközökre, csak néhány C# sorra.

## Amire szükséged lesz

- **Aspose.Words for .NET** (a legújabb verzió 2026 elejétől). Letöltheted a NuGet‑ről (`Install-Package Aspose.Words`).
- .NET fejlesztői környezet (Visual Studio, Rider vagy VS Code a C# kiegészítővel).
- Alapvető ismeretek a C# szintaxisban – semmi különös, csak a szokásos `using` utasítások és objektum létrehozás.

Ha már mindezek megvannak, nagyszerű – merüljünk el benne.

## Téglalap alakzat létrehozása – Alaplépések

Az alábbiakban a teljes forráskód található. Másold be egy új konzolos projektbe, nyomd meg a **F5**‑öt, és a megadott mappában megjelenik a `ShadowDemo.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Miért működik ez

- **`Document`** a belépési pont; a teljes Word fájlt képviseli.
- **`Shape`** a `ShapeType.Rectangle`‑el azt mondja az Aspose‑nak, hogy egy téglalap alakú rajzobjektumot szeretnénk.
- A **`Width`** és **`Height`** beállítása meghatározott méretet ad az alakzatnak; különben egy apró helyőrző lesz.
- A **`Shadow`** objektum lehetővé teszi minden vizuális tulajdonság finomhangolását: elmosódás, távolság, irány, szín, átlátszóság és terjesztés. Ez a *apply shadow to shape* lényege.
- Végül a **`AppendChild`** beilleszti az alakzatot a dokumentum első bekezdésébe, ami a legegyszerűbb módja a *add shape to Word* műveletnek táblák vagy fejlécek kezelése nélkül.

Amikor megnyitod a `ShadowDemo.docx`‑t, egy szürke téglalapot látsz a dokumentumban, amelynek árnyéka 45°‑os szöggel lefelé‑jobbra hajlik. Az árnyék nem egy szilárd blokk; az elmosódási sugár lágyítja a széleket, és az átlátszóság természetes vetett árnyékot kölcsönöz, nem pedig erőteljes fedést.

![téglalap alakzat példa](image.png "téglalap alakzat árnyékkal Word-ben az Aspose.Words használatával")

*(A fenti kép a kódrészlet végső eredményét mutatja.)*

## Alakzat hozzáadása Word dokumentumhoz – Elhelyezési lehetőségek

A példa a **first paragraph**‑t használja, mert ez a leggyorsabb módja, hogy valamit láss a képernyőn. Valós helyzetekben lehet, hogy szeretnéd:

- Az alakzat beillesztése egy adott **section** vagy **header/footer**‑be.
- Elhelyezése egy **table cell**‑ben a táblázati adatokhoz való igazításhoz.
- Körülötte **text wrapping** opciók (pl. `WrapType.Square`) használata, hogy a környező szöveg körbefolyja a téglalapot.

Itt egy gyors változat, amely az alakzatot egy új bekezdésbe helyezi egy egyedi stílussal:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Pro tip:* Mindig **after** add the shape **after** a tulajdonságok beállítása után; különben szükség lehet a `UpdateLayout` meghívására a vizuális megjelenés frissítéséhez.

## Árnyék alkalmazása alakzatra – A megjelenés finomhangolása

Az árnyékok drámaian megváltoztathatják egy dokumentum esztétikáját. A `Shadow` osztály több tulajdonságot tesz elérhetővé:

| Property      | Mit szabályoz                                       | Tipikus értékek |
|---------------|----------------------------------------------------|----------------|
| `BlurRadius`  | Az árnyék széleinek lágyasága                      | 2.0 – 10.0      |
| `Distance`    | Milyen messze van az árnyék az alakzattól          | 1.0 – 8.0       |
| `Direction`   | Szög fokban (0 = balra, 90 = felfelé)              | 0 – 360         |
| `Color`       | Árnyék színe (bármely `System.Drawing.Color`)      | Gray, Black, Custom |
| `Transparency`| Átlátszóság (0 = teljesen átlátszatlan, 1 = láthatatlan) | 0.0 – 0.5       |
| `Spread`      | Az árnyék kiterjesztése, mielőtt a blur alkalmazásra kerül | 0.0 – 1.0       |

Ha **subtle, professional look**-ot szeretnél, tartsd a `BlurRadius`-t 4‑6 körül és a `Transparency`-t 0.2 környékén, akárcsak a fenti kódban. **Dramatic effect** esetén növeld a `Distance`-t 6-ra, állítsd a `Direction`-t 135°-ra, és csökkentsd a `Transparency`-t 0.05-re.

## Alakzat átlátszóságának és árnyék terjesztésének beállítása

Az átlátszóság nem csak az árnyékról szól; a téglalapot is részben átlátszóvá teheted:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

A félig átlátszó kitöltés és egy lágy árnyék kombinálása gyakran modern UI érzetet ad – nagyszerű dashboardokhoz vagy a jelentésekbe beágyazott design mock‑up‑okhoz.

### Figyelni érdemes a szél esetekre

1. **Older Word versions** (pre‑2007) nem támogat bizonyos árnyék tulajdonságokat. Ha `.doc` fájlokra célozol, fontold meg az árnyék egyszerűsítését (pl. `BlurRadius` 0-ra állítása).
2. **High DPI displays** előfordulhat, hogy az árnyékot kissé másként jelenítik meg. Teszteld a célkörnyezetben, ha a vizuális hűség kritikus.
3. **Overlapping shapes**—Az Aspose az árnyékokat a hozzáadás sorrendjében rendereli. Helyezd be az alakzatokat hátulról előre, hogy elkerüld a nem kívánt takarást.

## Mentés és az eredmény ellenőrzése

A `Document.Save` metódus automatikusan felismeri a kimeneti formátumot a fájl kiterjesztéséből. **`.docx`** fájl esetén az Open XML formátumot kapod, amelyet a legtöbb modern Word processzor megért. Ha **PDF** verzióra van szükséged ugyanazzal a vizuális stílussal, csak változtasd meg a kiterjesztést:

```csharp
document.Save("ShadowDemo.pdf");
```

A generált `ShadowDemo.docx` (vagy `ShadowDemo.pdf`) megnyitása egy tiszta **rectangle with shadow**-t kell mutasson, ami megerősíti, hogy sikeresen *create rectangle shape* és *apply shadow to shape* műveleteket hajtottad végre az Aspose.Words segítségével.

## Gyakran Ismételt Kérdések

**Q: Használhatok más alakzatot, például ellipszist?**  
A: Természetesen. Cseréld le a `ShapeType.Rectangle`-t `ShapeType.Ellipse`-re (vagy bármely más `ShapeType` enumra). Az árnyék tulajdonságok változatlanok maradnak.

**Q: Mi van, ha a téglalapot kattinthatóvá kell tennem?**  
A: Hozzárendelhetsz egy hiperhivatkozást az alakzathoz:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: Működik ez .NET 6+ környezetben?**  
A: Igen. Az Aspose.Words 23.11 és újabb verziók teljes mértékben támogatják a .NET 6, .NET 7 és .NET 8-at. Csak hivatkozz a megfelelő NuGet csomagra.

**Q: Hogyan változtathatom meg az árnyék színét, hogy illeszkedjen a márkámhoz?**  
A: Használj bármilyen `System.Drawing.Color`-t, amit szeretnél:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Összegzés

Mindezt lefedtük, ami szükséges a Word dokumentumban **create rectangle shape**-hez, **add shape to Word**, **apply shadow to shape**, és **set shape transparency**-hez. A teljes, futtatható kód az oldal tetején található, és a magyarázatok elegendő bizalmat adnak ahhoz, hogy bármely projektnél méreteket, színeket és árnyék paramétereket módosíts.

Készen állsz a következő lépésre? Próbálj ki kísérletezni a következőkkel:

- Több alakzat egymásra rétegezése a jelvény hatásért.
- Dinamikus méretezés a dokumentum tartalma alapján (pl. a szélesség kiszámítása egy táblázat oszlopából).
- A dokumentum exportálása PDF vagy HTML formátumba az árnyék megőrzésével.

Nyugodtan hagyj megjegyzést, ha elakadsz, vagy oszd meg saját változataidat a „téglalap árnyékkal” témában.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}