---
title: Aktuellt tillstånd för kryssrutan
linktitle: Aktuellt tillstånd för kryssrutan
second_title: Aspose.Words Document Processing API
description: Lär dig hur du hanterar kryssrutor i Word-dokument med Aspose.Words för .NET. Den här guiden handlar om att ställa in, uppdatera och spara kryssrutor programmatiskt.
weight: 10
url: /sv/net/programming-with-sdt/current-state-of-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktuellt tillstånd för kryssrutan

## Introduktion

den här självstudien går vi igenom processen att arbeta med kryssrutor i Word-dokument. Vi kommer att ta upp hur du kommer åt en kryssruta, bestämmer dess tillstånd och uppdaterar den därefter. Oavsett om du utvecklar ett formulär som behöver kontrollerbara alternativ eller automatiserar dokumentändringar, kommer den här guiden att ge dig en solid grund.

## Förutsättningar

Innan vi dyker in i handledningen, se till att du har följande förutsättningar:

1.  Aspose.Words för .NET Library: Se till att du har Aspose.Words-biblioteket installerat. Om du inte har gjort det ännu kan du ladda ner det från[Aspose hemsida](https://releases.aspose.com/words/net/).

2. Visual Studio: En .NET-utvecklingsmiljö som Visual Studio kommer att vara nödvändig för att kompilera och köra din kod.

3. Grundläggande kunskaper om C#: Kännedom om C#-programmering hjälper dig att förstå och följa exemplen som ges.

4. Word-dokument med kryssrutor: För den här handledningen behöver du ett Word-dokument som innehåller kryssrutaformulär. Vi kommer att använda det här dokumentet för att visa hur man manipulerar kryssrutor programmatiskt.

## Importera namnområden

För att komma igång med Aspose.Words för .NET måste du importera de nödvändiga namnrymden. I början av din C#-fil, inkludera följande med hjälp av direktiv:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Dessa namnutrymmen låter dig komma åt och arbeta med Aspose.Words API och hantera strukturerade dokumenttaggar, inklusive kryssrutor.

## Steg 1: Konfigurera dokumentsökvägen

 Först måste du ange sökvägen till ditt Word-dokument. Det är här Aspose.Words kommer att leta efter filen för att utföra operationer. Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där ditt dokument är lagrat.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda dokumentet

 Ladda sedan in Word-dokumentet i en instans av`Document` klass. Den här klassen representerar ditt Word-dokument i kod och tillhandahåller olika metoder för att manipulera det.

```csharp
Document doc = new Document(dataDir + "Structured document tags.docx");
```

 Här,`"Structured document tags.docx"` ska ersättas med namnet på din Word-fil.

## Steg 3: Åtkomst till kryssrutans formulärfält

För att komma åt en specifik kryssruta måste du hämta den från dokumentet. Aspose.Words behandlar kryssrutor som strukturerade dokumenttaggar. Följande kod hämtar den första strukturerade dokumenttaggen i dokumentet och kontrollerar om det är en kryssruta.

```csharp
//Få den första innehållskontrollen från dokumentet.
StructuredDocumentTag sdtCheckBox =
    (StructuredDocumentTag) doc.GetChild(NodeType.StructuredDocumentTag, 0, true);
```

## Steg 4: Kontrollera och uppdatera tillståndet för kryssrutan

 När du väl har`StructuredDocumentTag` kan du kontrollera dess typ och uppdatera dess tillstånd. Det här exemplet ställer in kryssrutan till markerad om det verkligen är en kryssruta.

```csharp
if (sdtCheckBox.SdtType == SdtType.Checkbox)
    sdtCheckBox.Checked = true;
```

## Steg 5: Spara dokumentet

Slutligen, spara det ändrade dokumentet till en ny fil. Detta gör att du kan bevara originaldokumentet och arbeta med den uppdaterade versionen.

```csharp
doc.Save(dataDir + "WorkingWithSdt.CurrentStateOfCheckBox.docx");
```

 I det här exemplet,`"WorkingWithSdt.CurrentStateOfCheckBox.docx"` är namnet på filen där det ändrade dokumentet kommer att sparas.

## Slutsats

I den här handledningen har vi täckt hur man manipulerar kryssrutaformulär i Word-dokument med Aspose.Words för .NET. Vi utforskade hur man ställer in dokumentsökvägen, laddar dokumentet, kommer åt kryssrutor, uppdaterar deras tillstånd och sparar ändringarna. Med dessa färdigheter kan du nu skapa mer interaktiva och dynamiska Word-dokument programmatiskt.

## FAQ's

### Vilka typer av dokumentelement kan jag manipulera med Aspose.Words för .NET?
Aspose.Words för .NET låter dig manipulera olika dokumentelement inklusive stycken, tabeller, bilder, sidhuvuden, sidfötter och strukturerade dokumenttaggar som kryssrutor.

### Hur kan jag hantera flera kryssrutor i ett dokument?
För att hantera flera kryssrutor skulle du gå igenom samlingen av strukturerade dokumenttaggar och kontrollera var och en för att avgöra om det är en kryssruta.

### Kan jag använda Aspose.Words för .NET för att skapa nya kryssrutor i ett Word-dokument?
 Ja, du kan skapa nya kryssrutor genom att lägga till strukturerade dokumenttaggar av typen`SdtType.Checkbox` till ditt dokument.

### Är det möjligt att läsa statusen för en kryssruta från ett dokument?
 Absolut. Du kan läsa statusen för en kryssruta genom att gå till`Checked` egendom av`StructuredDocumentTag` om det är av typen`SdtType.Checkbox`.

### Hur får jag en tillfällig licens för Aspose.Words för .NET?
 Du kan få en tillfällig licens från[Aspose köpsida](https://purchase.aspose.com/temporary-license/), som låter dig utvärdera bibliotekets fulla funktionalitet.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
