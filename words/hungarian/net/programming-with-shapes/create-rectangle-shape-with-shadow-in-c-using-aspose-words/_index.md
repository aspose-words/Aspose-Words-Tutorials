---
category: general
date: 2026-03-22
description: Hozzon létre téglalap alakzatot C#-ban, és adjon árnyékot az alakzathoz
  az Aspose.Words segítségével. Tanulja meg, hogyan adjon árnyékot, hogyan hozza létre
  a téglalapot, és hogyan állítsa be az árnyék tulajdonságait.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: hu
og_description: Hozzon létre téglalap alakzatot C#‑ban, és adjon árnyékot az alakzathoz
  az Aspose.Words segítségével. Lépésről lépésre útmutató, amely bemutatja, hogyan
  adjon árnyékot, hogyan hozzon létre téglalapot, és hogyan állítsa be az árnyékot.
og_title: Téglalap alak létrehozása árnyékkal C#-ban – Teljes útmutató
tags:
- Aspose.Words
- C#
- Document Automation
title: Téglalap alakzat létrehozása árnyékkal C#-ban az Aspose.Words használatával
url: /hu/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alak létrehozása árnyékkal C#‑ban az Aspose.Words segítségével

Szükséged volt már **téglalap alak** létrehozására egy Word‑dokumentumban, de nem tudtad, hogyan adj hozzá egy finom vetett árnyékot? Nem vagy egyedül — sok fejlesztő ütközik ebbe a problémába, amikor először foglalkozik dokumentum‑automatizálással. Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan **adj árnyékot az alaknak** az Aspose.Words használatával, és válaszolunk a „**hogyan adjunk árnyékot**”, „**hogyan hozzunk létre téglalapot**” és „**hogyan állítsuk be az árnyékot**” kérdésekre is.

Kezdünk egy tiszta `Document`‑dal, lerajzolunk egy téglalapot, bekapcsoljuk az árnyékot, finomhangoljuk a elmosódást, távolságot, szöget és színt, majd elmentjük a fájlt. A végére egy használatra kész `.docx` fájlt kapsz, amely egy szürke árnyalatú téglalapot mutat, mintha a lap felett lebegne. Nincs rejtély, csak egyszerű kód, amelyet bármely .NET projektbe be lehet másolni.

## Előfeltételek

Mielőtt belevágnánk, győződj meg róla, hogy a következőkkel rendelkezel:

* **Aspose.Words for .NET** (a legújabb verzió 2026‑ márciusáig). A NuGet‑ről telepítheted a `Install-Package Aspose.Words` paranccsal.
* .NET fejlesztői környezet — Visual Studio, Rider vagy akár VS Code a C# kiegészítővel is megfelelő.
* Alapvető C# ismeretek — semmi bonyolult, csak a konzol‑ vagy WinForms‑alkalmazás létrehozásához szükséges tudás.

Ennyi. Nincs extra könyvtár, nincs rejtett lépés. Készen állsz? Kezdjünk bele.

## 1. lépés: Új üres dokumentum inicializálása

A **téglalap alak** létrehozásához először egy tárolóra van szükség — egy `Document` objektumra, amely a Word‑fájlt képviseli.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

A `Document` osztály minden Aspose.Words művelet kiindulópontja. Gondolj rá úgy, mint egy üres vászonra; nélküle nem tudsz alakzatot, táblázatot vagy szöveget hozzáadni.

## 2. lépés: A téglalap létrehozása, amely az árnyékot fogja tartalmazni

Most **hogyan hozzunk létre téglalapot** a `Shape` típusú `Rectangle` példányosításával. A méretet pontban adjuk meg (1 pont ≈ 1/72 hüvelyk).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Miért 200 × 100 pont? Ez egy megfelelő méret a bemutatóhoz — elég nagy ahhoz, hogy jól látható legyen az árnyék, de nem olyan hatalmas, hogy elnyomja az oldalt. Nyugodtan módosítsd ezeket a számokat a saját elrendezésednek megfelelően.

## 3. lépés: Az árnyék effektus engedélyezése és megjelenésének beállítása

Itt jön a tutorial középpontja: **hogyan adjunk árnyékot** és **hogyan állítsuk be az árnyékot**. Az Aspose.Words minden alakzatra biztosít egy `Shadow` objektumot, amely lehetővé teszi az effektus be‑ és kikapcsolását, valamint a vizuális paraméterek finomhangolását.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** lágyítja a széleket — magasabb érték esetén az árnyék diffúzabbnak tűnik.
* **Distance** távolabb helyezi az árnyékot a téglalaptól.
* **Angle** meghatározza, honnan jön a fény; a 45° egy természetes, átlós hatást eredményez.
* **Color** bármely `System.Drawing.Color` értéket elfogad. A szürke biztonságos alapértelmezés, de választhatsz merész `Color.Black` vagy finom `Color.LightGray` árnyalatot is.

Pro tipp: Ha `Enabled = false`‑ra állítod, az összes többi árnyékbeállítás figyelmen kívül marad, ezért mindig ellenőrizd ezt a jelzőt.

