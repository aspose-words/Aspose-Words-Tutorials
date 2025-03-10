---
title: Flytande bordsposition
linktitle: Flytande bordsposition
second_title: Aspose.Words Document Processing API
description: Lär dig hur du kontrollerar tabellernas flytande position i Word-dokument med Aspose.Words för .NET med vår detaljerade steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-tables/floating-table-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Flytande bordsposition

## Introduktion

Är du redo att dyka in i världen av att manipulera bordspositioner i Word-dokument med Aspose.Words för .NET? Spänn fast dig, för idag ska vi undersöka hur du enkelt kontrollerar bordens flytande position. Låt oss förvandla dig till en bordsplaceringsguide på nolltid!

## Förutsättningar

Innan vi ger oss ut på denna spännande resa, låt oss se till att vi har allt vi behöver:

1. Aspose.Words för .NET Library: Se till att du har den senaste versionen. Om du inte gör det,[ladda ner den här](https://releases.aspose.com/words/net/).
2. .NET Framework: Se till att din utvecklingsmiljö är konfigurerad med .NET.
3. Utvecklingsmiljö: Visual Studio eller någon föredragen IDE.
4. Ett Word-dokument: Ha ett Word-dokument redo som innehåller en tabell.

## Importera namnområden

För att komma igång måste du importera de nödvändiga namnrymden i ditt .NET-projekt. Här är utdraget att inkludera överst i din C#-fil:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Steg-för-steg-guide

Låt oss nu dela upp processen i enkla, lättsmälta steg.

## Steg 1: Ladda dokumentet

Först och främst måste du ladda ditt Word-dokument. Det är här ditt bord finns.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Föreställ dig att ditt Word-dokument är en duk och ditt bord är ett konstverk på det. Vårt mål är att placera denna konst precis där vi vill ha på duken.

## Steg 2: Gå till tabellen

Därefter måste vi komma åt tabellen i dokumentet. Vanligtvis kommer du att arbeta med den första tabellen i dokumentets brödtext.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Se det här steget som att lokalisera tabellen du vill arbeta med i ett fysiskt dokument. Du måste veta exakt var det är för att göra några ändringar.

## Steg 3: Ställ in horisontell position

Låt oss nu ställa in den horisontella positionen för bordet. Detta bestämmer hur långt från dokumentets vänstra kant bordet kommer att placeras.

```csharp
table.AbsoluteHorizontalDistance = 10;
```

 Visualisera detta som att du flyttar tabellen horisontellt över ditt dokument. De`AbsoluteHorizontalDistance` är det exakta avståndet från vänster kant.

## Steg 4: Ställ in vertikal justering

Vi måste också ställa in den vertikala inriktningen av tabellen. Detta kommer att centrera tabellen vertikalt inom den omgivande texten.

```csharp
table.RelativeVerticalAlignment = VerticalAlignment.Center;
```

Tänk dig att hänga en bild på en vägg. Du vill se till att den är centrerad vertikalt för estetiskt tilltalande. Detta steg uppnår det.

## Steg 5: Spara det ändrade dokumentet

Slutligen, efter att ha placerat tabellen, spara ditt modifierade dokument.

```csharp
doc.Save(dataDir + "WorkingWithTables.FloatingTablePosition.docx");
```

Det är som att trycka på "Spara" på ditt redigerade dokument. Alla dina ändringar är nu bevarade.

## Slutsats

Och där har du det! Du har precis bemästrat hur du kontrollerar tabellernas flytande position i ett Word-dokument med Aspose.Words för .NET. Med dessa färdigheter kan du säkerställa att dina tabeller är perfekt placerade för att förbättra läsbarheten och estetiken hos dina dokument. Fortsätt experimentera och utforska de enorma funktionerna i Aspose.Words för .NET.

## FAQ's

### Kan jag ställa in det vertikala avståndet för tabellen från toppen av sidan?

 Ja, du kan använda`AbsoluteVerticalDistance` egenskap för att ställa in tabellens vertikala avstånd från sidans övre kant.

### Hur justerar jag tabellen till höger om dokumentet?

 För att justera tabellen till höger kan du ställa in`HorizontalAlignment` egenskap av tabellen till`HorizontalAlignment.Right`.

### Är det möjligt att placera flera tabeller på olika sätt i samma dokument?

 Absolut! Du kan komma åt och ställa in positioner för flera bord individuellt genom att iterera genom`Tables` samling i dokumentet.

### Kan jag använda relativ positionering för horisontell inriktning?

Ja, Aspose.Words stöder relativ positionering för både horisontella och vertikala justeringar med hjälp av egenskaper som`RelativeHorizontalAlignment`.

### Stöder Aspose.Words flytande tabeller i olika delar av ett dokument?

Ja, du kan placera flytande tabeller i olika sektioner genom att komma åt den specifika sektionen och dess tabeller i ditt dokument.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
