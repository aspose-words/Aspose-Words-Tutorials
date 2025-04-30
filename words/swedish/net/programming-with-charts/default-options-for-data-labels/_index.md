---
"description": "Lär dig hur du ställer in standardinställningar för dataetiketter i ett diagram med Aspose.Words för .NET. Följ vår steg-för-steg-guide för att enkelt skapa och anpassa diagram."
"linktitle": "Ange standardalternativ för dataetiketter i ett diagram"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ange standardalternativ för dataetiketter i ett diagram"
"url": "/sv/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ange standardalternativ för dataetiketter i ett diagram

## Introduktion

Hej! Är du sugen på att dyka in i dokumentautomationens värld? Idag ska vi utforska hur man använder Aspose.Words för .NET för att skapa fantastiska dokument programmatiskt. Aspose.Words är ett kraftfullt bibliotek som låter dig enkelt manipulera Word-dokument, och i den här handledningen fokuserar vi på att ställa in standardinställningar för dataetiketter i ett diagram. Oavsett om du är en erfaren utvecklare eller nybörjare, kommer den här guiden att guida dig genom varje steg för att komma igång på nolltid.

## Förkunskapskrav

Innan vi börjar, låt oss se till att du har allt du behöver för att följa den här handledningen. Här är en snabb checklista:

- Visual Studio eller någon annan .NET-kompatibel IDE: Det är här du skriver och kör din kod.
- Aspose.Words för .NET: Du kan [ladda ner den senaste versionen](https://releases.aspose.com/words/net/) och installera det i ditt projekt.
- Grundläggande kunskaper i C#-programmering: Även om den här guiden är nybörjarvänlig, är lite förtrogenhet med C# bra.
- .NET Framework installerat: Se till att du har .NET Framework konfigurerat på din dator.
- En tillfällig licens för Aspose. Ord: Skaffa en [här](https://purchase.aspose.com/temporary-license/) för att låsa upp full funktionalitet.

När du har löst dessa förutsättningar är vi redo att köra igång!

## Importera namnrymder

Först och främst, låt oss konfigurera vårt projekt och importera de nödvändiga namnrymderna. Dessa namnrymder är avgörande för att komma åt Aspose.Words-funktionen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Steg 1: Skapa ett nytt dokument


Resan börjar med att skapa ett nytt dokument och initiera en `DocumentBuilder`Den `DocumentBuilder` klassen tillhandahåller en uppsättning metoder för att enkelt manipulera dokumentinnehållet.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Skapa ett nytt dokument
Document doc = new Document();

// Initiera DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Förklaring

det här steget har vi konfigurerat dokumentet och verktyget som vi ska använda för att infoga och formatera vårt innehåll. `dataDir` variabeln innehåller sökvägen där vi sparar vårt slutgiltiga dokument.

## Steg 2: Infoga ett diagram

Nästa steg är att lägga till ett cirkeldiagram i vårt dokument. `InsertChart` metod för `DocumentBuilder` klassen gör det här superenkelt.

```csharp
// Infoga ett cirkeldiagram
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Åtkomst till diagramobjektet
Chart chart = shape.Chart;
```

### Förklaring

Här infogar vi ett cirkeldiagram i vårt dokument. `InsertChart` Metoden kräver diagramtyp, bredd och höjd som parametrar. Efter att ha infogat diagrammet får vi tillgång till diagramobjektet för att ytterligare manipulera det.

## Steg 3: Anpassa diagramserien

Nu rensar vi alla befintliga serier i diagrammet och lägger till våra anpassade serier. Denna serie kommer att representera våra datapunkter.

```csharp
// Rensa befintliga diagramserier
chart.Series.Clear();

// Lägg till nya serier i diagrammet
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Förklaring

det här steget ser vi till att vårt diagram är tomt genom att rensa alla befintliga serier. Sedan lägger vi till en ny serie med anpassade kategorier och värden, som visas i vårt cirkeldiagram.

## Steg 4: Ange standardalternativ för dataetiketter

Dataetiketter är avgörande för att göra ditt diagram informativt. Vi ställer in alternativ för att visa procentandel, värde och anpassar avgränsaren.

```csharp
// Åtkomst till dataetikettsamlingen
ChartDataLabelCollection labels = series.DataLabels;

// Ange alternativ för dataetiketter
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Förklaring

Här har vi tillgång till `DataLabels` egenskapen för vår serie för att anpassa utseendet och informationen som visas på varje dataetikett. Vi har valt att visa både procentandel och värde, dölja hänvisningslinjer och ange en anpassad avgränsare.

## Steg 5: Spara dokumentet

Slutligen sparar vi vårt dokument i den angivna katalogen. Detta steg säkerställer att alla våra ändringar skrivs till en fil.

```csharp
// Spara dokumentet
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Förklaring

I det här sista steget sparar vi vårt dokument med hjälp av `Save` metod. Dokumentet kommer att sparas i den katalog som anges av `dataDir`, med namnet "WorkingWithCharts.DefaultOptionsForDataLabels.docx".

## Slutsats

Och där har du det! Du har skapat ett Word-dokument med ett anpassat cirkeldiagram med hjälp av Aspose.Words för .NET. Detta kraftfulla bibliotek gör det enkelt att automatisera skapande och hantering av dokument, vilket sparar tid och ansträngning. Oavsett om du genererar rapporter, fakturor eller någon annan typ av dokument, har Aspose.Words det du behöver.

Känn dig fri att utforska [Aspose.Words-dokumentation](https://reference.aspose.com/words/net/) för fler funktioner och exempel. Lycka till med kodningen!

## Vanliga frågor

### Kan jag använda Aspose.Words gratis?
Du kan använda Aspose.Words gratis med en [tillfällig licens](https://purchase.aspose.com/temporary-license/) eller utforska dess funktioner med hjälp av [gratis provperiod](https://releases.aspose.com/).

### Hur får jag support för Aspose.Words?
Du kan få stöd genom [Aspose.Words supportforum](https://forum.aspose.com/c/words/8).

### Kan jag lägga till andra typer av diagram?
Ja, Aspose.Words stöder olika diagramtyper som stapeldiagram, linjediagram och kolumndiagram. Kontrollera [dokumentation](https://reference.aspose.com/words/net/) för mer information.

### Är Aspose.Words kompatibelt med .NET Core?
Ja, Aspose.Words är kompatibelt med .NET Core. Du hittar mer information i [dokumentation](https://reference.aspose.com/words/net/).

### Hur kan jag köpa en licens för Aspose.Words?
Du kan köpa en licens från [Aspose-butik](https://purchase.aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}