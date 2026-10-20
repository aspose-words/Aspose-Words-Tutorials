---
category: general
date: 2026-01-14
description: Naplózza a betűkészlet-helyettesítési figyelmeztetéseket Word-dokumentumok
  betöltésekor az Aspose.Words használatával. Tanulja meg, hogyan lehet észlelni a
  hiányzó betűkészleteket, és hogyan rögzítheti a hiányzó betűkészleteket C#‑ban.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: hu
og_description: Naplózza a betűkészlet-helyettesítési figyelmeztetéseket Word-dokumentumok
  betöltésekor az Aspose.Words használatával. Ismerje meg, hogyan lehet észlelni a
  hiányzó betűkészleteket, és hogyan rögzítheti a hiányzó betűkészleteket C#-ban.
og_title: Betűtípus-helyettesítési figyelmeztetések naplózása – Teljes Aspose.Words
  útmutató
tags:
- Aspose.Words
- C#
- Document Processing
title: Betűtípus-helyettesítés naplózási figyelmeztetések – Teljes Aspose.Words útmutató
url: /hu/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus‑helyettesítési figyelmeztetések naplózása – Teljes Aspose.Words útmutató

A betűtípus‑helyettesítési figyelmeztetések naplózása elengedhetetlen, ha garantálni kell, hogy egy Word‑dokumentum pontosan ugyanúgy nézzen ki, miután az Aspose.Words betöltötte. Ha valaha is kíváncsi volt arra, hogyan **detektálhat hiányzó betűtípusokat**, vagy szeretné tudni, **hogyan rögzíthet hiányzó betűtípusokat**, jó helyen jár.  

Ebben az oktatóanyagban egy valós példán keresztül vezetünk végig, bemutatjuk a teljes C# kódot, és elmagyarázzuk, miért fontos minden egyes sor. A végére képes lesz naplózni minden betűtípus‑helyettesítési eseményt és reagálni rá – nincs több titokzatos figyelmeztetés.

![Betűtípus‑helyettesítési figyelmeztetések példája](/images/font-warnings.png "Képernyőkép, amely a betűtípus‑helyettesítési figyelmeztetések konzolkimenetét mutatja")

## Amit megtanul

- Hogyan konfigurálja a `LoadOptions`‑t, hogy az Aspose.Words típusos figyelmeztetéseket adjon a betűtípus‑helyettesítéshez.  
- A pontos lépések a **hiányzó betűtípusok detektálásához** a dokumentum betöltése során.  
- Egy tiszta mód a **hiányzó betűtípusok rögzítésére** és azok saját naplóba vagy felügyeleti rendszerbe írására.  
- Szélsőséges esetek kezelése (pl. amikor egy dokumentum olyan betűtípust tartalmaz, amely nincs telepítve a szerveren).  

### Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.6+ verzióval is működik).  
- Érvényes Aspose.Words for .NET licenc (vagy az ingyenes próba).  
- Alapvető ismeretek a C#‑ról és a konzolos alkalmazásokról.  

Ha már rendelkezik ezekkel, merüljünk el.

## 1. lépés – LoadOptions beállítása típusos figyelmeztetések kiadásához

A megoldás lényege a `LoadOptions.FontSubstitutionWarning`. Ha `RaiseTypedWarnings`‑ra állítja, akkor az Aspose.Words minden alkalommal eseményt vált ki, **minden alkalommal**, amikor nem találja meg a kért pontos betűtípust.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Miért fontos ez:**  
> Az alapértelmezett viselkedés csendben helyettesíti a hiányzó betűtípust a legközelebbi egyezővel, ami elrendezési hibákhoz vezethet, amiket nem látsz előre. A típusos figyelmeztetések kiadása teljes átláthatóságot biztosít.

## 2. lépés – Feliratkozás a figyelmeztetési eseményre

Most a `loadOptions.FontSubstitutionWarning`‑ra csatlakozunk. A lambda egy `e` objektumot kap, amely pontosan megmondja, melyik betűtípus hiányzott és melyik lett helyette használva.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tipp:** Ha ezt egy webszerveren futtatja, cserélje le a `Console.WriteLine`‑t egy strukturált naplózóval (Serilog, NLog, stb.), hogy később lekérdezhesse az adatokat.

## 3. lépés – Dokumentum betöltése a konfigurált beállításokkal

A figyelmeztetési mechanizmus beállítása után egyszerűen töltse be a dokumentumot, ahogy általában tenné. Az esemény automatikusan lefut minden hiányzó betűtípus esetén.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Várt konzolkimenet

