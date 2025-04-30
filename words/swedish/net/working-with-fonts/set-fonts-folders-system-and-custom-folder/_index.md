---
"description": "Lär dig hur du ställer in system- och anpassade teckensnittsmappar i Word-dokument med Aspose.Words för .NET, så att dina dokument visas korrekt i olika miljöer."
"linktitle": "Ställ in teckensnitt, mappar, system och anpassad mapp"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ställ in teckensnitt, mappar, system och anpassad mapp"
"url": "/sv/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in teckensnitt, mappar, system och anpassad mapp

## Introduktion

Tänk dig att du skapar ett dokument med ett unikt typsnitt, bara för att upptäcka att typsnitten inte visas korrekt på en annan maskin. Frustrerande, eller hur? Det är här konfigurering av typsnittsmappar kommer in i bilden. Med Aspose.Words för .NET kan du definiera system- och anpassade typsnittsmappar för att säkerställa att dina dokument alltid ser ut som avsett. Låt oss dyka ner i hur du kan uppnå detta.

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

- Aspose.Words för .NET-biblioteket: Ladda ner det om du inte redan har gjort det. [här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: En IDE som Visual Studio.
- Grundläggande kunskaper i C#: Bekantskap med C# hjälper dig att följa kodexemplen.

## Importera namnrymder

Importera först de nödvändiga namnrymderna i ditt projekt:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nu ska vi dela upp processen i enkla steg.

## Steg 1: Ladda dokumentet

För att börja, ladda ditt Word-dokument till en Aspose.Words `Document` objekt. Det här dokumentet kommer att vara det där du vill ange teckensnittsmapparna.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 2: Initiera teckensnittsinställningar

Skapa en ny instans av `FontSettings`Det här objektet låter dig hantera teckensnittskällor.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Steg 3: Hämta systemfontkällor

Hämta standardkällorna för systemets teckensnitt. På en Windows-dator inkluderar detta vanligtvis katalogen "Windows\Fonts".

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Steg 4: Lägg till en anpassad teckensnittsmapp

Lägg till en anpassad mapp som innehåller dina ytterligare teckensnitt. Detta är användbart om du har specifika teckensnitt som inte är installerade i systemets teckensnittskatalog.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Steg 5: Uppdatera teckensnittskällor

Konvertera listan över teckensnittskällor tillbaka till en array och sätt den till `FontSettings` objekt.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Steg 6: Tillämpa teckensnittsinställningar på dokumentet

Slutligen, använd den konfigurerade `FontSettings` till ditt dokument och spara det i önskat format, till exempel PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Slutsats

Och där har du det! Genom att följa dessa steg kan du säkerställa att dina Word-dokument använder rätt teckensnitt, oavsett om det är systemteckensnitt eller anpassade teckensnitt som lagras i en specifik katalog. Den här konfigurationen hjälper till att bibehålla dokumentets utseende i olika miljöer.

## Vanliga frågor

### Vad händer om ett teckensnitt saknas i både systemmappar och anpassade mappar?

Aspose.Words kommer att använda ett standardteckensnitt för att ersätta det saknade teckensnittet, vilket säkerställer att dokumentet förblir läsbart.

### Kan jag lägga till flera mappar för anpassade teckensnitt?

Ja, du kan lägga till flera mappar med anpassade teckensnitt genom att upprepa processen att skapa `FolderFontSource` objekt och lägga till dem i listan över teckensnittskällor.

### Är det möjligt att använda nätverkssökvägar för mappar med anpassade teckensnitt?

Ja, du kan ange en nätverkssökväg i `FolderFontSource` konstruktör.

### Vilka filformat stöder Aspose.Words för att spara dokument?

Aspose.Words stöder olika format, inklusive DOCX, PDF, HTML och mer.

### Hur hanterar jag aviseringar om teckensnittsersättning?

Du kan hantera meddelanden om teckensnittsersättning genom att använda `FontSettings` klassens `FontSubstitutionWarning` händelse.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}