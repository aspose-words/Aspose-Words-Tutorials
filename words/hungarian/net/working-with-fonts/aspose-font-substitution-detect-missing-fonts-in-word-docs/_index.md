---
category: general
date: 2026-05-04
description: Tanulja meg, hogyan használja az Aspose betűtípus‑helyettesítést a hiányzó
  betűtípusok felismerésére Word dokumentum betöltésekor, és hogyan szerezze meg a
  hiányzó betűtípusok részleteit – lépésről‑lépésre útmutató.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: hu
og_description: Mesteri Aspose betűtípus-helyettesítés a hiányzó betűtípusok észleléséhez
  Word-dokumentum betöltésekor, valamint a hiányzó betűtípusok információinak lekéréséhez
  teljes C# kóddal.
og_title: Aspose betűtípus helyettesítés – Hiányzó betűtípusok észlelése Word dokumentumokban
tags:
- Aspose.Words
- C#
- Font Management
title: 'Aspose betűtípus helyettesítés: Hiányzó betűtípusok felderítése Word dokumentumokban'
url: /hu/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose betűtípus‑helyettesítés – Hiányzó betűtípusok észlelése Word dokumentumokban

Gondolkodtál már azon, miért néz ki egy Word dokumentum rosszul egy másik gépen? Gyakran a bűnös egy hiányzó betűtípus, és az **Aspose betűtípus‑helyettesítés** az az eszköz, amely lehetővé teszi, hogy ezeket a hiányosságokat még a vizuális katasztrófa előtt felismerd. Ebben a bemutatóban végigvezetünk, hogyan **észleld a hiányzó betűtípusokat** már a **Word dokumentum betöltésekor**, majd hogyan **szerezd meg a hiányzó betűtípusok** részleteit, hogy kijavíthasd vagy helyettesíthesd őket.

Mindent lefedünk a figyelmeztetési callback beállításától a hiányzó betűtípusok tiszta listájának lekéréséig. A végére egy kész‑C# kódrészletet kapsz, amely pontosan megmutatja, mely betűtípusok nem kerültek betöltésre, és megérted, miért fontos ez a dokumentum hitelessége szempontjából.

---

## Prerequisites – What You Need Before You Start

- **Aspose.Words for .NET** (v23.12 vagy újabb ajánlott).  
- .NET fejlesztői környezet (Visual Studio, Rider vagy a `dotnet` CLI).  
- Egy minta DOCX, amely szándékosan egy olyan betűtípust használ, amely nincs telepítve – nevezzük `DocumentWithMissingFont.docx`‑nek.  
- Alapvető C# ismeretek – semmi bonyolult, csak a konzolos alkalmazás futtatásához szükséges tudás.

Ha bármelyik pont ismeretlen, állj meg és telepítsd a NuGet csomagot:

```bash
dotnet add package Aspose.Words
```

Ennyi. Nincs szükség extra betűtípusokra vagy külső szolgáltatásokra.

---

## Step 1: Load the Word Document (and Trigger Font Checks)

Az első lépés a **Word dokumentum betöltése**. Az Aspose.Words beolvassa a fájlt, és ha nem találja a hivatkozott betűtípust, egy *FontSubstitution* figyelmeztetést helyez a sorba. Íme a betöltést végző kód:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Miért fontos:** A dokumentum korai betöltése lehetővé teszi az Aspose számára, hogy minden szövegrészt, stílust és beágyazott objektumot átvizsgáljon. Ha egy betűtípus nincs a rendszerben vagy az egyéni betűtípus‑mappában, később figyelmeztetést kapsz.

---

## Step 2: Attach a Warning Callback to Capture Substitution Events

Az Aspose.Words egy callback mechanizmust használ, hogy tájékoztasson a hiányzó betűtípusokhoz hasonló problémákról. A `doc.WarningCallback`‑hez egy `IWarningCallback` megvalósítást rendelve minden figyelmeztetést elkapunk, amint az bekövetkezik.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Pro tipp:** Több callback‑et is csatolhatsz (pl. naplózás, UI‑frissítés) egy kompozit mintával, de ebben a bemutatóban egyetlen callback elegendő a tisztaság kedvéért.

---

## Step 3: Implement the Font Substitution Warning Callback

Most definiáljuk azt az osztályt, amely ténylegesen elvégzi a munkát. A callback egy `WarningInfo` objektumot kap; szűrünk a `WarningType.FontSubstitution` típusra, és a leírást későbbre elmentjük.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Mi történik:** Amikor az Aspose hiányzó betűtípust talál, egy figyelmeztetést hoz létre, például „Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” A callback kiírja ezt a sort, és elmenti.

---

## Step 4: Process the Document (Optional) and Gather Missing Fonts

