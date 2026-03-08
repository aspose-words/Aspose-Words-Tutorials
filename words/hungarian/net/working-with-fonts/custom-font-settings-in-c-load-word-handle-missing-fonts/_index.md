---
category: general
date: 2026-03-08
description: Az egyéni betűtípus-beállítások lehetővé teszik a betűtípus-beállítások
  megadását, a Word-dokumentum biztonságos betöltését és a hiányzó betűtípusok kezelését
  az Aspose.Words segítségével.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: hu
og_description: Az egyéni betűtípus-beállítások lehetővé teszik a betűtípus-beállítások
  megadását, a Word-dokumentum biztonságos betöltését és a hiányzó betűtípusok kezelését
  az Aspose.Words segítségével.
og_title: Egyéni betűtípus beállítások C#-ban – Szó betöltése és a hiányzó betűtípusok
  kezelése
tags:
- Aspose.Words
- C#
- Font Management
title: Egyéni betűtípus beállítások C#-ban – Szó betöltése és hiányzó betűtípusok
  kezelése
url: /hu/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Egyedi betűtípus beállítások C#‑ban – Word betöltése és hiányzó betűtípusok kezelése

Gondolkodtál már azon, hogy a **custom font settings** (egyedi betűtípus beállítások) hogyan működnek, amikor egy Word fájl olyan betűtípusokra hivatkozik, amelyek nincsenek telepítve? Ez egy gyakori probléma – a dokumentum egy gépen rendben néz ki, majd hirtelen minden bekezdés egy helyettesítő betűtípusra vált egy másikon.  

A jó hír? Az Aspose.Words segítségével **set font settings**, **load Word document** tartalmat, és **handle missing fonts** egy tiszta folyamatban kezelhetsz. Az alábbiakban egy teljes, azonnal futtatható példát találsz, amely pontosan megmutatja, hogyan kell ezt megtenni, valamint a „miért” magyarázatát minden lépéshez.

## Mit fogsz megtanulni

Ebben az útmutatóban a következőket fedjük le:

* Egy `LoadOptions` objektum létrehozása és egy `FontSettings` példány csatolása.  
* Figyelmeztető visszahívás (warning callback) regisztrálása, hogy lásd, mely betűtípusok kerülnek helyettesítésre.  
* DOCX fájl betöltése, amely esetleg hiányzó betűtípusokat tartalmaz, és a helyettesítési részletek kiírása a konzolra.  

A végére magabiztosan tudod majd szállítani a C# alkalmazásodat, tudva, hogy minden hiányzó betűtípus eset naplózásra kerül, és később kezelhető.

> **Előfeltétel:** Aspose.Words for .NET (v23.12 vagy újabb) telepítve NuGet‑en keresztül, valamint alapvető ismeretek a C# konzolalkalmazásokról.

---

## Egyedi betűtípus beállítások – LoadOptions konfigurálása

Az első dolog, amire szükséged van, egy `LoadOptions` objektum. Ez megmondja az Aspose.Words‑nek, hogyan kezelje a bejövő fájlt. Egy új `FontSettings` példány hozzárendelésével megadjuk a könyvtárnak, hol keresse az egyedi betűtípusokat.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Miért fontos ez:**  
Ha kihagyod a `FontSettings`‑t, az Aspose.Words a rendszer alapértelmezett betűtípus-gyűjteményére támaszkodik. Ez azt jelenti, hogy minden hiányzó betűtípus csendben helyettesítésre kerül, és nem fogod tudni, melyek lettek kicserélve. Egy explicit `FontSettings` tároló létrehozásával teljes irányítást kapsz a keresési folyamat felett.

---

## Betűtípus beállítások megadása a LoadOptions‑ban

Most, hogy van egy `FontSettings` objektumunk, elképzelhető, hogy merül fel a kérdés, hová mutassuk. Általában egy mappát adsz hozzá, amely a betűtípusokat tartalmazza, amelyeket az alkalmazásoddal szállítasz:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Ha nincs privát mappád, kihagyhatod ezt a blokkot – az Aspose.Words továbbra is jelenteni fogja a hiányzó betűtípusokat a warning callback‑on keresztül.*

