---
category: general
date: 2026-03-19
description: Ismerje meg, hogyan lehet figyelmeztetéseket elkapni az Aspose.Words-ben,
  alapértelmezett betűtípus-beállításokat megadni, és hiányzó betűtípusokat észlelni
  a Word-dokumentum betöltésekor.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: hu
og_description: Hogyan lehet figyelmeztetéseket elkapni az Aspose.Words-ben, alapértelmezett
  betűtípus-beállításokat megadni, és hiányzó betűtípusokat észlelni egy Word-dokumentum
  betöltésekor.
og_title: Hogyan rögzítsük a figyelmeztetéseket – Alapértelmezett betűtípus beállítások
tags:
- Aspose.Words
- C#
- Document Processing
title: Figyelmeztetések rögzítése – Alapértelmezett betűtípus beállítások
url: /hu/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan rögzítsünk figyelmeztetéseket – Alapértelmezett betűtípus beállítások megadása

**A figyelmeztetések rögzítése** gyakori igény, amikor az Aspose.Words-szal dolgozol, különösen ha a dokumentumaid olyan betűtípusokra támaszkodnak, amelyek a célgépen nem állnak rendelkezésre. Nyitottál már egy DOCX-et, és azon tűnődtél, miért néz ki a megjelenés hibásan? A válasz gyakran egy hiányzó betűtípusról szóló figyelmeztetésben rejlik.  

Ebben az útmutatóban végigvezetünk a **figyelmeztetések rögzítése** folyamatán, miközben **word dokumentumot töltesz be**, konfigurálod a **alapértelmezett betűtípus beállításait**, és végül **hiányzó betűtípusokat észlelsz**, hogy programozottan reagálhass. Nincs felesleges szöveg – csak egy teljes, futtatható példa és a magyarázat minden egyes sorhoz.

> *Pro tip:* A figyelmeztetések korai rögzítése megment a későbbi, rejtélyes megjelenési hibák hibakeresésétől.

---

## Amire szükséged lesz

- **Aspose.Words for .NET** (a legújabb verzió 2026-ig).  
- Egy .NET fejlesztői környezet (Visual Studio, Rider vagy VS Code).  
- Egy minta DOCX, amely egy olyan betűtípust hivatkozik, amelyet *nem* telepítettél (például *Comic Sans MS* egy Linux gépen).  

Ennyi. Nem szükséges további NuGet csomag az Aspose.Words-en kívül.

---

## 1. lépés – Miért kell figyelmeztetéseket rögzíteni

Amikor az Aspose.Words egy dokumentumot feldolgoz, előfordulhat, hogy olyan betűtípusokra akad, amelyek a gépen nem érhetők el. Alapértelmezés szerint a könyvtár csendben helyettesít egy tartalék betűtípussal, ami megváltoztathatja a sortöréseket, a távolságokat, sőt akár a szöveg eltűnését is okozhat.  

A **WarningCallback** és egy **FontSettings** objektum együttes használata két dolgot biztosít:

1. **Átláthatóság** – minden helyettesítéshez kapsz egy `WarningInfo` bejegyzést.  
2. **Kontroll** – előre beállíthatsz egy alapértelmezett betűtípust, hogy minimalizáld a vizuális meglepetéseket.

Olyan, mintha egy „őr” lenne, amely minden alkalommal felkiált, amikor a motor egy alkatrészt cserél a motorháztető alatt.

---

## 2. lépés – Alapértelmezett betűtípus beállítása

Az első másodlagos kulcsszó, **set default font settings**, itt jelenik meg. Létrehozol egy `FontSettings` példányt, és opcionálisan megadod azt a mappát, amely a tartalék betűtípusaidat tartalmazza.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Miért?**  
> Ha nem adsz meg tartalék betűtípust, az Aspose.Words a rendszer első olyan betűtípusát választja, amely megfelel a stílusnak, ami drámaian eltérhet az eredetitől. Egy ismert alapértelmezett beállításával garantálod a konzisztens megjelenítést a gépek között.

---

## 3. lépés – Figyelmeztetési visszahívás (Callback) előkészítése a figyelmeztetések rögzítéséhez

Most megmutatjuk, **hogyan rögzítsd a figyelmeztetéseket** egy `WarningInfoCollection` csatolásával a betöltési beállításokhoz. Ez a gyűjtemény minden betöltés közben keletkezett figyelmeztetést tárolni fog.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

A `WarningInfoCollection` implementálja az `IWarningCallback` interfészt, így az Aspose.Words automatikusan minden figyelmeztetést a `warningInfos` gyűjteménybe helyez. Nincs szükség lekérdezésre.

---

## 4. lépés – Word dokumentum betöltése a konfigurált beállításokkal

Itt jön a második másodlagos kulcsszó, **load word document**, a főszerepbe. A `FontSettings` és a `WarningCallback` objektumokat egy `LoadOptions` példányon keresztül adjuk át.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Ha a dokumentum egy nem telepített betűtípust hivatkozik, a figyelmeztetési visszahívás egy `WarningType.FontSubstitution` bejegyzést fog rögzíteni.

---

## 5. lépés – Hiányzó betűtípusok észlelése a gyűjtött figyelmeztetésekből

Végül megválaszoljuk a harmadik másodlagos kulcsszót, **detect missing fonts**, azzal, hogy végigiterálunk a gyűjtött figyelmeztetéseken.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

A tipikus kimenet így néz ki:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Ez a sor pontosan megmondja, melyik betűtípus hiányzik és melyik tartalékot használta – ezt az információt naplózhatod, megjelenítheted a felhasználónak, vagy akár egy egyedi betűtípus‑telepítési rutin indítására is felhasználhatod.

---

## Teljesen futtatható példa

Az alábbi teljes programot egyszerűen beillesztheted egy konzolalkalmazásba. Bemutatja a **figyelmeztetések rögzítését**, a **alapértelmezett betűtípus beállítását**, a **word dokumentum betöltését**, és a **hiányzó betűtípusok észlelését** egyetlen folyamatban.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Várható eredmény:** Ha a megadott DOCX egy nem telepített betűtípust hivatkozik, a konzol minden helyettesítéshez egy figyelmeztetést ír ki. Ha minden betűtípus jelen van, a ciklus nem ad ki semmit.

---

## Gyakori hibák és széljegyek

| Helyzet | Miért fordul elő | Hogyan kezeljük |
|-----------|----------------|------------------|
| **Nem jelennek meg figyelmeztetések**, pedig a megjelenés hibás | A dokumentum *beágyazott* betűtípusokat használhat, amelyeket az Aspose.Words helyettesítés nélkül jelenít meg. | Ellenőrizd a `Document.HasEmbeddedFonts` értékét, és fontold meg a beágyazott betűtípusok kinyerését, ha más gépen is szükséged van rájuk. |
| **Több figyelmeztetés a** |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}