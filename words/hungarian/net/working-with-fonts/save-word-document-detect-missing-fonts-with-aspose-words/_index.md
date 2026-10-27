---
category: general
date: 2026-03-22
description: Word-dokumentum mentése és hiányzó betűtípusok észlelése az Aspose.Words
  segítségével. Tanulja meg, hogyan követheti nyomon a hiányzó betűtípusokat és rögzítheti
  a betűtípus‑hibákat C#‑ban.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: hu
og_description: Word-dokumentum mentése és hiányzó betűtípusok felderítése C#-ban.
  Ez az útmutató bemutatja, hogyan követhetők nyomon a hiányzó betűtípusok, és hogyan
  lehet a betűtípus hibákat figyelmeztető visszahívással elkapni.
og_title: Word-dokumentum mentése – Hiányzó betűtípusok felismerése az Aspose.Words
  segítségével
tags:
- Aspose.Words
- C#
- Document Processing
title: Word-dokumentum mentése – Hiányzó betűtípusok felismerése az Aspose.Words segítségével
url: /hu/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum mentése – Hiányzó betűkészletek észlelése az Aspose.Words segítségével

Valaha szükséged volt **save word document**-ra, de nem voltál biztos benne, hogy a benne lévő betűkészletek túlélnek‑e a körutazást? Gyakrabban fordul elő, mint gondolnád, különösen, amikor a dokumentumok különböző betűkészlet‑könyvtárakkal rendelkező gépek között utaznak. A jó hír? Az Aspose.Words beépített módot biztosít a **detect missing fonts** elvégzésére, miközben **save word document**-ot hajtasz végre, így naplózhatod, figyelmeztetheted vagy akár helyettesítheted is őket, mielőtt a fájl a felhasználó képernyőjére kerül.

Ebben az útmutatóban egy teljes, azonnal futtatható példán keresztül vezetünk végig, amely nem csak egy Word dokumentumot ment, hanem **tracks missing fonts** és **captures font errors** is egy egyéni figyelmeztető kezelővel. A végére pontosan tudni fogod, miért fontos a figyelmeztető visszahívás, hogyan kell csatlakoztatni, és milyen lesz a konzol kimenete, amikor helyettesítés történik. Nincs felesleges töltelék – csak a kód, amelyet most beilleszthetsz egy .NET projektbe.

> **Előfeltételek**  
> • .NET 6 (vagy bármely friss .NET Framework) telepítve  
> • Visual Studio 2022 vagy a kedvenc IDE-d  
> • Egy licencelt példány a **Aspose.Words for .NET**-ből (az ingyenes próba verzió teszteléshez is működik)  

Ha ezek megvannak, kezdjünk bele.

---

## Word dokumentum mentése és a hiányzó betűkészletek észlelése

Az alapötlet egyszerű: mielőtt meghívod a `Document.Save`-t, rendelj egy olyan objektumot, amely implementálja az `IWarningCallback`-et a `Document.WarningCallback`-hez. Az Aspose.Words minden figyelmeztetésnél meghívja ezt az objektumot, beleértve a **font substitution** figyelmeztetéseket is, amelyek akkor fordulnak elő, amikor a forrásdokumentum egy olyan betűkészletet hivatkozik, amelyet a rendszered nem talál.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**What you’ll see:**  
Nyisd meg a `input.docx`-et, ha egy nem telepített betűkészletet hivatkozik, a konzol valami ilyesmit ír ki:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Ez a sor pontosan megmondja, melyik betűkészlet hiányzott, és mit használt helyette az Aspose.Words – tökéletes a **capturing font errors** elvégzéséhez, mielőtt a fájlt kiszállítanád.

---

## Hiányzó betűkészletek nyomon követése figyelmeztető visszahívással (lépésről‑lépésre)

### 1️⃣ Aspose.Words telepítése

Nyisd meg a projekt NuGet konzolját, és futtasd:

```bash
dotnet add package Aspose.Words
```

Ez letölti a legújabb stabil verziót (jelenleg 24.10). A könyvtár naprakészen tartása biztosítja, hogy megkapd a legújabb **detect missing fonts** funkciókat és a hibajavításokat.

### 2️⃣ A figyelmeztető kezelő definiálása

Miért van szükség egy külön osztályra? Az `IWarningCallback` implementálása lehetővé teszi, hogy az összes figyelmeztetési logikát egy helyen központosítsd. Ezen felül naplózhatsz egy fájlba, küldhetsz telemetriát, vagy dobhatod a kivételt, ha egy hiányzó betűkészlet kritikus hiba a munkafolyamatodban.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro tip:** Ha több dokumentumon is **track missing fonts**-ra van szükséged, tárold az üzeneteket egy `List<string>`-ben a kezelőben, és később tedd elérhetővé jelentéshez.

### 3️⃣ A forrásdokumentum betöltése

