---
title: Önskad breddinställningar
linktitle: Önskad breddinställningar
second_title: Aspose.Words Document Processing API
description: Lär dig hur du skapar tabeller med absoluta, relativa och automatiska breddinställningar i Aspose.Words för .NET med denna steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Önskad breddinställningar

## Introduktion

Tabeller är ett kraftfullt sätt att organisera och presentera information i dina Word-dokument. När du arbetar med tabeller i Aspose.Words för .NET har du flera alternativ för att ställa in bredden på tabellceller för att säkerställa att de passar ditt dokuments layout perfekt. Den här guiden leder dig genom processen att skapa tabeller med önskade breddinställningar med Aspose.Words för .NET, med fokus på absoluta, relativa och automatiska storleksalternativ. 

## Förutsättningar

Innan du dyker in i handledningen, se till att du har följande:

1.  Aspose.Words för .NET: Se till att du har Aspose.Words för .NET installerat i din utvecklingsmiljö. Du kan ladda ner den[här](https://releases.aspose.com/words/net/).

2. .NET-utvecklingsmiljö: Ha en .NET-utvecklingsmiljö inrättad, till exempel Visual Studio.

3. Grundläggande kunskaper om C#: Bekantskap med C#-programmering hjälper dig att förstå kodavsnitten och exemplen bättre.

4.  Aspose.Words-dokumentation: Se[Aspose.Words dokumentation](https://reference.aspose.com/words/net/) för detaljerad API-information och ytterligare läsning.

## Importera namnområden

Innan du börjar koda måste du importera de nödvändiga namnrymden till ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dessa namnrymder ger tillgång till kärnfunktionerna i Aspose.Words och Table-objektet, så att du kan manipulera dokumenttabeller.

Låt oss dela upp processen att skapa en tabell med olika föredragna breddinställningar i tydliga, hanterbara steg.

## Steg 1: Initiera Document and DocumentBuilder

Rubrik: Skapa ett nytt dokument och DocumentBuilder

 Förklaring: Börja med att skapa ett nytt Word-dokument och ett`DocumentBuilder` exempel. De`DocumentBuilder` klass ger ett enkelt sätt att lägga till innehåll i ditt dokument.

```csharp
// Definiera sökvägen för att spara dokumentet.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Skapa ett nytt dokument.
Document doc = new Document();

// Skapa en DocumentBuilder för detta dokument.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Här anger du katalogen där dokumentet ska sparas och initialiserar`Document` och`DocumentBuilder` föremål.

## Steg 2: Sätt in den första tabellcellen med absolut bredd

Infoga den första cellen i tabellen med en fast bredd på 40 punkter. Detta kommer att säkerställa att denna cell alltid bibehåller en bredd på 40 punkter oavsett tabellstorlek.

```csharp
// Infoga en cell i absolut storlek.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

 det här steget börjar du skapa tabellen och infogar en cell med absolut bredd. De`PreferredWidth.FromPoints(40)` metoden ställer in cellens bredd till 40 punkter, och`Shading.BackgroundPatternColor` tillämpar en ljusgul bakgrundsfärg.

## Steg 3: Infoga en cell av relativ storlek

Infoga ytterligare en cell med en bredd som är 20 % av tabellens totala bredd. Denna relativa storlek säkerställer att cellen anpassas proportionellt till bordets bredd.

```csharp
// Infoga en cell i relativ (procent) storlek.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Denna cells bredd kommer att vara 20 % av tabellens totala bredd, vilket gör den anpassningsbar till olika skärmstorlekar eller dokumentlayouter.

### Steg 4: Infoga en cell med automatisk storlek

Till sist, infoga en cell som automatiskt anpassar sig själv baserat på det återstående tillgängliga utrymmet i tabellen.

```csharp
// Infoga en cell i automatisk storlek.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 De`PreferredWidth.Auto` inställningen tillåter den här cellen att expandera eller dra ihop sig baserat på det utrymme som finns kvar efter att de andra cellerna har tagits med i beräkningen. Detta säkerställer att bordslayouten ser balanserad och professionell ut.

## Steg 5: Slutför och spara dokumentet

När du har infogat alla dina celler, fyll i tabellen och spara dokumentet till din angivna sökväg.

```csharp
// Spara dokumentet.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Det här steget slutför tabellen och sparar dokumentet med filnamnet "WorkingWithTables.PreferredWidthSettings.docx" i din angivna katalog.

## Slutsats

Att skapa tabeller med önskade breddinställningar i Aspose.Words för .NET är enkelt när du förstår de olika storleksalternativen som finns tillgängliga. Oavsett om du behöver fasta, relativa eller automatiska cellbredder ger Aspose.Words flexibiliteten att hantera olika scenarier för tabelllayout effektivt. Genom att följa stegen som beskrivs i den här guiden kan du säkerställa att dina tabeller är välstrukturerade och visuellt tilltalande i dina Word-dokument.

## FAQ's

### Vad är skillnaden mellan absoluta och relativa cellbredder?
Absoluta cellbredder är fasta och ändras inte, medan relativa bredder justeras baserat på tabellens totala bredd.

### Kan jag använda negativa procentsatser för relativa bredder?
Nej, negativa procentsatser är inte giltiga för cellbredder. Endast positiva procentsatser är tillåtna.

### Hur fungerar funktionen för automatisk dimensionering?
Automatisk storlek justerar cellens bredd för att fylla eventuellt kvarvarande utrymme i tabellen efter att andra celler har dimensionerats.

### Kan jag använda olika stilar på celler med olika breddinställningar?
Ja, du kan använda olika stilar och formatering på celler oavsett deras breddinställningar.

### Vad händer om tabellens totala bredd är mindre än summan av alla cellbredder?
Tabellen justerar automatiskt cellbredden så att den passar inom det tillgängliga utrymmet, vilket kan göra att vissa celler krymper.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
