---
language: hu
url: /hungarian/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Hiányzó betűtípusok észlelése Aspose.Words dokumentumokban – Teljes C# útmutató

Gondolkodtál már azon, hogyan **észlelheted a hiányzó betűtípusokat**, amikor egy Word fájlt töltesz be az Aspose.Words segítségével? A mindennapi munkám során néhány PDF-et találtam, amelyek rosszul néztek ki, mert az eredeti dokumentum egy olyan betűtípust használt, amely nincs telepítve a gépemen. A jó hír? Az Aspose.Words pontosan megmondja, mikor helyettesít egy betűtípust, és ezt az információt egy egyszerű figyelmeztető visszahívással (warning callback) el lehet kapni.

Ebben az útmutatóban egy **teljes, futtatható példán** keresztül vezetünk, amely megmutatja, hogyan naplózhatsz minden betűtípus helyettesítést, miért fontos a visszahívás, és néhány extra trükköt a robusztus hiányzó betűtípusok észleléséhez. Felesleges részletek nélkül, csak a kód és a gondolatmenet, amire ma működésre van szükséged.

---

## Mit fogsz megtanulni

- Hogyan valósítsd meg az **Aspose.Words warning callback**-et a betűtípus helyettesítési események elkapásához.  
- Hogyan konfiguráld a **LoadOptions C#**-t, hogy a visszahívás a dokumentum betöltésekor meghívódjon.  
- Hogyan ellenőrizd, hogy a hiányzó betűtípusok észlelése valóban működött-e, és hogy néz ki a konzol kimenete.  
- Opcionális finomhangolások nagy kötegelt feldolgozáshoz vagy fej nélküli környezetekhez.  

**Előfeltételek** – Szükséged van egy naprakész Aspose.Words for .NET verzióra (a kód 23.12-vel lett tesztelve), .NET 6 vagy újabb verzióra, valamint az C# alapjaira. Ha ezek megvannak, már indulhatsz.

---

## Hiányzó betűtípusok észlelése figyelmeztető visszahívással

A megoldás lényege a `IWarningCallback` megvalósítása. Az Aspose.Words számos helyzetben kibocsát egy `WarningInfo` objektumot, de csak a `WarningType.FontSubstitution` érdekel minket. Nézzük meg, hogyan kapcsolódhatunk ehhez.

### 1. lépés: Hozz létre egy betűtípus‑figyelmeztető gyűjtőt

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Miért fontos*: A `WarningType.FontSubstitution` szűrésével elkerüljük a nem releváns figyelmeztetések (például elavult funkciók) által okozott zajt. Az `info.Description` már tartalmazza az eredeti betűtípus nevét és a használt helyettesítőt, így egyértelmű nyomkövetést biztosít.

---

## LoadOptions konfigurálása a visszahívás használatához

Most azt mondjuk az Aspose.Words-nak, hogy a fájl betöltésekor használja a gyűjtőnket.

### 2. lépés: LoadOptions beállítása

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Miért fontos*: A `LoadOptions` az egyetlen hely, ahol a visszahívást, titkosítási jelszavakat és egyéb betöltési viselkedéseket csatlakoztathatod. A `Document` konstruktorától elkülönítve a kód újrahasználható több fájl esetén is.

---

## Dokumentum betöltése és a hiányzó betűtípusok rögzítése

Miután a visszahívás be lett kötve, a következő lépés egyszerűen a dokumentum betöltése.

### 3. lépés: Töltsd be a DOCX-et (vagy bármely támogatott formátumot)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Amikor a `Document` konstruktor feldolgozza a fájlt, minden hiányzó betűtípus aktiválja a `FontWarningCollector`-t. A konzol ilyen sorokat fog megjeleníteni:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Ez a sor a konkrét bizonyíték arra, hogy a **hiányzó betűtípusok észlelése** működött.

---

## A kimenet ellenőrzése – Mit várhatsz