## 4. lépés: Az alakzat beszúrása a dokumentum törzsébe

Miután a téglalap készen áll és az árnyék be van állítva, el kell helyezni a dokumentumban. A legegyszerűbb módja, ha az első szakasz első bekezdéséhez fűzzük hozzá.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Ha a dokumentum már tartalmaz szöveget, kereshetsz egy konkrét `Paragraph`‑t vagy akár egy `Table` cellát, és oda szúrhatod be az alakzatot. Az `AppendChild` metódus sokoldalú — bármely `Node` típusra alkalmazható.

## 5. lépés: Dokumentum mentése és az eredmény ellenőrzése

Végül a fájlt leírjuk a lemezre. Módosítsd az útvonalat a saját igényeid szerint; a mappának léteznie kell, különben kivételt kapsz.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Nyisd meg a keletkezett `ShadowedRectangle.docx` fájlt a Microsoft Word‑ben (vagy LibreOffice‑ban), és látnod kell egy szürke téglalapot egy tiszta, átlós árnyékkal, amely jobbra‑lefelé húzódik. Ha az árnyék túl halvány, növeld a `BlurRadius` vagy a `Distance` értékét, és futtasd újra a kódot — a kísérletezés a szórakozás része.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Téglalap alak létrehozása árnyékkal példa"}

### Várt kimenet

* Egyoldalas Word‑dokumentum.
* Egy 200 × 100 pont méretű szürke téglalap a lap bal‑felső sarkában.
* Egy finom szürke árnyék, 8 pixel eltolással, 45° szögben, 5 pixel elmosódással.

## Hogyan adjunk árnyékot az alaknak – mélyebb betekintés

Lehet, hogy felmerül a kérdés: *„Animálhatom az árnyékot, vagy változtathatom a felhasználói bemenet alapján?”* Bár az Aspose.Words önmagában nem támogat animációt, programozottan módosíthatod az árnyék tulajdonságait mentés előtt, így több változatot hozhatsz létre ugyanabból a dokumentumból különböző megjelenéssel. Például egy színgyűjteményen való iterálás:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Ez a rövid kódrészlet bemutatja, **hogyan állítsuk be dinamikusan az árnyékot** — remek témakör‑specifikus jelentések generálásához.

## Hogyan hozzunk létre téglalapot – alternatív alakzatok

Ha lekerekített téglalapra van szükséged, egyszerűen cseréld le a `ShapeType`‑ot:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Vagy ha tökéletes négyzetet szeretnél, állítsd a `Width`‑et egyenlőre a `Height`‑tel. Ugyanazok az árnyékbeállítások érvényesek, így már **hogyan adjunk árnyékot** minden általad választott alakzatra.

## Gyakori hibák és hibaelhárítás

| Tünet | Valószínű ok | Megoldás |
|-------|--------------|----------|
| Az árnyék nem jelenik meg | `Shadow.Enabled` `false`‑ra van állítva | `rectangleShape.Shadow.Enabled = true;` |
| Az árnyék túl éles | `BlurRadius` 0-ra van állítva | Növeld a `BlurRadius` értékét legalább 3-ra |
| `FileNotFoundException` a mentéskor | A célmappa nem létezik | Hozd létre a mappát előbb, vagy használj érvényes útvonalat |
| Az alakzat láthatatlan | Szélesség/Magasság 0 | Győződj meg róla, hogy mindkét méret > 0 |

Ezekre a problémákra való figyelés megment a klasszikus „miért nem jelenik meg az alakzat?” helyzetektől.

## Összefoglalás – mit valósítottunk meg

* **Téglalap alak** létrehozása egy új Word‑dokumentumban az Aspose.Words segítségével.  
* **Árnyék hozzáadása az alakhoz** a `Shadow.Enabled` kapcsoló beállításával és a blur, distance, angle, color finomhangolásával.  
* Bemutattuk, **hogyan adjunk árnyékot**, **hogyan hozzunk létre téglalapot**, és **hogyan állítsuk be az árnyékot** egy tiszta, újrahasználható kódrészletben.  
* Teljes, futtatható példát adtunk, amelyet bármely C#‑projektbe beilleszthetsz.

## Mi a következő lépés?

Miután elsajátítottad az alapokat, érdemes tovább kutatni:

* **Hogyan adjunk árnyékot képekhez** — ugyanaz a `Shadow` API működik a `ShapeType.Image` esetén.
* **Több alakzat kombinálása** — hozz létre folyamatábrákat vagy infografikákat közvetlenül Word‑ben.
* **Exportálás PDF‑be** — a `document.Save("output.pdf")` hívás után már árnyékokkal ellátott változatot kapsz nyomtatásra.

Nyugodtan kísérletezz különböző színekkel, szögekkel vagy akár gradient kitöltésekkel. Az API elég rugalmas ahhoz, hogy professzionális megjelenésű dokumentumokat készíts anélkül, hogy manuálisan megnyitnád a Word‑öt.

---

Boldog kódolást! Ha bármilyen akadályba ütközöl, írj egy megjegyzést alul, vagy nézd meg az Aspose.Words fórumait — a közösség gyorsan segít.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}