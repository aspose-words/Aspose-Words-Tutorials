---
category: general
date: 2026-03-19
description: Hozzon létre Word-dokumentumot C#-ban az Aspose.Words segítségével, tanulja
  meg, hogyan adjon hozzá alakzatot, téglalap alakzatot, alkalmazzon árnyékot, és
  mentse a dokumentumot docx formátumban percek alatt.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: hu
og_description: Készítsen Word dokumentumot az Aspose.Words segítségével, adjon hozzá
  téglalap alakzatot, alkalmazzon külső árnyékot, és mentse a dokumentumot docx formátumban.
  Lépésről‑lépésre útmutató.
og_title: Word-dokumentum létrehozása – Téglalap alakzat és árnyék hozzáadása
tags:
- Aspose.Words
- C#
- Document Automation
title: Word-dokumentum létrehozása – Hogyan adjunk hozzá téglalap alakzatot és árnyékot
url: /hu/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása – Hogyan adjunk hozzá téglalap alakzatot és árnyékot

Valaha is szükséged volt **create word document** programozottan, és nem tudtad, hol kezdjed? Nem vagy egyedül. Sok fejlesztő ugyanazon a problémán ütközik, amikor először próbál .docx fájlt generálni, amely egyedi grafikákat tartalmaz. Ebben a bemutatóban végigvezetünk a teljes folyamaton – hogyan adjunk hozzá alakzatot, konkrétan egy **add rectangle shape**‑t, hogyan alkalmazzunk rá egy stílusos **add shadow to shape**‑t, és végül hogyan **save document as docx**.  

A végére egy kész C# kódrészletet kapsz, amelyet bármely .NET projektbe beilleszthetsz. Nincs homályos hivatkozás, csak egy teljes, futtatható példa.  

## Prerequisites

- .NET 6.0 vagy újabb (a kód .NET Framework‑ön is működik).  
- Aspose.Words for .NET telepítve (NuGet csomag `Aspose.Words`).  
- Alapvető C# szintaxis ismeret – semmi bonyolultra nincs szükség.  

Ha hiányzik a könyvtár, futtasd:

```bash
dotnet add package Aspose.Words
```

Ennyi – nincs extra SDK, nincs COM interop, csak egyetlen NuGet hivatkozás.

---

## Step 1: Create a Word Document (Primary Goal)

Az első dolog, amire szükségünk van, egy tiszta vászon. Gondolj a `Document` osztályra, mint egy friss oldalra a Microsoft Word‑ben; tartalmaz szakaszokat, bekezdéseket és mindent, amit később hozzáadsz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Miért kezdünk egy üres `Document`‑tel? Mert garantálja, hogy semmilyen rejtett formázás ne kerüljön be egy sablonból. Tapasztalatom szerint a nulláról való indulás elkerüli a rejtélyes elrendezési változásokat, amikor később alakzatokat illesztesz be.

---

## Step 2: Insert a Rectangle Shape – Adding the Visual Element

Most, hogy van egy dokumentumunk, **add rectangle shape**‑t helyezünk el az első bekezdésben. A `Shape` objektum sokoldalú; választhatod a `ShapeType.Rectangle`, `Ellipse` vagy akár egyedi rajzokat is. Íme a minimális kód:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Mi történik a háttérben?**  
- `ShapeType.Rectangle` azt mondja az Aspose‑nak, hogy egy egyszerű dobozt szeretnénk.  
- `WrapType.Inline` biztosítja, hogy a téglalap a szövegfolyammal együtt mozogjon, ami általában a várt viselkedés egy szövegszerkesztőben.  
- Az `FirstParagraph`‑hez való hozzáfűzéssel elkerüljük egy új bekezdés kézi beszúrását; az Aspose automatikusan létrehozza, ha a dokumentum ténylegesen üres.

> **Pro tip:** Ha azt szeretnéd, hogy az alakzat a szöveg *mögött* legyen, állítsd a `WrapType`‑t `WrapType.Transparent`‑ra. Ez a kis változtatás óriási vizuális különbséget eredményezhet.

---

## Step 3: Apply an Outer Shadow – Enhancing the Look

