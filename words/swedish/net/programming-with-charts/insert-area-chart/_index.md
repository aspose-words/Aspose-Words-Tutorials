---
"description": "Lär dig hur du infogar ett ytdiagram i ett dokument med Aspose.Words för .NET. Lägg till seriedata och spara dokumentet med diagrammet."
"linktitle": "Infoga ytdiagram i ett Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Infoga ytdiagram i ett Word-dokument"
"url": "/sv/net/programming-with-charts/insert-area-chart/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga ytdiagram i ett Word-dokument

## Introduktion

Välkommen till den här steg-för-steg-guiden om hur du infogar ett ytdiagram i ett Word-dokument med Aspose.Words för .NET. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här handledningen att guida dig genom allt du behöver veta för att skapa fantastiska och informativa ytdiagram i dina Word-dokument. Vi går igenom förutsättningarna, visar dig hur du importerar de nödvändiga namnrymderna och guidar dig genom varje steg i processen med tydliga och lättförståeliga instruktioner.

## Förkunskapskrav

Innan vi börjar, låt oss se till att du har allt du behöver för att komma igång:

1. Aspose.Words för .NET: Se till att du har Aspose.Words för .NET installerat. Du kan ladda ner det [här](https://releases.aspose.com/words/net/).
2. .NET Framework: Se till att du har .NET Framework installerat på din dator.
3. IDE: En integrerad utvecklingsmiljö (IDE) som Visual Studio för att skriva och exekvera din kod.
4. Grundläggande C#-kunskaper: Grundläggande förståelse för C#-programmering är till hjälp.

När du har dessa förutsättningar på plats är du redo att börja skapa snygga ytdiagram i dina Word-dokument.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna. Dessa namnrymder tillhandahåller de klasser och metoder som krävs för att arbeta med Word-dokument och diagram i Aspose.Words för .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

Nu när vi har importerat de viktiga namnrymderna, låt oss gå vidare till att skapa vårt dokument och infoga ett ytdiagram steg för steg.

## Steg 1: Skapa ett nytt Word-dokument

Låt oss börja med att skapa ett nytt Word-dokument. Detta blir basen där vi infogar vårt ytdiagram.

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

I det här steget initierar vi ett nytt `Document` objekt som representerar vårt Word-dokument.

## Steg 2: Använd DocumentBuilder för att infoga ett diagram

Härnäst använder vi `DocumentBuilder` klass för att infoga ett ytdiagram i vårt dokument.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

Här skapar vi en `DocumentBuilder` objektet och använd det för att infoga ett ytdiagram med specifika dimensioner (432x252) i vårt dokument.

## Steg 3: Åtkomst till diagramobjektet

Efter att vi har infogat diagrammet behöver vi komma åt `Chart` objekt för att anpassa vårt ytdiagram.

```csharp
Chart chart = shape.Chart;
```

Den här kodraden hämtar `Chart` objekt från den form vi just infogade.

## Steg 4: Lägg till seriedata i diagrammet

Nu är det dags att lägga till lite data i vårt diagram. Vi lägger till en serie med datum och motsvarande värden.

```csharp
chart.Series.Add("Aspose Series 1", new []
{
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)
}, 
new double[] { 32, 32, 28, 12, 15 });
```

I det här steget lägger vi till en serie med namnet "Aspose Series 1" med en uppsättning datum och motsvarande värden.

## Steg 5: Spara dokumentet

Slutligen sparar vi vårt dokument med det infogade ytdiagrammet.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

Den här kodraden sparar dokumentet i den angivna katalogen med det angivna filnamnet.

## Slutsats

Grattis! Du har nu infogat ett ytdiagram i ett Word-dokument med Aspose.Words för .NET. Den här guiden har tagit dig igenom varje steg, från att konfigurera din miljö till att spara det slutliga dokumentet. Med Aspose.Words för .NET kan du skapa en mängd olika diagram och andra komplexa element i dina Word-dokument, vilket gör dina rapporter och presentationer mer dynamiska och informativa.

## Vanliga frågor

### Kan jag använda Aspose.Words för .NET med andra .NET-språk?
Ja, Aspose.Words för .NET stöder andra .NET-språk som VB.NET.

### Är det möjligt att anpassa utseendet på diagrammet?
Absolut! Aspose.Words för .NET erbjuder omfattande alternativ för att anpassa utseendet på dina diagram.

### Kan jag lägga till flera diagram i ett enda Word-dokument?
Ja, du kan infoga så många diagram som du behöver i ett enda Word-dokument.

### Stöder Aspose.Words för .NET andra diagramtyper?
Ja, Aspose.Words för .NET stöder olika diagramtyper inklusive stapeldiagram, linjediagram, cirkeldiagram med mera.

### Var kan jag få en tillfällig licens för Aspose.Words för .NET?
Du kan få en tillfällig licens från [här](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}