Futtasd a programot egy terminálból vagy a Visual Studio-ból. Ha a forrásdokumentum olyan betűtípust tartalmaz, amely nincs telepítve, legalább egy „Font substituted” sort fogsz látni. Ha a dokumentum csak telepített betűtípusokat használ, a visszahívás csendes marad, és csak a „Document loaded successfully.” üzenetet kapod.

**Tipp**: A dupla ellenőrzéshez nyisd meg a Word fájlt a Microsoft Wordben, és nézd meg a betűtípuslistát. Bármely betűtípus, amely a *Home → Font* csoport *Replace Fonts* részében megjelenik, helyettesítésre kerülhet.

---

## Haladó: Hiányzó betűtípusok észlelése tömegesen

Gyakran szükség van tucatnyi fájl átvizsgálására. Ugyanaz a minta szépen skálázható:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Mivel a `FontWarningCollector` minden meghíváskor a konzolra ír, fájlonként kapsz jelentést extra kód nélkül. Gyártási környezetben érdemes lehet fájlba vagy adatbázisba naplózni – egyszerűen cseréld le a `Console.WriteLine`-t a kedvenc naplózó eszközödre.

---

## Gyakori hibák és profi tippek

| Probléma | Miért fordul elő | Megoldás |
|----------|------------------|----------|
| **Nem jelennek meg figyelmeztetések** | A dokumentum valójában csak telepített betűtípusokat tartalmaz. | Ellenőrizd a fájl Wordben való megnyitásával vagy szándékosan egy betűtípus eltávolításával a rendszeredből. |
| **A visszahívás nem hívódik meg** | A `LoadOptions.WarningCallback` soha nem lett hozzárendelve, vagy később egy új `LoadOptions` példányt használtál. | Tarts egyetlen `LoadOptions` objektumot, és használd újra minden betöltésnél. |
| **Túl sok nem releváns figyelmeztetés** | Nem szűrtél a `WarningType.FontSubstitution` alapján. | Add hozzá a `if (info.Type == WarningType.FontSubstitution)` feltételt, ahogy a példában látható. |
| **Teljesítménycsökkenés nagy fájloknál** | A visszahívás minden figyelmeztetésnél lefut, ami nagy dokumentumoknál sok lehet. | Kapcsold ki a többi figyelmeztetést a `LoadOptions.WarningCallback`-on keresztül, vagy állítsd be a `LoadOptions.LoadFormat`-ot egy konkrét típusra, ha tudod. |

---

## Teljes működő példa (másolás‑beillesztés kész)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Várható konzol kimenet** (ha hiányzó betűtípusra bukkansz):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Ha nincs helyettesítés, csak a sikeres sor jelenik meg.

---

## Összegzés

Most már van egy **teljes, termelés‑kész módszered a hiányzó betűtípusok észlelésére** bármely, az Aspose.Words által feldolgozott dokumentumban. Az **Aspose.Words warning callback** és a **LoadOptions C#** konfigurálásával naplózhatod minden betűtípus helyettesítést, hibaelháríthatod a megjelenési problémákat, és biztosíthatod, hogy a PDF-ek megőrizzék a kívánt megjelenést.

Egyetlen fájltól egy hatalmas kötegig a minta ugyanaz marad – valósítsd meg a `IWarningCallback`-et, csatlakoztasd a `LoadOptions`-hoz, és hagyd, hogy az Aspose.Words végezze a nehéz munkát.

Készen állsz a következő lépésre? Próbáld meg kombinálni ezt **betűtípus beágyazással** vagy **helyettesítő betűtípus családokkal**, hogy automatikusan megoldja a problémát, vagy fedezd fel a **DocumentVisitor** API-t a mélyebb tartalomelemzéshez. Boldog kódolást, és legyenek a betűtípusaid mindig a várt helyen!

---

![Hiányzó betűtípusok észlelése Aspose.Words‑ben – konzol kimenet képernyőkép](https://example.com/images/detect-missing-fonts.png "hiányzó betűtípusok konzol kimenete")

{{< layout-end >}}

{{< layout-end >}}