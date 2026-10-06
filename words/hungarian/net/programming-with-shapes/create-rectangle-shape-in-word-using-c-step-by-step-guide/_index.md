---
category: general
date: 2026-01-03
description: Hozzon létre téglalap alakzatot a Wordben C#-vel, és adjon árnyékot az
  alakzathoz. Tanulja meg, hogyan szúrjon be alakzatot a Wordbe, hogyan adjon árnyékot
  az alakzathoz, és hogyan generáljon Word dokumentumokat programozottan.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: hu
og_description: Hozzon létre téglalap alakzatot a Wordben C#-val, és adjon árnyékot
  az alakzathoz. Kövesse ezt az útmutatót a Wordben való alakzat beszúrásához, az
  árnyékok beállításához, és a dokumentumok programozott generálásához.
og_title: Téglalap alakzat létrehozása Wordben C#-val – Teljes útmutató
tags:
- C#
- Word Automation
- Aspose.Words
title: Téglalap alakzat létrehozása Wordben C#‑val – Lépésről lépésre útmutató
url: /hu/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Word-ben C#-al – Teljes útmutató

Valaha is szükséged volt **create rectangle shape** egy Word dokumentumban, de nem tudtad, hol kezdjed? Nem vagy egyedül – sok fejlesztő ugyanebben a helyzetben van, amikor **add shadow to shape**-t szeretne a kifinomult megjelenésért. Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan **insert shape in Word**, hogyan alkalmazz egy finom árnyékot, és végül hogyan **c# generate word document** fájlokat készíts, amelyeket a felhasználóknak küldhetsz.

Mindent lefedünk a projekt beállításától az árnyék tulajdonságainak finomhangolásáig, és egy kész‑a‑futtatáshoz‑kész kódrészlettel zárjuk. Nincs felesleges részlet, csak a gyakorlati tudnivalók, amelyek elvégzik a feladatot.

## Mit fogsz megtanulni

- Hogyan **create rectangle shape** Aspose.Words (vagy Open XML) használatával C#-ban  
- A pontos tulajdonságok, amelyekre a **add shadow to shape** mélységhez szükséged van  
- Hol helyezd el az alakzatot a `DocumentBuilder` használatával  
- Hogyan mentsd a fájlt, hogy megfelelően nyíljon meg a Microsoft Wordben  
- Tippek, buktatók és változatok a valós helyzetekhez  

### Előfeltételek

- .NET 6.0 vagy újabb (a kód működik .NET Core és .NET Framework alatt is)  
- Egy NuGet csomag, amely képes Word fájlok manipulálására – a **Aspose.Words for .NET**-et fogjuk használni, mert az API-ja tömör. Ha az Open XML SDK-t részesíted előnyben, a koncepciók ugyanazok, csak az osztályok különböznek.  
- Visual Studio, VS Code vagy bármelyik kedvenc C# IDE  

> **Pro tip:** Ha szűkös a költségvetésed, az Aspose ingyenes próbaidőszakot kínál, ami tökéletes a tanuláshoz. Csak cseréld le a licenc sort egy megjegyzésre a tesztelés során.

## 1. lépés: A Word‑feldolgozó könyvtár telepítése

Először add hozzá a könyvtárat a projekthez. Nyiss egy terminált a megoldás mappájában, és futtasd:

```bash
dotnet add package Aspose.Words
```

Ha az Open XML SDK-t használod, a parancs `dotnet add package DocumentFormat.OpenXml`. A útmutató további része az Aspose.Words-ot feltételezi, de az API hívások cseréje egyszerű.

## 2. lépés: Új üres dokumentum létrehozása

Miután a könyvtár készen áll, **create rectangle shape**-t hozhatunk létre egy tiszta `Document` objektummal. Tekintsd ezt egy friss vászonnak.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

A `DocumentBuilder` magas szintű módot biztosít a tartalom beszúrására anélkül, hogy alacsony szintű csomópontfákba merülnénk.

## 3. lépés: A téglalap alakzat beszúrása

A builderrel a kezünkben, **insert shape in Word**-t hajthatunk végre. Az `InsertShape` metódus a forma típusát és méreteit (szélesség, magasság) pontban veszi.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Ebben a pontban a téglalap megjelenik a dokumentumban, de kissé laposnak tűnik. Itt jön a következő lépés.

## 4. lépés: Árnyék hozzáadása az alakzathoz

Az árnyékok mélységérzetet adnak az alakzatnak. A `Shadow` objektum lehetővé teszi a elmosódás, távolság, szög, szín és átlátszóság finomhangolását. Az alábbi teljes konfiguráció a legtöbb jelentésnél jól működik.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Miért ezek az értékek?**  
- **BlurRadius** `5.0`-val a szélek simák maradnak anélkül, hogy elmosódottak lennének.  
- **Distance** `4.0`-val az árnyék elég eltolódik ahhoz, hogy észrevehető legyen.  
- **Angle** `45` a természetes fényt a bal felső sarokból utánozza, ami gyakori UI konvenció.  
- **Transparency** `0.3` megakadályozza, hogy az árnyék elnyomja az alakzat kitöltését.  

