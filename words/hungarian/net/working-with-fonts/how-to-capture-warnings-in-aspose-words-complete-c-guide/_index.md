---
category: general
date: 2026-03-28
description: Hogyan lehet elkapni a figyelmeztetéseket a DOCX betöltésekor az Aspose.Words
  használatával, és hogyan kapjunk figyelmeztető üzeneteket a hiányzó betűtípusokról.
  Tanulja meg hatékonyan kezelni a hiányzó betűtípusokat.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: hu
og_description: Hogyan lehet figyelmeztetéseket elkapni egy DOCX betöltésekor az Aspose.Words
  használatával, figyelmeztető üzeneteket lekérni, és hiányzó betűtípusokat kezelni
  gyakorlati kódrészletekkel.
og_title: Hogyan rögzítsük a figyelmeztetéseket az Aspose.Words-ben – Teljes C# útmutató
tags:
- Aspose.Words
- C#
- Document Processing
title: Hogyan rögzítsük a figyelmeztetéseket az Aspose.Words-ben – Teljes C# útmutató
url: /hu/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan rögzítsünk figyelmeztetéseket az Aspose.Words‑ben – Teljes C# útmutató

Valaha is elgondolkodtál **arról, hogyan rögzítsd a figyelmeztetéseket**, amelyek megjelennek, amikor egy Word‑dokumentumot töltesz be az Aspose.Words‑szel? Lehet, hogy furcsa betűtípus‑változásokat látsz, és pontosan tudni szeretnéd, miért. Röviden, csatlakozhatsz a könyvtár figyelmeztetési rendszeréhez, **lekérheted a figyelmeztető üzeneteket**, és akár **kezelheted a hiányzó betűtípusokat** is, mielőtt azok tönkretennék a megjelenést.  

Ebben az oktatóanyagban egy valós példán keresztül vezetünk végig: egy DOCX betöltése, a motor által kibocsátott minden figyelmeztetés összegyűjtése, és a betűtípus‑helyettesítésekről szóló részletek kiírása. A végére egy azonnal futtatható kódrészletet kapsz, megérted az egyes lépések „miértjét”, és tudni fogod, hogyan bővítheted a megközelítést a saját projektjeidben.

## Mit fogsz megtanulni

- Hogyan konfiguráld a `LoadOptions`‑t úgy, hogy a figyelmeztetések automatikusan rögzítésre kerüljenek.  
- A pontos módja annak, hogy **lekérd a figyelmeztető üzeneteket** a `WarningInfoCollection`‑ből.  
- Hogyan azonosítsd és reagálj a **hiányzó betűtípusokra** a `WarningType.FontSubstitution` jelző segítségével.  
- Tippek a széljegyek (edge cases) hibaelhárításához, például beágyazott betűtípusok vagy egyedi betűtípus‑mappák esetén.  

Nincs szükség külső hivatkozásokra – minden, amire szükséged van, itt található.

---

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑on is működik).  
- Aspose.Words for .NET NuGet csomag (`Install-Package Aspose.Words`).  
- Egy minta DOCX (`input.docx`), amely vagy hiányos betűtípusokkal rendelkezik, vagy olyan betűtípusokat használ, amelyek nincsenek telepítve a gépeden.  

Ennyi. Ha már jártas vagy a C#‑ban és a Visual Studio‑ban, egyszerűen másold be a kódot, és futtasd.

---

## 1. lépés: Load Options előkészítése és figyelmeztetési visszahívás (Warning Callback) létrehozása

Az első dolog, amit az Aspose.Words csinál, amikor a `new Document(path, loadOptions)`‑t meghívod, a fájl elemzése. Az elemzés során hiányzó betűtípusokkal, nem támogatott funkciókkal vagy elavult markup‑okkal találkozhat. Ahhoz, hogy ezeket az eseményeket elkapd, szükséged van egy **figyelmeztetési visszahívás** objektumra.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Miért fontos:** Visszahívás nélkül az Aspose.Words csendben naplózza a figyelmeztetéseket a konzolra (vagy eldobja őket), így vak maradsz a betűtípus‑helyettesítésekkel szemben, amelyek befolyásolhatják a layoutot. Egy dedikált `WarningInfoCollection` biztosítja a teljes láthatóságot.

> **Pro tipp:** Ha csak a betűtípus‑kapcsolatú figyelmeztetéseket érdekelnek, később szűrhetsz – de az *összes* figyelmeztetés gyűjtése biztonsági hálót nyújt a jövőbeli problémákhoz.

---

## 2. lépés: A dokumentum betöltése a konfigurált opciókkal

Most, hogy a visszahívás készen áll, töltsd be a fájlt. A `Document` konstruktor automatikusan meghívja a visszahívást minden talált problémához.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Mi történik a háttérben?** Az Aspose.Words elemzi az Open XML‑t, feloldja a stílusokat, és megpróbálja minden betűtípus‑hivatkozást egy rendszer‑telepített betűtípusra leképezni. Ha nincs egyezés, egy `WarningInfo` bejegyzést hoz létre `FontSubstitution` típusúként.

---

## 3. lépés: A gyűjtött figyelmeztetések lekérdezése és vizsgálata

A betöltés befejeződése után a `warningCollector` már tartalmazza az összes előfordult figyelmeztetést. Húzzuk ki őket, és fókuszáljunk a betűtípus‑helyettesítési üzenetekre.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Minta kimenet** (a konzolod valami ilyesmit mutathat):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Ha *minden* figyelmeztetést szeretnél, egyszerűen távolítsd el az `if` ellenőrzést, vagy írd ki a `warning.Type`‑t minden bejegyzésnél.

---

