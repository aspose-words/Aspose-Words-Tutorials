---
category: general
date: 2026-01-08
description: Hozzon létre egy üres Word-dokumentumot, és tanulja meg, hogyan adhat
  árnyékot egy téglalap alakzathoz. Illessze be az alakzatot tartalmazó Word-fájlokat,
  és adjon hozzá alakzati árnyékot C#‑ban az Aspose.Words használatával.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: hu
og_description: Hozzon létre egy üres Word-dokumentumot, és nézze meg, hogyan adhat
  árnyékot egy téglalap alakzathoz C#-ban. Teljes kód, magyarázatok és tippek.
og_title: Üres Word-dokumentum létrehozása – Árnyékolt téglalap alakzat hozzáadása
tags:
- Aspose.Words
- C#
- Document Automation
title: Üres Word-dokumentum létrehozása árnyékolt téglalap alakzattal – Lépésről‑lépésre
  útmutató
url: /hu/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása árnyékolt téglalap alakzattal – Teljes útmutató

Valaha is szükséged volt **üres Word** fájlok programozott létrehozására, majd egy szép árnyékolt téglalappal díszítésükre? Nem vagy egyedül. Sok fejlesztő akad el, amikor rájön, hogy alakzatok beszúrása és hatások alkalmazása nem olyan egyszerű, mint a szöveg írása.  

Ebben az útmutatóban végigvezetünk a teljes folyamaton – az üres `.docx` létrehozásától a **árnyék hozzáadásának** módjáig egy **rectangle shape word** objektumhoz, és végül a **shape word** tartalom beszúrásáig egy kifinomult **add shape shadow** hatással. A végére egy kész, használatra kész kódrészletet kapsz, amely a legújabb Aspose.Words for .NET‑el működik.

---

## Amire szükséged lesz

- **Aspose.Words for .NET** (v24.10 vagy újabb) – a könyvtár, amely mindent alább hajt.  
- .NET fejlesztői környezet (Visual Studio, Rider vagy a `dotnet` CLI).  
- Alapvető C# tudás – ha tudsz “Hello World”‑t írni, készen állsz.  

Nem szükséges további NuGet csomag; minden az `Aspose.Words` és a `System.Drawing` része.

---

## 1. lépés: Üres Word dokumentum létrehozása

Az első teendő egy üres `Document` objektum felpörgetése. Gondolj rá úgy, mint egy friss vászonra – akárcsak egy új Word fájl manuális megnyitására.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Miért fontos ez:*  
Egy `Document` példány képviseli az egész Word fájlt. Egy üres dokumentummal kezdve teljes irányítást kapsz minden később hozzáadott elem felett, a bekezdésektől az alakzatokig.

---

## 2. lépés: Téglalap alakzat definiálása (Rectangle Shape Word)

Most szükségünk van egy alakzatra, amivel dolgozhatunk. A téglalap a legegyszerűbb geometria, és jól használható bannerekhez, helyőrzőkhöz vagy egyszerű UI makettekhez.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Miért fontos ez:*  
A `Width` és `Height` beállítása lehetővé teszi a forma vizuális lábnyomának szabályozását. A `ShapeType.Rectangle` azt mondja az Aspose‑nak, hogy egy klasszikus dobozt jelenítsen meg – tökéletes a későbbi **add shape shadow** bemutatásához.

---

## 3. lépés: Árnyék alkalmazása az alakzatra (How to Add Shadow)

Az árnyékok mélységet adnak, így egy lapos téglalap fizikai tárgyként érződik. Az Aspose.Words egy `Shadow` tulajdonságot biztosít, ahol a színt, távolságot, elmosódást és átlátszóságot állíthatod.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Miért fontos ez:*  
Minden tulajdonság befolyásolja a vizuális jelzést:

- **Enabled** – enélkül a többi beállítás figyelmen kívül marad.  
- **Color** – válassz egy színt, amely illik a dokumentum témájához.  
- **Distance** – nagyobb értékek távolabb húzzák az árnyékot.  
- **BlurRadius** – magasabb számok lágyabb árnyékot eredményeznek.  
- **Transparency** – finomhangolja az átlátszóságot a finom hatásért.

Nyugodtan kísérletezz; drámai hatáshoz emeld a `Distance` értékét `10`‑re és állítsd a `Transparency`‑t `0.5`‑ra.

---

## 4. lépés: Alakzat beszúrása a dokumentumba (Insert Shape Word)

A téglalap készen áll, most egy helyre kell tenni. A legegyszerűbb hely a dokumentum törzsének első bekezdése.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Miért fontos ez:*  
A `FirstSection.Body.FirstParagraph` mindig jelen van egy új `Document`‑ban. Ha itt fűzöd hozzá az alakzatot, garantálod, hogy a forma a fájl tetején jelenik meg – hasznos fejléc vagy címbannerek esetén.

