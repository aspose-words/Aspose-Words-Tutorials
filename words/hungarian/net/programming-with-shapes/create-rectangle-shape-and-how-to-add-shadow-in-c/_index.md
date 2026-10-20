---
category: general
date: 2026-04-04
description: Hozzon létre téglalap alakzatot C#‑ban az Aspose.Words segítségével,
  és tanulja meg, hogyan adjon hozzá árnyékot, hogyan alkalmazzon elmosódást az árnyékon,
  valamint hogyan tegye átlátszóvá az árnyékot – lépésről‑lépésre útmutató.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: hu
og_description: Hozzon létre téglalap alakzatot C#-ban az Aspose.Words segítségével.
  Tanulja meg, hogyan adjon árnyékot, hogyan alkalmazzon elmosódást az árnyékon, és
  hogyan tegye átlátszóvá az árnyékot egy tömör útmutatóban.
og_title: Téglalap alak létrehozása és árnyék hozzáadása C#-ban
tags:
- Aspose.Words
- C#
- Document Automation
title: Téglalap alakzat létrehozása és árnyék hozzáadása C#‑ban
url: /hu/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása és árnyék hozzáadása C#-ban

Valaha szükséged volt **téglalap alakzat létrehozására** egy Word dokumentumban, de nem tudtad, hogyan adj hozzá egy finom vetett árnyékot? Nem vagy egyedül. Sok jelentéskészítési vagy márkázási helyzetben egy egyszerű téglalap lágy, félig átlátszó árnyékkal professzionálisabbá teheti a megjelenést anélkül, hogy sok erőfeszítést igényelne.

Ebben az útmutatóban végigvezetünk a **dokumentum létrehozásának** folyamatán az Aspose.Words használatával, majd bemutatjuk, hogyan **adjunk hozzá árnyékot**, **alkalmazzunk elmosódást az árnyékon**, és akár **az árnyékot átlátszóvá tegyük**. A végére egy azonnal futtatható C# kódrészletet kapsz, amely egy *.docx* fájlt hoz létre szépen árnyékolt téglalappal – mindezt néhány perc alatt.

## Amire szükséged lesz

- .NET 6 vagy újabb (az API a .NET Framework 4.6+ verzióval is működik)
- Aspose.Words for .NET (az ingyenes próba verzió ebben a példában is működik)
- Kódszerkesztő – Visual Studio, VS Code, Rider, vagy bármi, amit kedvelsz
- Alap C# ismeretek – semmi bonyolult, csak a képesség, hogy konzolos alkalmazást futtass

Ha ezek megvannak, egyenesen a megoldásba ugorhatunk.

## 1. lépés – Dokumentum létrehozása és a vászon inicializálása

Először is: szükséged van egy üres `Document` objektumra. Tekintsd úgy, mint egy üres papírlapra, amelyet az Aspose.Words később Word fájllá alakít.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Miért hozunk létre `Document` példányt sablon betöltése helyett? A semmiből indulás biztosítja, hogy semmilyen rejtett stílus vagy szakasz ne zavarja a téglalapunkat. Emellett a fájlméretet is minimálisra tartja – ez jó szokás, ha sok dokumentumot generálsz egy ciklusban.

## 2. lépés – Téglalap alakzat létrehozása (a fő kulcsszavunk középpontja)

Most ténylegesen **téglalap alakzatot hozunk létre**. A `Shape` osztály rugalmas; megadod a típust (Rectangle), a méretet, és hogy hogyan kell körülölelni a környező szöveget.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Vedd észre az objektum inicializáló szintaxis használatát – ez tömör, és csökkenti annak esélyét, hogy később elfelejts beállítani egy tulajdonságot. A téglalap az első bekezdésben fog elhelyezkedni, amelyet a következő lépésben adunk hozzá.

## 3. lépés – Árnyék hozzáadása és megjelenés testreszabása

Az árnyék hozzáadása nem csak egyetlen sor; több tulajdonságot kell finomhangolni. Itt jönnek képbe a másodlagos kulcsszavak **apply blur to shadow** és **make shadow transparent**.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Egy gyors megjegyzés a számokról: a `BlurRadius` értéke 5 enyhe szórást ad; növeld 10-re, ha lágyabb hatást szeretnél, vagy csökkentsd 2-re, ha élesebb szélre vágysz. A `Transparency` érték 0 (átlátszatlan) és 1 (láthatatlan) között mozog. Állítsd a márkád kontrasztigényeihez.

