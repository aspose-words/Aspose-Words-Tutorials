---
"description": "Lär dig hur du skapar listor med flera nivåer med mellanslag i Aspose.Words för .NET. Steg-för-steg-guide för exakt dokumentformatering."
"linktitle": "Använd mellanslagstecken per nivå för listindrag"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Använd mellanslagstecken per nivå för listindrag"
"url": "/sv/net/programming-with-txtsaveoptions/use-space-character-per-level-for-list-indentation/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använd mellanslagstecken per nivå för listindrag

## Introduktion

När det gäller dokumentformatering, särskilt när man arbetar med listor, är precision nyckeln. I scenarier där du behöver skapa dokument med olika nivåer av indentering erbjuder Aspose.Words för .NET kraftfulla verktyg för att hantera denna uppgift. En särskild funktion som kan vara praktisk är att konfigurera listindrag i textfiler. Den här guiden guidar dig genom hur du använder mellanslagstecken för listindrag, vilket säkerställer att ditt dokument bibehåller önskad struktur och läsbarhet.

## Förkunskapskrav

Innan du börjar med handledningen behöver du följande:

- Aspose.Words för .NET: Se till att du har Aspose.Words-biblioteket installerat. Om du inte redan har det kan du ladda ner det från [Aspose webbplats](https://releases.aspose.com/words/net/).
- Visual Studio: En utvecklingsmiljö för att skriva och testa din kod.
- Grundläggande förståelse för C#: Bekantskap med C# och .NET framework hjälper dig att följa stegen smidigt.

## Importera namnrymder

För att börja arbeta med Aspose.Words måste du importera de nödvändiga namnrymderna. Så här kan du inkludera dem i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Låt oss gå igenom processen för att skapa ett dokument med en lista med flera nivåer och ange mellanslag för indentering. 

## Steg 1: Konfigurera ditt dokument

Först måste du skapa ett nytt dokument och initiera det `DocumentBuilder` objekt. Det här objektet låter dig enkelt lägga till innehåll och formatera det efter behov.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Skapa dokumentet och lägg till innehåll
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

I det här utdraget, ersätt `"YOUR DOCUMENTS DIRECTORY"` med den faktiska sökvägen där du vill spara dokumentet.

## Steg 2: Skapa en lista med flera indragningsnivåer

Med den `DocumentBuilder` till exempel kan du nu skapa en lista med olika nivåer av indentering. Använd `ListFormat` egenskapen för att tillämpa numrering och dra in listobjekten efter behov.

```csharp
// Skapa en lista med tre nivåer av indentering
builder.ListFormat.ApplyNumberDefault();
builder.Write("Element 1");
builder.ListFormat.ListIndent();
builder.Write("Element 2");
builder.ListFormat.ListIndent();
builder.Write("Element 3");
```

I det här steget, `ApplyNumberDefault` ställer in listformatet, och `ListIndent` används för att öka indragsnivån för varje efterföljande listobjekt.

## Steg 3: Konfigurera mellanslagstecken för indrag

Nu när du har konfigurerat din lista är nästa steg att konfigurera hur listindraget hanteras när dokumentet sparas till en textfil. Du kommer att använda `TxtSaveOptions` för att ange att mellanslagstecken ska användas för indentering.

```csharp
// Använd ett mellanslag per nivå för listindrag
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.ListIndentation.Count = 3;
saveOptions.ListIndentation.Character = ' ';
```

Här, `ListIndentation.Count` anger antalet mellanslagstecken per indragningsnivå, och `ListIndentation.Character` anger det faktiska tecknet som används för indentering.

## Steg 4: Spara dokumentet med de angivna alternativen

Slutligen sparar du dokumentet med de konfigurerade alternativen. Detta tillämpar indragsinställningarna och sparar filen i önskat format.

```csharp
// Spara dokumentet med de angivna alternativen
doc.Save(dataDir + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
```

Det här kodavsnittet sparar dokumentet till den sökväg som anges i `dataDir` med filnamnet `"WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt"`Den sparade filen kommer att ha listan formaterad enligt dina indragsinställningar.

## Slutsats

Genom att följa dessa steg har du skapat ett dokument med listindrag på flera nivåer med mellanslag för formatering. Denna metod säkerställer att dina listor är välstrukturerade och lättlästa, även när de sparas som textfiler. Aspose.Words för .NET tillhandahåller robusta verktyg för dokumenthantering, och att behärska dessa funktioner kan avsevärt förbättra dina arbetsflöden för dokumentbehandling.

## Vanliga frågor

### Kan jag använda andra tecken för listindrag förutom mellanslag?
Ja, du kan ange olika tecken för listindrag genom att ställa in `Character` fastighet i `TxtSaveOptions`.

### Hur använder jag punktlistor istället för siffror i listor?
Använda `ListFormat.ApplyBulletDefault()` i stället för `ApplyNumberDefault()` för att skapa en punktlista.

### Kan jag justera antalet mellanslag för indentering dynamiskt?
Ja, du kan justera `ListIndentation.Count` egenskap för att ställa in antalet utrymmen baserat på dina krav.

### Är det möjligt att ändra listans indrag efter att dokumentet har skapats?
Ja, du kan ändra listformatering och indenteringsinställningar när som helst innan du sparar dokumentet.

### Vilka andra dokumentformat stöder listindragningsinställningar?
Förutom textfiler kan listindragningsinställningar tillämpas på andra format som DOCX, PDF och HTML när Aspose.Words används.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}