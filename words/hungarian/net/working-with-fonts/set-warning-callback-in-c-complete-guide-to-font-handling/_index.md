---
category: general
date: 2026-02-10
description: Állítsa be a figyelmeztetési visszahívást a betűtípus‑változások nyomon
  követéséhez, miközben az alapértelmezett betűtípust konfigurálja és az alapértelmezett
  importálási betűtípust állítja be az Aspose.Words-ben. Ismerje meg a teljes lépésről‑lépésre
  megoldást.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: hu
og_description: Állítsa be a figyelmeztetési visszahívást a betűtípusváltozások nyomon
  követéséhez az alapértelmezett betűtípus konfigurálása és az alapértelmezett import
  betűtípus beállítása közben. Kövesse a teljes Aspose.Words oktatóanyagot.
og_title: Figyelmeztető visszahívás beállítása C#‑ban – Teljes útmutató
tags:
- Aspose.Words
- C#
- Document Import
title: Figyelmeztető visszahívás beállítása C#-ban – A betűkészlet-kezelés teljes
  útmutatója
url: /hu/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Figyelmeztető visszahívás beállítása C#‑ban – Teljes útmutató a betűkészlet kezeléséhez

Valaha szükséged volt **set warning callback** beállítására egy Word dokumentum betöltésekor, és azon tűnődtél, hogyan *configure default font*-ot állíthatsz be egyszerre? Nem vagy egyedül. Sok valós projektben—például automatizált jelentésgenerátorokban vagy dokumentumkonverziós csővezetékekben—a hiányzó betűkészletek csendben tönkretehetik az elrendezést, és az egyetlen módja annak, hogy ezeket a problémákat észrevegyük, a **monitor font changes** végrehajtása egy figyelmeztető visszahíváson keresztül.

Ebben a tutorialban egy gyakorlati példán keresztül mutatjuk be, hogyan **set warning callback**, **configure default font**, és akár **set default import font** is beállítható az Aspose.Words for .NET használatával. A végére egy kész, futtatható kódrészletet kapsz, megérted, miért fontos minden lépés, és tudni fogod, hogyan alkalmazd különböző esetekben, például egyedi betűkészlet‑mappák vagy csendes helyettesítések esetén.