### Profi tipp

Ha valaha színes árnyékra van szükséged (például vállalati kék), egyszerűen cseréld le a `Color.DarkGray`-t `Color.FromArgb(80, 0, 120, 215)`-re. Az első argumentum az alfa csatorna – tartsd alacsonyan a finomság érdekében.

## 4. lépés – Alakzat beszúrása a dokumentumba

Miután a téglalap és az árnyéka készen áll, most az első bekezdésbe helyezzük a dokumentumban. Ez a lépés biztosítja, hogy az alakzat a fájl legfelső részén jelenjen meg.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Miért az első bekezdés? Ez egy biztonságos alapértelmezés, amely akkor is működik, ha a dokumentum teljesen üres. Ha van egy konkrét hely (például egy címsor után), akkor azt a csomópontot keresnéd meg, és ott szúrnád be az alakzatot.

## 5. lépés – Fájl mentése és az eredmény ellenőrzése

Végül a dokumentumot lemezre mentjük. Bármilyen útvonalat választhatsz; csak győződj meg róla, hogy a mappa létezik.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Amikor megnyitod a *ShadowRectangle.docx* fájlt a Microsoft Wordben, egy 200 × 100 pont méretű téglalapot kell látnod, amelynek sötétszürke, enyhén elmosódott, 30 % átlátszó árnyéka három ponttal jobbra és lefelé van eltolva. A hatás finom, de mélységet ad a egyébként lapos elrendezéseknek.

![téglalap alakzat létrehozása árnyékkal az Aspose.Words-ben](https://example.com/placeholder-image.png "téglalap alakzat létrehozása árnyékkal az Aspose.Words-ben")

*Kép alternatív szövege:* **téglalap alakzat létrehozása árnyékkal az Aspose.Words-ben** – a kép a végleges dokumentumot mutatja a árnyékolt téglalappal.

## Gyakori variációk és szélhelyzetek

### Az árnyék színének dinamikus módosítása

Ha az alkalmazásod támogatja a témákat, az árnyék színét egy konfigurációs fájlból is beolvashatod:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Az alakzat beágyazotttól való leválasztása

Néha azt szeretnéd, hogy a téglalap a szöveg felett lebegjen. Állítsd a `WrapType`-ot `WrapType.Square`-ra, és a `RelativeHorizontalPosition`-t `RelativeHorizontalPosition.Margin`-re a nagyobb kontroll érdekében.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Több oldal kezelése

Ha minden oldalon szükséged van egy téglalapra, iterálj a `doc.Sections`-en, és minden szakasz első bekezdéséhez fűzz hozzá egy klónozott alakzatot. Ne felejtsd el meghívni a `rect.Clone(true)`-t is, hogy az árnyék beállításait is duplikáld.

## Összefoglalás – Mit értünk el

- **Téglalap alakzat létrehozása** az Aspose.Words használatával
- **Árnyék hozzáadása** színnel, eltolással, elmosódással és átlátszósággal
- Bemutattuk a **apply blur to shadow** és a **make shadow transparent** funkciókat
- Elmentettünk egy Word fájlt, amelyet azonnal megnyithatsz

Mindez csak néhány sor kóddal valósult meg, bizonyítva, hogy a kifinomult vizuális finomítások nem feltétlenül igényelnek nehéz grafikus könyvtárakat.

## Mi a következő?

- Kísérletezz más `ShapeType`-okkal (Ellipse, Cloud, stb.) és nézd meg, hogyan viselkednek az árnyékok.
- Kombináld a téglalapot szövegdobozokkal, hogy címkézett felhívásokat (call‑outs) építs.
- Merülj el a **how to create document** sablonokban, amelyek már tartalmaznak helyőrzőket alakzatok számára, majd töltsd fel őket programozottan.

Nyugodtan finomhangold az elmosódási sugár, a szín vagy az átlátszóság értékét, amíg az árnyék tökéletesen illeszkedik a tervezési nyelvedhez. Az API toleráns, és a változások azonnal láthatóak, amikor újra futtatod a konzolos alkalmazást.

Boldog kódolást, és legyenek a dokumentumaid mindig egy kis plusz mélységgel!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}