---
category: general
date: 2026-04-10
description: hogyan állítsunk be árnyékot egy alakzatra C#-ban – tanulja meg, hogyan
  alkalmazzunk vetett árnyékot, módosítsuk az átlátszóságot, állítsuk be a homályt,
  és adjunk hozzá alakzati árnyékot az Aspose.Words segítségével.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: hu
og_description: hogyan állítsunk be árnyékot egy alakzatra C#-ban – ez az útmutató
  megmutatja, hogyan alkalmazzunk vetésárnyékot, módosítsuk az átlátszóságot, állítsuk
  be az elmosódást, és adjunk hozzá alakzatarcát világos kódrészletekkel.
og_title: Hogyan állítsunk be árnyékot egy alakzatra C#‑ban – Teljes útmutató
tags:
- Aspose.Words
- C#
- Document Automation
title: Hogyan állítsunk be árnyékot egy alakzatra C#‑ban – lépésről‑lépésre útmutató
url: /hu/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hogyan állítsunk be árnyékot egy alakzatra C#‑ben – Teljes útmutató

Gondolkodtál már azon, **hogyan állítsunk be árnyékot** egy alakzatra, amikor programozottan építesz egy Word dokumentumot? Nem vagy egyedül. Sok fejlesztő akad el, amikor egy finom drop shadow‑ra van szüksége egy szövegdobozhoz, logóhoz vagy kiemelő dobozhoz, és az API dokumentáció kissé hiányosnak tűnik.  

Ebben az oktatóanyagban végigvezetünk a teljes folyamaton: egy `.docx` betöltésétől, az első `Shape` lekérésén, a drop shadow alkalmazásáig, az átlátszóság finomhangolásáig, a blur‑rádiusz beállításáig, és végül a megfelelő pozicionálásig. A végére egy újrahasználható kódrészletet kapsz, amely az Aspose.Words .NET 2023 vagy újabb verzióval működik, és megérted, *miért* fontos minden egyes tulajdonság.

## Amire szükséged lesz

- **Aspose.Words for .NET** (NuGet package `Aspose.Words`) – a könyvtár, amely biztosítja a `Document`, `Shape` és `ShadowFormat` osztályokat.  
- **.NET 6+** (or .NET Framework 4.7.2) – bármelyik újabb futtatókörnyezet megfelel.  
- Egy egyszerű Word fájl (`input.docx`), amely már tartalmaz legalább egy alakzatot, például egy szövegdobozt.  
- Visual Studio, VS Code vagy a kedvenc IDE‑d.

Ennyi. Nincs szükség extra harmadik féltől származó eszközre, COM interopra, csak tiszta C#.

![how to set shadow example](image-placeholder.png){:alt="árnyék beállítása egy alakzatra Word dokumentumban"}

## Árnyék beállítása – Áttekintés

A **hogyan állítsunk be árnyékot** alapgondolata, hogy a `Shape`-hez tartozó `ShadowFormat` objektumot manipuláljuk. Tekintsd a `ShadowFormat`-ot egy mini „stíluslapnak” az árnyék számára: megmondja a renderelőnek, hogy az árnyék látható‑e, milyen színű legyen, mennyire legyen átlátszó, mennyire legyen elmosódott, és hol helyezkedjen el az alakzathoz képest.  

Az alábbi *teljes* futtatható programot láthatod. Nyugodtan másold be egy konzolos alkalmazásba, nyomd meg a **F5**‑öt, és nézd meg, ahogy az árnyék megjelenik a mentett `output.docx`‑ben.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Miért fontosak ezek a beállítások

- **Visible** – Ennek a jelzőnek a bekapcsolása nélkül a többi tulajdonság figyelmen kívül marad.  
- **Color** – Egy sötétszürke tipikus UI drop shadow‑t utánoz; bármilyen `Color`‑t beállíthatsz.  
- **Transparency** – A 0.3 *lágy* megjelenést kölcsönöz, miközben az alakzat olvasható marad.  
- **Size** – A blur‑t szabályozza; a 6 érték általában elegendő egy professzionális hatáshoz.  
- **Distance & Angle** – Együtt határozzák meg az *eltolást*; 2 pt 45°‑os szögben egy finom átlós árnyékot eredményez.