Egy lapos téglalap… nos, lapos. Egy **add shadow to shape** hozzáadása mélységet kölcsönöz anélkül, hogy extra képeket kellene használni. Az Aspose `ShadowFormat`‑ja ezt egy soros megoldássá teszi.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Miért ezek a konkrét értékek?  
- **Blur** értéke `5.0` egy finom, szárnyas szélt ad, ami a legtöbb monitoron professzionális hatást kelt.  
- **Distance** `3.0` és **Angle** `45` egy természetes fényforrást szimulál a bal‑felső sarokból, ami gyakori tervezési konvenció.  
- **Color.Gray** mind világos, mind sötét témában jól működik; ha erősebb kontrasztot szeretnél, cseréld `Color.Black`‑ra.

Ha valaha *belső* árnyékra (pl. recesszelt gomb) lenne szükséged, egyszerűen változtasd a `ShadowType.OuterShadow`‑t `ShadowType.InnerShadow`‑ra. Ugyanazok a tulajdonságok maradnak érvényben.

---

## Step 4: Save the Document as DOCX – Persisting Your Work

Minden szórakozás jó, de végül is szeretnél egy fájlt a lemezen. A **save document as docx** lépés egyszerű:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Néhány megjegyzés:  
- A `SaveFormat.Docx` enum garantálja a modern Office Open XML formátumot, amely kompatibilis a Word 2007+ verziókkal.  
- Ha a fájlt közvetlenül egy webes válaszba szeretnéd streamelni, cseréld a fájl útvonalat egy `MemoryStream`‑re, és írd ki a HTTP válaszba.

A kód futtatása után nyisd meg a `ShadowedRectangle.docx`‑t a Microsoft Word‑ben. Egy szürke téglalapot látsz majd, amelynek lágy árnyéka van, és az első bekezdésbe beágyazva – pontosan úgy, ahogy terveztük.

---

## How to Add Shape – Alternative Approaches

A fenti példa az *inline* megközelítést használja, de néha olyan alakzatra van szükség, amely a szöveg fölött lebeg. Itt jön képbe a **how to add shape** különböző körbefuttatási beállításokkal.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Itt a `WrapType`‑t `Square`‑ra állítottuk, és középre helyeztük az alakzatot az oldalon. Ez a minta hasznos fedőlapok vagy díszítő bannerek esetén. Ne feledd: a lebegő alakzatok kissé megnövelik a fájlméretet, mivel a Word további pozicionálási adatokat tárol.

---

## Expected Output & Verification

A generált fájl megnyitásakor a következőt kell látnod:

- Egyetlen bekezdés, amely egy szürke téglalapot tartalmaz.  
- A téglalap mérete körülbelül 2,8 × 1,4 hüvelyk.  
- Egy finom külső árnyék, amely a jobb‑alsó irányba van eltolva.  

Ha az alakzat *a bekezdésen kívül* jelenik meg, ellenőrizd a `WrapType`‑t. Ha az árnyék túl erősnek tűnik, csökkentsd a `Blur` értékét, vagy állítsd a `Color`‑t egy világosabb árnyalatra.

---

## Common Pitfalls & How to Avoid Them

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Shape disappears after saving | `WrapType` set to `Inline` but paragraph was removed | Ensure the paragraph exists; use `doc.FirstSection.Body.FirstParagraph` to guarantee it. |
| Shadow looks pixelated | Using a very low `Blur` value | Increase `Blur` to at least `3.0` for smooth edges. |
| File size balloons | Adding many high‑resolution images alongside shapes | Use `doc.RemoveUnusedResources()` before saving if you added images. |
| Color not showing on dark mode | Using a dark `Color` for the shape itself | Choose a contrasting color (e.g., `Color.White`) for better visibility. |

---

## Full Working Example

Below is the complete, copy‑and‑paste‑ready code that incorporates everything we’ve discussed. Feel free to run it as a console app.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Explanation of each block** is inline as comments, satisfying both SEO readers and AI assistants that love self‑contained answers.

---

## Conclusion

We’ve just **create word document** from scratch, learned **how to add shape**, specifically an **add rectangle shape**, gave it an **add shadow to shape**, and finally **save document as docx**. The steps are simple, the code is compact, and the result looks polished.  

If you’re ready to take it further, try swapping the rectangle for a custom image, experiment with different shadow colors, or generate a whole report with multiple shaped sections. The Aspose.Words API is flexible enough to handle everything from invoices to marketing brochures.

Got questions about other shape types or need help integrating this into an ASP.NET Core service? Drop a comment below, and happy coding! 

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}