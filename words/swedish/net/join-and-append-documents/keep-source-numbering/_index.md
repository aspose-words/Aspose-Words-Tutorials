---
title: Behåll källnumrering
linktitle: Behåll källnumrering
second_title: Aspose.Words Document Processing API
description: Lär dig hur du importerar dokument samtidigt som du bevarar formateringen med Aspose.Words för .NET. Steg-för-steg guide med kodexempel.
weight: 10
url: /sv/net/join-and-append-documents/keep-source-numbering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Behåll källnumrering

## Introduktion

 När du arbetar med Aspose.Words för .NET kan import av dokument från en källa till en annan med bibehållen formatering hanteras effektivt med hjälp av`NodeImporter` klass. Denna handledning guidar dig genom processen steg för steg.

## Förutsättningar

Innan du börjar, se till att du har följande:
- Visual Studio installerat på din dator.
-  Aspose.Words för .NET installerat. Om inte, ladda ner den från[här](https://releases.aspose.com/words/net/).
- Grundläggande kunskaper i C# och .NET programmering.

## Importera namnområden

Inkludera först de nödvändiga namnrymden i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Steg 1: Konfigurera ditt projekt

Börja med att skapa ett nytt C#-projekt i Visual Studio och installera Aspose.Words via NuGet Package Manager.

## Steg 2: Initiera dokument
Skapa instanser av källan (`srcDoc`) och destination (`dstDoc`) dokument.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Steg 3: Konfigurera importalternativ
Ställ in importalternativ för att behålla källformateringen, inklusive numrerade stycken.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Steg 4: Importera stycken
Iterera genom stycken i källdokumentet och importera dem till måldokumentet.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Steg 5: Spara dokumentet
Spara det sammanslagna dokumentet på önskad plats.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Slutsats

 Sammanfattningsvis är det enkelt att använda Aspose.Words för .NET för att importera dokument med bibehållen formatering med`NodeImporter` klass. Den här metoden säkerställer att dina dokument behåller sitt ursprungliga utseende och struktur sömlöst.

## FAQ's

### Kan jag importera dokument med olika formateringsstilar?
 Ja, den`NodeImporter` class stöder import av dokument med olika formateringsstilar.

### Vad händer om mina dokument innehåller komplexa tabeller och bilder?
Aspose.Words för .NET hanterar komplexa strukturer som tabeller och bilder under importoperationer.

### Är Aspose.Words kompatibel med alla versioner av .NET?
Aspose.Words stöder .NET Framework och .NET Core versioner för sömlös integration.

### Hur kan jag hantera fel under dokumentimport?
Använd try-catch-block för att hantera undantag som kan inträffa under importprocessen.

### Var kan jag hitta mer detaljerad dokumentation om Aspose.Words för .NET?
 Besök[dokumentation](https://reference.aspose.com/words/net/) för omfattande guider och API-referenser.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
