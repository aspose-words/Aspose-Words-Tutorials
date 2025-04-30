---
"description": "Naučte se, jak detekovat formáty souborů dokumentů pomocí Aspose.Words pro .NET s tímto komplexním návodem krok za krokem."
"linktitle": "Rozpoznat formát souboru dokumentu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Rozpoznat formát souboru dokumentu"
"url": "/cs/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rozpoznat formát souboru dokumentu

## Zavedení

V dnešním digitálním světě je efektivní správa různých formátů dokumentů klíčová. Ať už pracujete s Wordem, PDF, HTML nebo jinými formáty, schopnost správně detekovat a zpracovávat tyto soubory vám může ušetřit spoustu času a úsilí. V tomto tutoriálu se podíváme na to, jak detekovat formáty souborů dokumentů pomocí Aspose.Words pro .NET. Tato příručka vás provede vším, co potřebujete vědět, od předpokladů až po podrobný návod krok za krokem.

## Předpoklady

Než se pustíme do kódu, ujistěme se, že máte vše potřebné:

- Aspose.Words pro .NET: Můžete si jej stáhnout z [zde](https://releases.aspose.com/words/net/)Ujistěte se, že máte platný řidičský průkaz. Pokud ne, můžete si ho nechat [dočasná licence](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Jakákoli novější verze bude fungovat dobře.
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

Rozdělme si příklad do několika kroků, aby se dal lépe pochopit.

## Krok 1: Nastavení adresářů

Nejprve musíme nastavit adresáře, kde budou soubory seřazeny podle jejich formátu.

```csharp
// Cesta k adresáři s dokumenty.
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

Dále získáme seznam souborů z adresáře, s výjimkou poškozených dokumentů.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Krok 3: Detekce formátů souborů

Nyní projdeme každý soubor a pomocí Aspose.Words zjistíme jeho formát.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Zobrazit typ dokumentu
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

Detekce formátů souborů dokumentů pomocí Aspose.Words pro .NET je jednoduchý proces. Nastavením adresářů, získáním seznamu souborů a využitím Aspose.Words k detekci formátů souborů můžete efektivně organizovat a spravovat své dokumenty. Tento přístup nejen šetří čas, ale také zajišťuje správnou práci s různými formáty dokumentů.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro programovou práci s dokumenty Wordu. Umožňuje vývojářům vytvářet, upravovat a převádět dokumenty v různých formátech.

### Dokáže Aspose.Words detekovat šifrované dokumenty?
Ano, Aspose.Words dokáže zjistit, zda je dokument zašifrovaný, a vy s takovými dokumenty můžete odpovídajícím způsobem zacházet.

### Jaké formáty dokáže Aspose.Words detekovat?
Aspose.Words dokáže detekovat širokou škálu formátů včetně DOC, DOCX, RTF, HTML, MHTML, ODT a mnoha dalších.

### Jak mohu získat dočasnou licenci pro Aspose.Words?
Dočasné povolení můžete získat od [Nákup Aspose](https://purchase.aspose.com/temporary-license/) strana.

### Kde najdu dokumentaci k Aspose.Words?
Dokumentaci k Aspose.Words naleznete [zde](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}