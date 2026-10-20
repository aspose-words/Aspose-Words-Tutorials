---
category: general
date: 2026-03-30
description: Hogyan lehet figyelmeztetéseket elkapni egy DOCX fájl betöltésekor –
  tanulja meg a hiányzó betűtípusok észlelését, a betűtípus-beállítások konfigurálását,
  és a betöltési opciók beállítását C#-ban.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: hu
og_description: Hogyan rögzítsünk figyelmeztetéseket egy DOCX fájl betöltésekor –
  lépésről‑lépésre útmutató a hiányzó betűtípusok észleléséhez és a betűtípus‑beállítások
  konfigurálásához C#‑ban.
og_title: Hogyan rögzítsünk figyelmeztetéseket – konfigurálja a betöltési beállításokat
  a hiányzó betűtípusokhoz
tags:
- Aspose.Words
- C#
- Font management
title: Hogyan rögzítsünk figyelmeztetéseket – konfiguráljuk a hiányzó betűtípusok
  betöltési beállításait
url: /hu/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hogyan rögzítsük a figyelmeztetéseket – betöltési beállítások konfigurálása hiányzó betűtípusokhoz

Gondoltad már, **hogyan rögzítsük a figyelmeztetéseket**, amelyek akkor jelennek meg, amikor egy dokumentum olyan betűtípust próbál használni, amely nincs telepítve a gépeden? Ez a helyzet sok fejlesztőt megzavar a Word‑feldolgozó könyvtárakkal dolgozva, különösen akkor, amikor **hiányzó betűtípusok** észlelésére van szükség, mielőtt azok tönkretennék a PDF export folyamatodat.

Ebben az útmutatóban bemutatunk egy gyakorlati, azonnal futtatható megoldást, amely **konfigurálja a betűtípus beállításokat**, **beállítja a betöltési opciókat**, és minden helyettesítési figyelmeztetést kiír a konzolra. A végére pontosan tudni fogod, **hogyan kezeld a hiányzó betűtípusokat** úgy, hogy az alkalmazásod robusztus marad, és a felhasználóid elégedettek.

## Amit megtanulsz

- Hogyan **állítsuk be a betöltési opciókat**, hogy a könyvtár a betűtípus problémákat jelentse ahelyett, hogy csendben helyettesítené őket.
- A pontos lépések a **betűtípus beállítások** konfigurálásához a figyelmeztetések rögzítéséhez.
- Módszerek a **hiányzó betűtípusok** programozott észlelésére és a megfelelő reagálásra.
- Egy teljes, másold‑be C# példa, amely működik a legújabb Aspose.Words for .NET (v24.10 a írás időpontjában).
- Tippek a megoldás kibővítéséhez, hogy figyelmeztetéseket naplózzunk, egyedi betűtípusokra térjünk vissza, vagy megszakítsuk a feldolgozást, ha kritikus betűtípusok hiányoznak.

> **Előfeltétel:** Telepítened kell az Aspose.Words for .NET NuGet csomagot (`Install-Package Aspose.Words`). Más külső függőség nem szükséges.

## 1. lépés: Névterek importálása és a projekt előkészítése

Először add hozzá a szükséges `using` direktívákat. Ez nem csak sablonkód; a fordítónak megmondja, hogy a `LoadOptions`, `FontSettings` és `Document` hol található.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Pro tipp:** Ha .NET 6+ verziót használsz, engedélyezheted a *global using* nyilatkozatokat, hogy elkerüld ezen sorok minden fájlban való ismétlését.

## 2. lépés: Betöltési opciók beállítása és a betűtípus‑helyettesítési figyelmeztetések engedélyezése

A **hogyan rögzítsük a figyelmeztetéseket** lényege a `LoadOptions` objektumban rejlik. Egy új `FontSettings` példány létrehozásával és egy eseménykezelő csatolásával a `SubstitutionWarning`‑hez, azt mondod a könyvtárnak, hogy minden alkalommal jelezze, amikor nem találja a kért betűtípust.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Miért fontos:** Az esemény feliratkozás nélkül az Aspose.Words csendben visszatér egy alapértelmezett betűtípusra, és sosem tudod, mely karakterek lettek helyettesítve. A `SubstitutionWarning` figyelésével teljes audit nyomot kapsz – ami elengedhetetlen a szigorú megfelelőségi környezetekben.

## 3. lépés: Dokumentum betöltése a konfigurált opciókkal

Miután a figyelmeztetések be vannak kötve, töltsd be a DOCX‑edet (vagy bármely támogatott formátumot) a frissen előkészített `loadOptions`‑szal. A `Document` konstruktor azonnal elindítja a betűtípus‑ellenőrzési logikát.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Ha a fájl például a *„Comic Sans MS”* betűtípust hivatkozza egy olyan gépen, amelynek csak a *„Arial”* van telepítve, akkor valami ilyesmit látsz:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Ez a sor közvetlenül a konzolra kerül, a korábban csatolt kezelőnek köszönhetően.

