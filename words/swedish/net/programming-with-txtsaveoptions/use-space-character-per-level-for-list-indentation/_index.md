---
title: Använd mellanslagstecken per nivå för listindrag
linktitle: Använd mellanslagstecken per nivå för listindrag
second_title: Aspose.Words Document Processing API
description: Lär dig hur du skapar listor på flera nivåer med indrag i mellanslagstecken i Aspose.Words för .NET. Steg-för-steg-guide för exakt dokumentformatering.
weight: 10
url: /sv/net/programming-with-txtsaveoptions/use-space-character-per-level-for-list-indentation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Använd mellanslagstecken per nivå för listindrag

## Introduktion

När det gäller dokumentformatering, särskilt när man arbetar med listor, är precision nyckeln. I scenarier där du behöver skapa dokument med olika nivåer av indrag, erbjuder Aspose.Words för .NET kraftfulla verktyg för att hantera denna uppgift. En speciell funktion som kan vara praktisk är att konfigurera listindrag i textfiler. Den här guiden går igenom hur du använder blanksteg för indrag i listan, och säkerställer att ditt dokument bibehåller den önskade strukturen och läsbarheten.

## Förutsättningar

Innan du dyker in i handledningen, här är vad du behöver:

-  Aspose.Words för .NET: Se till att du har Aspose.Words-biblioteket installerat. Om du inte har det ännu kan du ladda ner det från[Aspose hemsida](https://releases.aspose.com/words/net/).
- Visual Studio: En utvecklingsmiljö för att skriva och testa din kod.
- Grundläggande förståelse för C#: Bekantskap med C# och .NET framework hjälper dig att följa med smidigt.

## Importera namnområden

För att börja arbeta med Aspose.Words måste du importera de nödvändiga namnrymden. Så här kan du inkludera dem i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Låt oss bryta ner processen för att skapa ett dokument med en lista på flera nivåer och ange mellanslag för indrag. 

## Steg 1: Konfigurera ditt dokument

 Först måste du skapa ett nytt dokument och initiera`DocumentBuilder` objekt. Detta objekt låter dig enkelt lägga till innehåll och formatera det efter behov.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Skapa dokumentet och lägg till innehåll
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 I det här utdraget, ersätt`"YOUR DOCUMENTS DIRECTORY"` med den faktiska sökvägen där du vill spara ditt dokument.

## Steg 2: Skapa en lista med flera nivåer av indrag

 Med`DocumentBuilder` t.ex. kan du nu skapa en lista med olika nivåer av indrag. Använd`ListFormat` egenskap för att tillämpa numrering och dra in listobjekten efter behov.

```csharp
// Skapa en lista med tre nivåer av indrag
builder.ListFormat.ApplyNumberDefault();
builder.Write("Element 1");
builder.ListFormat.ListIndent();
builder.Write("Element 2");
builder.ListFormat.ListIndent();
builder.Write("Element 3");
```

 I detta steg,`ApplyNumberDefault` ställer in listformatet och`ListIndent` används för att öka indragsnivån för varje efterföljande listobjekt.

## Steg 3: Konfigurera mellanslagstecken för indrag

Nu när du har konfigurerat din lista är nästa steg att konfigurera hur listindragningen hanteras när dokumentet sparas i en textfil. Du kommer att använda`TxtSaveOptions` för att ange att mellanslag ska användas för indrag.

```csharp
// Använd ett blanksteg per nivå för listindrag
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.ListIndentation.Count = 3;
saveOptions.ListIndentation.Character = ' ';
```

 Här,`ListIndentation.Count` anger antalet mellanslagstecken per indragsnivå, och`ListIndentation.Character` ställer in det faktiska tecknet som används för indrag.

## Steg 4: Spara dokumentet med de angivna alternativen

Slutligen, spara ditt dokument med de konfigurerade alternativen. Detta kommer att tillämpa indragsinställningarna och spara din fil i önskat format.

```csharp
// Spara dokumentet med de angivna alternativen
doc.Save(dataDir + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
```

 Detta kodavsnitt sparar dokumentet till den sökväg som anges i`dataDir` med filnamnet`"WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt"`. Den sparade filen kommer att ha listan formaterad enligt dina indragsinställningar.

## Slutsats

Genom att följa dessa steg har du framgångsrikt skapat ett dokument med indrag på flera nivåer med blanksteg för formatering. Detta tillvägagångssätt säkerställer att dina listor är välstrukturerade och lätta att läsa, även när de sparas som textfiler. Aspose.Words för .NET tillhandahåller robusta verktyg för dokumenthantering, och att bemästra dessa funktioner kan avsevärt förbättra dina dokumentbearbetningsarbetsflöden.

## FAQ's

### Kan jag använda olika tecken för listindrag förutom mellanslag?
 Ja, du kan ange olika tecken för listindrag genom att ställa in`Character` fastighet i`TxtSaveOptions`.

### Hur använder jag punktpunkter istället för siffror i listor?
 Använda`ListFormat.ApplyBulletDefault()` i stället för`ApplyNumberDefault()` för att skapa en punktlista.

### Kan jag justera antalet blanksteg för indrag dynamiskt?
 Ja, du kan justera`ListIndentation.Count` egenskap för att ställa in antalet utrymmen baserat på dina krav.

### Är det möjligt att ändra listindrag efter att dokumentet har skapats?
Ja, du kan när som helst ändra listformatering och indragsinställningar innan du sparar dokumentet.

### Vilka andra dokumentformat stöder listindragsinställningar?
Förutom textfiler kan listindragsinställningar tillämpas på andra format som DOCX, PDF och HTML när du använder Aspose.Words.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