## 4. lépés: Hiányzó betűtípusok kezelése – nem csak naplózás

A figyelmeztetések rögzítése hasznos, de gyakran programozottan kell **kezelni a hiányzó betűtípusokat**. Íme két gyakori stratégia:

### 4.1 Hiányzó betűtípusok cseréje egy konkrét tartalékra

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Most minden hiányzó betűtípus *Calibri*‑ra lesz cserélve a könyvtár alapértelmezett tartalékja helyett.

### 4.2 Helyettesítő betűtípus beágyazása dinamikusan

Ha rendelkezel egy egyedi betűtípusfájllal (pl. `MyFallback.ttf`), regisztrálhatod futásidőben:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Ez a megközelítés akkor hasznos, ha egy specifikus vállalati betűtípust szeretnél szállítani az alkalmazásoddal.

> **Széljegy:** Azok a dokumentumok, amelyek már beágyazzák a szükséges betűtípust, figyelmen kívül hagyják a rendszer‑helyettesítési szabályokat. Ebben az esetben a figyelmeztető gyűjtemény az adott betűtípusra nézve üres lesz, ami éppen azt jelenti, amit szeretnél.

---

## 5. lépés: Teljes működő példa (másolás‑beillesztés kész)

Az alábbi önálló program mindent bemutat a kezdetektől a végéig. Csak cseréld le a `YOUR_DIRECTORY/input.docx`‑t a tesztfájlod elérési útjára.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Mire számíthatsz**

- A konzol minden betűtípus‑helyettesítési figyelmeztetést kiír, egy figyelmeztető emoji‑val előtagolva a láthatóság kedvéért.  
- A kimeneti DOCX (`output.docx`) minden hiányzó betűtípus helyén *Calibri*-t használ.  
- Nincs nem kezelt kivétel – a figyelmeztetési rendszer elegánsan kezeli a nem ismert betűtípusokat.

---

## Gyakori kérdések & válaszok

**Q: Működik ez PDF‑ekkel, amelyeket Word‑ből generáltak?**  
A: Igen. Az Aspose.Words a PDF‑eket egy másik kimeneti formátumnak tekinti. A figyelmeztetés‑rögzítés a *betöltés* fázisban történik, így független a végső exporttól.

**Q: Mi van, ha **minden** dokumentumművelethez (mentés, konvertálás, stb.) szeretnék figyelmeztetéseket rögzíteni?**  
A: Ugyanazt a `WarningInfoCollection`‑t újra felhasználhatod úgy, hogy a `Document.WarningCallback`‑t a dokumentum példányosítása után beállítod. Minden későbbi művelet új bejegyzéseket ad hozzá ugyanahhoz a gyűjteményhez.

**Q: Befolyásolja a teljesítményt a figyelmeztetési visszahívás?**  
A: Gyakorlatilag nem. A gyűjtemény egyszerűen objektumokat tárol; csak ha több ezer figyelmeztetést dolgozol fel szoros ciklusban, észrevehető lassulás lehet.

**Q: Hogyan szűrhetem el azokat a figyelmeztetéseket, amelyek nem érdekelnek?**  
A: Implementálj egy saját osztályt, amely örökli az `IWarningCallback`‑t, és szűrj a `Warning` metódusban. A beépített `WarningInfoCollection` csak tárol, nem szűr.

---

## Pro tippek & buktatók

- **Pro tipp:** Mindig nézd meg a `Warning.Description`‑t – ez tartalmazza a pontosan hiányzó betűtípus nevét. Ez segíthet eldönteni, hogy a betűtípust be kell-e csomagolni az alkalmazásoddal.  
- **Figyelj a beágyazott betűtípusokra:** Ha a forrás‑DOCX már beágyazza a szükséges betűtípust, az Aspose.Words nem ad ki helyettesítési figyelmeztetést, még ha a betűtípus nincs is telepítve helyileg.  
- **Szálbiztonság:** A `WarningInfoCollection` nem szál‑biztos. Ha egyszerre több dokumentumot töltesz be párhuzamosan, minden szálnak saját gyűjteményt kell biztosítania.  
- **Verzió ellenőrzés:** A figyelmeztetési API stabil a Aspose.Words 20.8‑tól. Győződj meg róla, hogy egy friss verziót használsz, hogy ne maradj le az újabb figyelmeztetéstípusokról.

---

## Összegzés

Áttekintettük, **hogyan rögzítsük a figyelmeztetéseket** az Aspose.Words‑ból, bemutattuk, **hogyan kapjuk meg a figyelmeztető üzeneteket**, és gyakorlati módon **kezeljük a hiányzó betűtípusokat** tartalék‑betűtípusok vagy egyedi betűtípus‑mappák segítségével. A teljes példa készen áll arra, hogy bármely .NET projektbe beilleszd, és a koncepciók skálázhatók nagyobb automatizálási csővezetékekre is.

A következő lépések lehetnek:

- A `Document.WarningCallback` használata a **mentési** műveletek során keletkező figyelmeztetések rögzítésére.  
- Figyelmeztetések naplózása fájlba vagy telemetriai rendszerbe a termelési környezet monitorozásához.  
- A visszahívás kiterjesztése, hogy automatikusan cserélje a hiányzó betűtípusokat a márkád specifikus betűtípusaival.

Nyugodtan kísérletezz – cseréld le a tartalék‑betűtípust, adj hozzá több dokumentumot a köteghez, vagy integráld a figyelmeztető gyűjtőt egy CI‑csővezetékbe, amely jelzi a betűtípus‑kapcsolódó regressziókat. Boldog kódolást, és legyenek a dokumentumaid mindig úgy megjelenítve, ahogy elvárod!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}