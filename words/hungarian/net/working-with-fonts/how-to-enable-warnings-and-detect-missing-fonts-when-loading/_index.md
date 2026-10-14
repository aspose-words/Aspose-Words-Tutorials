---
category: general
date: 2026-02-21
description: Tanulja meg, hogyan engedélyezhet figyelmeztetéseket, észlelheti a hiányzó
  betűtípusokat, valamint hogyan töltheti be biztonságosan a docx fájlokat az Aspose.Words
  C#-ban. Kövesse a lépésről‑lépésre útmutatót.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: hu
og_description: Hogyan kapcsoljunk be figyelmeztetéseket, észleljük a hiányzó betűtípusokat,
  és töltsük be helyesen a docx fájlokat az Aspose.Words használatával. Teljes kódrészlet
  mellékelve.
og_title: Hogyan engedélyezzük a figyelmeztetéseket és észleljük a hiányzó betűtípusokat
  a DOCX betöltésekor
tags:
- C#
- Aspose.Words
- Document processing
title: Hogyan kapcsoljunk be figyelmeztetéseket és észleljük a hiányzó betűtípusokat
  a DOCX fájlok betöltésekor
url: /hu/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan engedélyezzük a figyelmeztetéseket és észleljük a hiányzó betűtípusokat DOCX fájlok betöltésekor

Gondolkodtál már azon, **hogyan engedélyezzük a figyelmeztetéseket** a hiányzó betűtípusok esetén, mielőtt csendben tönkretennék a dokumentum megjelenítését? Nem vagy egyedül – a legtöbb fejlesztő azt hiszi, hogy a könyvtár egyszerűen „megteszi a helyeset”, csak később derül ki, hogy egy betűtípust cserélték ki anélkül, hogy egyetlen jelzés is lett volna.  

Ebben az útmutatóban pontosan megmutatjuk, **hogyan engedélyezzük a figyelmeztetéseket**, hogyan **észleljük a hiányzó betűtípusokat**, és a helyes módot **hogyan töltsük be a docx‑et** az Aspose.Words for .NET használatával. A végére egy kész, futtatható példát kapsz, amely minden betűtípus‑csere figyelmeztetést kiír a konzolra, így soha nem kell tippelni, mi történt a fájlban.

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑on is működik)  
- Visual Studio 2022 vagy bármelyik kedvenc C# IDE‑d  
- A **Aspose.Words** NuGet csomag (`Install-Package Aspose.Words`)  
- Egy DOCX fájl, amely olyan betűtípusokat tartalmazhat, amelyek nincsenek telepítve a gépeden (ezt `input.docx`‑nek hívjuk)

> **Pro tipp:** Ha nincs tesztfájlod, egyszerűen nyiss meg egy Word dokumentumot, amely egy egyedi vállalati betűtípust használ, és mentsd el `input.docx`‑ként. Ez kiváltja a rögzíteni kívánt figyelmeztetést.

## A megoldás áttekintése

1. **Create** egy `LoadOptions` objektumot, amelyben a `FontSubstitutionWarnings` be van kapcsolva.  
2. **Load** a DOCX fájlt ezekkel a beállításokkal.  
3. **Inspect** a `WarningCallback` gyűjteményt bármilyen `FontSubstitution` bejegyzésért.  
4. **React** – naplózhatsz, megjeleníthetsz, vagy akár programozottan helyettesítheted a hiányzó betűtípust.

Az alábbiakban minden lépést részletezünk, elmagyarázzuk, *miért* fontos, és egy teljes, futtatható kódrészletet adunk.

---

## 1. lépés: Az Aspose.Words telepítése és a projekt beállítása

Mielőtt **hogyan engedélyezzük a figyelmeztetéseket**, szükségünk van arra a könyvtárra, amely valóban támogatja őket.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Vagy a Visual Studio Package Manager Console‑ban:

```powershell
Install-Package Aspose.Words
```

> **Miért ez a lépés?**  
> A csomag nélkül a `LoadOptions`, `Document` és a figyelmeztetési infrastruktúra egyszerűen nem létezik. A NuGet hivatkozás hozzáadása biztosítja, hogy a legújabb stabil verziót (ezt a írás időpontjában 24.5) használod.

---

## 2. lépés: Betöltési beállítások létrehozása, amelyek engedélyezik a betűtípus‑csere figyelmeztetéseket

A **hogyan engedélyezzük a figyelmeztetéseket** lényege a `LoadOptions` osztályban rejlik. A `FontSubstitutionWarnings` `true`‑ra állítása azt mondja a motornak, hogy minden alkalommal rögzítse, amikor hiányzó betűtípust kell helyettesíteni.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Miért engedélyezzük ezt a jelzőt?**  
> Alapértelmezés szerint az Aspose.Words csendben kicseréli a hiányzó betűtípusokat egy tartalékra (általában Arial). Ez elrendezési eltolódásokhoz, láthatatlan karakterekhez vagy márka‑szabályok megsértéséhez vezethet. A jelző bekapcsolása teljes láthatóságot biztosít.