Ha az `input.docx` egy *MyFancyFont* nevű betűtípust hivatkozik, amely nincs telepítve, a következőt fogja látni:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Minden sor egy **hiányzó betűtípusok detektálása** eseménynek felel meg, ami teljes audit nyomot biztosít.

## 4. lépés – Szélsőséges esetek és fejlett forgatókönyvek kezelése

### 4.1 Amikor nem történik helyettesítés

Néha egy dokumentum csak olyan rendszerbetűtípusokat használ, amelyek már jelen vannak. Ebben az esetben a figyelmeztetési esemény soha nem fut le, és egy tiszta konzolt kap kimenet nélkül. Ez jó jel – a környezet már rendelkezik az összes szükséges betűtípussal.

### 4.2 Figyelmeztetések rögzítése későbbi elemzéshez

Ha a figyelmeztetéseket egy éjszakai jelentéshez kell tárolni, gyűjtse őket egy listába:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Betöltés után a `missingFonts`‑t sorosíthatja JSON‑be, írhatja adatbázisba, vagy e‑mailben küldhet összefoglalót.

### 4.3 Munkavégzés PDF‑ekkel vagy más formátumokkal

Ugyanez a `LoadOptions` megközelítés működik a PDF, RTF és még a HTML fájlok `Load` hívásainál is. Csak adja át ugyanazt a beállítási példányt, és az Aspose.Words figyelmeztetéseket ad minden olyan betűtípusra, amelyet nem tud egyeztetni.

## 5. lépés – Az eredmény programozott ellenőrzése

Ha inkább automatizált tesztet szeretne a konzol szemrevételezése helyett, ellenőrizze, hogy a lista tartalmazza a várt elemeket:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Ez a kódrészlet bemutatja, **hogyan rögzítsük a hiányzó betűtípusokat** a kódban, nem csak a naplóban.

## Gyakori buktatók és elkerülésük módja

| Buktató | Miért fordul elő | Javítás |
|---------|------------------|--------|
| A `RaiseTypedWarnings` beállításának elhagyása | Az alapértelmezett érték a `DoNotRaise`, ezért nem indulnak el események. | Állítsa be kifejezetten a `FontSubstitutionWarning`‑t, ahogy az 1. lépésben látható. |
| `Console.WriteLine` használata webalkalmazásban | A konzolkimenet eltűnik az IIS/ASP.NET Core alatt. | Váltson tartós naplózóra (pl. Serilog). |
| Dokumentum betöltése relatív úttal | A munkakönyvtár futásidőben eltérhet. | Használjon abszolút útvonalakat vagy `Path.Combine(AppContext.BaseDirectory, "input.docx")`‑t. |
| A `SubstitutedFontName` figyelmen kívül hagyása | Elveszíti a betekintést, hogy melyik helyettesítő lett kiválasztva. | Mindig naplózza a `FontName` és a `SubstitutedFontName` értékeket. |

## Bónusz: Betűtípusok automatikus telepítése

Ha Ön irányítja a telepítési környezetet, előre telepítheti a hiányzó betűtípusokat egy PowerShell szkript segítségével:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Ennek a futtatása az alkalmazás indítása előtt szinte minden **hiányzó betűtípusok detektálása** figyelmeztetést megszünteti.

## Következtetés

Mindezt lefedtük, ami szükséges a **betűtípus‑helyettesítési figyelmeztetések naplózásához** Word‑dokumentumok Aspose.Words‑szal történő betöltésekor. A `LoadOptions` konfigurálásával, a figyelmeztetési eseményre való feliratkozással és a találatok opcionális tárolásával megbízhatóan **detektálhatja a hiányzó betűtípusokat** és megértheti, **hogyan rögzítse a hiányzó betűtípusokat** bármely .NET projektben.

Vegye a kódot, igazítsa a naplózót a saját környezetéhez, és többé már nem érheti meglepetés egy csendes betűtípuscsere. A következő lépések lehetnek:

- A figyelmeztetési lista integrálása a CI/CD folyamatba, hogy a buildek hibára fussanak, ha kritikus betűtípusok hiányoznak.  
- A megközelítés kiterjesztése a betűtípus‑használat monitorozására dokumentumflottákban.  
- Az Aspose.Words `FontSettings` API‑jának felfedezése egyedi helyettesítő betűtípusok biztosításához.

Van kérdése vagy bonyolult helyzete? Hagyjon megjegyzést, és oldjuk meg együtt. Boldog kódolást!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}