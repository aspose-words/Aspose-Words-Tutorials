---
"description": "Lär dig hur du anger gränserna för en axel i ett diagram med hjälp av Aspose.Words för .NET som styr intervallet av värden som visas på axeln."
"linktitle": "Axelgränser i ett diagram"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Axelgränser i ett diagram"
"url": "/sv/net/programming-with-charts/bounds-of-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Axelgränser i ett diagram

## Introduktion

Vill du skapa professionella dokument med diagram i .NET? Då har du kommit rätt! Den här guiden guidar dig genom processen att använda Aspose.Words för .NET för att ange axelgränserna i ett diagram. Vi bryter ner varje steg för att säkerställa att du enkelt kan följa med, även om du är nybörjare i biblioteket. Så, låt oss dyka in och komma igång!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

- Aspose.Words för .NET: Du kan [ladda ner](https://releases.aspose.com/words/net/) den senaste versionen eller använd en [gratis provperiod](https://releases.aspose.com/).
- .NET Framework: Se till att du har .NET installerat på ditt system.
- IDE: En utvecklingsmiljö som liknar Visual Studio.

När du har allt klart kan vi gå vidare till nästa steg.

## Importera namnrymder

För att börja måste du importera de nödvändiga namnrymderna. Dessa ger dig åtkomst till Aspose.Words-biblioteket och dess diagramfunktioner.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Steg 1: Konfigurera din dokumentkatalog

Först och främst måste du konfigurera katalogen där ditt dokument ska sparas. Detta är ett enkelt steg men avgörande för att organisera dina filer.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Skapa ett nytt dokument

Skapa sedan ett nytt dokumentobjekt. Detta dokument kommer att fungera som behållare för ditt diagram.

```csharp
Document doc = new Document();
```

## Steg 3: Initiera dokumentbyggaren

Klassen DocumentBuilder erbjuder ett snabbt och enkelt sätt att skapa dokument. Initiera den med ditt dokument.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 4: Infoga ett diagram

Nu är det dags att infoga ett diagram i ditt dokument. I det här exemplet använder vi ett stapeldiagram.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Steg 5: Rensa befintliga serier

För att säkerställa att du börjar med en nystart, rensa alla befintliga serier från diagrammet.

```csharp
chart.Series.Clear();
```

## Steg 6: Lägg till data i diagrammet

Här lägger vi till data i diagrammet. Detta inkluderar att ange serienamnet och datapunkterna.

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

Och det var allt! Du har skapat ett dokument med ett diagram med hjälp av Aspose.Words för .NET. 

## Slutsats

Med Aspose.Words för .NET kan du enkelt skapa och manipulera diagram i dina dokument. Den här steg-för-steg-guiden har visat dig hur du ställer in axelgränserna i ett diagram, vilket gör din datapresentation mer exakt och professionell. Oavsett om du genererar rapporter, presentationer eller något annat dokument, tillhandahåller Aspose.Words de verktyg du behöver.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett bibliotek som låter dig skapa, modifiera och konvertera Word-dokument programmatiskt med hjälp av .NET-ramverket.

### Hur konfigurerar jag Aspose.Words för .NET?
Du kan ladda ner den från [här](https://releases.aspose.com/words/net/) och följ de medföljande installationsanvisningarna.

### Kan jag använda Aspose.Words gratis?
Ja, du kan använda en [gratis provperiod](https://releases.aspose.com/) eller få en [tillfällig licens](https://purchase.aspose.com/temporary-license/).

### Var kan jag hitta dokumentation för Aspose.Words för .NET?
Detaljerad dokumentation finns tillgänglig [här](https://reference.aspose.com/words/net/).

### Hur kan jag få support för Aspose.Words?
Du kan besöka [supportforum](https://forum.aspose.com/c/words/8) för hjälp.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}