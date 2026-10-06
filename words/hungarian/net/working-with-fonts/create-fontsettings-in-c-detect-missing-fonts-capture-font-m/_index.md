---
category: general
date: 2026-03-01
description: Hozzon létre FontSettings objektumot C#-ban a hiányzó betűtípusok észleléséhez,
  a betűtípus‑üzenetek rögzítéséhez, valamint a hiányzó betűtípusok kezeléséhez az
  Aspose.Words segítségével. Lépésről‑lépésre útmutató fejlesztőknek.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: hu
og_description: Hozzon létre FontSettings objektumot C#-ban a hiányzó betűtípusok
  észleléséhez, a betűtípus-üzenetek rögzítéséhez, és a hiányzó betűtípusok kezeléséhez
  az Aspose.Words segítségével. Teljes útmutató kóddal.
og_title: FontSettings létrehozása C#‑ban – Hiányzó betűtípusok felderítése és betűtípus‑üzenetek
  rögzítése
tags:
- Aspose.Words
- C#
- Font Management
title: FontSettings létrehozása C#‑ban – Hiányzó betűtípusok felderítése és betűtípus‑üzenetek
  rögzítése
url: /hu/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hozzon létre FontSettings-et C#‑ban – Hiányzó betűtípusok észlelése és betűtípus‑üzenetek rögzítése

Valaha is szüksége volt **create FontSettings**‑re egy .NET projektben, de nem tudta, hogyan találja meg a célgépen nem telepített betűtípusokat? Nem vagy egyedül. Sok valós alkalmazásban – gondoljunk automatizált jelentéskészítőkre vagy dokumentumkonvertálókra – a hiányzó betűtípusok csendben tönkretehetik a megjelenést, és csak akkor veszi észre, amikor a PDF hibásan néz ki.  

Mi lenne, ha **detect missing fonts**, **capture font messages**, és **handle missing fonts** funkciókat már a kimenet romlása előtt tudná használni? A jó hír, hogy az Aspose.Words ezt gyerekjátékra változtatja. Ebben az útmutatóban végigvezetjük a teljes folyamatot, a `FontSettings` objektum beállításától a figyelmeztető visszahívás (warning callback) összekapcsolásáig, amely pontosan megmondja, mely glifek lettek helyettesítve.

> **TL;DR:** A végére egy azonnal futtatható C# konzolalkalmazást kap, amely naplózza minden betűtípus‑helyettesítést, így eldöntheti, beágyazza‑e a helyettesítőt vagy értesíti‑e a felhasználót.

---

## Előfeltételek

- .NET 6 SDK (vagy bármely friss .NET verzió)  
- Visual Studio 2022 vagy VS Code C# kiegészítőkkel  
- Aspose.Words for .NET licenc (az ingyenes próba megfelelő a bemutatóhoz)  
- Egy minta DOCX, amely olyan betűtípust hivatkozik, amely nincs telepítve (például *Comic Sans MS* egy Linux gépen)  

Nem szükséges semmilyen speciális NuGet csomag a `Aspose.Words`‑en kívül.

---

## Step 1 – Install Aspose.Words and Set Up the Project

Először is hozzon létre egy új konzolprojektet, és adja hozzá az Aspose.Words könyvtárat.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Ha már van megoldása, egyszerűen adja hozzá a csomagot a NuGet Package Manager UI‑n keresztül – így könnyebb a verziókövetés.

---

## Step 2 – Create FontSettings (Primary Keyword Appears Here)

A **create FontSettings** lépés minden betűtípus‑kapcsolódó munkafolyamat sarokköve. A `FontSettings` megmondja az Aspose.Words‑nek, hol keresse a betűtípusokat, használjon‑e rendszerkönyvtárakat, és hogyan térjen vissza, ha valami hiányzik.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Miért fontos ez? Ha a `FontSettings` nincs megfelelően konfigurálva, a motor csendben helyettesíti a hiányzó glifeket az alapértelmezett rendszer‑betűtípussal, és Ön soha nem kap figyelmeztetést.

---

## Step 3 – Wire Up LoadOptions with the FontSettings

A `LoadOptions` lehetővé teszi, hogy a `FontSettings`‑et átadja a dokumentum‑betöltőnek. Ez a híd, amely a motor számára **detect missing fonts** funkciót biztosít a `Document` létrehozási fázisában.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Mostantól minden alkalommal, amikor `loadOptions`‑szel tölt be egy DOCX‑et, az Aspose.Words a korábban beállított `FontSettings`‑et használja.

---

## Step 4 – Attach a Warning Callback to **Capture Font Messages**

Az Aspose.Words különféle feltételekhez figyelmeztetéseket ad – a betűtípus‑helyettesítés gyakori ilyen. Egy `IWarningCallback` megvalósításával **capture font messages**‑t tud rögzíteni valós időben.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### A Figyelmeztető Kezelő Osztály

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Az `info.Description` mező ember által olvasható üzenetet tartalmaz, például *„Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* Ez pontosan az a kimenet, amelyre szüksége van a **handle missing fonts** folyamat során.

