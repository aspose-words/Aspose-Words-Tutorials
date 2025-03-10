---
title: Ställ in standardalternativ för dataetiketter i ett diagram
linktitle: Ställ in standardalternativ för dataetiketter i ett diagram
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in standardalternativ för dataetiketter i ett diagram med Aspose.Words för .NET. Följ vår steg-för-steg-guide för att skapa och anpassa diagram utan ansträngning.
weight: 10
url: /sv/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in standardalternativ för dataetiketter i ett diagram

## Introduktion

Hej där! Är du sugen på att dyka in i dokumentautomatiseringens värld? Idag ska vi utforska hur man använder Aspose.Words för .NET för att skapa fantastiska dokument programmatiskt. Aspose.Words är ett kraftfullt bibliotek som låter dig manipulera Word-dokument med lätthet, och i den här handledningen kommer vi att fokusera på att ställa in standardalternativ för dataetiketter i ett diagram. Oavsett om du är en erfaren utvecklare eller nybörjare, kommer den här guiden att gå igenom varje steg för att komma igång på nolltid.

## Förutsättningar

Innan vi börjar, låt oss se till att du har allt du behöver följa tillsammans med den här handledningen. Här är en snabb checklista:

- Visual Studio eller någon annan .NET-kompatibel IDE: Det är här du ska skriva och köra din kod.
-  Aspose.Words för .NET: Du kan[ladda ner den senaste versionen](https://releases.aspose.com/words/net/) och installera det i ditt projekt.
- Grundläggande kunskaper om C#-programmering: Även om den här guiden är nybörjarvänlig, kommer lite bekantskap med C# att vara till hjälp.
- .NET Framework installerat: Se till att du har konfigurerat .NET Framework på din dator.
-  En tillfällig licens för Aspose.Words: Skaffa en[här](https://purchase.aspose.com/temporary-license/) för att låsa upp full funktionalitet.

När du har fått ordning på dessa förutsättningar är vi redo att börja!

## Importera namnområden

Först till kvarn, låt oss ställa in vårt projekt och importera de nödvändiga namnrymden. Dessa namnutrymmen är avgörande för att få tillgång till Aspose.Words-funktionaliteten.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Steg 1: Skapa ett nytt dokument


 Resan börjar med att skapa ett nytt dokument och initialisera ett`DocumentBuilder` . De`DocumentBuilder` klass tillhandahåller en uppsättning metoder för att enkelt manipulera dokumentinnehållet.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Skapa ett nytt dokument
Document doc = new Document();

// Initiera DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Förklaring

 I det här steget har vi ställt in dokumentet och byggaren som vi ska använda för att infoga och formatera vårt innehåll. De`dataDir` variabeln innehåller sökvägen där vi ska spara vårt slutliga dokument.

## Steg 2: Infoga ett diagram

 Därefter lägger vi till ett cirkeldiagram till vårt dokument. De`InsertChart` metod för`DocumentBuilder` klass gör detta superenkelt.

```csharp
// Infoga ett cirkeldiagram
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Gå till sjökortsobjektet
Chart chart = shape.Chart;
```

### Förklaring

Här infogar vi ett cirkeldiagram i vårt dokument. De`InsertChart` Metoden kräver diagramtyp, bredd och höjd som parametrar. Efter att ha infogat diagrammet kommer vi åt diagramobjektet för att ytterligare manipulera det.

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

I det här steget ser vi till att vårt diagram är tomt genom att rensa eventuella redan existerande serier. Sedan lägger vi till en ny serie med anpassade kategorier och värden, som kommer att visas i vårt cirkeldiagram.

## Steg 4: Ställ in standardalternativ för dataetiketter

Dataetiketter är avgörande för att göra ditt diagram informativt. Vi kommer att ställa in alternativ för att visa procent, värde och anpassa avgränsaren.

```csharp
// Få tillgång till insamlingen av dataetiketter
ChartDataLabelCollection labels = series.DataLabels;

// Ställ in alternativ för dataetikett
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Förklaring

 Här kommer vi åt`DataLabels`egenskapen i vår serie för att anpassa utseendet och informationen som visas på varje dataetikett. Vi har valt att visa både procent och värde, dölja ledarlinjer och ställa in en anpassad avgränsare.

## Steg 5: Spara dokumentet

Slutligen kommer vi att spara vårt dokument i den angivna katalogen. Detta steg säkerställer att alla våra ändringar skrivs till en fil.

```csharp
// Spara dokumentet
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Förklaring

 I det här sista steget sparar vi vårt dokument med hjälp av`Save` metod. Dokumentet kommer att sparas i den katalog som anges av`dataDir`, med namnet "WorkingWithCharts.DefaultOptionsForDataLabels.docx".

## Slutsats

Och där har du det! Du har framgångsrikt skapat ett Word-dokument med ett anpassat cirkeldiagram med Aspose.Words för .NET. Detta kraftfulla bibliotek gör det enkelt att automatisera skapande och manipulering av dokument, vilket sparar tid och ansträngning. Oavsett om du genererar rapporter, fakturor eller någon annan typ av dokument, har Aspose.Words dig täckt.

 Utforska gärna[Aspose.Words dokumentation](https://reference.aspose.com/words/net/) för fler funktioner och exempel. Glad kodning!

## FAQ's

### Kan jag använda Aspose.Words gratis?
Du kan använda Aspose.Words gratis med en[tillfällig licens](https://purchase.aspose.com/temporary-license/) eller utforska dess funktioner med hjälp av[gratis provperiod](https://releases.aspose.com/).

### Hur får jag support för Aspose.Words?
 Du kan få stöd genom[Aspose.Words supportforum](https://forum.aspose.com/c/words/8).

### Kan jag lägga till andra typer av diagram?
 Ja, Aspose.Words stöder olika diagramtyper som stapel-, linje- och kolumndiagram. Kontrollera[dokumentation](https://reference.aspose.com/words/net/) för mer information.

### Är Aspose.Words kompatibelt med .NET Core?
 Ja, Aspose.Words är kompatibelt med .NET Core. Du kan hitta mer information i[dokumentation](https://reference.aspose.com/words/net/).

### Hur kan jag köpa en licens för Aspose.Words?
 Du kan köpa en licens från[Aspose butik](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
