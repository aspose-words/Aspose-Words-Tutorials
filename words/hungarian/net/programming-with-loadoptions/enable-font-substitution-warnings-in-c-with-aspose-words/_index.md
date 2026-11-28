---
category: general
date: 2026-06-20
description: Engedélyezze a betűtípus helyettesítési figyelmeztetéseket C#-ban az
  Aspose.Words használatával. Ismerje meg, hogyan konfigurálja a LoadOptions-t, rögzítse
  a figyelmeztetéseket, és hatékonyan kezelje a hiányzó betűtípusokat.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: hu
og_description: Aspose.Words használatával engedélyezze a betűtípus-helyettesítési
  figyelmeztetéseket C#-ban. Ez az útmutató bemutatja, hogyan állítsa be a LoadOptions-t,
  olvassa a WarningInfo-t, és jelenítse meg a hiányzó betűtípusok üzeneteit.
og_title: Betűtípus-helyettesítési figyelmeztetések engedélyezése C#-ban – Teljes
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Betűtípus helyettesítési figyelmeztetések engedélyezése C#-ban az Aspose.Words
  segítségével
url: /hu/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#‑ban a betűkészlet‑helyettesítési figyelmeztetések engedélyezése az Aspose.Words segítségével

Valaha is elgondolkodtál, hogyan **engedélyezheted a betűkészlet‑helyettesítési figyelmeztetéseket**, amikor egy Word‑dokumentum olyan betűtípust hivatkozik, amely nincs telepítve a szerveren? Nem vagy egyedül. A hiányzó betűtípusok csendben tönkretehetik a generált PDF‑ek vagy képek elrendezését, és az egyetlen módja annak, hogy ezt időben észrevegyük, ha figyeljük az Aspose.Words által kibocsátott figyelmeztetéseket.

Ebben az útmutatóban egy gyakorlati példán keresztül mutatjuk be, hogyan kapcsolhatod be ezeket a figyelmeztetéseket, hogyan nyerheted ki őket a `WarningInfo` gyűjteményből, és hogyan írhatsz érthető üzeneteket a konzolra. A végére megtanulod, hogyan konfiguráld a **Aspose.Words LoadOptions**‑t, hogyan kezeld a **C# betűkészlet‑helyettesítési figyelmeztetéseket**, és hogyan tedd a dokumentum‑feldolgozó csővezetékedet hibamentessé.

Röviden kitérünk néhány széljegyre – mi történik, ha elnyomod a figyelmeztetéseket, vagy ha a konzolra írás helyett naplózni szeretnéd őket – és egy teljes, másolás‑beillesztésre kész kódrészletet adunk, amely a legújabb Aspose.Words for .NET (24.10-es verzió) verzióval működik.

## Amire szükséged lesz

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑on is működik)
- NuGet‑referencia a `Aspose.Words`‑hez (`dotnet add package Aspose.Words` paranccsal telepíthető)
- Egy Word‑fájl, amely olyan betűtípust hivatkozik, **amely nincs** telepítve (pl. `DocumentWithMissingFont.docx`)
- Egy megfelelő IDE (Visual Studio, Rider vagy VS Code)

Ennyi – nincs szükség extra szolgáltatásokra vagy zárt eszközökre. Készen állsz? Merüljünk el.

## 1. lépés: Betűkészlet‑helyettesítési figyelmeztetések engedélyezése

Az első dolog, amit meg kell tenned, hogy jelezd az Aspose.Words‑nek, hogy értesítést szeretnél kapni, amikor hiányzó betűtípust helyettesít. Ezt a `LoadOptions` objektum `FontSettings` tulajdonságán keresztül teheted meg. Alapértelmezés szerint a figyelmeztetések **ki vannak kapcsolva**, hogy az API ne legyen zajos, ezért nekünk kell bekapcsolni őket.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Miért működik:** Ha a `FontSettings` nem `null`, a könyvtár automatikusan feltölti a `Document.WarningInfo` gyűjteményt minden `WarningType.FontSubstitution` bejegyzéssel, amelyet a dokumentum betöltése közben talál. Olyan, mintha a betűkészletek „debug‑módját” kapcsolnád be.

## 2. lépés: Dokumentum betöltése a beállított opciókkal

Most, hogy a figyelmeztetési gyűjtemény aktív, töltsd be a dokumentumot a korábban előkészített `LoadOptions`‑szal. Ha a dokumentum hiányzó betűtípust tartalmaz, az Aspose.Words egy helyettesítő betűtípust használ, és egy figyelmeztetést helyez a `WarningInfo` listába.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Pro tipp:** Ha sok fájlt dolgozol fel egy ciklusban, használd ugyanazt a `LoadOptions` példányt – egyszeri létrehozása néhány ezredmásodpercet takarít meg iterációnként.