## 4. lépés: A rögzített figyelmeztetések ellenőrzése és reagálás

A figyelmeztetések rögzítése csak a harc felét jelenti; gyakran el kell dönteni, mi a következő lépés. Az alábbi gyors minta a figyelmeztetéseket egy listában tárolja későbbi elemzéshez – tökéletes, ha fájlba szeretnéd naplózni őket vagy megszakítani az importálást, ha kritikus betűtípus hiányzik.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Különleges esetek kezelése:**  
- **Több hiányzó betűtípus:** A lista minden helyettesítéshez egy bejegyzést tartalmaz, így iterálhatsz és részletes jelentést készíthetsz.  
- **Egyedi tartalék betűtípusok:** Ha saját betűtípus fájljaid vannak, add hozzá őket a `FontSettings`‑hez a betöltés előtt: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. A figyelmeztetések ezután az egyedi tartalékot mutatják a rendszer alapértelmezett helyett.

## 5. lépés: Teljes működő példa (másold‑be készen)

Mindent összevonva, itt egy önálló konzolalkalmazás, amelyet most lefordíthatsz és futtathatsz.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Várható konzol kimenet** (ha a DOCX hiányzó betűtípust hivatkozik):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Ha egy *kritikus* betűtípus, például a „Times New Roman” hiányzik, akkor a megszakítási üzenetet fogod látni.

## Gyakori kérdések és buktatók

| Kérdés | Válasz |
|----------|--------|
| **Szükséges-e meghívni a `SetFontsFolder`‑t a figyelmeztetések rögzítéséhez?** | Nem. A figyelmeztetési esemény az alapértelmezett rendszerbetűtípusokkal működik. A `SetFontsFolder`‑t csak akkor használd, ha további tartalék betűtípusokat szeretnél biztosítani. |
| **Működni fog ez .NET Core / .NET 5+ környezetben?** | Természetesen. Az Aspose.Words 24.10 támogatja az összes modern .NET futtatókörnyezetet. Csak győződj meg róla, hogy a NuGet csomag megfelel a célkeretrendszernek. |
| **Mi van, ha a figyelmeztetéseket fájlba szeretném naplózni a konzol helyett?** | Cseréld le a `Console.WriteLine(msg);`-t bármilyen naplózási keretrendszer hívására, például `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Lehet-e elnyomni a figyelmeztetéseket bizonyos betűtípusoknál?** | Igen. Az eseménykezelőben szűrhetsz: `if (e.FontName == "SomeFont") return;`. Ez finomhangolt vezérlést biztosít. |
| **Van mód arra, hogy a hiányzó betűtípusokat hibaként kezeljük?** | Dobj egy kivételt manuálisan a kezelőben, ha egy feltétel teljesül, vagy állíts be egy jelzőt, és a `Document` konstrukció után szakítsd meg a folyamatot, ahogyan a példában látható. |

## Összegzés

Most már van egy robusztus, termelés‑kész mintád a **hogyan rögzítsük a figyelmeztetéseket**, amelyek hiányzó betűtípusok betöltésekor jelentkeznek. A **hiányzó betűtípusok** észlelésével, a **betűtípus beállítások** konfigurálásával és a **betöltési opciók** megfelelő beállításával teljes átláthatóságot kapsz a betűtípus helyettesítési események felett, és eldöntheted, hogy naplózod, tartalékot használsz vagy megszakítod a folyamatot.

Tedd a következő lépést, és integráld ezt a logikát a PDF konverziós folyamatodba, adj hozzá egyedi tartalék betűtípusokat, vagy küldd a figyelmeztetési listát egy felügyeleti rendszernek. A megközelítés skálázható a kis segédprogramoktól az vállalati szintű dokumentumfeldolgozó szolgáltatásokig.

### További olvasmányok és következő lépések

- **Fedezd fel a FontSettings további funkcióit** – egyedi betűtípusok beágyazása, a tartalék sorrendjének vezérlése és licencelési szempontok.  
- **Kombináld PDF konverzióval** – a figyelmeztetések rögzítése után hívd meg a `doc.Save("output.pdf");`-t, és ellenőrizd, hogy a PDF a várt betűtípusokat használja.  
- **Automatizáld a tesztelést** – írj egységteszteket, amelyek ismert hiányzó betűtípusokkal töltenek be dokumentumokat, és ellenőrzik, hogy a figyelmeztetési lista tartalmazza a várt üzeneteket.

Ha bármilyen problémába ütközöl vagy van ötleted a fejlesztéshez, nyugodtan hagyj egy megjegyzést. Boldog kódolást!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}