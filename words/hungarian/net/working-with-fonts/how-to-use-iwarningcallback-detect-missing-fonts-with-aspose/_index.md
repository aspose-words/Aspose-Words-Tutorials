---
category: general
date: 2026-06-24
description: Hogyan használjuk az IWarningCallback-et a hiányzó betűtípusok felismerésére
  az Aspose.Words dokumentumokban. Ismerjen meg egy teljes, futtatható példát és a
  legjobb gyakorlatokat.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: hu
og_description: Hogyan használjuk az IWarningCallback-et a hiányzó betűtípusok észlelésére
  az Aspose.Words-ben. Kövesse a lépésről‑lépésre útmutatót egy teljes, termelésre
  kész megoldáshoz.
og_title: Az IWarningCallback használata – Hiányzó betűtípusok felderítése
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Az IWarningCallback használata – Hiányzó betűtípusok felderítése az Aspose.Words
  segítségével
url: /hu/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan használjuk az IWarningCallback‑t – Hiányzó betűkészletek észlelése az Aspose.Words‑ban

Az **IWarningCallback** használata elengedhetetlen, ha az Aspose.Words‑szal dolgozunk, és **hiányzó betűkészletek** észlelésére van szükségünk egy DOCX fájlban. Ebben az útmutatóban egy teljes, másolás‑beillesztéses példán keresztül mutatjuk be, hogyan használjuk az IWarningCallback‑t a betűkészlet‑helyettesítési figyelmeztetések elkapására, miért fontos ez, és mit tegyünk, miután rögzítettük őket.

Ha már nyitottál már dokumentumot, és összezavart szöveget láttál, mert egy egyedi betűkészlet nem volt telepítve, akkor ismered a frusztrációt. A tutorial végére egy megbízható módszert kapsz arra, hogy ezeket a problémákat programozottan felderítsd, naplózd, vagy akár automatikusan alkalmazz egy tartalék betűkészletet.

## Mit fogsz megtanulni

- Az **IWarningCallback** célja és mikor kell használni.  
- Hogyan valósítsunk meg egy egyedi figyelmeztető gyűjtőt, amely izolálja a **detect missing fonts** eseményeket.  
- A gyűjtő bekötése a **LoadOptions**‑ba, hogy minden dokumentum betöltése figyelve legyen.  
- A kimenet ellenőrzése és a szélsőséges esetek kezelése (több hiányzó betűkészlet, csendes figyelmeztetések stb.).  

### Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.6+ esetén is működik).  
- Aspose.Words for .NET telepítve NuGet‑en keresztül (`Install-Package Aspose.Words`).  
- Egy DOCX fájl, amely egy a gépen nem létező betűkészletre hivatkozik (pl. `DocumentWithMissingFont.docx`).  

További könyvtárak nem szükségesek – minden az Aspose.Words‑ban található.

---

## Hogyan használjuk az IWarningCallback‑t a hiányzó betűkészletek észlelésére az Aspose.Words‑ban

Az alábbi **teljes, futtatható program**. Másold be egy új konzolos projektbe, állítsd be a fájl útvonalát, és futtasd. A konzolon minden hiányzó betűkészlet figyelmeztetést láthatsz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Várható kimenet

Ha a `DocumentWithMissingFont.docx` egy *„MyFancyFont”* nevű betűkészletre hivatkozik, amely nincs telepítve, a következőhöz hasonló kimenetet kapsz:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Minden **[Missing Font]** előtaggal ellátott sor az **IWarningCallback** megvalósításunk által generált, bizonyítva, hogy sikeresen **detect missing fonts**.

---

## 1. lépés: Az IWarningCallback interfész megvalósítása

Miért van szükség egy egyedi osztályra? Az Aspose.Words különféle okokból **figyelmeztetéseket** dob – fájlformátum‑problémák, elavult funkciók, és legfontosabb számunkra a betűkészlet‑helyettesítés. Az `IWarningCallback` megvalósításával egy horgot kapunk, amely minden figyelmeztetést megkap a keletkezésekor. A `WarningType.FontSubstitution` szűrése izolálja azt a konkrét esetet, amikor egy betűkészlet hiányzik.

**Pro tipp:** Ha *minden* figyelmeztetést szeretnél rögzíteni diagnosztikához, egyszerűen távolítsd el az `if` ellenőrzést, és naplózd minden `info.Type` értéket.

---