Ha csak a **hiányzó betűtípusok észlelésére** van szükséged, a betöltési lépés elegendő – a figyelmeztetések automatikusan aktiválódnak. Sok fejlesztő azonban **hiányzó betűtípus** információt szeretne lekérni valamilyen művelet (pl. mentés, konvertálás) után. Az alábbiakban egy apró műveletet kényszerítünk – PDF‑be mentést – hogy minden figyelmeztetés kibocsátásra kerüljön, majd a gyűjtött üzeneteket kiolvassuk.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Várható konzolkimenet** (példa):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Figyeld meg, hogy minden sor egyértelműen jelzi az eredeti betűtípust és az Aspose által választott helyettesítőt. Ez a **aspose betűtípus‑helyettesítés** jelentésének a lényege.

---

## Step 5: Advanced – Using Custom Font Sources to Reduce Substitutions

Néha **van** a hiányzó betűtípus, csak nem a rendszer alapértelmezett mappájában. Az Aspose.Words lehetővé teszi, hogy egy egyéni könyvtárra mutass a `FontSettings`‑en keresztül. Ennek hozzáadása drámaian csökkentheti a helyettesítési figyelmeztetések számát.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Miért érdemes:** Ha dokumentumokat osztasz meg gépek között, a szükséges betűtípusok egy ismert mappában való csomagolása biztosítja, hogy mindenhol ugyanaz a vizuális megjelenés legyen. Emellett a **hiányzó betűtípusok észlelése** rutinod pontosabb lesz, mivel az Aspose előbb ezt a mappát ellenőrzi, mielőtt visszaesik a fallback‑re.

---

## Complete Working Example

Összeállítva, itt egy teljes, másolás‑beillesztés‑kész konzolos program. Mentsd `Program.cs`‑ként, és futtasd a `dotnet run` paranccsal.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Ami meg kell jelenjen:** Ha a forrás DOCX olyan betűtípusokra hivatkozik, amelyek nincsenek telepítve, a konzol minden helyettesítési sort kiír, majd egy tömör összegzést. Ha minden betűtípus jelen van, a „No missing fonts were detected.” üzenetet kapod.

---

## Common Pitfalls & How to Avoid Them

| Probléma | Miért fordul elő | Megoldás |
|----------|------------------|----------|
| **Nem jelenik meg figyelmeztetés** | A dokumentum csak rendszer‑betűtípusokat használ, vagy már hozzáadtál egy egyéni mappát a hiányzó betűtípusokkal. | Ellenőrizd, hogy a DOCX valóban egy nem elérhető betűtípust hivatkozik. Megnyithatod Word‑ben, és egy ritka betűtípust (pl. „Papyrus”) állíthatsz be egy bekezdésnél. |
| **Duplikált üzenetek** | Ugyanaz a betűtípus több futtatásban is előfordul, így több figyelmeztetés keletkezik. | Használd a `Distinct()`‑t a lista egyedi elemeinek megtartásához, ha csak egyedi betűtípusokra van szükséged. |
| **Teljesítménycsökkenés nagy dokumentumoknál** | Minden figyelmeztetést a UI‑szálon dolgozol fel. | Tedd a betöltést háttérfeladatba, vagy használj `Parallel.ForEach`‑t az utófeldolgozáshoz. |
| **Rossz fallback betűtípus** | Az Aspose alapértelmezett fallbackje nem egyezik a márkád stílusával. | Állítsd be a `FontSettings.SubstitutionSettings.DefaultFontName`‑t egy preferált fallbackre (pl. „Calibri”). |

---

## Extending the Solution – Exporting Missing Fonts to JSON

Ha egy webszolgáltatást építesz, amelynek a kliensnek kell jelenteni a hiányzó betűtípusokat, a lista sorosítása egyszerű:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Most az API-d egy tiszta JSON payload‑ot adhat vissza, amelyet egy másik rendszer könnyedén felhasználhat.

---

## Conclusion

Ebben az útmutatóban bemutattuk a **Aspose betűtípus‑helyettesítés** teljes folyamatát: Word dokumentum betöltése, figyelmeztetési callback csatolása, minden *detect missing fonts* esemény elkapása, és végül a **hiányzó betűtípus** információk lekérése jelentés vagy javítás céljából. Az opcionális egyéni betűtárak hozzáadásával csökkentheted a helyettesítések számát, néhány extra sorral pedig JSON‑ba exportálhatod az eredményeket.

Ne feledd, a dokumentumaid vizuális integritása a betűtípusoktól függ. A bemutatott technikával soha többé nem leszel meglepve egy váratlan fallback‑tel.  

Készen állsz a következő lépésre? Próbáld meg ezt a logikát egy nagyobb dokumentum‑feldolgozó csővezetékbe integrálni, vagy fedezd fel az Aspose.Words további funkcióit, például a betűtípus‑beágyazást (`doc.FontSettings.EmbeddedFonts`). A lehetőségek végtelenek, és a felhasználóid megköszönik a kifinomult kimenetet.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}