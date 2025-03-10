---
title: Använd konturgräns
linktitle: Använd konturgräns
second_title: Aspose.Words Document Processing API
description: Lär dig hur du tillämpar en konturram på en tabell i Word med Aspose.Words för .NET. Följ vår steg-för-steg-guide för perfekt tabellformatering.
weight: 10
url: /sv/net/programming-with-table-styles-and-formatting/apply-outline-border/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Använd konturgräns

## Introduktion

dagens självstudie dyker vi in i världen av dokumentmanipulation med Aspose.Words för .NET. Specifikt ska vi lära oss hur man applicerar en konturram på en tabell i ett Word-dokument. Detta är en fantastisk färdighet att ha i din verktygslåda om du ofta arbetar med automatiserad dokumentgenerering och formatering. Så låt oss börja på denna resa för att göra dina bord inte bara funktionella utan också visuellt tilltalande.

## Förutsättningar

Innan vi hoppar in i koden finns det några saker du behöver:

1.  Aspose.Words för .NET: Du måste ha Aspose.Words för .NET installerat. Du kan ladda ner den[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En lämplig utvecklingsmiljö som Visual Studio.
3. Grundläggande kunskaper om C#: En grundläggande förståelse för C# hjälper dig att följa handledningen.

## Importera namnområden

Till att börja med, se till att du har de nödvändiga namnrymden importerade. Detta är avgörande för att få tillgång till Aspose.Words-funktioner.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Låt oss dela upp processen i enkla, hanterbara steg.

## Steg 1: Ladda dokumentet

Först måste vi ladda Word-dokumentet som innehåller tabellen vi vill formatera.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

 I det här steget använder vi`Document` klass från Aspose.Words för att ladda ett befintligt dokument. Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där ditt dokument är lagrat.

## Steg 2: Gå till tabellen

Därefter måste vi komma åt den specifika tabell vi vill formatera. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

 Här,`GetChild` metoden hämtar den första tabellen i dokumentet. Parametrarna`NodeType.Table, 0, true` se till att vi får rätt nodtyp.

## Steg 3: Rikta in tabellen

Låt oss nu centrera tabellen på sidan.

```csharp
table.Alignment = TableAlignment.Center;
```

Detta steg säkerställer att bordet är snyggt centrerat, vilket ger det ett professionellt utseende.

## Steg 4: Rensa befintliga gränser

Innan vi tillämpar nya gränser måste vi rensa eventuella befintliga.

```csharp
table.ClearBorders();
```

Att rensa gränserna säkerställer att våra nya gränser appliceras rent utan att några gamla stilar stör.

## Steg 5: Ställ in konturgränser

Låt oss nu tillämpa de gröna konturkanterna på tabellen.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

 Varje kanttyp (vänster, höger, topp, botten) ställs in individuellt. Vi använder`LineStyle.Single` för en heldragen linje,`1.5` för linjebredden, och`Color.Green` för kantfärgen.

## Steg 6: Använd cellskuggning

För att göra bordet mer visuellt tilltalande, låt oss fylla cellerna med en ljusgrön färg.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

 Här,`SetShading` används för att applicera en fast ljusgrön färg på cellerna, vilket gör att bordet sticker ut.

## Steg 7: Spara dokumentet

Spara slutligen det ändrade dokumentet.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Detta steg sparar ditt dokument med den tillämpade formateringen. Du kan öppna den för att se den vackert formaterade tabellen.

## Slutsats

Och där har du det! Genom att följa dessa steg har du lyckats tillämpa en konturram på en tabell i ett Word-dokument med Aspose.Words för .NET. Denna handledning handlade om att ladda dokumentet, komma åt tabellen, justera den, rensa befintliga ramar, använda nya ramar, lägga till cellskuggning och slutligen spara dokumentet. 

Med dessa färdigheter kan du förbättra den visuella presentationen av dina tabeller, vilket gör dina dokument mer professionella och tilltalande. Glad kodning!

## FAQ's

### Kan jag använda olika stilar på varje kant i tabellen?  
 Ja, du kan använda olika stilar och färger på varje kant genom att justera parametrarna i`SetBorder` metod.

### Hur kan jag ändra bredden på kanten?  
 Du kan ändra bredden genom att ändra den tredje parametern i`SetBorder` metod. Till exempel,`1.5` ställer in en bredd på 1,5 poäng.

### Är det möjligt att applicera skuggning på enskilda celler?  
 Ja, du kan tillämpa skuggning på enskilda celler genom att komma åt varje cell och använda`SetShading` metod.

### Kan jag använda andra färger för kanter och skuggning?  
 Absolut! Du kan använda vilken färg som helst i`System.Drawing.Color` klass.

### Hur centrerar jag bordet horisontellt?  
 De`table.Alignment = TableAlignment.Center;` raden i koden centrerar tabellen horisontellt på sidan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
