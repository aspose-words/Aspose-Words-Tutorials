---
title: Ställ in relativ horisontell eller vertikal position
linktitle: Ställ in relativ horisontell eller vertikal position
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in relativa horisontella och vertikala positioner för tabeller i Word-dokument med Aspose.Words för .NET med denna steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-tables/set-relative-horizontal-or-vertical-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in relativ horisontell eller vertikal position

## Introduktion

Har du någonsin känt dig fast med hur du placerar tabeller precis som du vill i dina Word-dokument? Tja, du är inte ensam. Oavsett om du skapar en professionell rapport eller en snygg broschyr, kan justering av tabeller göra en värld av skillnad. Det är där Aspose.Words för .NET kommer väl till pass. Denna handledning guidar dig steg-för-steg om hur du ställer in relativa horisontella eller vertikala positioner för tabeller i dina Word-dokument. Låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande:

1.  Aspose.Words för .NET: Om du inte redan har gjort det kan du ladda ner det[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller någon annan .NET-kompatibel IDE.
3. Grundläggande kunskaper om C#: Denna handledning förutsätter att du är bekant med grunderna i C#-programmering.

## Importera namnområden

Först och främst måste du importera de nödvändiga namnrymden. Detta är viktigt för att komma åt Aspose.Words-funktionerna.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Steg 1: Ladda ditt dokument

För att komma igång måste du ladda ditt Word-dokument i programmet. Så här kan du göra det:

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Det här kodavsnittet ställer in sökvägen till din dokumentkatalog och laddar det specifika dokument du vill arbeta med. Se till att din dokumentsökväg är korrekt för att undvika laddningsproblem.

## Steg 2: Gå till tabellen

Därefter måste vi komma åt tabellen i dokumentet. Vanligtvis skulle du vilja arbeta med den första tabellen i huvuddelen.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Denna kodrad hämtar den första tabellen från dokumentets brödtext. Om ditt dokument har flera tabeller kan du justera indexet därefter.

## Steg 3: Ställ in horisontell position

Låt oss nu ställa in den horisontella positionen för tabellen i förhållande till ett specifikt element. I det här exemplet kommer vi att placera det i förhållande till kolumnen.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

 Genom att ställa in`HorizontalAnchor` till`RelativeHorizontalPosition.Column`, säger du till tabellen att anpassa sig horisontellt i förhållande till kolumnen den finns i.

## Steg 4: Ställ in vertikal position

I likhet med horisontell positionering kan du också ställa in den vertikala positionen. Här placerar vi den i förhållande till sidan.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

 Ställa in`VerticalAnchor` till`RelativeVerticalPosition.Page` ser till att tabellen är vertikalt inriktad enligt sidan.

## Steg 5: Spara ditt dokument

Slutligen, spara dina ändringar i ett nytt dokument. Detta är ett avgörande steg för att se till att dina ändringar bevaras.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Detta kommando sparar det ändrade dokumentet med ett nytt namn, så att du inte skriver över din ursprungliga fil.

## Slutsats

Och där har du det! Du har framgångsrikt angett de relativa horisontella och vertikala positionerna för en tabell i ett Word-dokument med Aspose.Words för .NET. Med denna nyfunna färdighet kan du förbättra layouten och läsbarheten för dina dokument, så att de ser mer professionella och polerade ut. Fortsätt att experimentera med olika positioner och se vad som fungerar bäst för dina behov.

## FAQ's

### Kan jag placera tabeller i förhållande till andra element?  
Ja, Aspose.Words låter dig placera tabeller i förhållande till olika element som marginaler, sidor, kolumner och mer.

### Behöver jag en licens för att använda Aspose.Words för .NET?  
 Ja, du kan köpa en licens[här](https://purchase.aspose.com/buy) eller få en tillfällig licens[här](https://purchase.aspose.com/temporary-license/).

### Finns det en gratis testversion tillgänglig för Aspose.Words för .NET?  
 Absolut! Du kan ladda ner en gratis testversion[här](https://releases.aspose.com/).

### Kan jag använda Aspose.Words med andra programmeringsspråk?  
Aspose.Words är främst designat för .NET, men det finns versioner tillgängliga för Java, Python och andra plattformar.

### Var kan jag hitta mer detaljerad dokumentation?  
För mer djupgående information, kolla in Aspose.Words-dokumentationen[här](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