Ez a **hogyan állítsunk be árnyékot** lényege. Ezután minden részt részletezünk, hogy **drop shadow‑t alkalmazz**, **átlátszóságot változtass**, **blur‑t állíts**, és **alakzat árnyékot adj** izoláltan.

---

## Drop Shadow alkalmazása egy alakzatra

Amikor valaki azt kérdezi, “hogyan **apply drop shadow** C#‑ban?”, gyakran csak a láthatóság kapcsolót és egy színt igényli. Az alábbi kódrészlet ezeket a két sort izolálja:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** Ha régebbi Word verziókat (2003‑2007) célozol, tartsd magad a szabványos színekhez. Néhány egzotikus ARGB értéket a régi renderelő figyelmen kívül hagyhat.

---

## Az árnyék átlátszóságának módosítása

Az átlátszóság **0 és 1 közötti float** értékkel van kifejezve. A **0** érték teljesen átlátszatlan árnyékot jelent; az **1** láthatatlanná teszi. A legtöbb tervező a **0.2‑0.4** körüli értéket választja a természetes megjelenésért.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Szélső esetek

- **Negative values** – Az Aspose.Words 0‑ra korlátozza őket, de jobb, ha már a bemenetet validálod.  
- **Values > 1** – 1‑re lesz korlátozva, ezzel hatékonyan elrejtve az árnyékot.  

Ha a felhasználóknak százalékot kell választaniuk, előbb konvertáld át:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Az árnyék elmosódásának (Size) beállítása

A **Size** tulajdonság szabályozza a blur‑rádiust. A nagyobb számok puhább, szórtabb árnyékot eredményeznek. Pontban (pt) van mérve, nem pixelben.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Mikor használjunk kis vagy nagy elmosódást

- **Small blur (2‑4 pt)** – Jó UI‑stílusú kiemelésekhez, ahol éles szegélyt szeretnél.  
- **Large blur (8‑12 pt)** – Kiváló nyomtatott jelentésekhez vagy ha az alakzat messze van a háttértől.

---

## Alakzat árnyék hozzáadása – Pozicionálás és irány

A **add shape shadow** végső része az eltolás. Két tulajdonság működik együtt:

| Property | Meaning |
|----------|---------|
| **Distance** | Milyen távolságra helyezkedik el az árnyék az alakzattól (pontban). |
| **Angle**    | Az eltolás iránya (0° = jobbra, 90° = le, 180° = balra, 270° = fel). |

Példa, amely egy finom jobb‑alsó árnyékot hoz létre:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Kísérletezhetsz a szögekkel, hogy különböző fényforrások hatását szimuláld. Egy gyakori trükk, hogy a felhasználó egy legördülő menüből választhat “fényforrást”, amelyet egy szögértékre mapelünk.

---

## Teljes működő példa (minden lépés kombinálva)

Az alábbi program ugyanaz, mint korábban, de **extra kommentárokkal** van ellátva, amelyek kristálytiszta logikát adnak. Másold be a `Program.cs`‑be és futtasd; a kimeneti fájl egy szövegdobozt tartalmaz majd tökéletesen hangolt árnyékkal.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Várható eredmény:** Nyisd meg az `output.docx`‑t. Az első szövegdoboz egy sötétszürke, 30 % átlátszó árnyékot mutat, amely enyhén elmosódott (size = 6) és 2 pt‑rel 45°‑os szögben van eltolva. A hatás finom, de észrevehető – pontosan azt, amit a legtöbb UI‑tervező célul tűz ki.

---

## Gyakori kérdések és buktatók

- **“Működik ez képekkel is?”**  
  Igen. Bármely `Shape` – legyen az szövegdoboz, kép vagy auto‑shape – rendelkezik `ShadowFormat`‑tal. Csak cseréld le az alakzat lekérdezési logikát a megfelelő indexre vagy névre.

- **“Mi van, ha a dokumentumnak több alakzata van?”**  
  Iterálj a `doc.GetChildNodes(NodeType.Shape, true)`‑en, és alkalmazd ugyanazokat a beállításokat mindegyikre. Szűrhetsz `shape.Name` vagy `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}