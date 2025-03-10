---
title: Ställ in teckensnittsmappsystem och anpassad mapp
linktitle: Ställ in teckensnittsmappsystem och anpassad mapp
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in system- och anpassade teckensnittsmappar i Word-dokument med Aspose.Words för .NET, vilket säkerställer att dina dokument visas korrekt i olika miljöer.
weight: 10
url: /sv/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in teckensnittsmappsystem och anpassad mapp

## Introduktion

Föreställ dig att du skapar ett dokument med en unik typsnittsstil, bara för att upptäcka att typsnitten inte visas korrekt på en annan maskin. Frustrerande, eller hur? Det är här konfigurering av typsnittsmappar kommer in i bilden. Med Aspose.Words för .NET kan du definiera system- och anpassade teckensnittsmappar för att säkerställa att dina dokument alltid ser ut som de är tänkta. Låt oss dyka in i hur du kan uppnå detta.

## Förutsättningar

Innan vi börjar, se till att du har följande:

-  Aspose.Words för .NET Library: Ladda ner det om du inte redan har gjort det[här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: En IDE som Visual Studio.
- Grundläggande kunskaper om C#: Bekantskap med C# hjälper dig att följa med i kodexemplen.

## Importera namnområden

Importera först de nödvändiga namnrymden i ditt projekt:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Låt oss nu dela upp processen i enkla steg.

## Steg 1: Ladda dokumentet

 Börja med att ladda ditt Word-dokument i en Aspose.Words`Document` objekt. Detta dokument kommer att vara det där du vill ställa in teckensnittsmapparna.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 2: Initiera teckensnittsinställningar

 Skapa en ny instans av`FontSettings`. Detta objekt låter dig hantera teckensnittskällor.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Steg 3: Hämta systemteckensnittskällor

Hämta standardkällorna för systemteckensnitt. På en Windows-dator inkluderar detta vanligtvis "Windows\Fonts\" katalog.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Steg 4: Lägg till en anpassad typsnittsmapp

Lägg till en anpassad mapp som innehåller dina ytterligare teckensnitt. Detta är användbart om du har specifika teckensnitt som inte är installerade i systemfontkatalogen.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Steg 5: Uppdatera teckensnittskällor

 Konvertera listan över teckensnittskällor tillbaka till en array och ställ in den till`FontSettings` objekt.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Steg 6: Tillämpa teckensnittsinställningar på dokument

 Till sist, tillämpa den konfigurerade`FontSettings` till ditt dokument och spara det i önskat format, till exempel PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Slutsats

Och där har du det! Genom att följa dessa steg kan du säkerställa att dina Word-dokument använder rätt teckensnitt, oavsett om de är systemteckensnitt eller anpassade som lagras i en specifik katalog. Denna inställning hjälper till att bibehålla integriteten hos ditt dokuments utseende i olika miljöer.

## FAQ's

### Vad händer om ett teckensnitt saknas i både system- och anpassade mappar?

Aspose.Words kommer att använda ett standardteckensnitt för att ersätta det saknade teckensnittet, vilket säkerställer att dokumentet förblir läsbart.

### Kan jag lägga till flera anpassade teckensnittsmappar?

 Ja, du kan lägga till flera anpassade teckensnittsmappar genom att upprepa processen att skapa`FolderFontSource` objekt och lägga till dem i listan över teckensnittskällor.

### Är det möjligt att använda nätverkssökvägar för anpassade teckensnittsmappar?

 Ja, du kan ange en nätverkssökväg i`FolderFontSource` konstruktör.

### Vilka filformat stöder Aspose.Words för att spara dokument?

Aspose.Words stöder olika format, inklusive DOCX, PDF, HTML och mer.

### Hur hanterar jag meddelanden om teckensnittsersättning?

 Du kan hantera meddelanden om teckensnittsersättning genom att använda`FontSettings` klass`FontSubstitutionWarning`händelse.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
