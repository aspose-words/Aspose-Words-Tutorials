---
category: general
date: 2026-01-11
description: Engedélyezze a betűkészlet‑helyettesítési figyelmeztetéseket a hiányzó
  betűkészletek észleléséhez .NET dokumentumaiban. Ismerje meg, hogyan lehet lekérni
  a hiányzó betűkészlet nevét, és listázni a hiányzó betűkészleteket az Aspose.Words
  segítségével.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: hu
og_description: Engedélyezze a betűtípus-helyettesítési figyelmeztetéseket az Aspose.Words-ben
  a hiányzó betűtípusok észleléséhez, a hiányzó betűtípus nevének lekéréséhez, valamint
  a dokumentumokban található hiányzó betűtípusok listázásához.
og_title: Betűkészlet‑helyettesítés figyelmeztetések engedélyezése – Lépésről‑lépésre
  C# útmutató
tags:
- Aspose.Words
- C#
- Document Processing
title: Betűkészlet helyettesítési figyelmeztetések engedélyezése az Aspose.Words-ben
  – Teljes útmutató
url: /hu/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus‑helyettesítési figyelmeztetések engedélyezése – Teljes útmutató

Gondolkodtál már azon, miért néz ki egy Word‑dokumentum kissé hibásnak, miután feltöltöd egy szerverre? Valószínűleg a szerző által használt betűtípus nincs telepítve a gépeden, és az Aspose.Words csendben a legközelebbi helyettesítőre cserélte. **Engedélyezd a betűtípus‑helyettesítési figyelmeztetéseket**, és azonnal megtudod, mely betűtípusok hiányoznak, mire cserélték őket, és hogyan járhatsz el az információ alapján.

Ebben az útmutatóban egy gyakorlati, vég‑től‑végig példán keresztül mutatjuk be, hogyan **észlelheted a hiányzó betűtípusokat**, hogyan kaphatod meg a **hiányzó betűtípus nevét**, és akár **listázhatod a hiányzó betűtípusokat** jelentéshez. Felesleges szó nélkül, csak egy tiszta megoldás, amelyet ma beilleszthetsz bármely .NET projektbe.

---

## Mit fogsz megtanulni

- Hogyan konfiguráljuk a `LoadOptions`‑t, hogy az Aspose.Words részletes figyelmeztetéseket adjon ki.
- A pontos kód, amely egy dokumentum betöltéséhez és a betűtípus‑kapcsolatú figyelmeztetések felsorolásához szükséges.
- Módszerek a hiányzó betűtípus nevének és helyettesítőjének kinyerésére, majd egy rendezett jelentés kiírására.
- Tippek a szélsőséges esetek kezeléséhez, például több tucat hiányzó betűtípussal rendelkező dokumentumok vagy egyedi betűtípus‑mappák esetén.

### Előfeltételek

- .NET 6+ (a kód .NET Framework 4.7+‑tel is működik)
- Aspose.Words for .NET 23.10 vagy újabb (letöltheted a NuGet‑ből)
- Egy minta DOCX, amely egy olyan betűtípust hivatkozik, amely nincs telepítve (nevezzük `MissingFont.docx`‑nek)

Ha megvannak ezek az alapok, merüljünk el.

---

## 1. lépés: LoadOptions beállítása a betűtípus‑helyettesítési figyelmeztetések engedélyezéséhez  

Az első dolog, amit tenned kell, hogy közöld az Aspose.Words‑nek, hogy érdekelnek a hiányzó betűtípusok. Alapértelmezés szerint a könyvtár csak belsőleg naplózza a figyelmeztetéseket. A `SubstitutionWarningLevel` beállítása `Typical`‑ra (vagy `All`‑ra a legrészletesebb kimenethez) bekapcsolja a funkciót.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Miért fontos:**  
Amikor a `SubstitutionWarningLevel` be van állítva, minden alkalommal, amikor az Aspose.Words nem találja a hivatkozott betűtípust, egy `FontSubstitutionWarning` elemet ad a dokumentum `Warnings` gyűjteményéhez. Ez a gyűjtemény az egyetlen megbízható mód a **hiányzó betűtípusok észlelésére** anélkül, hogy manuálisan elemeznéd a dokumentumot.

> **Pro tipp:** Ha egy dokumentumcsomaggal dolgozol, és biztosra akarsz menni, hogy minden helyettesítést elkapj, használd a `FontSubstitutionWarningLevel.All`‑t. Kicsit zajosabb, de garantálja, hogy egy figyelmeztetés se maradjon ki.

---

## 2. lépés: Dokumentum betöltése a konfigurált beállításokkal  

Miután a figyelmeztetési rendszer készen áll, töltsd be a DOCX‑et a most előkészített `LoadOptions`‑szel. Az elérési út lehet abszolút vagy relatív; csak győződj meg róla, hogy a fájl létezik.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Mi történik a háttérben?**  
Az Aspose.Words beolvassa a dokumentum XML‑ét, feloldja minden `<w:font>` elemet, és ellenőrzi a rendszer betűtípus‑katalógusát (plusz minden egyéni mappát, amelyet a `FontSettings`‑hez adtál). Ha nem talál betűtípust, egy figyelmeztetést rögzít – pontosan azt, amire később a **hiányzó betűtípusok listázásához** szükségünk van.

