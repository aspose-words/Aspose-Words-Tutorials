---
"description": "Lär dig hur du uppdaterar egenskapen för den senaste sparade tiden i Word-dokument med Aspose.Words för .NET. Följ vår detaljerade steg-för-steg-guide."
"linktitle": "Uppdatera egenskapen för senast sparade tid"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Uppdatera egenskapen för senast sparade tid"
"url": "/sv/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uppdatera egenskapen för senast sparade tid

## Introduktion

Har du någonsin undrat hur du programmatiskt kan hålla reda på egenskapen för den senaste sparade tiden i dina Word-dokument? Om du arbetar med flera dokument och behöver underhålla deras metadata kan det vara ganska praktiskt att uppdatera egenskapen för den senaste sparade tiden. Idag ska jag guida dig genom den här processen med Aspose.Words för .NET. Så, spänn fast säkerhetsbältet och låt oss dyka in!

## Förkunskapskrav

Innan vi går vidare till steg-för-steg-guiden finns det några saker du behöver:

1. Aspose.Words för .NET: Se till att du har Aspose.Words för .NET installerat. Om du inte har det kan du [ladda ner den här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En utvecklingsmiljö som Visual Studio.
3. Grundläggande kunskaper i C#: Att förstå grunderna i C#-programmering kommer att vara till hjälp.

## Importera namnrymder

Till att börja med, se till att importera nödvändiga namnrymder till ditt projekt. Detta ger dig tillgång till de klasser och metoder som krävs för att manipulera Word-dokument.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Nu ska vi dela upp processen i enkla steg. Varje steg guidar dig genom processen att uppdatera den senast sparade tidsegenskapen i ditt Word-dokument.

## Steg 1: Konfigurera din dokumentkatalog

Först måste du ange sökvägen till din dokumentkatalog. Det är här ditt befintliga dokument lagras och där det uppdaterade dokumentet kommer att sparas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din katalog.

## Steg 2: Ladda ditt Word-dokument

Ladda sedan in Word-dokumentet du vill uppdatera. Du kan göra detta genom att skapa en instans av `Document` klassen och skickar sökvägen till ditt dokument.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

Se till att dokumentet med namnet `Document.docx` finns i den angivna katalogen.

## Steg 3: Konfigurera sparalternativ

Skapa nu en instans av `OoxmlSaveOptions` klass. Den här klassen låter dig ange alternativ för att spara ditt dokument i Office Open XML (OOXML)-format. Här ställer du in `UpdateLastSavedTimeProperty` till `true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Detta anger att Aspose.Words ska uppdatera egenskapen för den senaste sparade tiden i dokumentet.

## Steg 4: Spara det uppdaterade dokumentet

Slutligen, spara dokumentet med hjälp av `Save` metod för `Document` klass, och ange sökvägen där du vill spara det uppdaterade dokumentet och sparalternativen.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Detta sparar dokumentet med den uppdaterade egenskapen för senast sparade tid.

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt uppdatera egenskapen för senaste sparade tid i dina Word-dokument med hjälp av Aspose.Words för .NET. Detta är särskilt användbart för att upprätthålla korrekta metadata i dina dokument, vilket kan vara avgörande för dokumenthanteringssystem och diverse andra applikationer.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att skapa, redigera och konvertera Word-dokument i .NET-applikationer.

### Varför ska jag uppdatera egenskapen för den senast sparade tiden?
Att uppdatera egenskapen för den senast sparade tiden hjälper till att bibehålla korrekta metadata, vilket är viktigt för dokumentspårning och hantering.

### Kan jag uppdatera andra egenskaper med Aspose.Words för .NET?
Ja, Aspose.Words för .NET låter dig uppdatera olika dokumentegenskaper, till exempel titel, författare och ämne.

### Är Aspose.Words för .NET gratis?
Aspose.Words för .NET erbjuder en gratis provperiod, men för full funktionalitet krävs en licens. Du kan skaffa en licens [här](https://purchase.aspose.com/buy).

### Var kan jag hitta fler handledningar om Aspose.Words för .NET?
Du kan hitta fler handledningar och dokumentation [här](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}