---
"description": "Lär dig hur du hanterar kryssrutor i Word-dokument med Aspose.Words för .NET. Den här guiden beskriver hur du konfigurerar, uppdaterar och sparar kryssrutor programmatiskt."
"linktitle": "Kryssrutans nuvarande tillstånd"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Kryssrutans nuvarande tillstånd"
"url": "/sv/net/programming-with-sdt/current-state-of-check-box/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kryssrutans nuvarande tillstånd

## Introduktion

I den här handledningen går vi igenom processen att arbeta med kryssrutor i Word-dokument. Vi går igenom hur man öppnar en kryssruta, avgör dess status och uppdaterar den därefter. Oavsett om du utvecklar ett formulär som behöver kryssrutor eller automatiserar dokumentändringar, kommer den här guiden att ge dig en solid grund.

## Förkunskapskrav

Innan vi går in i handledningen, se till att du har följande förkunskaper:

1. Aspose.Words för .NET-biblioteket: Se till att du har Aspose.Words-biblioteket installerat. Om du inte redan har gjort det kan du ladda ner det från [Aspose webbplats](https://releases.aspose.com/words/net/).

2. Visual Studio: En .NET-utvecklingsmiljö som Visual Studio kommer att vara nödvändig för att kompilera och köra din kod.

3. Grundläggande kunskaper i C#: Bekantskap med C#-programmering hjälper dig att förstå och följa de exempel som ges.

4. Word-dokument med kryssrutor: För den här handledningen behöver du ett Word-dokument som innehåller fält för kryssrutor. Vi använder det här dokumentet för att visa hur man manipulerar kryssrutor programmatiskt.

## Importera namnrymder

För att komma igång med Aspose.Words för .NET måste du importera de nödvändiga namnrymderna. I början av din C#-fil, inkludera följande använddirektiv:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Dessa namnrymder låter dig komma åt och arbeta med Aspose.Words API och hantera strukturerade dokumenttaggar, inklusive kryssrutor.

## Steg 1: Konfigurera dokumentsökvägen

Först måste du ange sökvägen till ditt Word-dokument. Det är här Aspose.Words letar efter filen för att utföra operationer. Ersätt `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där ditt dokument är lagrat.

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda dokumentet

Ladda sedan Word-dokumentet in i en instans av `Document` klass. Den här klassen representerar ditt Word-dokument i kod och tillhandahåller olika metoder för att manipulera det.

```csharp
Document doc = new Document(dataDir + "Structured document tags.docx");
```

Här, `"Structured document tags.docx"` ska ersättas med namnet på din Word-fil.

## Steg 3: Åtkomst till kryssruteformulärfältet

För att komma åt en specifik kryssruta måste du hämta den från dokumentet. Aspose.Words behandlar kryssrutor som strukturerade dokumenttaggar. Följande kod hämtar den första strukturerade dokumenttaggen i dokumentet och kontrollerar om det är en kryssruta.

```csharp
// Hämta den första innehållskontrollen från dokumentet.
StructuredDocumentTag sdtCheckBox =
    (StructuredDocumentTag) doc.GetChild(NodeType.StructuredDocumentTag, 0, true);
```

## Steg 4: Kontrollera och uppdatera kryssrutans status

När du väl har `StructuredDocumentTag` till exempel kan du kontrollera dess typ och uppdatera dess tillstånd. I det här exemplet anges kryssrutan som markerad om det verkligen är en kryssruta.

```csharp
if (sdtCheckBox.SdtType == SdtType.Checkbox)
    sdtCheckBox.Checked = true;
```

## Steg 5: Spara dokumentet

Slutligen, spara det ändrade dokumentet till en ny fil. Detta gör att du kan bevara originaldokumentet och arbeta med den uppdaterade versionen.

```csharp
doc.Save(dataDir + "WorkingWithSdt.CurrentStateOfCheckBox.docx");
```

I det här exemplet, `"WorkingWithSdt.CurrentStateOfCheckBox.docx"` är namnet på filen där det ändrade dokumentet kommer att sparas.

## Slutsats

I den här handledningen har vi gått igenom hur man manipulerar kryssrutefält i Word-dokument med hjälp av Aspose.Words för .NET. Vi utforskade hur man konfigurerar dokumentsökvägen, laddar dokumentet, öppnar kryssrutor, uppdaterar deras status och sparar ändringarna. Med dessa färdigheter kan du nu skapa mer interaktiva och dynamiska Word-dokument programmatiskt.

## Vanliga frågor

### Vilka typer av dokumentelement kan jag manipulera med Aspose.Words för .NET?
Med Aspose.Words för .NET kan du manipulera olika dokumentelement, inklusive stycken, tabeller, bilder, sidhuvuden, sidfot och strukturerade dokumenttaggar som kryssrutor.

### Hur kan jag hantera flera kryssrutor i ett dokument?
För att hantera flera kryssrutor går du igenom samlingen av strukturerade dokumenttaggar och markerar var och en för att avgöra om det är en kryssruta.

### Kan jag använda Aspose.Words för .NET för att skapa nya kryssrutor i ett Word-dokument?
Ja, du kan skapa nya kryssrutor genom att lägga till strukturerade dokumenttaggar av typen `SdtType.Checkbox` till ditt dokument.

### Är det möjligt att läsa statusen för en kryssruta från ett dokument?
Absolut. Du kan läsa statusen för en kryssruta genom att öppna `Checked` egendomen tillhörande `StructuredDocumentTag` om det är av typen `SdtType.Checkbox`.

### Hur får jag en tillfällig licens för Aspose.Words för .NET?
Du kan få en tillfällig licens från [Aspose köpsida](https://purchase.aspose.com/temporary-license/), vilket gör att du kan utvärdera bibliotekets fullständiga funktionalitet.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}