---
category: general
date: 2026-04-21
description: Ismerje meg, hogyan lehet felismerni a betűtípusokat, elkapni a figyelmeztetéseket,
  konfigurálni a visszahívást, és felsorolni a figyelmeztetéseket az Aspose.Words
  C#-ban. Lépésről lépésre útmutató a megbízható betűtípus‑kezeléshez.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: hu
og_description: Hogyan lehet felismerni a betűtípusokat az Aspose.Words-ben? Ez az
  útmutató megmutatja, hogyan lehet figyelmeztetéseket rögzíteni, visszahívási függvényt
  konfigurálni, és figyelmeztetéseket felsorolni C#-ban.
og_title: Hogyan lehet betűtípusokat felismerni az Aspose.Words-ben – Teljes útmutató
tags:
- Aspose.Words
- C#
- Document Processing
title: Hogyan lehet felismerni a betűtípusokat az Aspose.Words-ben – Teljes útmutató
url: /hu/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan észleljük a betűtípusokat az Aspose.Words‑ban – Teljes útmutató

Gondolkodtál már azon, **hogyan lehet észlelni a hiányzó betűtípusokat**, amikor egy Word‑dokumentumot betöltesz? Ez a helyzet gyakrabban előfordul, mint szeretnéd, különösen régi fájlok vagy több platformon futó alkalmazások esetén. Ebben a bemutatóban egy teljes, futtatható példán keresztül megmutatjuk, hogyan **rögzítsünk figyelmeztetéseket**, **konfiguráljunk visszahívást**, és **listázzuk a figyelmeztetéseket**, hogy mindig tudd, mely betűtípusok lettek helyettesítve.

Az Aspose.Words for .NET‑et (v24.9 a cikk írásakor) és egyszerű C#‑t használunk. Nincs külső szolgáltatás, nincs varázslat – csak az API és néhány kódsor. A végére képes leszel minden betűtípus‑helyettesítést észlelni, naplózni, sőt akár megszakítani a betöltést, ha kritikus betűtípus hiányzik.  

### Amire szükséged lesz
- **Aspose.Words for .NET** (telepítsd NuGet‑en: `Install-Package Aspose.Words`)
- .NET 6.0 vagy újabb (a kód .NET Framework‑ön is működik)
- Egy minta DOCX, amely egy a gépen nem létező betűtípust hivatkozik (pl. “MyCustomFont.ttf”)
- Visual Studio, Rider vagy bármelyik kedvenc C#‑szerkesztőd

> **Pro tipp:** Ha nincs hiányzó betűtípussal rendelkező dokumentumod, egyszerűen nevezd át egy betűtípus‑fájlt a rendszereden, vagy módosítsd a DOCX XML‑ét, hogy egy nem létező betűtípus‑családra hivatkozzon.

---

## Hogyan észleljük a betűtípusokat az Aspose.Words‑szal

A lényeg, hogy bekapcsoljuk az Aspose.Words figyelmeztetési rendszerét. Amikor a könyvtár nem találja a kért betűtípust, egy `WarningType.FontSubstitution` figyelmeztetést küld. Egy saját `IWarningCallback` megvalósításával **észlelheted a betűtípus‑helyettesítéseket** a betöltés során.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Miért működik:** Az Aspose.Words minden nem kritikus problémához meghívja a `Warning` metódust. A `WarningInfo` objektumok tárolásával teljes hozzáférést kapsz a típushoz, az üzenethez és a kontextushoz, ami pontosan azt a lehetőséget adja, hogy **észleld a helyettesített betűtípusokat**.

---

## Hogyan rögzítsük a figyelmeztetéseket a dokumentum betöltésekor

Miután megvan a gyűjtő, el kell mondanunk a `LoadOptions`‑nak, hogy használja azt. Ez a **hogyan rögzítsük a figyelmeztetéseket** része a feladványnak.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Széljegyzet:** Ha egy dokumentumot stream‑ből töltesz be (`new Document(stream, loadOptions)`), ugyanaz a visszahívás működik – csak a fájlútvonal helyett add át a stream‑et.

Ekkor a dokumentum teljesen betöltődik, de minden betűtípus‑helyettesítési figyelmeztetés biztonságosan a `warningCollector.Warnings` gyűjteményben tárolódik.

