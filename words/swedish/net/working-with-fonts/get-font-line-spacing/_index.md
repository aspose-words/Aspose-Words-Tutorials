---
"description": "Lär dig hur du får radavstånd i teckensnitt med Aspose.Words för .NET med den här steg-för-steg-handledningen. Perfekt för utvecklare."
"linktitle": "Hämta radavstånd för teckensnitt"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Hämta radavstånd för teckensnitt"
"url": "/sv/net/working-with-fonts/get-font-line-spacing/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hämta radavstånd för teckensnitt

## Introduktion

Aspose.Words för .NET är ett kraftfullt bibliotek som låter dig skapa, manipulera och konvertera Word-dokument programmatiskt. En vanlig uppgift du kan behöva utföra är att hämta radavståndet för ett specifikt teckensnitt i ett dokument. I den här handledningen guidar vi dig genom processen steg för steg, så att du enkelt kan få radavstånd för teckensnitt med Aspose.Words för .NET. 

## Förkunskapskrav

Innan vi går in i koden, se till att du har följande förutsättningar på plats:

1. Aspose.Words för .NET-biblioteket: Ladda ner och installera den senaste versionen från [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Se till att du har en IDE som Visual Studio konfigurerad.
3. Grundläggande kunskaper i C#: Den här handledningen förutsätter att du har grundläggande förståelse för C#-programmering.

## Importera namnrymder

Först måste du importera de nödvändiga namnrymderna i ditt C#-projekt. Dessa namnrymder ger dig åtkomst till Aspose.Words-funktionerna.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Låt oss dela upp processen för att få radavstånd mellan teckensnitt i enkla, hanterbara steg.

## Steg 1: Skapa ett nytt dokument

Det första steget är att skapa en ny Word-dokumentinstans med hjälp av Aspose.Words för .NET.

```csharp
Document doc = new Document();
```

## Steg 2: Initiera DocumentBuilder

Nästa steg är att initialisera `DocumentBuilder` objekt. Detta objekt hjälper oss att konstruera och manipulera dokumentinnehållet.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 3: Ställ in teckensnittsegenskaperna

Nu ställer vi in teckensnittsegenskaperna för den text vi vill infoga. I det här exemplet använder vi teckensnittet "Calibri".

```csharp
builder.Font.Name = "Calibri";
```

## Steg 4: Skriv text till dokumentet

Använda `DocumentBuilder` objektet, skriv lite text i dokumentet. Denna text kommer att använda de teckensnittsegenskaper vi angav i föregående steg.

```csharp
builder.Writeln("Sample Text");
```

## Steg 5: Hämta teckensnittsobjektet

För att få radavståndet behöver vi komma åt fontobjektet för texten vi just lade till. Detta kan göras genom att navigera genom dokumentstrukturen till den första styckeskörningen.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Steg 6: Hämta radavståndet

Slutligen hämtar vi radavståndet från font-objektet och skriver ut det till konsolen.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Slutsats

Och där har du det! Att hämta radavståndet för teckensnittet med Aspose.Words för .NET är enkelt när du delar upp det i dessa enkla steg. Oavsett om du skapar ett nytt dokument eller arbetar med ett befintligt, tillhandahåller Aspose.Words alla verktyg du behöver för att hantera teckensnittsegenskaper effektivt.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, manipulera och konvertera Word-dokument programmatiskt med hjälp av C#.

### Kan jag använda Aspose.Words för .NET i andra .NET-språk?
Ja, du kan använda Aspose.Words för .NET med vilket .NET-språk som helst, inklusive VB.NET och F#.

### Hur kan jag ladda ner Aspose.Words för .NET?
Du kan ladda ner den senaste versionen av Aspose.Words för .NET från [här](https://releases.aspose.com/words/net/).

### Finns det en gratis testversion av Aspose.Words för .NET?
Ja, du kan få en gratis provperiod från [här](https://releases.aspose.com/).

### Var kan jag hitta dokumentationen för Aspose.Words för .NET?
Dokumentationen för Aspose.Words för .NET finns tillgänglig [här](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}