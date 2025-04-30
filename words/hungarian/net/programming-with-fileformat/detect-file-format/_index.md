---
"description": "Tanulja meg, hogyan ismerheti fel a dokumentumfájl-formátumokat az Aspose.Words for .NET segítségével ezzel az átfogó, lépésről lépésre haladó útmutatóval."
"linktitle": "Dokumentumfájl formátumának észlelése"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Dokumentumfájl formátumának észlelése"
"url": "/hu/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumfájl formátumának észlelése

## Bevezetés

A mai digitális világban kulcsfontosságú a különböző dokumentumformátumok hatékony kezelése. Akár Word, PDF, HTML vagy más formátumokat kezel, ezeknek a fájloknak a helyes felismerése és feldolgozása sok időt és energiát takaríthat meg. Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan lehet felismerni a dokumentumfájl-formátumokat az Aspose.Words for .NET segítségével. Ez az útmutató végigvezet mindenen, amit tudnod kell, az előfeltételektől kezdve a részletes, lépésről lépésre bemutatott útmutatóig.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjünk meg róla, hogy minden szükséges dolog megvan:

- Aspose.Words .NET-hez: Letöltheti innen: [itt](https://releases.aspose.com/words/net/)Győződjön meg róla, hogy érvényes jogosítvánnyal rendelkezik. Ha nem, akkor szerezhet egyet. [ideiglenes engedély](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Bármely újabb verzió jól fog működni.
- .NET-keretrendszer: Győződjön meg arról, hogy a megfelelő verzió van telepítve.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket a projektjébe:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Bontsuk a példát több lépésre, hogy könnyebb legyen követni.

## 1. lépés: Könyvtárak beállítása

Először is létre kell hoznunk azokat a könyvtárakat, amelyekben a fájlok formátumuk alapján rendezve lesznek.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Hozza létre a könyvtárakat, ha még nem léteznek.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## 2. lépés: Fájlok listájának lekérése

Ezután lekérjük a könyvtárban található fájlok listáját, a sérült dokumentumok kivételével.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## 3. lépés: Fájlformátumok észlelése

Most végigmegyünk az egyes fájlokon, és az Aspose.Words segítségével megállapítjuk a formátumukat.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // A dokumentum típusának megjelenítése
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Következtetés

dokumentumfájlok formátumainak felismerése az Aspose.Words for .NET segítségével egy egyszerű folyamat. A könyvtárak beállításával, a fájlok listájának lekérésével és az Aspose.Words fájlformátumok felismerésére való használatával hatékonyan rendszerezheti és kezelheti dokumentumait. Ez a megközelítés nemcsak időt takarít meg, hanem biztosítja a különböző dokumentumformátumok helyes kezelését is.

## GYIK

### Mi az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy hatékony függvénytár a Word dokumentumok programozott kezeléséhez. Lehetővé teszi a fejlesztők számára, hogy különféle formátumú dokumentumokat hozzanak létre, módosítsanak és konvertáljanak.

### Az Aspose.Words képes felismerni a titkosított dokumentumokat?
Igen, az Aspose.Words képes érzékelni, ha egy dokumentum titkosítva van, és ennek megfelelően lehet kezelni az ilyen dokumentumokat.

### Milyen formátumokat képes felismerni az Aspose.Words?
Az Aspose.Words számos formátumot képes felismerni, beleértve a DOC, DOCX, RTF, HTML, MHTML, ODT és sok mást.

### Hogyan szerezhetek ideiglenes licencet az Aspose.Words-höz?
Ideiglenes jogosítványt igényelhet a [Aspose vásárlás](https://purchase.aspose.com/temporary-license/) oldal.

### Hol találom az Aspose.Words dokumentációját?
Az Aspose.Words dokumentációja megtalálható itt: [itt](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}