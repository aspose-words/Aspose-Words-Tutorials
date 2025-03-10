---
title: Upptäck dokumentfilformat
linktitle: Upptäck dokumentfilformat
second_title: Aspose.Words Document Processing API
description: Lär dig hur du upptäcker dokumentfilformat med Aspose.Words för .NET med denna omfattande, steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-fileformat/detect-file-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Upptäck dokumentfilformat

## Introduktion

I dagens digitala värld är det avgörande att hantera olika dokumentformat effektivt. Oavsett om du hanterar Word, PDF, HTML eller andra format, kan du spara mycket tid och ansträngning om du kan upptäcka och bearbeta dessa filer på rätt sätt. I den här självstudien kommer vi att utforska hur man upptäcker dokumentfilformat med Aspose.Words för .NET. Den här guiden går igenom allt du behöver veta, från förutsättningar till en detaljerad steg-för-steg-guide.

## Förutsättningar

Innan vi dyker in i koden, låt oss se till att du har allt du behöver:

-  Aspose.Words för .NET: Du kan ladda ner det från[här](https://releases.aspose.com/words/net/) . Se till att du har en giltig licens. Om inte kan du få en[tillfällig licens](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Alla nyare versioner fungerar bra.
- .NET Framework: Se till att du har rätt version installerad.

## Importera namnområden

För att komma igång måste du importera de nödvändiga namnrymden i ditt projekt:

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

Först måste vi sätta upp kataloger där filerna kommer att sorteras baserat på deras format.

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

## Steg 2: Hämta listan över filer

Därefter får vi en lista över filer från katalogen, exklusive eventuella korrupta dokument.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Steg 3: Upptäck filformat

Nu går vi igenom varje fil och upptäcker dess format med Aspose.Words.

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

Att upptäcka dokumentfilformat med Aspose.Words för .NET är en enkel process. Genom att ställa in dina kataloger, få din lista över filer och använda Aspose.Words för att upptäcka filformat, kan du effektivt organisera och hantera dina dokument. Detta tillvägagångssätt sparar inte bara tid utan säkerställer också att du hanterar olika dokumentformat korrekt.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att arbeta med Word-dokument programmatiskt. Det låter utvecklare skapa, ändra och konvertera dokument i olika format.

### Kan Aspose.Words upptäcka krypterade dokument?
Ja, Aspose.Words kan upptäcka om ett dokument är krypterat och du kan hantera sådana dokument därefter.

### Vilka format kan Aspose.Words upptäcka?
Aspose.Words kan upptäcka ett brett utbud av format inklusive DOC, DOCX, RTF, HTML, MHTML, ODT och många fler.

### Hur kan jag få en tillfällig licens för Aspose.Words?
 Du kan få en tillfällig licens från[Aspose köp](https://purchase.aspose.com/temporary-license/) sida.

### Var kan jag hitta dokumentationen för Aspose.Words?
 Dokumentationen för Aspose.Words finns[här](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