## 2. lépés: A callback bekötése a LoadOptions‑ba

A `LoadOptions` az a kapu, amely megmondja az Aspose.Words‑nak, hogyan kezelje a bejövő dokumentumot. A `WarningCallback` beállítása a gyűjtőnk egy példányára biztosítja, hogy a callback a teljes betöltési művelet alatt aktív legyen. Ugyanazt a `LoadOptions` objektumot újra‑felhasználhatod több dokumentumhoz, ami hasznos kötegelt feldolgozási csővezetékekben.

**Gyakori kérdés:** *Mi van, ha LoadOptions nélkül töltök be egy dokumentumot?*  
Válasz: Az Aspose.Words továbbra is belsőleg dob figyelmeztetéseket, de callback nélkül ezek csendben elvésznek, és elveszíted a lehetőséget a **detect missing fonts** elvégzésére.

---

## 3. lépés: Dokumentum betöltése és a hiányzó betűkészlet‑figyelmeztetések rögzítése

A `Document` konstruktor, amely fájlútvonalat és `LoadOptions`‑t kap, elvégzi a nehéz munkát. Ahogy a fájlt feldolgozza, minden hiányzó betűkészlet aktiválja a `FontWarningCollector.Warning` metódusunkat. A konzol kimenete bizonyítja, hogy a mechanizmus működik.

**Szélsőséges eset:** Egy dokumentum több hiányzó betűkészletre is hivatkozhat. A callback minden hiányzó betűkészlethez egyszer lefut, így több sor jelenik meg – tökéletes egy átfogó jelentés összeállításához.

---

## Miért használjuk az IWarningCallback‑t a manuális betűkészlet‑ellenőrzés helyett?

Manuálisan bejárhatnád a dokumentum `Run.Font` tulajdonságait a betöltés után, de ez csak akkor működik, ha a dokumentum sikeresen betöltődik – ami akkor nem sikerül, ha a betűkészlet teljesen hiányzik. A figyelmeztetési rendszer **mielőtt** bármilyen helyettesítés megtörténik, pontos képet ad a hiányzó elemekről.

Ezen felül a callback a betöltési csővezeték részeként fut, ami lehetővé teszi a korai megszakítást, a betűkészletek helyettesítését menet közben, vagy részletes diagnosztika naplózását anélkül, hogy további átfutásra lenne szükség a dokumentumfán.

---

## Több hiányzó betűkészlet kezelése elegánsan

Ha sok hiányzó betűkészletre számítasz, érdemes őket egy gyűjteménybe összegyűjteni:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Betöltés után iterálhatsz a `MissingFonts`-en, és például CSV‑fájlba írhatod a tervezőcsapat számára.

---

## Bónusz: Figyelmeztetések naplózása fájlba

A konzol kimenet rendben van demókhoz, de a production kódban általában tartós tárolóba naplózunk. Cseréld le a `Console.WriteLine` hívást valami ilyesmire:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Így egy audit naplóval rendelkezel, amely később áttekinthető, és megfelel a megfelelőségi követelményeknek.

---

## Összegzés

Áttekintettük, **hogyan használjuk az IWarningCallback‑t** a **hiányzó betűkészletek** észlelésére az Aspose.Words‑ban, a callback megvalósításától a `LoadOptions`‑ba való bekötésig, valamint a kapott figyelmeztetések kezeléséig. Ez a megközelítés valós idejű betekintést nyújt a betűkészlet‑problémákba, lehetővé téve a naplózást, helyettesítést vagy felhasználói értesítést a dokumentum renderelése előtt.

Következő lépések, amelyeket érdemes felfedezni:

- **Fallback betűkészletek:** programozottan állíts be alapértelmezett betűt, amikor helyettesítés történik.  
- **Kötegelt feldolgozás:** egy mappában lévő dokumentumok ciklikus feldolgozása, ugyanazzal az `AggregatingFontCollector`‑rel.  
- **Felhasználói visszajelzés:** a hiányzó betűkészlet‑figyelmeztetések megjelenítése UI‑ban a konzol helyett.

Próbáld ki a saját projektedben – többé nem lesznek rejtélyes, összezavart szövegek, csak tiszta, cselekvőképes diagnosztika. Boldog kódolást!


## Mit érdemes még tanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek további API‑funkciók elsajátításában és alternatív megvalósítási megközelítések felfedezésében a saját projektjeidben.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}