---

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.6+‑on is működik)  
- Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`)  
- Egy mappa, amely tartalmazza a használni kívánt helyettesítő betűkészletet (pl. `fonts/Arial.ttf`)  
- Alapvető ismeretek a C# konzolos alkalmazásokról  

További könyvtárak nem szükségesek.

---

## 1. lépés: LoadOptions létrehozása és **configure default font**

Az első dolog, amit meg kell tenned a betűkészlet‑kezelés irányításához, egy `LoadOptions` példány felépítése. Ez az objektum azt mondja meg az Aspose.Words‑nek, hogyan kezelje a hiányzó betűkészleteket az importálás során.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Miért fontos ez:**  
Ha a forrásdokumentum olyan betűkészletet hivatkozik, amely nincs telepítve a szerveren, az Aspose.Words a megadott mappát fogja átnézni. Ez a **set default import font** lényege — kifejezetten megmondod a könyvtárnak, hol találjon helyettesítőt, még mielőtt bármilyen figyelmeztetés megjelenne.

---

## 2. lépés: **Set warning callback** a **monitor font changes** érdekében

Az Aspose.Words egy `WarningInfoCollection`‑t bocsát ki, amikor betűkészletet kell helyettesíteni, többek között. Egy kezelő hozzákapcsolásával naplózhatod vagy reagálhatsz minden egyes helyettesítésre.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Miért fontos ez:**  
Az egyszerű **configure default font** nem elegendő, ha auditálni szeretnéd, mely betűkészletek lettek ténylegesen cserélve. A visszahívás valós idejű naplót biztosít, ezzel teljesítve a **monitor font changes** követelményt, és segít időben észlelni a nem várt helyettesítéseket egy CI‑csővezetékben.

---

## 3. lépés: Dokumentum betöltése a előkészített beállításokkal

Miután a betöltési beállítások teljesen elkészültek, biztonságosan betölthetsz bármilyen `.docx` fájlt. A visszahívás automatikusan lefut, ha helyettesítés történik.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Ami megjelenik:**  
Ha a forrás egy nem létező betűkészletet használ, a konzol valami ilyesmit fog kiírni:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Ez a kimenet megerősíti, hogy sikeresen **set warning callback**‑t állítottál be, és a **default import font** hatályba lépett.

---

## 4. lépés: (Opcionális) A betűkészlet‑helyettesítés finomhangolása

Előfordulhat, hogy minden hiányzó betűkészletet egyetlen családdal szeretnél helyettesíteni, függetlenül az eredeti kéréstől. Az Aspose.Words lehetővé teszi egy globális *fallback font* beállítását.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Mikor érdemes használni:**  
Ha PDF‑eket generálsz egy olyan márka számára, amely csak korlátozott betűkészletkészletet engedélyez, ez biztosítja a konzisztenciát minden dokumentumban, még akkor is, ha a forrás valami egzotikus betűt próbál használni.

---

## 5. lépés: Dokumentum mentése vagy további feldolgozása

Betöltés után folytathatod a szükséges feldolgozást — szerkesztés, PDF‑re konvertálás, szöveg kinyerése stb. Íme egy gyors példa a dokumentum PDF‑ként való mentésére, miközben a helyettesített betűkészletek megmaradnak.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Az eredményül kapott PDF minden helyettesítésnél a fallback betűkészletet fogja megjeleníteni, így vizuálisan is ellenőrizheted, hogy a **set warning callback** megfelelően működött.

---

## Gyakori hibák és profi tippek

| Hiba | Miért fordul elő | Javítás |
|------|------------------|--------|
| **Callback never fires** | `LoadOptions.WarningCallback` nem lett hozzárendelve *a* dokumentum betöltése **előtt**. | Mindig csatold a visszahívást **mielőtt** meghívod a `new Document(...)`-t. |
| **Wrong font folder** | Elgépelés az útvonalban vagy hiányzó olvasási jogosultság. | Ellenőrizd, hogy a mappa létezik, és az alkalmazásnak van `Read` hozzáférése. Használj abszolút útvonalakat a megbízhatóság érdekében. |
| **Multiple substitutions, noisy output** | Nagy dokumentumok sok hiányzó betűkészlettel. | Szűrd a figyelmeztetéseket `WarningType.FontSubstitution` szerint (ahogy a példában látható), vagy írd őket egy naplófájlba a konzol helyett. |
| **Fallback font not applied** | A fallback betűkészlet nincs telepítve a gépen. | Helyezd a `.ttf`/`.otf` fájlt abba a mappába, amelyet a `SetFontsFolder`‑nak adtál. Az Aspose.Words közvetlenül betölti, nincs szükség operációs rendszer szintű telepítésre. |

**Pro tip:** Ha CI/CD csővezetékben futtatod, irányítsd a konzolkimenetet egy build‑artifact‑ba. Így minden betűkészlet‑helyettesítés audit nyoma megmarad a build során.

---

## Teljes működő példa (másolás‑beillesztés kész)

Az alábbi programot egyszerűen beillesztheted egy új Console App projektbe. Tartalmazza az összes lépést, `using` direktívákat és a szükséges megjegyzéseket.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Várható konzolkimenet** (ha a `Times New Roman` hiányzik):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Futtasd a programot, nyisd meg az `output.pdf`‑t, és látni fogod, hogy a dokumentum a fallback betűkészlettel jelenik meg minden szükséges helyen.

---

## Összegzés

Most már van egy stabil, termelés‑kész mintád arra, hogyan **set warning callback**‑t használj C#‑ban, **configure default font**, **monitor font changes**, és **set default import font** az Aspose.Words‑szal. A figyelmeztető gyűjtő csatolásával a betöltés előtt, a `FontSettings`‑et egy megbízható betűkészlet‑mappára mutatva, és opcionálisan egy globális fallback‑ot kényszerítve, teljes láthatóságot és irányítást kapsz a betűkészlet‑helyettesítés felett — ami minden robusztus dokumentum‑feldolgozó csővezeték alapkövetelménye.

Készen állsz a következő szintre? Próbáld ki a következőket:

- **Dynamic font loading** adatbázisból (használd a `FontSettings.SetFontsFolder`‑t futásidőben).  
- **Custom warning handlers**, amelyek strukturált naplóba (JSON vagy CSV) írnak elemzési célokra.  
- **Parallel document processing**, ahol minden szál saját `LoadOptions`‑t kap, hogy elkerülje a kereszt‑kommunikációt.

Nyugodtan kísérletezz, igazítsd a kódot a saját architektúrádhoz, és oszd meg felfedezéseidet a hozzászólásokban. Boldog kódolást!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}