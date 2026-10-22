---
category: general
date: 2026-10-13
description: Ismerje meg a betűtípus-helyettesítést a dokumentumban C#-ban. Ez az
  útmutató bemutatja, hogyan állítható be a big5 kódolás, hogyan tölthető be egy DOCX,
  és hogyan cserélhetők le a régi betűtípusok a modernakra.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: hu
lastmod: 2026-10-13
og_description: A betűkészlet helyettesítése a dokumentumban elengedhetetlen a régi
  kínai fájlokkal való munka során. Kövesd ezt a lépésről‑lépésre útmutatót, hogy
  betölts egy BIG5 kódolású DOCX-et, és cseréld le a régi betűkészleteket.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Betűtípus helyettesítés dokumentumban C#-val – teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: Hogyan hajtsunk végre betűtípus-helyettesítést egy dokumentumban C#‑val
url: /hu/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus helyettesítés dokumentumban – teljes C# útmutató

Ha **font substitution in document**-ra van szüksége a régi kínai fájlok helyes megjelenítéséhez, ez az útmutató pontosan megmutatja, hogyan kell ezt megtenni. A megfelelő szövegkódolás beállításával és egy elavult betűtípus modernra cserélésével garantálja, hogy a végső DOCX a kívánt módon jelenjen meg.

A dokumentumfeldolgozás gyakran hibát jelez, ha a forrás egy régi kódolást, például **big5**-öt használ, vagy olyan betűtípust hivatkozik, amely már nem létezik a rendszeren. Ez az útmutató végigvezet a DOCX helyes **big5 encoding**-kel történő betöltésén, a **legacy font replacement** alkalmazásán, és egy tiszta kimenet előállításán, amely bármely Windows gépen működik.

Megtanulja:

* Hogyan hozzon létre egy `LoadOptions` objektumot **big5 encoding**-kel.  
* Hogyan nyisson meg egy DOCX fájlt **C# LoadOptions** használatával.  
* Hogyan hajtson végre **font substitution in document**-t egy régi betűtípust egy modern megfelelőre leképezve.  
* Különleges esetek kezelése hiányzó betűtípusok és több betűtípuscsalád esetén.

Külső eszközök nem szükségesek az Aspose.Words for .NET könyvtárán kívül, és a teljes kód másolható egy konzolprojekthez, majd azonnal futtatható.

## Előfeltételek

* .NET 6.0 vagy újabb (a példa .NET 6 konzolos szintaxist használ).  
* Aspose.Words for .NET – telepítés: `dotnet add package Aspose.Words`.  
* Egy DOCX fájl, amely **big5 encoding**-kel van mentve, és a régi `MingLiU-ExtB` betűtípust hivatkozza.  
* Alapvető ismeretek C#-ban és a Visual Studio-ban vagy bármely általad választott IDE-ben.

## 1. lépés: A projekt beállítása és a névterek importálása

Hozzon létre egy új konzolalkalmazást, és adja hozzá a szükséges `using` direktívákat. Ez biztosítja, hogy a kód extra módosítások nélkül forduljon le.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Pro tipp:** Tartsa a `Main` metódust minimálisra; ez javítja az olvashatóságot és könnyebbé teszi az útmutató követését.

## 2. lépés: A betöltési beállítások meghatározása a megfelelő szövegkódolással (big5 a hagyományos kínaihoz)

A `LoadOptions` osztály megmondja az Aspose.Words-nek, hogyan értelmezze a forrásfájl nyers bájtjait. A **big5 encoding** használata kritikus a hagyományos kínai karakterekhez, amelyek ezzel a régi kódlappal lettek mentve.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Miért fontos:** Ha kihagyja a kódolást vagy az alapértelmezett UTF‑8-at használja, a karakterek torz szimbólumokként (mojibake) jelenhetnek meg. A `big5` megadása megőrzi az eredeti glifeket, mielőtt bármilyen betűtípus helyettesítés megtörténne.

## 3. lépés: A DOCX fájl betöltése a megadott kódolással

Adja át a `loadOptions` példányt a `Document` konstruktorának. Ez betölti a fájlt, miközben tiszteletben tartja a korábban meghatározott **document encoding for Chinese**-t.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Ha a fájl nem található, a program `FileNotFoundException`-t dob. Győződjön meg róla, hogy az útvonal helyes, és az alkalmazásnak olvasási jogosultsága van.

