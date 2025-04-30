---
"description": "Lär dig hur du anger relativa horisontella och vertikala positioner för tabeller i Word-dokument med Aspose.Words för .NET med den här steg-för-steg-guiden."
"linktitle": "Ställ in relativ horisontell eller vertikal position"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ställ in relativ horisontell eller vertikal position"
"url": "/sv/net/programming-with-tables/set-relative-horizontal-or-vertical-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in relativ horisontell eller vertikal position

## Introduktion

Har du någonsin känt dig osäker på hur du ska placera tabeller precis som du vill i dina Word-dokument? Då är du inte ensam. Oavsett om du skapar en professionell rapport eller en snygg broschyr kan justering av tabeller göra en enorm skillnad. Det är där Aspose.Words för .NET kommer väl till pass. Den här handledningen guidar dig steg för steg om hur du ställer in relativa horisontella eller vertikala positioner för tabeller i dina Word-dokument. Nu kör vi!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET: Om du inte redan har gjort det kan du ladda ner det [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller annan .NET-kompatibel IDE.
3. Grundläggande kunskaper i C#: Den här handledningen förutsätter att du är bekant med grunderna i C#-programmering.

## Importera namnrymder

Först och främst måste du importera de nödvändiga namnrymderna. Detta är viktigt för att komma åt Aspose.Words-funktionerna.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Steg 1: Ladda ditt dokument

För att komma igång måste du ladda ditt Word-dokument i programmet. Så här gör du:

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Det här kodavsnittet anger sökvägen till din dokumentkatalog och laddar det specifika dokument du vill arbeta med. Se till att din dokumentsökväg är korrekt för att undvika laddningsproblem.

## Steg 2: Åtkomst till tabellen

Nästa steg är att komma åt tabellen i dokumentet. Vanligtvis vill du arbeta med den första tabellen i brödtexten.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Den här kodraden hämtar den första tabellen från dokumentets brödtext. Om ditt dokument har flera tabeller kan du justera indexet därefter.

## Steg 3: Ställ in horisontellt läge

Nu ska vi ställa in tabellens horisontella position i förhållande till ett specifikt element. I det här exemplet positionerar vi den i förhållande till kolumnen.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

Genom att ställa in `HorizontalAnchor` till `RelativeHorizontalPosition.Column`, du ber tabellen att justera sig horisontellt i förhållande till kolumnen den finns i.

## Steg 4: Ställ in vertikal position

likhet med horisontell positionering kan du även ställa in den vertikala positionen. Här positionerar vi den i förhållande till sidan.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

Inställning av `VerticalAnchor` till `RelativeVerticalPosition.Page` säkerställer att tabellen är vertikalt justerad enligt sidan.

## Steg 5: Spara ditt dokument

Slutligen, spara dina ändringar i ett nytt dokument. Detta är ett viktigt steg för att se till att dina ändringar bevaras.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Det här kommandot sparar det ändrade dokumentet med ett nytt namn, vilket säkerställer att du inte skriver över din ursprungliga fil.

## Slutsats

Och där har du det! Du har framgångsrikt ställt in de relativa horisontella och vertikala positionerna för en tabell i ett Word-dokument med hjälp av Aspose.Words för .NET. Med denna nyfunna färdighet kan du förbättra layouten och läsbarheten hos dina dokument, vilket gör att de ser mer professionella och eleganta ut. Fortsätt experimentera med olika positioner och se vad som fungerar bäst för dina behov.

## Vanliga frågor

### Kan jag placera tabeller i förhållande till andra element?  
Ja, Aspose.Words låter dig placera tabeller i förhållande till olika element som marginaler, sidor, kolumner med mera.

### Behöver jag en licens för att använda Aspose.Words för .NET?  
Ja, du kan köpa en licens [här](https://purchase.aspose.com/buy) eller skaffa ett tillfälligt körkort [här](https://purchase.aspose.com/temporary-license/).

### Finns det en gratis testversion av Aspose.Words för .NET?  
Absolut! Du kan ladda ner en gratis provversion [här](https://releases.aspose.com/).

### Kan jag använda Aspose.Words med andra programmeringsspråk?  
Aspose.Words är främst utformat för .NET, men det finns versioner tillgängliga för Java, Python och andra plattformar.

### Var kan jag hitta mer detaljerad dokumentation?  
För mer ingående information, se Aspose.Words-dokumentationen. [här](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}