Ha máshová kell beszúrni az alakzatot, megtalálhatsz egy konkrét `Paragraph`‑ot vagy `Run`‑t, és használhatod az `InsertAfter` vagy `InsertBefore` metódusokat.

---

## 5. lépés: Word fájl mentése

Az utolsó lépés a memóriában lévő dokumentum lemezre írása. Válassz egy mappát, amelyhez írási jogosultságod van, és adj a fájlnak egy értelmes nevet.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Miért fontos ez:*  
A `Save` hívás egy teljesen szabványos `.docx` fájlt ír ki. Nyisd meg Microsoft Word‑ben, LibreOffice‑ban vagy bármely nézőben, és egy szürke árnyékú téglalapot látsz – pontosan azt, amit beállítottunk.

---

## Teljes működő példa

Az alábbiakban a teljes program látható, amelyet beilleszthetsz egy konzolalkalmazásba. Tartalmazza az összes `using` direktívát, a forma létrehozását, az árnyék konfigurálását, a beszúrást és a mentést.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Várható kimenet:**  
Nyisd meg a `ShadowedRectangle.docx`‑et, és egy világosszürke téglalapot látsz a lap tetején középen, egy finom, 5 pt‑es eltolású vetett árnyékkal. Nincs extra szöveg, csak a forma – pontosan úgy, ahogy a kód előállítja.

---

## Gyakori kérdések és széljegyek

### Mi van, ha más alakzatra van szükségem?

Cseréld le a `ShapeType.Rectangle`‑t bármely más `ShapeType` enum értékre (`Ellipse`, `Triangle`, `Star`, stb.). Az árnyék tulajdonságok ugyanúgy működnek.

### Hozzáadhatok több árnyékot?

Az Aspose.Words csak egy árnyékot támogat alakzatonként. Ha rétegezett hatásra van szükséged, hozz létre két átfedő alakzatot különböző árnyékbeállításokkal.

### Hogyan működik ez .NET Core‑on?

Ugyanaz az API működik .NET 6/7/8‑on. Csak győződj meg róla, hogy hivatkozol az **Aspose.Words.NETCore** csomagra (vagy a standard csomagra, amely most már platformfüggetlen).

### Támogatott még a `System.Drawing` Linuxon?

A `System.Drawing.Common` .NET 6‑tól kezdve csak Windowsra érhető el. Platformfüggetlen projektekhez használd az `Aspose.Drawing`‑t (külön NuGet) vagy maradj a `Aspose.Words` által definiált színeknél.

### Mi a helyzet a DPI skálázással?

Az alakzat méretei pontban vannak megadva (1 pt = 1/72 inch). Ha pixel‑pontos méretre van szükséged egy adott DPI‑hez, számold ki a pontokat a `pixels * 72 / dpi` képlettel.

---

## Pro tippek és buktatók

- **Pro tip:** Állítsd be a `rectangleShape.WrapType = WrapType.Inline;`‑t, ha azt szeretnéd, hogy a forma a szöveggel együtt folyjon, a lebegő helyett.  
- **Figyelj:** Ne felejtsd el engedélyezni az árnyékot (`Enabled = true`). A többi beállítás csendben figyelmen kívül marad.  
- **Teljesítmény:** Sok alakzat szigorú ciklusban való hozzáadása lassú lehet. Csoportosítsd őket egyetlen `Section`‑ban, és a végén egyszer hívd meg a `document.UpdatePageLayout()`‑t.  
- **Verzió ellenőrzés:** Az árnyék API a Aspose.Words 20.2‑ben került bevezetésre. Ha régebbi verziót használsz, frissíts a hiányzó tulajdonságok elkerülése érdekében.

---

## Összegzés

Létrehoztunk egy **üres Word** dokumentumot, építettünk egy **rectangle shape word**‑et, megtanultuk **hogyan adjunk hozzá árnyékot**, és végül **insert shape word** tartalmat egy kifinomult **add shape shadow** hatással – mindezt az Aspose.Words for .NET segítségével.  

A kódrészlet teljesen futtatható, Windows‑on és a platformfüggetlen .NET‑en egyaránt működik, és könnyen kiterjeszthető más alakzatokra, színekre vagy akár animált GIF‑ekre. Legközelebb érdemes lehet szöveget elhelyezni a téglalapon belül, gradient kitöltéseket alkalmazni, vagy egy teljes jelentést generálni több stílusos alakzattal.

Van még ötleted? Próbáld ki a szürke árnyék kicserélését kék árnyalatra, növeld a blur‑t egy álomszerű hatáshoz, vagy kombinálj több alakzatot egy egyedi logóvá. A lehetőségek végtelenek, és most már megvannak az építőelemek a megvalósításhoz.

Boldog kódolást, és legyenek a dokumentumaid mindig élesek (a megfelelő mennyiségű árnyékkal)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}