---

## Step 5 – Load the Document and Let the Callback Do Its Job

Minden összekapcsolva, a dokumentum betöltése egyszerű. Ha a forrásfájl olyan betűtípust hivatkozik, amely hiányzik a rendszerről, a figyelmeztető kezelő aktiválódik.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

A program futtatásakor a konzolon a következőhöz hasonló kimenetet fogja látni:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Ez a kimenet a **capture font messages** részét képezi a munkafolyamatnak. A kezelőt kibővítheti, hogy fájlba naplózzon, telemetriát küldjön, vagy akár megszakítsa a konverziót, ha kritikus betűtípusok hiányoznak.

---

## Step 6 – Full Working Example (All Pieces Together)

Az alábbiakban egy teljes, másolás‑beillesztésre kész programot talál. Illessze be a `Program.cs`‑be, állítsa be a fájlútvonalakat, és futtassa a `dotnet run` paranccsal.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Várható Kimenet

Ha a gépen nincs telepítve a *Comic Sans MS*, a program valami ilyesmit fog kiírni:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Emellett egy `Result.pdf` fájlt kap, amely a helyettesített betűtípusokat használja, biztosítva, hogy a konverzió ne fusson hibába.

---

## Common Questions & Edge Cases

| Kérdés | Válasz |
|----------|--------|
| **Mi van, ha azt szeretném, hogy a konverzió hibával álljon le a helyettesítés helyett?** | A `FontSubstitutionWarningHandler`‑ben dobjon kivételt, ha az `info.Description` kritikus betűtípusnevet tartalmaz. |
| **Be tudok-e ágyazni egy helyettesítő betűtípust automatikusan?** | Igen. Hiányzó betűtípus észlelése után betölthet egy tartalék `FontInfo`‑t egy ismert útvonalról, és hozzáadhatja a `fontSettings`‑hez a `fontSettings.SetFontsFolder` segítségével. |
| **Működik ez Linuxon/macOS‑on?** | Természetesen. A `FontSettings` platformfüggetlen; csak győződjön meg róla, hogy a tartalék mappa a megfelelő `.ttf` vagy `.otf` fájlokat tartalmazza. |
| **A warning callback szálbiztos?** | A callback ugyanazon a szálon fut, amely a dokumentumot betölti, így a konzol‑naplózáshoz nincs szükség extra szinkronizációra. Többszálú környezetben óvja a megosztott erőforrásokat. |
| **Hogyan naplózhatom a figyelmeztetéseket fájlba?** | Cserélje le a `Console.WriteLine`‑t `File.AppendAllText("font_warnings.log", ...)`‑ra, vagy használjon bármelyik naplózási keretrendszert (Serilog, NLog). |

---

## Pro Tips for Production‑Ready Font Handling

1. **Cache Font Lookups** – Ugyanazt a `FontSettings` példányt használja több dokumentum betöltésekor, így elkerülhető a fájlrendszer ismételt beolvasása.  
2. **Whitelist Critical Fonts** – Ha a márkájához specifikus betűtípus szükséges, ellenőrizze korán a jelenlétét, és állítsa le a folyamatot egy egyértelmű hibaüzenettel.  
3. **Use `SetFontFolder` Recursively** – A `recursive: true` beállítás biztosítja az almappák beolvasását, ami akkor hasznos, ha egy teljes betűtípus‑gyűjteményt szállít.  
4. **Combine with `FontSubstitutionSettings`** – Finomhangolhatja a helyettesítési szabályokat (például előnyben részesítheti ugyanazzal a családnévvel rendelkező betűtípusokat).  

---

## Conclusion

Most **created FontSettings**‑et, a `LoadOptions`‑t **detect missing fonts**‑re konfiguráltuk, egy visszahívást csatoltunk, amely **captures font messages**, és bemutattuk, hogyan **handle missing fonts** egy tiszta, termelés‑kész módon. Az egész folyamat néhány tucat C# sorba fér, mégis teljes láthatóságot biztosít a bármely DOCX betűtípus‑környezetéről.

A következőket érdemes felfedezni:

- **Fallback betűtípusok beágyazása** közvetlenül a kimeneti PDF‑be (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programozott betűtípus‑helyettesítés** vállalati márka‑szabályok alapján.  
- **Integráció CI pipeline‑nal**, hogy automatikusan jelzéseket kapjon a nem engedélyezett betűtípusok használatáról.

Próbálja ki, finomítsa a figyelmeztető kezelőt saját igényei szerint, és hagyja, hogy dokumentumfolyamatai magabiztosan fusson – többé nem lesznek rejtett elrendezési hibák láthatatlan betűtípus‑csere miatt.

Boldog kódolást! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}