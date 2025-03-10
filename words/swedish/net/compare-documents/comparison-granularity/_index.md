---
title: Jämförelsegranularitet i Word-dokument
linktitle: Jämförelsegranularitet i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig Jämför granularitet i word-dokumentfunktionen i Aspose.Words för .NET som gör att dokument kan jämföras tecken för tecken, och rapporterar gjorda ändringar.
weight: 10
url: /sv/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jämförelsegranularitet i Word-dokument

Här är en steg-för-steg-guide för att förklara C#-källkoden nedan, som använder funktionen Jämför granularitet i word-dokument i Aspose.Words för .NET.

## Steg 1: Introduktion

Funktionen Compare Granularity i Aspose.Words för .NET låter dig jämföra dokument på teckennivå. Detta innebär att varje karaktär kommer att jämföras och ändringar kommer att rapporteras därefter.

## Steg 2: Sätta upp miljön

Innan du börjar måste du ställa in din utvecklingsmiljö för att fungera med Aspose.Words för .NET. Se till att du har Aspose.Words-biblioteket installerat och har ett lämpligt C#-projekt att bädda in koden i.

## Steg 3: Lägg till nödvändiga sammansättningar

För att använda funktionen Compare Granularity i Aspose.Words för .NET måste du lägga till de nödvändiga sammansättningarna till ditt projekt. Se till att du har rätt referenser till Aspose.Words i ditt projekt.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Steg 4: Skapa dokument

I det här steget kommer vi att skapa två dokument med klassen DocumentBuilder. Dessa dokument kommer att användas för jämförelsen.

```csharp
// Skapa dokument A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Skapa dokument B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Steg 5: Konfigurera jämförelsealternativ

I det här steget kommer vi att konfigurera jämförelsealternativen för att specificera jämförelsegranulariteten. Här kommer vi att använda granularitet på teckennivå.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Steg 6: Dokumentjämförelse

Låt oss nu jämföra dokumenten med hjälp av metoden Compare för klassen Document. Ändringar sparas i dokument A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 De`Compare`metoden jämför dokument A med dokument B och sparar ändringarna i dokument A. Du kan ange författarens namn och datum för jämförelsen som referens.

## Slutsats

I den här artikeln utforskade vi funktionen Compare Granularity i Aspose.Words för .NET. Den här funktionen låter dig jämföra dokument på teckennivå och rapportera ändringar. Du kan använda denna kunskap för att utföra detaljerade dokumentjämförelser i dina projekt.

### Exempel på källkod för Comparison Granularity med Aspose.Words för .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Slutsats

I den här handledningen utforskade vi funktionen Comparison Granularity i Aspose.Words för .NET. Den här funktionen låter dig ange detaljnivån när du jämför dokument. Genom att välja olika granularitetsnivåer kan du utföra detaljerade jämförelser på tecken-, ord- eller blocknivå, beroende på dina specifika krav. Aspose.Words för .NET ger en flexibel och kraftfull dokumentjämförelsefunktion, vilket gör det enkelt att identifiera skillnader i dokument med varierande grad av granularitet.

### FAQ's

#### F: Vad är syftet med att använda Comparison Granularity i Aspose.Words för .NET?

S: Jämförelsegranularitet i Aspose.Words för .NET låter dig specificera detaljnivån när du jämför dokument. Med den här funktionen kan du jämföra dokument på olika nivåer, till exempel teckennivå, ordnivå eller till och med blocknivå. Varje granularitetsnivå ger olika detaljnivåer i jämförelseresultaten.

#### F: Hur använder jag Comparison Granularity i Aspose.Words för .NET?

S: För att använda Comparison Granularity i Aspose.Words för .NET, följ dessa steg:
1. Ställ in din utvecklingsmiljö med Aspose.Words-biblioteket.
2. Lägg till de nödvändiga sammansättningarna till ditt projekt genom att referera till Aspose.Words.
3.  Skapa de dokument som du vill jämföra med hjälp av`DocumentBuilder` klass.
4.  Konfigurera jämförelsealternativen genom att skapa en`CompareOptions` objekt och ställa in`Granularity` egenskap till önskad nivå (t.ex.`Granularity.CharLevel` för jämförelse på teckennivå).
5.  Använd`Compare`metod på ett dokument, passerar det andra dokumentet och`CompareOptions` objekt som parametrar. Denna metod kommer att jämföra dokumenten baserat på den specificerade granulariteten och spara ändringarna i det första dokumentet.

#### F: Vilka är de tillgängliga nivåerna av jämförelsegranularitet i Aspose.Words för .NET?

S: Aspose.Words för .NET tillhandahåller tre nivåer av jämförelsegranularitet:
- `Granularity.CharLevel`: Jämför dokument på teckennivå.
- `Granularity.WordLevel`: Jämför dokument på ordnivå.
- `Granularity.BlockLevel`: Jämför dokument på blocknivå.

#### F: Hur kan jag tolka jämförelseresultaten med granularitet på teckennivå?

S: Med granularitet på teckennivå analyseras varje tecken i de jämförda dokumenten för skillnader. Jämförelseresultaten kommer att visa ändringar på individuell karaktärsnivå, inklusive tillägg, raderingar och ändringar.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
