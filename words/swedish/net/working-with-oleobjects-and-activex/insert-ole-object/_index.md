---
"description": "Lär dig hur du infogar OLE-objekt i Word-dokument med Aspose.Words för .NET med den här steg-för-steg-guiden. Förbättra dina dokument med inbäddat innehåll."
"linktitle": "Infoga Ole-objekt i Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Infoga Ole-objekt i Word-dokument"
"url": "/sv/net/working-with-oleobjects-and-activex/insert-ole-object/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga Ole-objekt i Word-dokument

## Introduktion

När man arbetar med Word-dokument i .NET kan det vara viktigt att integrera olika typer av data. En kraftfull funktion är möjligheten att infoga OLE-objekt (Object Linking and Embedding) i Word-dokument. OLE-objekt kan vara vilken typ av innehåll som helst, till exempel Excel-kalkylblad, PowerPoint-presentationer eller HTML-innehåll. I den här guiden går vi igenom hur man infogar ett OLE-objekt i ett Word-dokument med Aspose.Words för .NET. Nu kör vi!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET-biblioteket: Ladda ner det från [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller annan .NET-utvecklingsmiljö.
3. Grundläggande kunskaper i C#: Förtrogenhet med C#-programmering förutsätts.

## Importera namnrymder

Till att börja med, se till att du importerar de nödvändiga namnrymderna i ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Låt oss dela upp processen i hanterbara steg.

## Steg 1: Skapa ett nytt dokument

Först måste du skapa ett nytt Word-dokument. Detta kommer att fungera som behållare för vårt OLE-objekt.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga OLE-objektet

Härnäst använder du `DocumentBuilder` klassen för att infoga OLE-objektet. Här använder vi en HTML-fil som finns på "http://www.aspose.com" som exempel.

```csharp
builder.InsertOleObject("http://"www.aspose.com", "html-fil", sant, sant, null);
```

## Steg 3: Spara dokumentet

Slutligen, spara ditt dokument till en angiven sökväg. Se till att sökvägen är korrekt och tillgänglig.

```csharp
doc.Save("Path_to_your_directory/WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
```

## Slutsats

Att infoga OLE-objekt i Word-dokument med Aspose.Words för .NET är en kraftfull funktion som möjliggör inkludering av olika innehållstyper. Oavsett om det är en HTML-fil, ett Excel-kalkylblad eller annat OLE-kompatibelt innehåll, kan den här funktionen avsevärt förbättra funktionaliteten och interaktiviteten i dina Word-dokument. Genom att följa stegen som beskrivs i den här guiden kan du sömlöst integrera OLE-objekt i dina dokument, vilket gör dem mer dynamiska och engagerande.

## Vanliga frågor

### Vilka typer av OLE-objekt kan jag infoga med Aspose.Words för .NET?
Du kan infoga olika typer av OLE-objekt, inklusive HTML-filer, Excel-kalkylblad, PowerPoint-presentationer och annat OLE-kompatibelt innehåll.

### Kan jag visa OLE-objektet som en ikon istället för dess faktiska innehåll?
Ja, du kan välja att visa OLE-objektet som en ikon genom att ställa in `asIcon` parameter till `true`.

### Är det möjligt att länka OLE-objektet till dess källfil?
Ja, genom att ställa in `isLinked` parameter till `true`, kan du länka OLE-objektet till dess källfil.

### Hur kan jag anpassa ikonen som används för OLE-objektet?
Du kan tillhandahålla en anpassad ikon genom att ange en `Image` objektet som `image` parametern i `InsertOleObject` metod.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
Du kan hitta detaljerad dokumentation på [Dokumentationssida för Aspose.Words för .NET](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}