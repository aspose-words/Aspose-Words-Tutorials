---
"description": "Lär dig hur du infogar ett punktdiagram i Word med Aspose.Words för .NET. Enkla steg för att integrera visuella datarepresentationer i dina dokument."
"linktitle": "Infoga punktdiagram i Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Infoga punktdiagram i Word-dokument"
"url": "/sv/net/programming-with-charts/insert-scatter-chart/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga punktdiagram i Word-dokument

## Introduktion

den här handledningen lär du dig hur du använder Aspose.Words för .NET för att infoga ett punktdiagram i ditt Word-dokument. Punktdiagram är kraftfulla visuella verktyg som effektivt kan visa datapunkter baserat på två variabler, vilket gör dina dokument mer engagerande och informativa.

## Förkunskapskrav

Innan vi börjar skapa spridningsdiagram med Aspose.Words för .NET, se till att du har följande förutsättningar:

1. Installation av Aspose.Words för .NET: Ladda ner och installera Aspose.Words för .NET från [här](https://releases.aspose.com/words/net/).
   
2. Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# och .NET framework är meriterande.

## Importera namnrymder

För att komma igång måste du importera de nödvändiga namnrymderna i ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Nu ska vi gå igenom processen för att infoga ett punktdiagram i ditt Word-dokument med hjälp av Aspose.Words för .NET:

## Steg 1: Initiera dokumentet och DocumentBuilder

Först, initiera en ny instans av `Document` klass och `DocumentBuilder` klass för att börja bygga ditt dokument.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga punktdiagrammet

Använd `InsertChart` metod för `DocumentBuilder` klassen för att infoga ett punktdiagram i dokumentet.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Steg 3: Lägg till dataserier i diagrammet

Lägg nu till dataserier i ditt spridningsdiagram. Det här exemplet visar hur man lägger till en serie med specifika datapunkter.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Steg 4: Spara dokumentet

Spara slutligen det ändrade dokumentet på önskad plats med hjälp av `Save` metod för `Document` klass.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Slutsats

Grattis! Du har nu lärt dig hur man infogar ett punktdiagram i ditt Word-dokument med Aspose.Words för .NET. Punktdiagram är utmärkta verktyg för att visualisera datarelationer, och med Aspose.Words kan du enkelt integrera dem i dina dokument för att förbättra tydlighet och förståelse.

## Vanliga frågor

### Kan jag anpassa utseendet på spridningsdiagrammet med hjälp av Aspose.Words?
Ja, Aspose.Words tillåter omfattande anpassning av diagramegenskaper som färger, axlar och etiketter.

### Är Aspose.Words kompatibelt med olika versioner av Microsoft Word?
Aspose.Words stöder olika versioner av Microsoft Word, vilket säkerställer kompatibilitet mellan plattformar.

### Har Aspose.Words stöd för andra typer av diagram?
Ja, Aspose.Words stöder en mängd olika diagramtyper, inklusive stapeldiagram, linjediagram och cirkeldiagram.

### Kan jag dynamiskt uppdatera data i punktdiagrammet programmatiskt?
Absolut, du kan uppdatera diagramdata dynamiskt med hjälp av Aspose.Words API-anrop.

### Var kan jag få ytterligare hjälp eller support för Aspose.Words?
För ytterligare hjälp, besök [Aspose.Words supportforum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}