---
title: Hämta teckensnittsradavstånd
linktitle: Hämta teckensnittsradavstånd
second_title: Aspose.Words Document Processing API
description: Lär dig hur du får teckensnitt radavstånd med Aspose.Words för .NET med denna steg-för-steg handledning. Perfekt för utvecklare.
weight: 10
url: /sv/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hämta teckensnittsradavstånd

## Introduktion

Aspose.Words för .NET är ett kraftfullt bibliotek som låter dig skapa, manipulera och konvertera Word-dokument programmatiskt. En vanlig uppgift du kan behöva utföra är att hämta radavståndet för ett specifikt teckensnitt i ett dokument. I den här handledningen går vi igenom processen steg-för-steg, och säkerställer att du enkelt kan få teckensnittsradavstånd med Aspose.Words för .NET. 

## Förutsättningar

Innan vi dyker in i koden, se till att du har följande förutsättningar på plats:

1.  Aspose.Words för .NET Library: Ladda ner och installera den senaste versionen från[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Se till att du har en IDE som Visual Studio inställd.
3. Grundläggande kunskaper om C#: Denna handledning förutsätter att du har en grundläggande förståelse för C#-programmering.

## Importera namnområden

Först måste du importera de nödvändiga namnrymden i ditt C#-projekt. Dessa namnrymder ger dig tillgång till Aspose.Words-funktionerna.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Låt oss dela upp processen att få teckensnittsradavstånd i enkla, hanterbara steg.

## Steg 1: Skapa ett nytt dokument

Det första steget är att skapa en ny Word-dokumentinstans med Aspose.Words för .NET.

```csharp
Document doc = new Document();
```

## Steg 2: Initiera DocumentBuilder

Därefter måste vi initiera`DocumentBuilder` objekt. Detta objekt hjälper oss att konstruera och manipulera dokumentinnehållet.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 3: Ställ in teckensnittsegenskaper

Nu ställer vi in teckensnittsegenskaperna för texten som vi vill infoga. För det här exemplet kommer vi att använda typsnittet "Calibri".

```csharp
builder.Font.Name = "Calibri";
```

## Steg 4: Skriv text till dokumentet

 Med hjälp av`DocumentBuilder` objekt, skriv lite text i dokumentet. Den här texten kommer att använda de teckensnittsegenskaper vi ställde in i föregående steg.

```csharp
builder.Writeln("Sample Text");
```

## Steg 5: Hämta teckensnittsobjektet

För att få radavståndet måste vi komma åt teckensnittsobjektet för texten vi just lade till. Detta kan göras genom att navigera genom dokumentstrukturen till första styckekörningen.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Steg 6: Få radavståndet

Slutligen hämtar vi radavståndet från teckensnittsobjektet och skriver ut det till konsolen.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Slutsats

Och där har du det! Att hämta teckensnittets radavstånd med Aspose.Words för .NET är enkelt när du delar upp det i dessa enkla steg. Oavsett om du skapar ett nytt dokument eller arbetar med ett befintligt, tillhandahåller Aspose.Words alla verktyg du behöver för att hantera teckensnittsegenskaper effektivt.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, manipulera och konvertera Word-dokument programmatiskt med C#.

### Kan jag använda Aspose.Words för .NET på andra .NET-språk?
Ja, du kan använda Aspose.Words för .NET med vilket .NET-språk som helst, inklusive VB.NET och F#.

### Hur kan jag ladda ner Aspose.Words för .NET?
 Du kan ladda ner den senaste versionen av Aspose.Words för .NET från[här](https://releases.aspose.com/words/net/).

### Finns det en gratis testversion tillgänglig för Aspose.Words för .NET?
 Ja, du kan få en gratis provperiod från[här](https://releases.aspose.com/).

### Var kan jag hitta dokumentationen för Aspose.Words för .NET?
 Dokumentationen för Aspose.Words för .NET finns tillgänglig[här](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
