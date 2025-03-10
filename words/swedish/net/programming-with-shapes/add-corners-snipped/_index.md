---
title: Lägg till hörn avklippta
linktitle: Lägg till hörn avklippta
second_title: Aspose.Words Document Processing API
description: Lär dig hur du lägger till en form av klippt hörn i dina Word-dokument med Aspose.Words för .NET. Denna steg-för-steg-guide säkerställer att du enkelt kan förbättra dina dokument.
weight: 10
url: /sv/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till hörn avklippta

## Introduktion

Att lägga till anpassade former till dina Word-dokument kan vara ett roligt och visuellt tilltalande sätt att lyfta fram viktig information eller lägga till lite stil till ditt innehåll. I den här handledningen kommer vi att dyka in i hur du kan infoga "Corners Snipped"-former i dina Word-dokument med Aspose.Words för .NET. Den här guiden går igenom varje steg och säkerställer att du enkelt kan lägga till dessa former och anpassa dina dokument som ett proffs.

## Förutsättningar

Innan vi går in i koden, låt oss se till att du har allt du behöver för att komma igång:

1.  Aspose.Words för .NET: Om du inte redan har gjort det, ladda ner den senaste versionen från[Aspose releaser sida](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Ställ in din utvecklingsmiljö. Visual Studio är ett populärt val, men du kan använda vilken IDE som helst som stöder .NET.
3.  Licens: Om du bara experimenterar kan du använda en[gratis provperiod](https://releases.aspose.com/) eller skaffa en[tillfällig licens](https://purchase.aspose.com/temporary-license/) för att låsa upp full funktionalitet.
4. Grundläggande förståelse för C#: Bekantskap med C#-programmering hjälper dig att följa exemplen.

## Importera namnområden

Innan vi kan börja arbeta med Aspose.Words för .NET måste vi importera de nödvändiga namnrymden. Lägg till dessa överst i din C#-fil:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Låt oss nu dela upp processen att lägga till en "Hörnklippta" form i flera steg. Följ dessa steg noga för att säkerställa att allt fungerar smidigt.

## Steg 1: Initiera Document and DocumentBuilder

 Det första vi behöver göra är att skapa ett nytt dokument och initiera ett`DocumentBuilder` objekt. Denna byggare hjälper oss att lägga till innehåll i vårt dokument.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 I det här steget har vi ställt in vårt dokument och byggverktyg. Tänk på`DocumentBuilder` som din digitala penna, redo att skriva och rita i ditt Word-dokument.

## Steg 2: Sätt in den avskurna hörnen

 Därefter kommer vi att använda`DocumentBuilder` för att infoga en "Hörn avklippta" form. Denna formtyp är fördefinierad i Aspose.Words och kan enkelt infogas med en enda kodrad.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Här anger vi formtypen och dess dimensioner (50x50). Föreställ dig att du sätter en liten, perfekt klippt hörndekal på ditt dokument. 

## Steg 3: Definiera sparaalternativ med efterlevnad

Innan vi sparar vårt dokument måste vi definiera sparalternativen för att säkerställa att vårt dokument följer specifika standarder. Vi kommer att använda`OoxmlSaveOptions` klass för detta.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

Dessa sparalternativ säkerställer att vårt dokument följer ISO/IEC 29500:2008-standarden, vilket är avgörande för kompatibilitet och dokumentets livslängd.

## Steg 4: Spara dokumentet

Slutligen sparar vi vårt dokument i den angivna katalogen med hjälp av sparaalternativen vi definierade tidigare.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

Och precis så innehåller ditt dokument nu en anpassad "Hörnklippta"-form, sparad med de nödvändiga efterlevnadsalternativen.

## Slutsats

Där har du det! Det är enkelt att lägga till anpassade former till dina Word-dokument med Aspose.Words för .NET och kan avsevärt förbättra dina dokuments visuella tilltalande. Genom att följa dessa steg kan du enkelt infoga en "Hörnklippta" form och säkerställa att ditt dokument uppfyller de krav som krävs. Glad kodning!

## FAQ's

### Kan jag anpassa storleken på formen "Hörnklippta"?
Ja, du kan justera storleken genom att ändra måtten i`InsertShape` metod.

### Är det möjligt att lägga till andra typer av former?
 Absolut! Aspose.Words stöder olika former. Ändra bara`ShapeType` till önskad form.

### Behöver jag en licens för att använda Aspose.Words?
Även om du kan använda en gratis provperiod eller tillfällig licens, krävs en fullständig licens för obegränsad användning.

### Hur kan jag styla formerna ytterligare?
Du kan använda ytterligare egenskaper och metoder som tillhandahålls av Aspose.Words för att anpassa utseendet och beteendet hos former.

### Är Aspose.Words kompatibelt med andra format?
Ja, Aspose.Words stöder flera dokumentformat inklusive DOCX, PDF, HTML och mer.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
