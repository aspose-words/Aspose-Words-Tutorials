---
title: Dokumentumfájl formátum észlelése
linktitle: Dokumentumfájl formátum észlelése
second_title: Aspose.Words Document Processing API
description: Ebből az átfogó, lépésenkénti útmutatóból megtudhatja, hogyan észlelheti a dokumentumfájl-formátumokat az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-fileformat/detect-file-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumfájl formátum észlelése

## Bevezetés

A mai digitális világban kulcsfontosságú a különböző dokumentumformátumok hatékony kezelése. Függetlenül attól, hogy Word, PDF, HTML vagy más formátumokat kezel, az ilyen fájlok helyes észlelése és feldolgozása sok időt és erőfeszítést takaríthat meg. Ebben az oktatóanyagban megvizsgáljuk, hogyan lehet felismerni a dokumentumfájl-formátumokat az Aspose.Words for .NET használatával. Ez az útmutató végigvezeti Önt mindenen, amit tudnia kell, az előfeltételektől a részletes, lépésről lépésre szóló útmutatóig.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy mindennel rendelkezik, amire szüksége van:

-  Aspose.Words for .NET: Letöltheti innen[itt](https://releases.aspose.com/words/net/) . Győződjön meg arról, hogy rendelkezik érvényes jogosítvánnyal. Ha nem, akkor kaphat a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Bármelyik legújabb verziója jól működik.
- .NET-keretrendszer: Győződjön meg arról, hogy a megfelelő verzió van telepítve.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket a projektbe:

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

## 1. lépés: Állítsa be a könyvtárakat

Először is be kell állítanunk könyvtárakat, ahol a fájlok formátumuk alapján lesznek rendezve.

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

## 2. lépés: Szerezze be a fájlok listáját

Ezután megkapjuk a fájlok listáját a könyvtárból, kizárva a sérült dokumentumokat.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## 3. lépés: Fájlformátumok észlelése

Most ismételjük végig az egyes fájlokat, és az Aspose.Words segítségével észleljük a formátumukat.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Jelenítse meg a dokumentum típusát
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

A dokumentumfájl-formátumok észlelése az Aspose.Words for .NET használatával egyszerű folyamat. A könyvtárak beállításával, a fájlok listájának lekérésével és az Aspose.Words használatával a fájlformátumok észlelésére hatékonyan rendszerezheti és kezelheti dokumentumait. Ez a megközelítés nemcsak időt takarít meg, hanem biztosítja a különböző dokumentumformátumok megfelelő kezelését is.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár Word-dokumentumokkal való programozott munkavégzéshez. Lehetővé teszi a fejlesztők számára a különböző formátumú dokumentumok létrehozását, módosítását és konvertálását.

### Az Aspose.Words képes észlelni a titkosított dokumentumokat?
Igen, az Aspose.Words képes észlelni, hogy egy dokumentum titkosítva van-e, és Ön ennek megfelelően tudja kezelni az ilyen dokumentumokat.

### Milyen formátumokat képes észlelni az Aspose.Words?
Az Aspose.Words formátumok széles skáláját képes észlelni, beleértve a DOC, DOCX, RTF, HTML, MHTML, ODT és még sok más formátumot.

### Hogyan szerezhetek ideiglenes licencet az Aspose.Words számára?
 Ideiglenes jogosítványt kaphat a[Aspose Vásárlás](https://purchase.aspose.com/temporary-license/) oldalon.

### Hol találom az Aspose.Words dokumentációját?
 Az Aspose.Words dokumentációja megtalálható[itt](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
