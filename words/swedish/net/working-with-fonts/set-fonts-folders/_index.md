---
title: Ställ in teckensnittsmappar
linktitle: Ställ in teckensnittsmappar
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in anpassade teckensnittsmappar i Aspose.Words för .NET med denna omfattande, steg-för-steg-guide. Perfekt för utvecklare som vill förbättra dokumentteckensnitt.
weight: 10
url: /sv/net/working-with-fonts/set-fonts-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in teckensnittsmappar

## Introduktion

Hej där! Är du redo att dyka in i världen av anpassade typsnitt i Aspose.Words för .NET? Låt oss börja. Den här handledningen guidar dig genom processen för att ställa in anpassade teckensnittsmappar, vilket säkerställer att dina dokument ser ut precis som du vill ha dem. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här guiden att leda dig genom varje steg. Så låt oss få de typsnitten att se fantastiska ut!

## Förutsättningar

Innan vi hoppar in, låt oss se till att du har allt du behöver:

-  Aspose.Words för .NET: Du kan[ladda ner](https://releases.aspose.com/words/net/) det om du inte redan har gjort det.
- Visual Studio: Alla versioner fungerar, men den senaste är alltid den bästa.
- Ett dokument: Vi kommer att använda ett Word-dokument för denna handledning. Du kan skapa din egen eller använda en befintlig.
- Anpassade teckensnitt: Ha några anpassade teckensnitt redo. Vi kommer att använda dessa för att visa hur man ställer in teckensnittsmappar.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Detta är viktigt för att komma åt de klasser och metoder vi behöver från Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Med dessa namnrymder importerade är vi redo att börja konfigurera våra anpassade teckensnittsmappar.

## Steg 1: Definiera din dokumentkatalog

 Låt oss börja med att definiera sökvägen till din dokumentkatalog. Det är här ditt Word-dokument lagras. Vi kommer att använda en variabel som heter`dataDir` för att lagra denna väg.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din katalog. Detta är avgörande eftersom Aspose.Words kommer att behöva veta var du kan hitta ditt dokument.

## Steg 2: Ställ in teckensnittskällor

 Därefter måste vi ställa in teckensnittskällorna. Det är här vi berättar för Aspose.Words var vi kan hitta våra anpassade typsnitt. Vi kommer att använda`FontSettings.DefaultInstance.SetFontsSources` metod för att uppnå detta.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Här är vad vi gör:

- SystemFontSource: Detta talar om för Aspose.Words att använda systemets standardteckensnitt.
-  FolderFontSource: Det är här vi anger mappen som innehåller våra anpassade typsnitt. Ersätta`"C:\\MyFonts\\"` med sökvägen till din anpassade teckensnittskatalog. De`true` parameter indikerar att underkataloger också ska inkluderas.

## Steg 3: Ladda ditt dokument

Nu när vi har ställt in våra teckensnittskällor är det dags att ladda dokumentet vi vill arbeta med. Vi kommer att använda`Document` klass från Aspose.Words för detta.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Se till att`"Rendering.docx"` är namnet på ditt Word-dokument. Om ditt dokument har ett annat namn, se till att uppdatera detta därefter.

## Steg 4: Spara ditt dokument som PDF

 Slutligen, låt oss spara vårt dokument som en PDF för att se de anpassade typsnitten i aktion. Vi kommer att använda`Save` metod för`Document` klass.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Detta kommer att spara ditt dokument som en PDF i den angivna katalogen, med hjälp av de anpassade teckensnitt som vi ställt in tidigare.

## Slutsats

Och där har du det! Du har framgångsrikt ställt in anpassade typsnittsmappar i Aspose.Words för .NET och sparat ditt dokument som en PDF med dessa anpassade typsnitt. Ganska coolt, eller hur? Att anpassa teckensnitt kan göra en enorm skillnad i utseendet på dina dokument, och nu vet du exakt hur du gör det. Glad kodning!

## FAQ's

### Hur installerar jag Aspose.Words för .NET?

 Du kan[ladda ner](https://releases.aspose.com/words/net/) den senaste versionen av Aspose.Words för .NET från webbplatsen.

### Kan jag använda flera anpassade teckensnittsmappar?

 Ja, du kan lägga till flera`FolderFontSource` instanser till`SetFontsSources`metod för att använda typsnitt från olika kataloger.

### Är det nödvändigt att inkludera systemteckensnitt?

Att inkludera systemteckensnitt är valfritt men rekommenderas för att säkerställa att alla standardteckensnitt är tillgängliga.

### Vilka filtyper stöds av Aspose.Words?

Aspose.Words stöder ett brett utbud av filformat, inklusive DOCX, DOC, PDF, TXT, HTML och många fler.

### Hur kan jag få en tillfällig licens för Aspose.Words?

 Du kan få en[tillfällig licens](https://purchase.aspose.com/temporary-license/) från Asposes webbplats för att prova alla funktioner i Aspose.Words.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
