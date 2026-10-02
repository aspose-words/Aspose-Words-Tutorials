---
category: general
date: 2026-02-18
description: Ismerje meg, hogyan lehet elkapni a betűtípus‑figyelmeztetéseket és észlelni
  a hiányzó betűtípusokat C#‑ban az Aspose.Words használatával. Kövesse ezt a lépésről‑lépésre
  útmutatót a hiányzó betűtípusok hatékony kezeléséhez.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: hu
og_description: Rögzítsd a betűtípus-figyelmeztetéseket C#-ban, és tanuld meg a hiányzó
  betűtípusok észlelését, kezelését, valamint a hiányzó betűtípusok listázását egy
  teljes kódrészlettel.
og_title: Betűtípus‑figyelmeztetések rögzítése C#‑ban – Teljes útmutató
tags:
- Aspose.Words
- C#
- Font Management
title: Betűtípus‑figyelmeztetések rögzítése C#‑ban – Teljes programozási útmutató
url: /hu/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus Figyelmeztetések Rögzítése C#‑ban – Teljes Programozási Útmutató

Gondolkodtál már azon, hogyan **rögzítsd a betűtípus figyelmeztetéseket**, amikor egy dokumentum olyan betűtípust hivatkozik, amely nincs telepítve a szerveren? Nem vagy egyedül. Sok vállalati alkalmazásban a hiányzó betűtípusok elrendezési hibákat okoznak, és az egyetlen megbízható módja annak, hogy észrevegyük őket, ha figyeljük a könyvtár által kibocsátott figyelmeztetéseket.  

Ebben az útmutatóban egy azonnal futtatható megoldást mutatunk be, amely nem csak **rögzíti a betűtípus figyelmeztetéseket**, hanem **felismeri a hiányzó betűtípusokat**, **kezelni tudja a hiányzó betűtípusokat**, és akár **listázza is a hiányzó betűtípusokat**, így eldöntheted, hogy helyettesíted, beágyazod vagy értesíted a felhasználót. Nem szükséges külső dokumentáció – csak másold, illeszd be és futtasd.

## Mit Tanulhatsz Meg

- Hogyan konfiguráljuk a `LoadOptions`‑t a betűtípus‑helyettesítési figyelmeztetések bekapcsolásához.  
- A pontos kód, amellyel betölthetsz egy DOCX‑et és kinyerheted az összes figyelmeztetést.  
- Miért fontos minden lépés, beleértve a teljesítménybeli szempontokat is.  
- Szélsőséges esetek kezelése, például vegyes írásrendszerű betűtípusokkal vagy egyedi betűtípus mappákkal rendelkező dokumentumok.

**Előfeltételek**: .NET 6+ (vagy .NET Framework 4.6+), egy hivatkozás a **Aspose.Words** NuGet csomagra, és az C# alapvető ismerete. Ha még sosem használtad az Aspose.Words‑ot, ne aggódj – ez az útmutató minden részletet végigvezet.

![Diagram showing capture font warnings flow](image.png){alt="capture font warnings diagram"}

## Betűtípus Figyelmeztetések Rögzítése – Miért Fontos

Amikor az Aspose.Words betölt egy dokumentumot, csendben helyettesíti a nem elérhető betűtípust egy tartalék betűtípussal. Ez a tartalék a betöltési műveletet életben tartja, de a vizuális eredmény teljesen eltolódhat. A **SubstitutionWarningLevel.All** jelző bekapcsolásával a könyvtár minden hiányzó betűtípushoz hozzáad egy `WarningInfo` bejegyzést, lehetővé téve a **hiányzó betűtípusok** felismerését, mielőtt a dokumentum megjelenik vagy mentésre kerül.

> **Pro tipp:** Ha egy kötegelt feladatban több száz fájlt dolgozol fel, a figyelmeztetések központi tárolóba naplózása órákat takaríthat meg a későbbi manuális QA‑ban.

## 1. lépés: A projekt beállítása

1. Nyisd meg a kedvenc IDE‑det (Visual Studio, Rider, VS Code).  
2. Hozz létre egy új konzolos projektet:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Add hozzá az Aspose.Words csomagot:

```bash
dotnet add package Aspose.Words
```

Ennyi—nincs szükség extra DLL‑ekre, COM interopra. A könyvtár mindent tartalmaz, ami a **hiányzó betűtípusok** kezeléséhez szükséges.

