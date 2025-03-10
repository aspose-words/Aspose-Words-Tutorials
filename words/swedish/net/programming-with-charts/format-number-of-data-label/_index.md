---
title: Format Antal Data Etikett I Ett Diagram
linktitle: Format Antal Data Etikett I Ett Diagram
second_title: Aspose.Words Document Processing API
description: Lär dig hur du formaterar dataetiketter i diagram med Aspose.Words för .NET med denna steg-för-steg-guide. Förbättra dina Word-dokument utan ansträngning.
weight: 10
url: /sv/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Format Antal Data Etikett I Ett Diagram

## Introduktion

Att skapa engagerande och informativa dokument innebär ofta att man inkluderar diagram med välformaterade dataetiketter. Om du är en .NET-utvecklare som vill förbättra dina Word-dokument med sofistikerade diagram, är Aspose.Words för .NET ett fantastiskt bibliotek som hjälper dig att uppnå det. Den här handledningen leder dig genom processen att formatera nummeretiketter i ett diagram med Aspose.Words för .NET, steg för steg.

## Förutsättningar

Innan du dyker in i koden finns det några förutsättningar du måste ha på plats:

-  Aspose.Words for .NET: Se till att du har Aspose.Words for .NET-biblioteket installerat. Om du inte har installerat det än kan du göra det[ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Du bör ha en .NET-utvecklingsmiljö inrättad. Visual Studio rekommenderas starkt.
- Grundläggande kunskaper om C#: Bekantskap med C#-programmering är väsentligt eftersom denna handledning involverar att skriva och förstå C#-kod.
-  Tillfällig licens: För att använda Aspose.Words utan några begränsningar kan du få en[tillfällig licens](https://purchase.aspose.com/temporary-license/).

Låt oss nu dyka in i den steg-för-steg-process att formatera nummeretiketter i ett diagram.

## Importera namnområden

Först och främst måste vi importera de nödvändiga namnområdena för att fungera med Aspose.Words för .NET. Lägg till följande rader överst i din C#-fil:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Steg 1: Konfigurera din dokumentkatalog

Innan du kan börja manipulera ditt Word-dokument måste du ange katalogen där ditt dokument ska sparas. Detta är viktigt för att spara operationen senare.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentkatalog.

## Steg 2: Initiera Document and DocumentBuilder

 Nästa steg är att initiera en ny`Document` och a`DocumentBuilder` . De`DocumentBuilder` är en hjälpklass som låter oss konstruera dokumentinnehållet.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 3: Infoga ett diagram i dokumentet

 Låt oss nu infoga ett diagram i dokumentet med hjälp av`DocumentBuilder`. I den här handledningen kommer vi att använda ett linjediagram som exempel.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Här infogar vi ett linjediagram med en specifik bredd och höjd och ställer in diagrammets titel.

## Steg 4: Rensa standardserier och lägg till ny serie

Som standard kommer diagrammet att ha några förgenererade serier. Vi måste rensa dessa och lägga till våra egna serier med specifika datapunkter.

```csharp
// Ta bort standardgenererade serier.
chart.Series.Clear();

// Lägg till nya serier med anpassade datapunkter.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Steg 5: Aktivera dataetiketter

För att visa dataetiketterna på diagrammet måste vi aktivera dem för vår serie.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Steg 6: Formatera dataetiketter

Kärnan i denna handledning är att formatera dataetiketterna. Vi kan tillämpa olika nummerformat på varje dataetikett individuellt.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Valutaformat
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Datumformat
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Procentformat
```

 Dessutom kan du länka en dataetiketts format till en källcell. När den är länkad,`NumberFormat` kommer att återställas till allmänt och ärvas från källcellen.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Steg 7: Spara dokumentet

Slutligen, spara dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Detta sparar ditt dokument med det angivna namnet och säkerställer att ditt diagram med formaterade dataetiketter bevaras.

## Slutsats

Att formatera dataetiketter i ett diagram med Aspose.Words för .NET kan avsevärt förbättra läsbarheten och professionaliteten hos dina Word-dokument. Genom att följa denna steg-för-steg-guide bör du nu kunna skapa ett diagram, lägga till dataserier och formatera dataetiketterna för att möta dina behov. Aspose.Words för .NET är ett kraftfullt verktyg som möjliggör omfattande anpassning och automatisering av Word-dokument, vilket gör det till en ovärderlig tillgång för .NET-utvecklare.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att skapa, manipulera och konvertera Word-dokument programmatiskt med C#.

### Kan jag formatera andra typer av diagram med Aspose.Words för .NET?
Ja, Aspose.Words för .NET stöder en mängd olika diagramtyper, inklusive stapel, kolumn, cirkel och mer.

### Hur får jag en tillfällig licens för Aspose.Words för .NET?
Du kan få en tillfällig licens[här](https://purchase.aspose.com/temporary-license/).

### Är det möjligt att länka dataetiketter till källceller i Excel?
Ja, du kan länka dataetiketter till källceller, vilket gör att talformatet kan ärvas från källcellen.

### Var kan jag hitta mer detaljerad dokumentation för Aspose.Words för .NET?
 Du kan hitta omfattande dokumentation[här](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
