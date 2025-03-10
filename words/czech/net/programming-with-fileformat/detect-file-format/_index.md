---
title: Rozpoznat formát souboru dokumentu
linktitle: Rozpoznat formát souboru dokumentu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak detekovat formáty souborů dokumentů pomocí Aspose.Words for .NET, pomocí tohoto komplexního průvodce krok za krokem.
weight: 10
url: /cs/net/programming-with-fileformat/detect-file-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rozpoznat formát souboru dokumentu

## Zavedení

V dnešním digitálním světě je efektivní správa různých formátů dokumentů zásadní. Ať už pracujete s formáty Word, PDF, HTML nebo jinými formáty, schopnost správně detekovat a zpracovat tyto soubory vám může ušetřit spoustu času a úsilí. V tomto tutoriálu prozkoumáme, jak zjistit formáty souborů dokumentů pomocí Aspose.Words for .NET. Tento průvodce vás provede vším, co potřebujete vědět, od předpokladů až po podrobného průvodce krok za krokem.

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words for .NET: Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/) . Ujistěte se, že máte platnou licenci. Pokud ne, můžete získat a[dočasná licence](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Jakákoli nejnovější verze bude fungovat dobře.
- .NET Framework: Ujistěte se, že máte nainstalovanou správnou verzi.

## Importovat jmenné prostory

Chcete-li začít, budete muset do projektu importovat potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Rozdělme si příklad do několika kroků, aby bylo snazší ho následovat.

## Krok 1: Nastavení adresářů

Nejprve musíme nastavit adresáře, kde budou soubory seřazeny podle jejich formátu.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Vytvořte adresáře, pokud ještě neexistují.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Krok 2: Získejte seznam souborů

Dále získáme seznam souborů z adresáře, kromě poškozených dokumentů.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Krok 3: Zjistěte formáty souborů

Nyní iterujeme každý soubor a zjistíme jeho formát pomocí Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Zobrazte typ dokumentu
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

## Závěr

Detekce formátů souborů dokumentů pomocí Aspose.Words for .NET je jednoduchý proces. Nastavením adresářů, získáním seznamu souborů a využitím Aspose.Words k detekci formátů souborů můžete efektivně organizovat a spravovat své dokumenty. Tento přístup nejen šetří čas, ale také zajišťuje správné zacházení s různými formáty dokumentů.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro programovou práci s dokumenty Wordu. Umožňuje vývojářům vytvářet, upravovat a převádět dokumenty v různých formátech.

### Dokáže Aspose.Words detekovat šifrované dokumenty?
Ano, Aspose.Words dokáže zjistit, zda je dokument zašifrován, a podle toho s takovými dokumenty můžete zacházet.

### Jaké formáty může Aspose.Words detekovat?
Aspose.Words dokáže detekovat širokou škálu formátů včetně DOC, DOCX, RTF, HTML, MHTML, ODT a mnoha dalších.

### Jak mohu získat dočasnou licenci pro Aspose.Words?
 Dočasnou licenci můžete získat od[Aspose Nákup](https://purchase.aspose.com/temporary-license/) strana.

### Kde najdu dokumentaci k Aspose.Words?
 Dokumentaci pro Aspose.Words lze nalézt[zde](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
