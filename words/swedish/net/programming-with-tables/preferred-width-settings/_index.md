---
"description": "Lär dig hur du skapar tabeller med absoluta, relativa och automatiska breddinställningar i Aspose.Words för .NET med den här steg-för-steg-guiden."
"linktitle": "Föredragna breddinställningar"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Föredragna breddinställningar"
"url": "/sv/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Föredragna breddinställningar

## Introduktion

Tabeller är ett kraftfullt sätt att organisera och presentera information i dina Word-dokument. När du arbetar med tabeller i Aspose.Words för .NET har du flera alternativ för att ställa in bredden på tabellceller för att säkerställa att de passar dokumentets layout perfekt. Den här guiden guidar dig genom processen att skapa tabeller med önskade breddinställningar med Aspose.Words för .NET, med fokus på absoluta, relativa och automatiska storleksalternativ. 

## Förkunskapskrav

Innan du går in i handledningen, se till att du har följande:

1. Aspose.Words för .NET: Se till att du har Aspose.Words för .NET installerat i din utvecklingsmiljö. Du kan ladda ner det [här](https://releases.aspose.com/words/net/).

2. .NET-utvecklingsmiljö: Ha en .NET-utvecklingsmiljö konfigurerad, till exempel Visual Studio.

3. Grundläggande kunskaper i C#: Bekantskap med C#-programmering hjälper dig att förstå kodavsnitt och exempel bättre.

4. Aspose.Words-dokumentationen: Se [Aspose.Words-dokumentation](https://reference.aspose.com/words/net/) för detaljerad API-information och vidare läsning.

## Importera namnrymder

Innan du börjar koda måste du importera nödvändiga namnrymder till ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dessa namnrymder ger åtkomst till kärnfunktionerna i Aspose.Words och Table-objektet, vilket gör att du kan manipulera dokumenttabeller.

Låt oss dela upp processen att skapa en tabell med olika önskade breddinställningar i tydliga, hanterbara steg.

## Steg 1: Initiera dokumentet och DocumentBuilder

Rubrik: Skapa ett nytt dokument och DocumentBuilder

Förklaring: Börja med att skapa ett nytt Word-dokument och en `DocumentBuilder` exempel. Den `DocumentBuilder` klassen erbjuder ett enkelt sätt att lägga till innehåll i ditt dokument.

```csharp
// Definiera sökvägen för att spara dokumentet.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Skapa ett nytt dokument.
Document doc = new Document();

// Skapa en dokumentbyggare för detta dokument.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Här anger du katalogen där dokumentet ska sparas och initierar `Document` och `DocumentBuilder` föremål.

## Steg 2: Infoga den första tabellcellen med absolut bredd

Infoga den första cellen i tabellen med en fast bredd på 40 punkter. Detta säkerställer att cellen alltid bibehåller en bredd på 40 punkter oavsett tabellstorlek.

```csharp
// Infoga en cell med absolut storlek.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

I det här steget börjar du skapa tabellen och infogar en cell med absolut bredd. `PreferredWidth.FromPoints(40)` Metoden ställer in cellens bredd till 40 punkter, och `Shading.BackgroundPatternColor` tillämpar en ljusgul bakgrundsfärg.

## Steg 3: Infoga en cell med relativ storlek

Infoga en annan cell med en bredd som är 20 % av tabellens totala bredd. Denna relativa storlek säkerställer att cellen justeras proportionellt mot tabellens bredd.

```csharp
// Infoga en cell av relativ (procentuell) storlek.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Den här cellens bredd kommer att vara 20 % av tabellens totala bredd, vilket gör den anpassningsbar till olika skärmstorlekar eller dokumentlayouter.

### Steg 4: Infoga en automatiskt storleksanpassad cell

Slutligen infogar du en cell som automatiskt anpassar storleken baserat på det återstående tillgängliga utrymmet i tabellen.

```csharp
// Infoga en cell med automatisk storlek.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. De size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` Inställningen tillåter att den här cellen expanderar eller krymper baserat på utrymmet som finns kvar efter att de andra cellerna har tagits med i beräkningen. Detta säkerställer att tabelllayouten ser balanserad och professionell ut.

## Steg 5: Slutför och spara dokumentet

När du har infogat alla celler, fyll i tabellen och spara dokumentet till den angivna sökvägen.

```csharp
// Spara dokumentet.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Det här steget slutför tabellen och sparar dokumentet med filnamnet "WorkingWithTables.PreferredWidthSettings.docx" i din angivna katalog.

## Slutsats

Att skapa tabeller med önskade breddinställningar i Aspose.Words för .NET är enkelt när du väl förstår de olika storleksalternativen som finns tillgängliga. Oavsett om du behöver fasta, relativa eller automatiska cellbredder ger Aspose.Words flexibiliteten att hantera olika tabelllayoutscenarier effektivt. Genom att följa stegen som beskrivs i den här guiden kan du säkerställa att dina tabeller är välstrukturerade och visuellt tilltalande i dina Word-dokument.

## Vanliga frågor

### Vad är skillnaden mellan absoluta och relativa cellbredder?
Absoluta cellbredder är fasta och ändras inte, medan relativa bredder justeras baserat på tabellens totala bredd.

### Kan jag använda negativa procenttal för relativa bredder?
Nej, negativa procenttal är inte giltiga för cellbredder. Endast positiva procenttal är tillåtna.

### Hur fungerar funktionen för automatisk storleksanpassning?
Automatisk storleksjustering justerar cellens bredd för att fylla eventuellt återstående utrymme i tabellen efter att andra celler har storleksändrats.

### Kan jag tillämpa olika stilar på celler med olika breddinställningar?
Ja, du kan använda olika stilar och formateringar på celler oavsett deras breddinställningar.

### Vad händer om tabellens totala bredd är mindre än summan av alla cellbredder?
Tabellen justerar automatiskt cellernas bredd så att den passar inom det tillgängliga utrymmet, vilket kan göra att vissa celler krymper.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}