A `Document` konstruktor elfogadhat fájlútvonalat, streamet vagy akár nyers bájtokat is. A legtöbb esetben egy `.docx` fájlra mutatsz, amelyet egy felhasználótól vagy egy másik rendszertől kaptál.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Ha a fájl nagy, fontold meg a `LoadOptions` használatát a lusta betöltés engedélyezéséhez, ami csökkenti a memória terhelését.

### 4️⃣ A visszahívás csatolása

Rendeld hozzá az példányt a `doc.WarningCallback`-hez. Ettől a ponttól minden figyelmeztetés (beleértve a betűkészlet helyettesítéseket) át fog menni a kezelőn.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ A dokumentum mentése

Most már biztonságosan meghívhatod a `Save`-et. A figyelmeztető kezelő **szinkron módon** fut a mentési művelet során, így a kimenetet azonnal látni fogod.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Ha inkább más formátumba (PDF, HTML stb.) szeretnéd menteni, ugyanaz a figyelmeztetési mechanizmus működik – az Aspose.Words továbbra is jelzi a hiányzó betűkészleteket a konverzió előtt.

---

## Betűkészlet hibák rögzítése – Gyakori szélhelyzetek

Miközben az alapfolyamat a legtöbb esetet lefedi, a valós projektek gyakran ütköznek néhány akadályba. Az alábbiakban néhány változatot mutatunk, amelyekkel találkozhatsz, és hogyan kezeld őket.

### Hiányzó betűkészlet a fejlécben/láblécben

A fejlécek és láblécek különálló csomópontok, de a figyelmeztető rendszer ugyanúgy kezeli őket, mint a törzsszöveget. Nem szükséges extra kód; a visszahívás ezekre a betűkészletekre is lefut. Csak győződj meg róla, hogy a teljes dokumentumot töltöd be (az alapértelmezett viselkedés ezt teszi).

### Több helyettesítés egy dokumentumban

Ha egy dokumentum több ismeretlen betűkészletet használ, a kezelő minden helyettesítésnél egyszer meghívásra kerül. A konzol túlterhelésének elkerülése érdekében deduplikálhatod az üzeneteket:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Figyelmeztetések kivétellé alakítása

Néha egy hiányzó betűkészlet döntő hiba. Dobj kivételt a kezelőben a mentés megszakításához:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Ne felejtsd el a `doc.Save`-t egy `try/catch` blokkba helyezni, hogy a kivételt elegánsan kezeld.

---

## Az eredmény ellenőrzése – Mit várhatsz

A mentés befejezése után nyisd meg az `output.docx`-et a Microsoft Wordben (vagy bármely kompatibilis megjelenítőben). Ugyanazt a vizuális elrendezést kell látnod, mint az eredeti, de a helyettesített betűkészletek a konzolban megfigyelt tartalékként fognak megjelenni. A duplán ellenőrzéshez a következőket teheted:

1. Nyisd meg a **File → Options → Advanced → Show document content → Use draft quality** menüt – ez arra kényszeríti a Wordet, hogy felfedje a rejtett betűkészlet helyettesítéseket.
2. Használd a Word **Replace Fonts** párbeszédablakát (`Ctrl+Shift+F`), hogy lásd, mely betűkészletek vannak ténylegesen beágyazva.

Ha minden egyezik, akkor sikeresen **saved word document**-ot hajtottál végre, miközben **detecting missing fonts** és **capturing font errors**-t is végrehajtottál. 🎉

---

## Teljes működő példa (másolás‑beillesztés kész)

Az alábbiakban az egész program látható, amelyet beilleszthetsz egy új Console App projektbe. Csak cseréld le a `YOUR_DIRECTORY`-t a gépeden lévő tényleges mappára.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Várható konzol kimenet** (példa):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Ez a teljes történet – nincs rejtett lépés, nincs külső dokumentum, amit keresned kell.

---

## Összegzés

Most bemutattuk, hogyan **save word document**-ot hajthatsz végre, miközben aktívan **detect missing fonts**, **track missing fonts**, és **capture font errors**-t használsz az Aspose.Words figyelmeztető visszahívásával. Egy kis `IWarningCallback` implementáció bekötésével teljes láthatóságot kapsz a betűkészlet helyettesítésekre a mentés időpontjában, lehetővé téve a naplózást, helyettesítést vagy megszakítást szükség szerint.  

Készen állsz a következő kihívásra? Próbáld meg kibővíteni a kezelőt, hogy a figyelmeztetéseket strukturált JSON naplóba írja, vagy kombináld az Aspose.PDF-vel, hogy ugyanazt a dokumentumot konvertáld, miközben megőrzöd a betűkészlet információkat. Továbbá felfedezheted a hiányzó betűkészletek közvetlen beágyazását a kimeneti fájlba – az Aspose.Words támogatja a betűkészlet beágyazást a `LoadOptions.FontSettings` segítségével.  

Próbáld ki, finomítsd a kódot a saját folyamatodhoz, és tudasd velünk, hogyan működik nálad. Boldog kódolást!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}