## 3. lépés: Figyelmeztetések bejárása és betűkészlet‑helyettesítési üzenetek megjelenítése

Miután a dokumentum betöltődött, a `WarningInfo` gyűjtemény tartalmazza az összes betöltés közben keletkezett figyelmeztetést. Csak a `WarningType.FontSubstitution` típusúak érdekelnek, ezért szűrjük le őket.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

A fenti kódrészlet egy olyan dokumentum esetén, amely a hiányzó „Papyrus” betűtípust hivatkozza, a következőhöz hasonló kimenetet adhat:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Ez a **betűkészlet‑helyettesítési üzenet**, amit kerestél – egyértelmű, cselekvésre ösztönző, és készen áll a naplózásra vagy egy riasztórendszerbe való továbbításra.

## Teljes működő példa

Az alábbi önálló konzolprogram mindent egy helyen mutat. Másold be egy új `.csproj`‑ba, majd indítsd el **Run**‑nal.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Várt kimenet

Ha a dokumentum olyan betűtípusokat hivatkozik, amelyek nincsenek telepítve, valami ilyesmit látsz majd:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Ha minden betűtípus jelen van a gépen, a program egyszerűen ezt írja ki:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Gyakori hibák és pro tippek

| Probléma | Miért fordul elő | Hogyan javítsuk / kerüljük el |
|----------|------------------|------------------------------|
| **Figyelmeztetések eltűnnek** | Törölted a `FontSettings`‑et, vagy olyan `LoadOptions`‑t használtál, amelyik nem tartalmazza. | Mindig hozd létre a `FontSettings`‑et, még akkor is, ha nem módosítasz semmilyen tulajdonságot. |
| **Túl sok figyelmeztetés** | A dokumentum sok egzotikus betűtípust használ. | Adj hozzá egy egyedi betűkészlet‑mappát a `FontSettings`‑hez a `SetFontsFolder` metódussal, így csökkentheted a helyettesítéseket. |
| **Teljesítménycsökkenés szoros ciklusban** | Minden iterációban újra létrehozod a `LoadOptions`‑t, ami plusz terhet jelent. | Használd ugyanazt a `LoadOptions` példányt az összes dokumentumhoz. |
| **Hiányzó konzolkimenet** | GUI‑alkalmazásban futtatod, ahol a `Console.WriteLine` figyelmen kívül marad. | Irányítsd a figyelmeztetéseket egy naplózóba (`ILogger`) vagy írd ki fájlba. |

### Figyelmeztetések kezelése egy valós szolgáltatásban

Web‑API‑ban valószínűleg nem akarod a konzolra írni őket. Ehelyett a figyelmeztetéseket strukturált naplóba küldheted:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Így megőrzöd a **dokumentum‑figyelmeztetések kezelését**, miközben a szolgáltatásod tiszta marad.

## A példa kibővítése

- **Más figyelmeztetéstípusok rögzítése** (pl. `WarningType.UnknownFileFormat`) a `if` szűrő eltávolításával.
- **Jelentés készítése** minden figyelmeztetésről JSON‑formátumban a további elemzésekhez.
- **Egy konkrét helyettesítő betűtípus kényszerítése** a `FontSettings.SubstitutionSettings.DefaultFontName` beállításával.

Ezek természetes bővítések, miután már elsajátítottad a **betűkészlet‑helyettesítési figyelmeztetések engedélyezését**.

## Összegzés

Megmutattuk, hogyan **engedélyezheted a betűkészlet‑helyettesítési figyelmeztetéseket** C#‑ban az Aspose.Words segítségével, a `LoadOptions` konfigurálásától a `WarningInfo` bejárásáig és a barátságos üzenetek kiírásáig. A fenti lépéseket követve megvédheted a dokumentum‑feldolgozó csővezetékedet a hiányzó betűtípusok által okozott csendes elrendezésváltozásoktól.

Most próbáld ki egy egyedi betűkészlet‑mappa hozzáadását, a figyelmeztetések fájlba naplózását, vagy akár egy felügyeleti irányítópultba küldését. Ugyanez a minta minden **dokumentum‑figyelmeztetés kezelési** szituációra alkalmazható, legyen szó PDF‑re konvertálásról, képek rendereléséről vagy levél‑összevonásról.

Van kérdésed a **C# betűkészlet‑helyettesítési figyelmeztetésekkel** kapcsolatban, vagy szeretnél egy okos megoldást megosztani? Írj egy megjegyzést alább – jó kódolást!


## Mi legyen a következő tanulnivalód?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépés‑ről‑lépésre magyarázatokkal, hogy segítsenek további API‑funkciók elsajátításában és alternatív megvalósítási megközelítések felfedezésében a saját projektjeidben.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}