---

## Hogyan listázzuk a figyelmeztetéseket és jelentjük a betűtípus‑helyettesítéseket

Végül átnézzük a gyűjtött figyelmeztetéseket, és **listázzuk a figyelmeztetéseket**, amelyek kifejezetten a betűtípus‑helyettesítésről szólnak. Ez a lépés alakítja a nyers adatot egy olvasható jelentéssé.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Várható kimenet** (példa):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Ha a dokumentumban nincs hiányzó betűtípus, a ciklus egyszerűen nem ad ki semmit – nincs mit aggódni.

---

## Teljes működő példa (minden lépés egy fájlban)

Az alábbiakban a komplett programot találod, amelyet egyszerűen beilleszthetsz egy konzol‑projektbe. Összekapcsolja a **hogyan észleljük a betűtípusokat**, **hogyan rögzítsük a figyelmeztetéseket**, **hogyan konfiguráljuk a visszahívást**, és **hogyan listázzuk a figyelmeztetéseket** egy koherens folyamatban.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**A program futtatása** kiírja minden olyan betűtípust, amelyet az Aspose.Words‑nak helyettesítenie kellett. Átirányíthatod a kimenetet egy naplófájlba, riasztást generálhatsz, vagy akár megszakíthatod a betöltést, ha kritikus betűtípus hiányzik.

---

## Gyakori kérdések és buktatók

### Mi a teendő, ha a betöltést meg kell állítani, amikor egy kötelező betűtípus hiányzik?
A `WarningInfo` objektumokat a visszahívásban ellenőrizheted, és kivételt dobhatod, ha egy adott betűtípus neve megjelenik. A kivétel megszakítja a betöltést, így teljes kontrollt kapsz.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Működik ez PDF‑ekkel vagy más formátumokkal is?
Igen. Az Aspose.Words ugyanazt a figyelmeztetési infrastruktúrát használja PDF, RTF és HTML esetén is. Csak cseréld le a fájlkiterjesztést, a kód többi része változatlan marad.

### Hogyan naplózhatom a figyelmeztetéseket fájlba a konzol helyett?
Cseréld le a `Console.WriteLine`‑t a kedvenc naplókeretrendszeredre (`Serilog`, `NLog`, stb.). A `WarningInfo` osztály a `Message`, `Source` és `Exception` tulajdonságokkal részletes naplózást tesz lehetővé.

### Befolyásolja ez a teljesítményt?
Az overhead elhanyagolható – az Aspose.Words már belül generálja a figyelmeztetéseket. Egy visszahívás hozzáadása csak egy listába helyezi el őket, ami O(n) a figyelmeztetések számához képest. Átlagos dokumentumok esetén a hatás jóval 1 % alatti a teljes betöltési időből.

---

## Vizuális összefoglaló

![How to Detect Fonts in Aspose.Words – warning flow diagram](https://example.com/images/font-detection-diagram.png "how to detect fonts")

*Alt szöveg:* **how to detect fonts** – diagram a figyelmeztetési visszahívás, gyűjtés és listázás lépéseiről.

---

## Összegzés

Áttekintettük, **hogyan észleljük a betűtípusokat** az Aspose.Words‑ban **figyelmeztetések rögzítésével**, **visszahívás konfigurálásával**, és **figyelmeztetések listázásával**. A teljes kódminta egy termelés‑kész mintát mutat, amelyet bármely .NET‑alkalmazásba be lehet illeszteni.  

A következő lépések, amiket érdemes felfedezni:

- **Hogyan rögzítsük a figyelmeztetéseket** más problémákra (pl. képek konvertálási hibái)
- **Hogyan konfiguráljuk a visszahívást** egyedi naplózási keretrendszerekhez
- **Hogyan listázzuk a figyelmeztetéseket** több dokumentum esetén egy kötegelt feladatban
- Az **Aspose.Words.Fonts.FontSettings** használata tartalék betűtípus‑mappák megadásához, ami már a kezdetekkor csökkentheti a helyettesítések számát.

Próbáld ki, igazítsd a gyűjtőt a saját naplózási stílusodhoz, és többé nem ér majd meglepetés egy váratlan betűtípus‑csere. Ha bármilyen furcsaságra bukkansz, írj egy megjegyzést alább – jó kódolást!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}