**Pro tip:**  
Használd a `recursive: true` kapcsolót, ha a betűtípusok alkönyvtárakban vannak szórva. Ez megspórolja a manuális útvonalak hozzáadását.

---

## Word dokumentum betöltése egyedi betűtípus beállításokkal

A beállítások elkészítése után a dokumentum betöltése gyerekjáték. A `Document` konstruktor elfogadja a fájl útvonalát és a most épített `LoadOptions`‑t.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Mi történik a háttérben?**  
Az Aspose.Words beolvassa a DOCX‑et, ellenőrzi minden `<w:font>` hivatkozást, és a megadott `FontSettings`‑et használja. Ha egy betűtípus nem található, egy `FontSubstitution` típusú figyelmeztetést generál. A saját kezelőnk (a következőben látható) elkapja ezeket a figyelmeztetéseket.

---

## Hiányzó betűtípusok kezelése warning callback‑kel

Az `IWarningCallback` interfész lehetővé teszi, hogy reagálj a betöltés során felmerülő problémákra. Ennek megvalósítása egyszerű:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Amikor a dokumentum betöltődik, minden hiányzó betűtípus egy ilyen sort eredményez:

```
Font substituted: Arial -> Liberation Sans
```

**Miért érdemes ezt naplózni:**  
Éles környezetben ezeket az üzeneteket átirányíthatod egy fájlba vagy telemetriai rendszerbe, így könnyen megtalálod, mely betűtípusokat kell csomagolnod vagy licencelned.

---

## Teljes működő példa

Az alábbi önálló konzolprogram mindent összekapcsol. Másold be egy új .NET Core konzolprojektbe, és nyomd meg a **Run**‑t.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Várható kimenet** (feltételezve, hogy az `input.docx` olyan betűtípust használ, amely nincs nálad):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Ha minden betűtípus jelen van, csak a végső megerősítő sort fogod látni.

---

## Gyakori kérdések és szélhelyzetek

| Question | Answer |
|----------|--------|
| **Mi van, ha a hiányzó betűtípusokat be kell ágyazni a PDF‑be?** | A betöltés után hívd meg a `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` kódot, majd engedélyezd a beágyazást a `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;` segítségével. |
| **Elnyomhatom a figyelmeztetéseket a naplózás helyett?** | Igen – állítsd be a `loadOptions.WarningCallback = null;` értéket, vagy valósítsd meg a callback‑et úgy, hogy figyelmen kívül hagyja a nem betűtípusra vonatkozó figyelmeztetéseket. |
| **Működik ez `.doc` és `.rtf` fájlokkal is?** | Természetesen. Ugyanaz a `LoadOptions` objektum minden, az Aspose.Words által támogatott formátumra alkalmazható. |
| **A callback szálbiztos?** | A callback ugyanazon a szálon fut, amely a dokumentumot betölti, így biztonságosan írhat a konzolra. Többszálas esetekben használj párhuzamos gyűjteményt vagy naplózási keretrendszert. |

---

## Pro tippek és buktatók

* **Pro tip:** Ha olyan betűtípust szállítasz, amely nincs telepítve a célgépen, add hozzá a `SetFontsFolder`‑nak átadott mappához. Ez garantálja a determinisztikus megjelenítést.
* **Figyelj a licencelésre:** Egyes betűtípusok beágyazáshoz kereskedelmi licencet igényelnek. Mindig ellenőrizd a betűtípus EULA‑ját a csomagolás előtt.
* **Teljesítményjegyzet:** Nagy betűtípus‑könyvtárak betöltése lelassíthatja a dokumentum elemzését. Tartsd a mappát karcsúnak – csak a ténylegesen szükséges betűtípusokat tartalmazza.
* **Szélhelyzet:** Ha egy dokumentum a betűtípust a *PostScript név* alapján hivatkozza a családnév helyett, az Aspose.Words még mindig feloldja, amennyiben a betűtípusfájl jelen van a keresési útvonalon.

---

## Következtetés

Most már van egy teljes, éles környezetben használható minta a **custom font settings** (egyedi betűtípus beállítások) C#‑ban történő használatához. A `LoadOptions` konfigurálásával, egy warning callback regisztrálásával, és opcionálisan egy privát betűtípus mappára mutatva, megbízhatóan **set font settings**, **load Word document** tartalmat tudsz kezelni.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}