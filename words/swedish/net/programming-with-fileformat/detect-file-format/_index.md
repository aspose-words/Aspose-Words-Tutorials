---
"description": "Lär dig hur du identifierar dokumentfilformat med Aspose.Words för .NET med den här omfattande steg-för-steg-guiden."
"linktitle": "Identifiera dokumentfilformat"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Identifiera dokumentfilformat"
"url": "/sv/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Identifiera dokumentfilformat

## Introduktion

I dagens digitala värld är det avgörande att hantera olika dokumentformat effektivt. Oavsett om du hanterar Word, PDF, HTML eller andra format kan det spara dig mycket tid och ansträngning att kunna identifiera och bearbeta dessa filer korrekt. I den här handledningen utforskar vi hur man identifierar dokumentfilformat med Aspose.Words för .NET. Den här guiden guidar dig genom allt du behöver veta, från förutsättningar till en detaljerad steg-för-steg-guide.

## Förkunskapskrav

Innan vi går in i koden, låt oss se till att du har allt du behöver:

- Aspose.Words för .NET: Du kan ladda ner det från [här](https://releases.aspose.com/words/net/)Se till att du har ett giltigt körkort. Om inte kan du få ett [tillfällig licens](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Alla nyare versioner fungerar bra.
- .NET Framework: Se till att du har rätt version installerad.

## Importera namnrymder

För att komma igång måste du importera de nödvändiga namnrymderna i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Låt oss dela upp exemplet i flera steg för att göra det lättare att följa.

## Steg 1: Konfigurera kataloger

Först måste vi skapa kataloger där filerna sorteras baserat på deras format.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Skapa katalogerna om de inte redan finns.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Steg 2: Hämta fillistan

Nästa steg är att få en lista över filer från katalogen, exklusive eventuella skadade dokument.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Steg 3: Identifiera filformat

Nu itererar vi igenom varje fil och identifierar dess format med hjälp av Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Visa dokumenttypen
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

## Slutsats

Att identifiera dokumentfilformat med hjälp av Aspose.Words för .NET är en enkel process. Genom att konfigurera dina kataloger, hämta din fillista och använda Aspose.Words för att identifiera filformat kan du effektivt organisera och hantera dina dokument. Denna metod sparar inte bara tid utan säkerställer också att du hanterar olika dokumentformat korrekt.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att arbeta med Word-dokument programmatiskt. Det låter utvecklare skapa, modifiera och konvertera dokument i olika format.

### Kan Aspose.Words upptäcka krypterade dokument?
Ja, Aspose.Words kan upptäcka om ett dokument är krypterat och du kan hantera sådana dokument därefter.

### Vilka format kan Aspose.Words upptäcka?
Aspose.Words kan identifiera en mängd olika format, inklusive DOC, DOCX, RTF, HTML, MHTML, ODT och många fler.

### Hur kan jag få en tillfällig licens för Aspose.Words?
Du kan få ett tillfälligt körkort från [Aspose-köp](https://purchase.aspose.com/temporary-license/) sida.

### Var kan jag hitta dokumentationen för Aspose.Words?
Dokumentationen för Aspose.Words finns här [här](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}