Ha drámaibb hatást szeretnél, növeld a `BlurRadius`-t és csökkentsd a `Transparency`-t. Egy finom, szinte láthatatlan emeléshez fordítsd meg ezeket a számokat.

## 5. lépés: Dokumentum mentése

Végül írd a fájlt a lemezre. A `Save` metódus a fájlkiterjesztés alapján észleli a formátumot, így a `.docx` a modern Word formátumot adja.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Nyisd meg a `ShadowRectangle.docx`-t a Microsoft Wordben, és egy tiszta téglalapot látsz majd egy lágy árnyékkal – pontosan azt, amit akkor szerettél volna, amikor a “**how to add shape**” professzionális befejezéssel kérdezted.

![Téglalap alakzat létrehozása árnyékkal Word-ben](placeholder-image.png "Téglalap alakzat létrehozása árnyékkal Word-ben")

*Kép alt szöveg: create rectangle shape with shadow in Word*

## Teljes működő példa

Összegezve, itt van a teljes, futtatható program. Másold be egy konzolalkalmazásba, és nyomd meg a **F5**-öt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Várható eredmény

- A generált `ShadowRectangle.docx` **egy rectangle shape**-t tartalmaz, amely a kurzor pozíciójában középre van helyezve.  
- A téglalap egy **soft, 30 % transparent black shadow**-t jelenít meg, 45° szögben eltolva.  
- Nem kerül hozzá más tartalom, így a fájl könnyű és egyszerűen beágyazható nagyobb jelentésekbe.  

## Gyakori kérdések és szélhelyzetek

### Mi van, ha más alakzatra van szükségem?

Cseréld le a `ShapeType.Rectangle`-t bármely más `ShapeType` enum értékre (pl. `Ellipse`, `Triangle`). Az árnyék API ugyanúgy működik, így újra felhasználhatod a konfigurációt.

### Hogyan változtassam meg a kitöltő színt?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Hozzáadhatom az alakzatot egy adott bekezdéshez?

Igen. Mozgasd a `DocumentBuilder`-t a cél bekezdéshez a `builder.MoveToParagraph(index)` segítségével, mielőtt meghívnád az `InsertShape`-t. Ez biztosítja, hogy az alakzat pontosan ott jelenjen meg, ahol szükséged van.

### Mi a helyzet a régebbi Word formátumokkal (.doc)?

Csak cseréld le a kiterjesztést:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

Az árnyék funkció a Word 2003 és újabb verziókban támogatott, így továbbra is látható lesz a hatás.

### Open XML SDK használata Aspose helyett?

A lépések ugyanazok: hozz létre egy `WordprocessingDocument`-ot, adj hozzá egy `Drawing` elemet, állítsd be a `<a:shadow>` tulajdonságokat. Az XML részletesebb, de ugyanazok a koncepciók (méret, blur, distance, angle) érvényesek.

## Tippek a buktatók elkerüléséhez

- **Ne felejtsd el a licencet**, ha fizetős Aspose verziót használsz; különben vízjelet kapsz.  
- **Az egységek pontok**, nem pixelek. Egy tipikus képernyőpixel ≈ 0.75 pt, ezért ennek megfelelően állítsd be a méreteket.  
- **Az árnyék tulajdonságok figyelmen kívül maradnak**, ha az alakzat `WrapType`-ja `Inline`-ra van állítva. Használd a `WrapType = WrapType.Square`-t lebegő alakzatoknál, amelyek figyelembe veszik az árnyék megjelenítését.  
- **Hálózati megosztásra mentés** megfelelő jogosultságokat igényelhet; mindig először teszteld az elérési utat.  

## Összegzés

Most már tudod, hogyan **create rectangle shape** egy Word dokumentumban C# használatával, hogyan **add shadow to shape**, és hogyan **c# generate word document** fájlokat készíts, amelyek azonnal kifinomultak. Az alaplépések – a könyvtár telepítése, a `Document` példányosítása, az alakzat beszúrása, az árnyék konfigurálása és a mentés – könnyen megjegyezhetők és alkalmazhatók más alakzatokra, színekre vagy akár dinamikus adatokra is.

Mi a következő? Próbálj meg több alakzatot rétegezni, képeket beágyazni, vagy egy teljes jelentést generálni táblázatokkal és diagramokkal. Felfedezheted a feltételes formázást is – az árnyék intenzitásának adatértékek alapján történő változtatását –, hogy a dokumentumaid ne csak funkcionálisak, hanem vizuálisan is vonzóak legyenek.

Nyugodtan kísérletezz, és ha valami furcsaságba ütközöl, hagyj egy megjegyzést alább. Boldog kódolást, és legyenek a Word dokumentumaid mindig tökéletes drop shadow‑dal!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}