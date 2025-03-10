---
title: Infoga punktdiagram i Word-dokument
linktitle: Infoga punktdiagram i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du infogar ett punktdiagram i Word med Aspose.Words för .NET. Enkla steg för att integrera visuella datarepresentationer i dina dokument.
weight: 10
url: /sv/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga punktdiagram i Word-dokument

## Introduktion

I den här handledningen kommer du att lära dig hur du använder Aspose.Words för .NET för att infoga ett punktdiagram i ditt Word-dokument. Spridningsdiagram är kraftfulla visuella verktyg som effektivt kan visa datapunkter baserat på två variabler, vilket gör dina dokument mer engagerande och informativa.

## Förutsättningar

Innan vi dyker in i att skapa spridningsdiagram med Aspose.Words för .NET, se till att du har följande förutsättningar:

1.  Installation av Aspose.Words for .NET: Ladda ner och installera Aspose.Words for .NET från[här](https://releases.aspose.com/words/net/).
   
2. Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# och .NET-ramverket kommer att vara fördelaktigt.

## Importera namnområden

För att komma igång måste du importera de nödvändiga namnrymden i ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Låt oss nu dela upp processen för att infoga ett punktdiagram i ditt Word-dokument med Aspose.Words för .NET:

## Steg 1: Initiera Document and DocumentBuilder

 Initiera först en ny instans av`Document` klass och`DocumentBuilder` klass för att börja bygga ditt dokument.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga spridningsdiagrammet

 Använd`InsertChart` metod för`DocumentBuilder` klass för att infoga ett punktdiagram i dokumentet.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Steg 3: Lägg till dataserier i diagrammet

Lägg nu till dataserier till ditt spridningsdiagram. Det här exemplet visar hur man lägger till en serie med specifika datapunkter.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Steg 4: Spara dokumentet

 Slutligen sparar du det ändrade dokumentet på önskad plats med hjälp av`Save` metod för`Document` klass.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Slutsats

Grattis! Du har framgångsrikt lärt dig hur du infogar ett punktdiagram i ditt Word-dokument med Aspose.Words för .NET. Spridningsdiagram är utmärkta verktyg för att visualisera datarelationer, och med Aspose.Words kan du enkelt integrera dem i dina dokument för att öka tydlighet och förståelse.

## FAQ's

### Kan jag anpassa utseendet på punktdiagrammet med Aspose.Words?
Ja, Aspose.Words tillåter omfattande anpassning av diagramegenskaper som färger, axlar och etiketter.

### Är Aspose.Words kompatibel med olika versioner av Microsoft Word?
Aspose.Words stöder olika versioner av Microsoft Word, vilket säkerställer kompatibilitet mellan plattformar.

### Ger Aspose.Words stöd för andra typer av diagram?
Ja, Aspose.Words stöder ett brett utbud av diagramtyper inklusive stapeldiagram, linjediagram och cirkeldiagram.

### Kan jag dynamiskt uppdatera data i spridningsdiagrammet programmatiskt?
Absolut, du kan uppdatera diagramdata dynamiskt med Aspose.Words API-anrop.

### Var kan jag få ytterligare hjälp eller support för Aspose.Words?
 För ytterligare hjälp, besök[Aspose.Words supportforum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
