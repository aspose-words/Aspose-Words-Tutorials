---
title: Få lista över tillgängliga teckensnitt
linktitle: Få lista över tillgängliga teckensnitt
second_title: Aspose.Words Document Processing API
description: Upptäck hur du får en lista över tillgängliga typsnitt med Aspose.Words för .NET i denna detaljerade steg-för-steg-handledning. Öka dina färdigheter i teckensnittshantering.
weight: 10
url: /sv/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Få lista över tillgängliga teckensnitt

## Introduktion

Har du någonsin kämpat med att hantera teckensnitt i dina Word-dokument? Om du är en .NET-utvecklare är Aspose.Words för .NET här för att rädda dig! Det här kraftfulla biblioteket hjälper dig inte bara att skapa och manipulera Word-dokument programmatiskt utan erbjuder också omfattande fonthanteringsfunktioner. I den här guiden går vi igenom en steg-för-steg handledning om hur du får en lista över tillgängliga typsnitt med Aspose.Words för .NET. Vi delar upp det i lättsmälta steg för att säkerställa att du enkelt kan följa med. Så låt oss dyka in och göra teckensnittshantering till en lek!

## Förutsättningar

Innan vi sätter igång finns det några saker du behöver:

-  Aspose.Words for .NET: Se till att du har Aspose.Words for .NET-biblioteket installerat. Du kan ladda ner den från[här](https://releases.aspose.com/words/net/).
- Visual Studio: Det här exemplet använder Visual Studio som utvecklingsmiljö.
- .NET Framework: Se till att du har .NET Framework installerat på din dator.
- Dokumentkatalog: En katalogsökväg där dina dokument lagras.

## Importera namnområden

Importera först de nödvändiga namnrymden till ditt projekt:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Steg 1: Initiera teckensnittsinställningar

Det första steget är att initiera teckensnittsinställningarna. Detta gör att du kan hantera teckensnittskällorna för dina dokument.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Denna klass används för att specificera inställningarna för teckensnittsersättning och teckensnittskällor.
- fontSources: Vi skapar en lista över befintliga teckensnittskällor från de nuvarande teckensnittsinställningarna.

## Steg 2: Definiera dokumentkatalog

Ange sedan sökvägen till din dokumentkatalog. Det är här Aspose.Words kommer att söka efter typsnitt.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: Denna strängvariabel innehåller sökvägen till katalogen där dina typsnitt finns. Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska vägen.

## Steg 3: Lägg till anpassad typsnittsmapp

Lägg nu till en ny mappkälla för att instruera Aspose.Words att söka efter teckensnitt i den här mappen.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Denna klass representerar en mappfontkälla. Den andra parametern (`true`) anger om teckensnitt ska sökas rekursivt i undermappar.

## Steg 4: Uppdatera teckensnittskällor

Lägg till mappen för anpassade teckensnitt i listan över befintliga teckensnittskällor och uppdatera teckensnittsinställningarna.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Lägger till den anpassade teckensnittsmappen till de befintliga teckensnittskällorna.
- updatedFontSources: Konverterar listan över teckensnittskällor till en array.

## Steg 5: Hämta och visa teckensnitt

Slutligen, hämta de tillgängliga typsnitten och visa deras detaljer.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Hämtar listan över tillgängliga teckensnitt från den första teckensnittskällan i den uppdaterade listan.
-  fontInfo: En instans av`PhysicalFontInfo` innehåller information om varje typsnitt.

## Slutsats

Grattis! Du har framgångsrikt hämtat en lista över tillgängliga typsnitt med Aspose.Words för .NET. Den här handledningen har gått igenom varje steg, från att initiera teckensnittsinställningar till att visa teckensnittsdetaljer. Med denna kunskap kan du nu enkelt hantera teckensnitt i dina Word-dokument. Kom ihåg att Aspose.Words för .NET är ett kraftfullt verktyg som avsevärt kan förbättra dina dokumentbehandlingsmöjligheter. Så fortsätt och utforska fler funktioner för att göra din utvecklingsprocess ännu mer effektiv.

## FAQ's

### Kan jag använda Aspose.Words för .NET med andra .NET-ramverk?
Ja, Aspose.Words för .NET är kompatibelt med olika .NET-ramverk inklusive .NET Core och .NET 5+.

### Hur installerar jag Aspose.Words för .NET?
Du kan installera det via NuGet Package Manager i Visual Studio genom att söka efter "Aspose.Words".

### Är det möjligt att lägga till flera anpassade teckensnittsmappar?
 Ja, du kan lägga till flera anpassade teckensnittsmappar genom att skapa flera`FolderFontSource` instanser och lägga till dem i listan över teckensnittskällor.

### Kan jag hämta teckensnittsdetaljer från en specifik teckensnittskälla?
 Ja, du kan hämta teckensnittsinformation från vilken typsnittskälla som helst genom att ange indexet för teckensnittskällan i`updatedFontSources` array.

### Stöder Aspose.Words for .NET teckensnittsersättning?
Ja, det stöder teckensnittsersättning för att säkerställa att texten återges korrekt även om det ursprungliga teckensnittet inte är tillgängligt.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
