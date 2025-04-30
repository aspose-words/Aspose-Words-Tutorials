---
"description": "Lär dig hur du anpassar diagramdataetiketter med Aspose.Words för .NET i en steg-för-steg-guide. Perfekt för .NET-utvecklare."
"linktitle": "Anpassa diagramdataetikett"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Anpassa diagramdataetikett"
"url": "/sv/net/programming-with-charts/chart-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Anpassa diagramdataetikett

## Introduktion

Vill du fräscha upp dina .NET-applikationer med dynamiska och anpassade dokumentbehandlingsfunktioner? Aspose.Words för .NET kan vara precis vad du behöver! I den här guiden går vi djupare in på att anpassa diagramdataetiketter med hjälp av Aspose.Words för .NET, ett kraftfullt bibliotek för att skapa, modifiera och konvertera Word-dokument. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här handledningen att guida dig genom varje steg och säkerställa att du förstår hur du använder det här verktyget effektivt.

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Visual Studio: Installera Visual Studio 2019 eller senare.
2. .NET Framework: Se till att du har .NET Framework 4.0 eller senare.
3. Aspose.Words för .NET: Ladda ner och installera Aspose.Words för .NET från [nedladdningslänk](https://releases.aspose.com/words/net/).
4. Grundläggande kunskaper i C#: Bekantskap med C#-programmering är viktigt.
5. Giltig licens: Skaffa en [tillfällig licens](https://purchase.aspose.com/temporary-license/) eller köp en från [köplänk](https://purchase.aspose.com/buy).

## Importera namnrymder

För att komma igång behöver du importera de nödvändiga namnrymderna till ditt C#-projekt. Detta steg är avgörande eftersom det säkerställer att du har tillgång till alla klasser och metoder som tillhandahålls av Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## Steg 1: Initiera dokumentet och DocumentBuilder

För att skapa och manipulera Word-dokument måste vi först initiera en instans av `Document` klass och en `DocumentBuilder` objekt.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Förklaring

- Dokument doc: Skapar en ny instans av Dokument-klassen.
- DocumentBuilder-byggaren: DocumentBuilder hjälper till att infoga innehåll i Document-objektet.

## Steg 2: Infoga ett diagram

Nästa steg är att infoga ett stapeldiagram i dokumentet med hjälp av `DocumentBuilder` objekt.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Förklaring

- Form form: Representerar diagrammet som en form i dokumentet.
- builder.InsertChart(ChartType.Bar, 432, 252): Infogar ett stapeldiagram med angivna dimensioner.

## Steg 3: Få åtkomst till diagramserien

För att anpassa dataetiketterna måste vi först komma åt serien i diagrammet.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Förklaring

- Diagramserie serie0: Hämtar den första serien i diagrammet, som vi kommer att anpassa.

## Steg 4: Anpassa dataetiketter

Dataetiketter kan anpassas för att visa olika typer av information. Vi konfigurerar etiketterna så att de visar förklaringsnyckel, serienamn och värde, medan kategorinamn och procentandel döljs.

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### Förklaring

- ChartDataLabelCollection-etiketter: Åtkomst till seriens dataetiketter.
- labels.ShowLegendKey: Visar förklaringsnyckeln.
- labels.ShowLeaderLines: Visar hänvisningslinjer för dataetiketter som är placerade långt utanför datapunkterna.
- labels.ShowCategoryName: Döljer kategorinamnet.
- labels.ShowPercentage: Döljer procentvärdet.
- labels.ShowSeriesName: Visar seriens namn.
- labels.ShowValue: Visar värdet för datapunkterna.
- labels.Separator: Anger avgränsaren för dataetiketterna.

## Steg 5: Spara dokumentet

Slutligen, spara dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Förklaring

- doc.Save: Sparar dokumentet med det angivna namnet i den angivna katalogen.

## Slutsats

Grattis! Du har framgångsrikt anpassat diagramdataetiketter med Aspose.Words för .NET. Det här biblioteket erbjuder en robust lösning för att hantera Word-dokument programmatiskt, vilket gör det enklare för utvecklare att skapa sofistikerade och dynamiska dokumentbehandlingsprogram. Dyk ner i... [dokumentation](https://reference.aspose.com/words/net/) för att utforska fler funktioner och möjligheter.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt dokumentbehandlingsbibliotek som låter utvecklare skapa, modifiera och konvertera Word-dokument programmatiskt.

### Hur installerar jag Aspose.Words för .NET?
Du kan ladda ner och installera den från [nedladdningslänk](https://releases.aspose.com/words/net/)Följ de medföljande installationsanvisningarna.

### Kan jag prova Aspose.Words för .NET gratis?
Ja, du kan få en [gratis provperiod](https://releases.aspose.com/) eller en [tillfällig licens](https://purchase.aspose.com/temporary-license/) att utvärdera produkten.

### Är Aspose.Words för .NET kompatibelt med .NET Core?
Ja, Aspose.Words för .NET är kompatibelt med .NET Core, .NET Standard och .NET Framework.

### Var kan jag få support för Aspose.Words för .NET?
Du kan besöka [supportforum](https://forum.aspose.com/c/words/8) för hjälp och stöd från Aspose-communityn och experter.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}