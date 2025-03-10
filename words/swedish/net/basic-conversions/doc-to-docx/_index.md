---
title: Konvertera Doc till Docx
linktitle: Konvertera Doc till Docx
second_title: Aspose.Words Document Processing API
description: Lär dig hur du konverterar DOC till DOCX med Aspose.Words för .NET. Steg-för-steg guide med kodexempel. Perfekt för utvecklare.
weight: 10
url: /sv/net/basic-conversions/doc-to-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera Doc till Docx

## Introduktion

I den här handledningen kommer vi att utforska hur man konverterar DOC-filer till DOCX-format med Aspose.Words för .NET. Aspose.Words är ett kraftfullt dokumentbehandlingsbibliotek som tillåter utvecklare att manipulera och konvertera Word-dokument programmatiskt.

## Förutsättningar

Innan vi börjar, se till att du har följande inställning:
- Visual Studio installerat på ditt system.
-  Aspose.Words för .NET installerat. Du kan ladda ner den från[här](https://releases.aspose.com/words/net/).
- Grundläggande kunskaper i programmeringsspråket C#.

## Importera namnområden

Först måste du importera de nödvändiga namnrymden i din C#-kod:
```csharp
using Aspose.Words;
```

Detta namnutrymme ger tillgång till Aspose.Words API, vilket gör att du kan arbeta med Word-dokument i din applikation.

## Steg 1: Ladda DOC-filen

Börja med att ladda DOC-filen du vill konvertera:
```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Ladda DOC-filen med Aspose.Words
Document doc = new Document(dataDir + "Document.doc");
```

## Steg 2: Spara som DOCX

Spara sedan det laddade dokumentet som DOCX-format:
```csharp
//Spara dokumentet som DOCX
doc.Save(dataDir + "ConvertedDocument.docx", SaveFormat.Docx);
```

## Steg 3: Kör koden

Kompilera och kör din applikation för att utföra konverteringsprocessen. Se till att indatafilen "Document.doc" finns i den angivna katalogen.

## Steg 4: Verifiera utdata

Kontrollera utdatakatalogen för den konverterade DOCX-filen med namnet "ConvertedDocument.docx". Du har framgångsrikt konverterat en DOC-fil till DOCX med Aspose.Words för .NET!

## Slutsats

Att konvertera DOC till DOCX programmatiskt med Aspose.Words för .NET är enkelt och effektivt. Med bara några rader kod kan du automatisera dokumentkonverteringar, vilket sparar tid och ansträngning. Oavsett om du hanterar batchkonverteringar eller integrerar dokumentbehandling i din applikation, tillhandahåller Aspose.Words robusta funktioner för att möta dina behov.

## FAQ's

### Kan Aspose.Words konvertera andra dokumentformat?
Ja, Aspose.Words stöder konvertering mellan olika format, inklusive DOC, DOCX, RTF, HTML, PDF och mer.

### Var kan jag hitta Aspose.Words-dokumentationen?
 Du kan komma åt dokumentationen[här](https://reference.aspose.com/words/net/).

### Finns det en gratis testversion tillgänglig för Aspose.Words?
 Ja, du kan få en gratis provperiod från[här](https://releases.aspose.com/).

### Hur kan jag köpa en licens för Aspose.Words?
 Du kan köpa en licens[här](https://purchase.aspose.com/buy).

### Var kan jag få support för Aspose.Words?
 För support, besök Aspose.Words[forum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
