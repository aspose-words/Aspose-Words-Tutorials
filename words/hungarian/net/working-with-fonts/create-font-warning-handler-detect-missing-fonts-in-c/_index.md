---
category: general
date: 2026-02-12
description: Hozzon létre betűtípus-figyelmeztető kezelőt a hiányzó betűtípusok észleléséhez
  és nyomon követéséhez az Aspose.Words-ben. Tanulja meg, hogyan lehet hatékonyan
  naplózni a figyelmeztetéseket.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: hu
og_description: Készítsen betűtípus-figyelmeztető kezelőt C#-ban a hiányzó betűtípusok
  észleléséhez, és tanulja meg, hogyan naplózhat figyelmeztetéseket, amikor az Aspose.Words
  betűtípusokat helyettesít.
og_title: Betűtípus Figyelmeztetés Kezelő létrehozása – Hiányzó betűtípusok észlelése
tags:
- Aspose.Words
- C#
- Document Processing
title: Betűtípus Figyelmeztetés Kezelő létrehozása – Hiányzó betűtípusok észlelése
  C#-ban
url: /hu/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fontfigyelmeztető kezelő létrehozása – Hiányzó betűkészletek észlelése C#‑ban

Szükséged volt már **fontfigyelmeztető kezelő** létrehozására, mert egy Word‑dokumentum csendben egy nem várt betűtípust helyettesített? Nem vagy egyedül. Amikor az Aspose.Words betölt egy DOCX‑et, amely egy a szerveren hiányzó betűtípust hivatkozik, csendben egy alapértelmezett betűtípusra vált – így a megjelenés finoman megbomlik.

Ebben az útmutatóban pontosan megmutatjuk, hogyan **észleld a hiányzó betűtípusokat**, **kövesd nyomon a hiányzó betűtípusokat**, és **hogyan naplózd a figyelmeztetéseket**, hogy a helyettesítéseket még mielőtt problémát okoznának, észrevedd. A végére egy újrahasználható figyelmeztető kezelővel leszel felvértezve, amely minden betűtípus‑helyettesítési eseményt kiír a konzolra (vagy bármely általad preferált naplózóba). Nincs rejtély, csak tiszta, cselekvő kód.

## Előfeltételek

- .NET 6.0 vagy újabb (az API ugyanaz a .NET Framework 4.6+ esetén is)
- Aspose.Words for .NET telepítve (`dotnet add package Aspose.Words`)
- Egy Word‑fájl, amely egy a gépeden nem telepített betűtípust hivatkozik (pl. `MissingFont.docx`)

Ha már megvan mindez, nagyszerű – vágjunk bele.

## 1. lépés: LoadOptions beállítása figyelmeztető visszahívással  

Az első dolog, amit megteszel, amikor **fontfigyelmeztető kezelőt** szeretnél **létrehozni**, hogy megmondod az Aspose.Words‑nek, hogy minden probléma esetén hívjon vissza. A `LoadOptions` ebben a konfigurációban a tároló.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Miért fontos:**  
A `LoadOptions` az egyetlen hely, ahol be lehet illeszteni egy `IWarningCallback`‑et. Enélkül az Aspose.Words belsőleg naplózza a figyelmeztetéseket, de te sosem látod őket. A `FontWarningHandler` hozzárendelésével teljes irányítást kapsz arról, mi történik, ha egy hiányzó betűtípust helyettesítenek.

## 2. lépés: A FontWarningHandler osztály megvalósítása  

Most ténylegesen **létrehozzuk a fontfigyelmeztető kezelő** kódot. Az osztály implementálja az `IWarningCallback`‑et, és minden egyes figyelmeztetéshez kap egy `WarningInfo` objektumot, amelyet az Aspose.Words kibocsát.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Magyarázat:**  
- `info.Type` megadja a figyelmeztetés kategóriáját. A `WarningType.FontSubstitution` érdekel minket, mert ez jelzi a hiányzó betűtípust.  
- `info.Description` egy ember által olvasható üzenetet tartalmaz, például *„Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- A `Console.WriteLine`‑nal **azonnal naplózzuk a figyelmeztetéseket**. Egy valós alkalmazásban ezt helyettesítheted `ILogger`‑rel, fájlíróval vagy telemetria‑szolgáltatással.

> **Pro tipp:** Ha később jelentést szeretnél készíteni az összes hiányzó betűtípusról, tárold a `info.Description`‑t egy `List<string>`‑ben a kiírás helyett.

## 3. lépés: Dokumentum betöltése a konfigurált LoadOptions‑szal  

