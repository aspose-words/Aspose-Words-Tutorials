---
"description": "Lär dig funktionen Jämför granularitet i Word-dokument i Aspose.Words för .NET som gör det möjligt att jämföra dokument tecken för tecken och rapportera gjorda ändringar."
"linktitle": "Jämförelsegranularitet i Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Jämförelsegranularitet i Word-dokument"
"url": "/sv/net/compare-documents/comparison-granularity/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jämförelsegranularitet i Word-dokument

Här är en steg-för-steg-guide som förklarar C#-källkoden nedan, som använder funktionen Jämför granularitet i Word-dokument i Aspose.Words för .NET.

## Steg 1: Introduktion

Funktionen Jämför granularitet i Aspose.Words för .NET låter dig jämföra dokument på teckennivå. Det betyder att varje tecken jämförs och ändringar rapporteras därefter.

## Steg 2: Konfigurera miljön

Innan du börjar måste du konfigurera din utvecklingsmiljö för att fungera med Aspose.Words för .NET. Se till att du har Aspose.Words-biblioteket installerat och att du har ett lämpligt C#-projekt att bädda in koden i.

## Steg 3: Lägg till nödvändiga sammansättningar

För att använda funktionen Jämför granularitet i Aspose.Words för .NET måste du lägga till nödvändiga assembler i ditt projekt. Se till att du har rätt referenser till Aspose.Words i ditt projekt.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Steg 4: Skapa dokument

det här steget skapar vi två dokument med hjälp av DocumentBuilder-klassen. Dessa dokument kommer att användas för jämförelsen.

```csharp
// Skapa dokument A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Skapa dokument B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Steg 5: Konfigurera jämförelsealternativ

I det här steget konfigurerar vi jämförelsealternativen för att ange jämförelsens granularitet. Här använder vi granularitet på teckennivå.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Steg 6: Dokumentjämförelse

Nu ska vi jämföra dokumenten med hjälp av Compare-metoden i Document-klassen. Ändringarna sparas i dokument A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

De `Compare` Metoden jämför dokument A med dokument B och sparar ändringarna i dokument A. Du kan ange författarens namn och jämförelsedatumet som referens.

## Slutsats

I den här artikeln utforskade vi funktionen Jämför granularitet i Aspose.Words för .NET. Den här funktionen låter dig jämföra dokument på teckennivå och rapportera ändringar. Du kan använda denna kunskap för att utföra detaljerade dokumentjämförelser i dina projekt.

### Exempel på källkod för jämförelsegranularitet med Aspose.Words för .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Slutsats

I den här handledningen utforskade vi funktionen Jämförelsegranularitet i Aspose.Words för .NET. Den här funktionen låter dig ange detaljnivån när du jämför dokument. Genom att välja olika granularitetsnivåer kan du utföra detaljerade jämförelser på tecken-, ord- eller blocknivå, beroende på dina specifika krav. Aspose.Words för .NET tillhandahåller en flexibel och kraftfull dokumentjämförelsefunktion, vilket gör det enkelt att identifiera skillnader i dokument med varierande granularitetsnivåer.

### Vanliga frågor

#### F: Vad är syftet med att använda jämförelsegranularitet i Aspose.Words för .NET?

A: Jämförelsegranularitet i Aspose.Words för .NET låter dig ange detaljnivån när du jämför dokument. Med den här funktionen kan du jämföra dokument på olika nivåer, till exempel teckennivå, ordnivå eller till och med blocknivå. Varje granularitetsnivå ger en annan detaljnivå i jämförelseresultaten.

#### F: Hur använder jag jämförelsegranularitet i Aspose.Words för .NET?

A: För att använda jämförelsegranularitet i Aspose.Words för .NET, följ dessa steg:
1. Konfigurera din utvecklingsmiljö med Aspose.Words-biblioteket.
2. Lägg till nödvändiga sammansättningar i ditt projekt genom att referera till Aspose.Words.
3. Skapa de dokument som du vill jämföra med hjälp av `DocumentBuilder` klass.
4. Konfigurera jämförelsealternativen genom att skapa en `CompareOptions` objektet och inställningen av `Granularity` egendom till önskad nivå (t.ex. `Granularity.CharLevel` för jämförelse på teckennivå).
5. Använd `Compare` metod på ett dokument, skickar det andra dokumentet och `CompareOptions` objekt som parametrar. Den här metoden jämför dokumenten baserat på den angivna granulariteten och sparar ändringarna i det första dokumentet.

#### F: Vilka nivåer av jämförelsegranularitet finns tillgängliga i Aspose.Words för .NET?

A: Aspose.Words för .NET erbjuder tre nivåer av jämförelsegranularitet:
- `Granularity.CharLevel`: Jämför dokument på teckennivå.
- `Granularity.WordLevel`Jämför dokument på ordnivå.
- `Granularity.BlockLevel`Jämför dokument på blocknivå.

#### F: Hur kan jag tolka jämförelseresultaten med granularitet på teckennivå?

A: Med granularitet på teckennivå analyseras varje tecken i de jämförda dokumenten för skillnader. Jämförelseresultaten visar förändringar på individuell teckennivå, inklusive tillägg, borttagningar och ändringar.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}