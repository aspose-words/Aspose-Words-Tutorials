---
title: Axelgränser I Ett Diagram
linktitle: Axelgränser I Ett Diagram
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in gränserna för en axel i ett diagram med Aspose.Words för .NET som kontrollerar intervallet av värden som visas på axeln.
weight: 10
url: /sv/net/programming-with-charts/bounds-of-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Axelgränser I Ett Diagram

## Introduktion

Vill du skapa professionella dokument med diagram i .NET? Du är på rätt plats! Den här guiden leder dig genom processen att använda Aspose.Words för .NET för att sätta gränserna för axeln i ett diagram. Vi kommer att dela upp varje steg för att säkerställa att du enkelt kan följa med, även om du är ny på biblioteket. Så, låt oss dyka in och komma igång!

## Förutsättningar

Innan vi börjar, se till att du har följande:

-  Aspose.Words för .NET: Du kan[ladda ner](https://releases.aspose.com/words/net/) den senaste versionen eller använd en[gratis provperiod](https://releases.aspose.com/).
- .NET Framework: Se till att du har .NET installerat på ditt system.
- IDE: En utvecklingsmiljö som Visual Studio.

När du har allt klart kan vi gå vidare till nästa steg.

## Importera namnområden

För att börja måste du importera de nödvändiga namnrymden. Dessa ger dig tillgång till Aspose.Words-biblioteket och dess kartfunktioner.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Steg 1: Konfigurera din dokumentkatalog

Först och främst måste du ställa in katalogen där ditt dokument ska sparas. Detta är ett enkelt steg men avgörande för att organisera dina filer.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Skapa ett nytt dokument

Skapa sedan ett nytt dokumentobjekt. Detta dokument kommer att fungera som behållare för ditt diagram.

```csharp
Document doc = new Document();
```

## Steg 3: Initiera Document Builder

Klassen DocumentBuilder ger ett snabbt och enkelt sätt att bygga dokument. Initiera det med ditt dokument.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 4: Infoga ett diagram

Nu är det dags att infoga ett diagram i ditt dokument. I det här exemplet använder vi ett kolumndiagram.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Steg 5: Rensa befintliga serier

För att säkerställa att du börjar med ett rent blad, rensa alla befintliga serier från diagrammet.

```csharp
chart.Series.Clear();
```

## Steg 6: Lägg till data i diagrammet

Här lägger vi till data till diagrammet. Detta inkluderar att specificera serienamnet och datapunkterna.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

## Steg 7: Ställ in axelgränser

Att ställa in gränserna för Y-axeln säkerställer att ditt diagram skalas korrekt.

```csharp
chart.AxisY.Scaling.Minimum = new AxisBound(0);
chart.AxisY.Scaling.Maximum = new AxisBound(6);
```

## Steg 8: Spara dokumentet

Slutligen, spara ditt dokument i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithCharts.BoundsOfAxis.docx");
```

Och det är det! Du har framgångsrikt skapat ett dokument med ett diagram med Aspose.Words för .NET. 

## Slutsats

Med Aspose.Words för .NET kan du enkelt skapa och manipulera diagram i dina dokument. Denna steg-för-steg-guide har visat dig hur du anger gränserna för axeln i ett diagram, vilket gör din datapresentation mer exakt och professionell. Oavsett om du genererar rapporter, presentationer eller något annat dokument, tillhandahåller Aspose.Words de verktyg du behöver.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett bibliotek som låter dig skapa, ändra och konvertera Word-dokument programmatiskt med hjälp av .NET-ramverket.

### Hur ställer jag in Aspose.Words för .NET?
 Du kan ladda ner den från[här](https://releases.aspose.com/words/net/)och följ installationsanvisningarna.

### Kan jag använda Aspose.Words gratis?
 Ja, du kan använda en[gratis provperiod](https://releases.aspose.com/) eller skaffa en[tillfällig licens](https://purchase.aspose.com/temporary-license/).

### Var kan jag hitta dokumentation för Aspose.Words för .NET?
 Detaljerad dokumentation finns tillgänglig[här](https://reference.aspose.com/words/net/).

### Hur kan jag få support för Aspose.Words?
 Du kan besöka[supportforum](https://forum.aspose.com/c/words/8) för hjälp.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