---

## 3. lépés: A DOCX fájl betöltése a konfigurált beállításokkal

Most, hogy tudjuk, **hogyan töltsük be a docx‑et** figyelmeztetésekkel bekapcsolva, ténylegesen elvégezzük a betöltést.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Mi történik a háttérben?**  
> A DOCX elemzése során az Aspose.Words minden `<w:rFonts>` elemet ellenőriz. Ha a megadott betűtípus nincs telepítve, egy `FontSubstitution` figyelmeztetést rögzít, és egy alapértelmezett betűtípusra vált. Mivel engedélyeztük a figyelmeztetéseket, ezek a bejegyzések a `document.WarningCallback.Warnings`‑ben jelennek meg.

---

## 4. lépés: Betűtípus‑csere figyelmeztetések lekérése és megjelenítése

A `WarningCallback` tulajdonság egy `WarningInfoCollection`‑t tartalmaz. Iterálj rajta, szűrd ki a `WarningType.FontSubstitution` típusú bejegyzéseket, és írd ki az üzeneteket.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Várható kimenet** (példa):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Mit tegyünk ezekkel az üzenetekkel?**  
> Naplózhatod őket egy fájlba, megjelenítheted egy UI‑ban, vagy akár egy egyedi betűtípus‑tartalék rutin is indítható. A lényeg, hogy most már *észleled a hiányzó betűtípusokat*, ahelyett, hogy később tippelnél.

---

## 5. lépés: (Opcionális) Hiányzó betűtípusok helyettesítése egy meghatározott tartalékkal

Ha van egy vállalati betűtípus, amelyet kötelezően használni szeretnél, kezelheted a figyelmeztetéseket és helyben cserélheted őket.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Miért érdemes ezt megfontolni?**  
> Biztosítja a vizuális konzisztenciát az összes generált dokumentumban, ami a márka‑megfelelés szempontjából kritikus.

---

## Teljes, futtatható példa

Az alábbi egyetlen C# fájl, amelyet beilleszthetsz egy konzolalkalmazásba. Mindent lefed – a csomag telepítésétől a figyelmeztetések kiírásáig.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Futtasd**: `dotnet run` a projekt mappájából. Ha bármely betűtípus hiányzik, a figyelmeztetések megjelennek, és az opcionális helyettesítés a fájl mentése előtt alkalmazásra kerül.

---

## Gyakran ismételt kérdések

### Működik ez PDF konverzióval is?

Igen. Miután kezelted a figyelmeztetéseket, meghívhatod a `doc.Save("output.pdf")`‑t, és a helyettesített betűtípusok a PDF‑ben is megjelennek, ahogy a DOCX‑ben.

### Mit tegyek, ha egy adott betűtípus figyelmeztetéseit el akarom nyomni?

Szűrheted őket a ciklusban – egyszerűen hagyd ki azt a `WarningInfo`‑t, amelynek a `Message` tartalmazza a figyelmen kívül hagyandó betűtípus nevét.

### Elérhető a `FontSubstitutionWarnings` régebbi Aspose.Words verziókban?

Ez a 20.5‑ös verzióban került bevezetésre. Ha egy régebbi kiadással vagy elakadt, frissíts a NuGet‑en keresztül; az API‑változás visszafelé kompatibilis.

---

## Összegzés

Átbeszéltük, **hogyan engedélyezzük a figyelmeztetéseket**, megmutattuk, **hogyan észleljük a hiányzó betűtípusokat**, és bemutattuk a helyes módot, **hogyan töltsük be a docx‑et** az Aspose.Words használatával, miközben teljes láthatóságot biztosítunk a betűtípus‑cserékről. A `document.WarningCallback.Warnings` vizsgálatával megbízható audit nyomot kapsz – többé nem lesznek csendes helyettesítések.

Következő lépések? Próbáld meg a figyelmeztetési logikát egy naplózási keretrendszerhez, például a Serilog‑hoz csatlakoztatni, vagy építs egy UI‑t, amely kiemeli a hiányzó betűtípusokat, mielőtt a dokumentumot a felhasználóknak küldenéd. Érdemes továbbá megvizsgálni a `FontSettings` osztályt a betűtípus‑csere szabályok finomabb vezérléséhez.

Boldog kódolást, és legyenek a dokumentumaid mindig pontosan úgy megjelenítve, ahogy szeretnéd! 

![Diagram, amely a DOCX fájl betöltésétől a betűtípus‑csere figyelmeztetések rögzítéséig tartó folyamatot ábrázolja – hogyan engedélyezzük a figyelmeztetéseket az Aspose.Words‑ban](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}