A visszahívás beállítása után a dokumentum betöltése automatikusan aktiválja a kezelőnket, amikor betűtípus hiányzik.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Ami megjelenik:**  
A program futtatása valami hasonlót ír ki:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Ez a sor megerősíti, hogy **sikeresen észlelted a hiányzó betűtípusokat** és most **valós időben követed a hiányzó betűtípusokat**.

## 4. lépés: A kezelő ellenőrzése különböző forgatókönyvekkel  

Könnyű azt feltételezni, hogy a kezelő csak DOCX fájloknál működik, de az Aspose.Words sok formátumot támogat. Próbálj meg betölteni egy PDF‑et, amely egy beágyazott betűtípust hivatkozik, vagy egy régebbi `.doc` fájlt. Ugyanaz a visszahívás aktiválódik minden olyan formátumnál, amely a betűtípus‑feloldási csővezetékén megy keresztül.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Ha a PDF egy nem telepített betűtípust hivatkozik, ugyanazt a konzolkimenetet kapod. Ez azt mutatja, hogy a **fontfigyelmeztető kezelő** megoldásod formátum‑független.

## 5. lépés: A kezelő kibővítése – naplózás fájlba  

A konzolkimenet kényelmes demókhoz, de a produkciós kódban általában naplófájlba írunk. Íme egy gyors módosítás.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Most minden betűtípus‑helyettesítéskor az üzenet a `font-warnings.log` fájlhoz lesz hozzáfűzve. Ez kielégíti a **hogyan naplózzuk a figyelmeztetéseket** részt, és tartós audit nyomot biztosít.

## 6. lépés: Összeállítás – teljes, futtatható példa  

Az alábbi teljes programot másold be egy konzolalkalmazásba. Semmi hiányzik; csak cseréld le a fájlútvonalat a saját dokumentumodra.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Várható eredmény:**  

- A konzol minden helyettesítési sort kiír.  
- A `font-warnings.log` most már időbélyeggel ellátott rekordot tartalmaz minden hiányzó betűtípus‑eseményről.  
- Az `output.pdf` fájl a helyettesített betűtípusokkal jön létre, biztosítva, hogy a konverzió sikeres legyen még akkor is, ha az eredeti betűtípusok nem érhetők el.

## Gyakori kérdések és széljegyek  

| Kérdés | Válasz |
|----------|--------|
| *Mi van, ha bizonyos betűtípusokat figyelmen kívül szeretnék hagyni?* | A `Warning`‑ban ellenőrizd a `info.Description`‑t a betűtípus neve miatt, és `return;`‑val lépj ki korán azoknál, amelyeket elfogadhatónak tartasz. |
| *A kezelő aktiválódik beágyazott betűtípusoknál?* | Nem – a beágyazott betűtípusok mindig elérhetők a dokumentum számára, így nem keletkezik helyettesítési figyelmeztetés. |
| *Más figyelmeztetéstípusokat is le tudok fogni (pl. kép‑felbontási problémák)?* | Természetesen. Távolítsd el a `if (info.Type == WarningType.FontSubstitution)` feltételt, vagy adj hozzá további `if` blokkokat a `WarningType.ImageResolution`‑hez. |
| *A kezelő szálbiztos?* | A bemutatott alapimplementáció fájlba ír szinkronizáció nélkül. Több szálas környezetben csomagold a fájlírást egy lock‑ba, vagy használj párhuzamos naplózót. |

## Következő lépések  

Most, hogy tudod, **hogyan naplózd a figyelmeztetéseket** hiányzó betűtípusok esetén, érdemes lehet:

- **Hiányzó betűtípusok észlelése** egy kötegelt importfolyamat során, és összefoglaló jelentés generálása.  
- **Hiányzó betűtípusok nyomon követése** több dokumentumon keresztül, és e‑mail riasztás küldése, ha egy adott betűtípus gyakran előfordul.  
- **Integráció egy felügyeleti rendszerrel** (pl. Azure Application Insights), hogy idővel megjelenjenek a betűtípus‑helyettesítési trendek.  

Mindez ugyanazon `IWarningCallback` alapra épül, amelyet létrehoztunk.

---

*Boldog kódolást! Ha valami furcsaságba ütközöl – például egy egyedi betűtípus‑mappa vagy hálózati megosztás – írj egy megjegyzést alul. A közösség (és én) mindig szívesen segít finomhangolni a font‑figyelmeztetési stratégiádat.* 

![fontfigyelmeztető kezelő példa](image-placeholder.png "fontfigyelmeztető kezelő példa")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}