## 2. lépés: Load Options előkészítése az összes betűtípus helyettesítési figyelmeztetés rögzítéséhez

Ahhoz, hogy a motor **rögzítse a betűtípus figyelmeztetéseket**, meg kell mondanod neki, hogy minden helyettesítést rögzítsen. Az alábbi kódrészlet létrehoz egy `LoadOptions` példányt, engedélyezi a figyelmeztetési szintet, és (opcionálisan) egy mappára mutat, amely egyedi betűtípusokat tartalmaz, amelyeket esetleg használni szeretnél.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Miért fontos ez:**  
- `SubstitutionWarningLevel.All` biztosítja, hogy **minden** hiányzó betűtípus esemény rögzítésre kerüljön, nem csak az első.  
- E flag nélkül az Aspose.Words csendben helyettesíti a betűtípust, és sosem tudod, hogy probléma van-e.

## 3. lépés: A dokumentum betöltése a konfigurált beállításokkal

Most ténylegesen megnyitjuk a fájlt. Cseréld le a `DocumentWithMissingFonts.docx`‑t a tesztdokumentumod elérési útjára.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Ha a fájl olyan betűtípusokra hivatkozik, amelyek nincsenek a gépen (vagy az általad hozzáadott opcionális mappában), a `document.WarningInfoCollection` fel lesz töltve.

## 4. lépés: Betűtípus helyettesítési figyelmeztetések keresése és megjelenítése

Itt van az útmutató szíve: a `WarningInfoCollection` iterálása a **hiányzó betűtípusok** listázásához. Szűrni fogunk a `WarningType.FontSubstitution` alapján, és barátságos üzenetet írunk ki.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Várható Kimenet

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Ha a dokumentum csak telepített betűtípusokat használ, akkor a „✅ No missing fonts detected” sort fogod látni.

## 5. lépés: Haladó – Hogyan **kezeljük programozottan a hiányzó betűtípusokat**

Csak egy lista kiírása is elegendő lehet egy diagnosztikai eszközhöz, de sok termelési rendszernek automatikusan kell **kezelnie a hiányzó betűtípusokat**. Az alábbiakban két gyakori stratégia látható:

### 5.1 Helyettesítés egy ismert tartalékkal

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Egyedi betűtípus beágyazása menet közben

Ha van egy vállalati betűtípus fájlod (`MyBrand.ttf`), beágyazhatod, amikor hiányzó betűtípust észlel a rendszer:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Megjegyzés:** A betűtípusok beágyazása növelheti a kimeneti fájl méretét, ezért mérlegeld a pontosság és a sávszélesség közötti kompromisszumot.

## Gyakori Hibák és Hogyan Kerüld El Őket

| Szimbólum | Valószínű Ok | Javítás |
|-----------|--------------|--------|
| Nem jelennek meg figyelmeztetések, pedig a dokumentum hibásan néz ki | `SubstitutionWarningLevel` nincs `All`‑ra állítva | Győződj meg róla, hogy a 2. lépésben a jelző pontosan úgy van beállítva, ahogy látható |
| A figyelmeztetések ugyanazt a betűtípust többször listázzák | A dokumentum több stílusban tartalmazza a betűtípust | Távolítsd el a duplikátumokat, ha csak egyedi listára van szükség: `fontWarnings.Select(w => w.Description).Distinct()` |
| Az alkalmazás összeomlik nagy DOCX fájlok esetén | Betöltés alapértelmezett memória beállításokkal | Használd a `LoadOptions.LoadFormat`‑t vagy streameld a fájlt a memória terhelés csökkentése érdekében |

## Teljes Működő Példa (Másolás‑Beillesztés Kész)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Futtasd a programot a `dotnet run` paranccal. A konzolon meg kell jelennie a hiányzó betűtípusok listájának, ami megerősíti, hogy sikeresen **rögzítetted a betűtípus figyelmeztetéseket**.

## Összegzés

Most már egy teljes, termelés‑kész mintát rendelkezel, amely **rögzíti a betűtípus figyelmeztetéseket**, **felismeri a hiányzó betűtípusokat**, **kezelni tudja a hiányzó betűtípusokat**, és **listázza a hiányzó betűtípusokat** az Aspose.Words használatával C#‑ban. A megközelítés könnyű, csak néhány kódsort igényel, és bármely meglévő folyamatba beilleszthető – akár...

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}