## 4. lépés: Egy régi betűtípus helyettesítése modern megfelelővel

Sok régi kínai dokumentum a `MingLiU-ExtB` betűtípust hivatkozza, amely újabb Windows telepítéseken esetleg nem érhető el. Ennek `Microsoft JhengHei`-re (széles körben elérhető Unicode betűtípus) történő leképezése biztosítja a megfelelő megjelenítést.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Magyarázat:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` egy globális helyettesítési szabályt regisztrál. Minden alkalommal, amikor az Aspose.Words `MingLiU-ExtB`-t talál, azt `Microsoft JhengHei`-re cseréli.  
* A opcionális ciklus kiírja a leképezést, ami hasznos a hibakereséshez nagy dokumentumokban több betűtípuscsaláddal.

## 5. lépés: A feldolgozott dokumentum mentése

A helyettesítés után írja a dokumentumot egy új fájlba. A kimenet a kínai szöveget a modern betűtípussal jeleníti meg, eltávolítva a hiányzó glifekre vonatkozó figyelmeztetéseket.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Nyissa meg a keletkezett fájlt a Microsoft Wordben vagy bármely DOCX megjelenítőben; a hagyományos kínai karaktereknek tisztán kell megjelenniük a `Microsoft JhengHei` betűtípussal.

## Szélsőséges esetek és gyakori buktatók kezelése

| Helyzet | Ajánlott megközelítés |
|-----------|----------------------|
| **A forrás betűtípusa nincs felsorolva a dokumentumban** | Használja a `doc.FontInfos.Substitution.Add`-t helyettesítő karakterekkel, például `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Több régi betűtípust kell helyettesíteni** | Hívja meg az `Add`-ot minden párosra, vagy töltsön be egy helyettesítési szótárat egy konfigurációs fájlból. |
| **A cél betűtípus nem érhető el a célgépen** | Válasszon egy Windows-szal szállított betűtípust (pl. `Arial Unicode MS`), vagy ágyazza be a betűtípust a `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll` használatával. |
| **A kódolási hibák továbbra is megjelennek** | Ellenőrizze, hogy a forrásfájl valóban **big5**-öt használ; megtekintheti a fájlt hex szerkesztővel vagy a `File.ReadAllBytes` segítségével, és összehasonlíthatja a bájtmintákat. |

## Teljes működő példa

Az alábbiakban a teljes, önálló program látható. Másolja be a `Program.cs`‑be, állítsa be a fájlutakat, és futtassa.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Várható eredmény:** A `big5_doc_fixed.docx` megnyitása során minden hagyományos kínai karakter helyesen jelenik meg, hiányzó glifek figyelmeztetése nélkül, mivel a `MingLiU-ExtB` helyett a `Microsoft JhengHei` lett használva.

## Következtetés

Most már rendelkezik egy megbízható módszerrel a **font substitution in document** feladatokhoz C#-ban. A **big5 encoding** beállításával, a DOCX `LoadOptions`‑szel történő betöltésével és a régi betűtípusok modern megfelelőkre történő leképezésével megszünteti a régi kínai fájlok megjelenítési problémáit.

Innen tovább:

* Bővítse a helyettesítési térképet további régi betűtípusok lefedésére.  
* Automatizálja a folyamatot dokumentumcsoportok számára (ciklus egy könyvtáron).  
* Kombinálja a betűtípus helyettesítést más dokumentumtranszformációkkal, például vízjel vagy PDF konverzió.

Nyugodtan kísérletezzen különböző célbetűtípusokkal vagy ágyazzon be egyedi betűtípusokat a teljes hordozhatóság érdekében. Ha problémába ütközik, nézze meg újra a fenti szélsőséges esetek táblázatát, vagy tekintse meg az Aspose.Words dokumentációját a fejlett betűtípuskezeléshez.

Boldog kódolást!

## Mit érdemes még megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Betűtípus helyettesítési figyelmeztetések engedélyezése az Aspose.Words‑ben – Teljes útmutató](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Betűtípus helyettesítési figyelmeztetések naplózása – Teljes Aspose.Words útmutató](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Betöltés kódolással Word dokumentumban](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}