---

## 3. lépés: Figyelmeztetések bejárása és a hiányzó betűtípus részleteinek kinyerése  

A dokumentum memóriában van, a `Warnings` gyűjtemény tartalmazza minden `FontSubstitutionWarning` elemet. Végig fogunk iterálni rajta, szűrni a megfelelő típusra, és egy barátságos jelentést kiírunk.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Várható kimenet** (feltételezve, hogy a forrásdokumentum a `MyCustomFont`‑ot hivatkozza, amely nincs telepítve):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Vedd észre, hogy minden bejegyzés megadja a **hiányzó betűtípus nevét** (`MyCustomFont`) és a helyettesítőt (`Arial`). Ez pontosan az információ, amire szükséged van annak eldöntéséhez, hogy beágyazd-e az eredeti betűtípust, kérd meg a szerzőt egy helyettesítőre, vagy egyszerűen elfogadod a helyettesítést.

---

## 4. lépés: Opcionális – Az adatok listába gyűjtése további feldolgozáshoz  

Ha a jelentést CSV‑be szeretnéd exportálni, egy API‑nak küldeni, vagy csak memóriában tartani későbbre, elhelyezheted a figyelmeztetéseket egy erősen típusos listában.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Most már **listáztad a hiányzó betűtípusokat** egy olyan formátumban, amelyet bármely downstream rendszer felhasználhat. Akár egy irányítópultba, akár audit naplóba töltöd, az adatok készen állnak.

---

## 5. lépés: Szélsőséges esetek és gyakori buktatók kezelése  

### Több hiányzó betűtípus egy futtatásban  

Nagy vállalati sablonok gyakran több tucat egyedi betűtípust hivatkoznak. A figyelmeztetési gyűjtemény nagy lehet, de a fent bemutatott iteráció lineárisan skálázódik, így a teljesítmény nem jelent problémát. Csak ne feledd, hogy a kimenetet olvashatóan tartsd – csoportosítás oldal vagy stílus szerint hasznos lehet, ha mélyebb elemzésre van szükség.

### Egyedi betűtípus mappák  

Ha a betűtípusokat nem szabványos könyvtárban tárolod (pl. egy megosztott hálózati meghajtón), add meg az Aspose.Words‑nek, hol keresse őket:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Ennek a *betöltés előtt* történő beállítása lehetőséget ad a könyvtárnak a betűtípusok megtalálására, ami akár teljesen is eltüntetheti a figyelmeztetéseket.

### Bizonyos figyelmeztetések elnyomása  

Néha tudod, hogy egy adott helyettesítés elfogadható (pl. egy díszítő betűtípus, amelyet nem bánod kicserélni). Ezeket később szűrheted:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Verzió kompatibilitás  

A `FontSubstitutionWarningLevel` enum stabil maradt az Aspose.Words 20.12 óta. Ha régebbi verziót használsz, frissítened kell a figyelmeztetési szint funkció eléréséhez.

---

## Teljes működő példa  

Az alábbiakban a teljes, azonnal futtatható program látható, amely tartalmazza a fenti összes lépést. Illeszd be egy új konzolprojektbe, add hozzá az Aspose.Words NuGet csomagot, és állítsd be a `docPath`‑t egy olyan dokumentumra, amely hiányzó betűtípust hivatkozik.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

A program futtatása **engedélyezi a betűtípus‑helyettesítési figyelmeztetéseket**, **észleli a hiányzó betűtípusokat**, **lekéri a hiányzó betűtípus nevét**, és **listázza a hiányzó betűtípusokat** a konzolon és egy CSV fájlban is.

---

## Összegzés  

Most már mindent lefedtünk, amire szükséged van a **betűtípus‑helyettesítési figyelmeztetések engedélyezéséhez** az Aspose.Words‑ben, az első konfigurációtól a hiányzó betűtípusok tiszta listájának kinyeréséig. A fenti lépések követésével képes leszel auditálni a dokumentumaidat, biztosítani a vizuális hűséget, és elkerülni a kellemetlen meglepetéseket a szerveren történő rendereléskor.

Ezután érdemes lehet felfedezni:

- **Hiányzó betűtípusok beágyazása** közvetlenül a kimeneti PDF‑be vagy DOCX‑be (használd a `FontSettings.EmbeddedFonts`‑t).
- **Betűtípus‑telepítés automatizálása** a build‑ügynökökön a generált jelentés alapján.
- **Integráció CI pipeline‑okkal**, hogy a build hibára álljon, ha kritikus betűtípusok hiányoznak.

Próbáld ki ezeket, és egy egyszerű figyelmeztetési rendszert teljes körű betűtípus‑kezelési munkafolyammá alakíthatsz.

Boldog kódolást, és legyen minden betűtípusod megtalálva!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}