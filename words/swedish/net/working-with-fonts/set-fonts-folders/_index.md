---
"description": "Lär dig hur du ställer in anpassade teckensnittsmappar i Aspose.Words för .NET med den här omfattande steg-för-steg-guiden. Perfekt för utvecklare som vill förbättra dokumentteckensnitt."
"linktitle": "Ställ in teckensnittsmappar"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ställ in teckensnittsmappar"
"url": "/sv/net/working-with-fonts/set-fonts-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in teckensnittsmappar

## Introduktion

Hej där! Är du redo att dyka in i världen av anpassade typsnitt i Aspose.Words för .NET? Nu sätter vi igång. Den här handledningen guidar dig genom processen att ställa in mappar för anpassade typsnitt, vilket säkerställer att dina dokument ser ut precis som du vill. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här guiden att guida dig genom varje steg. Så, låt oss få dessa typsnitt att se fantastiska ut!

## Förkunskapskrav

Innan vi sätter igång, låt oss se till att du har allt du behöver:

- Aspose.Words för .NET: Du kan [ladda ner](https://releases.aspose.com/words/net/) det om du inte redan har gjort det.
- Visual Studio: Alla versioner fungerar, men den senaste är alltid bäst.
- Ett dokument: Vi kommer att använda ett Word-dokument för den här handledningen. Du kan skapa ett eget eller använda ett befintligt.
- Anpassade teckensnitt: Ha några anpassade teckensnitt redo. Vi kommer att använda dessa för att demonstrera hur man ställer in teckensnittsmappar.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna. Detta är viktigt för att komma åt de klasser och metoder vi behöver från Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Med dessa namnrymder importerade är vi redo att börja konfigurera våra anpassade teckensnittsmappar.

## Steg 1: Definiera din dokumentkatalog

Låt oss börja med att definiera sökvägen till din dokumentkatalog. Det är här ditt Word-dokument lagras. Vi kommer att använda en variabel som heter `dataDir` för att lagra den här sökvägen.

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din katalog. Detta är avgörande eftersom Aspose.Words behöver veta var ditt dokument finns.

## Steg 2: Ställ in teckensnittskällor

Nästa steg är att konfigurera typsnittskällorna. Det är här vi anger för Aspose.Words var våra anpassade typsnitt finns. Vi kommer att använda `FontSettings.DefaultInstance.SetFontsSources` metod för att uppnå detta.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Här är vad vi gör:

- SystemFontSource: Detta anger att Aspose.Words ska använda systemets standardteckensnitt.
- FolderFontSource: Det är här vi anger mappen som innehåller våra anpassade teckensnitt. Ersätt `"C:\\MyFonts\\"` med sökvägen till din katalog för anpassade teckensnitt. `true` parametern anger att underkataloger också ska inkluderas.

## Steg 3: Ladda ditt dokument

Nu när vi har konfigurerat våra teckensnittskällor är det dags att ladda dokumentet vi vill arbeta med. Vi kommer att använda `Document` klass från Aspose. Ord för detta.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Se till att `"Rendering.docx"` är namnet på ditt Word-dokument. Om ditt dokument har ett annat namn, se till att uppdatera detta därefter.

## Steg 4: Spara ditt dokument som PDF

Slutligen, låt oss spara vårt dokument som en PDF för att se de anpassade teckensnitten i aktion. Vi kommer att använda `Save` metod för `Document` klass.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Detta sparar ditt dokument som en PDF i den angivna katalogen med hjälp av de anpassade teckensnitt som vi konfigurerade tidigare.

## Slutsats

Och där har du det! Du har konfigurerat anpassade teckensnittsmappar i Aspose.Words för .NET och sparat ditt dokument som en PDF med dessa anpassade teckensnitt. Ganska coolt, eller hur? Att anpassa teckensnitt kan göra en enorm skillnad i utseendet på dina dokument, och nu vet du exakt hur du gör det. Lycka till med kodningen!

## Vanliga frågor

### Hur installerar jag Aspose.Words för .NET?

Du kan [ladda ner](https://releases.aspose.com/words/net/) den senaste versionen av Aspose.Words för .NET från webbplatsen.

### Kan jag använda flera mappar för anpassade teckensnitt?

Ja, du kan lägga till flera `FolderFontSource` instanser till `SetFontsSources` metod för att använda teckensnitt från olika kataloger.

### Är det nödvändigt att inkludera systemfonter?

Att inkludera systemteckensnitt är valfritt men rekommenderas för att säkerställa att alla standardteckensnitt är tillgängliga.

### Vilka filtyper stöds av Aspose.Words?

Aspose.Words stöder ett brett utbud av filformat, inklusive DOCX, DOC, PDF, TXT, HTML och många fler.

### Hur kan jag få en tillfällig licens för Aspose.Words?

Du kan få en [tillfällig licens](https://purchase.aspose.com/temporary-license/) från Asposes webbplats för att testa alla funktioner i Aspose.Words.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}