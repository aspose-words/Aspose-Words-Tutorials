---
title: Håll ihop bordet
linktitle: Håll ihop bordet
second_title: Aspose.Words Document Processing API
description: Lär dig hur du förhindrar tabeller från att delas över sidor med Aspose.Words för .NET med denna steg-för-steg-guide. Säkerställ snygga, professionella Word-dokument
weight: 10
url: /sv/net/join-and-append-documents/keep-source-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Håll ihop bordet

## Introduktion

Tabeller är en viktig del av många Word-dokument, men ibland kan du stöta på en situation där din tabell delas över två sidor. Detta kan störa flödet av ditt dokument och påverka dess läsbarhet. Skulle det inte vara trevligt om det fanns ett sätt att hålla ihop hela bordet på en sida? Tja, med Aspose.Words för .NET finns det en enkel lösning på detta problem! I den här självstudien går vi igenom hur du förhindrar att tabeller delas upp på sidorna och ser till att ditt dokument ser snyggt och professionellt ut.

## Förutsättningar

Innan vi hoppar in i handledningen, låt oss se till att du har allt du behöver för att följa smidigt.

### Aspose.Words för .NET Library

Först måste du ha Aspose.Words för .NET installerat. Detta är det kraftfulla biblioteket som låter dig arbeta med Word-dokument programmatiskt.

- [Ladda ner Aspose.Words för .NET](https://releases.aspose.com/words/net/)

### Utvecklingsmiljö

Du bör ha en utvecklingsmiljö inställd för att köra C#-kod, till exempel:

- Visual Studio (alla nyare versioner)
- .NET Framework 2.0 eller senare

### Ett Word-dokument med en tabell

 Du behöver ett Word-dokument som innehåller en tabell. I den här handledningen kommer vi att arbeta med ett exempeldokument som heter`"Table spanning two pages.docx"`. Den här filen innehåller en tabell som för närvarande sträcker sig över två sidor.

### Tillfällig licens (valfritt)

 Medan Aspose.Words kommer med en gratis provperiod, kanske du vill använda en[tillfällig licens](https://purchase.aspose.com/temporary-license/) för att låsa upp bibliotekets fulla potential.

## Importera paket

Innan vi skriver någon kod måste vi importera de nödvändiga namnrymden för att arbeta med Aspose.Words för .NET. Lägg till följande importer överst i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

 Dessa namnrymder ger dig tillgång till klasser som`Document`, `Table`, `Cell`, och andra som vi kommer att använda i den här handledningen.

## Steg 1: Ladda dokumentet

 Det första vi behöver göra är att ladda Word-dokumentet som innehåller tabellen. För detta kommer vi att använda`Document` klass från Aspose.Words. Denna klass låter dig öppna och manipulera Word-filer programmatiskt.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

 I det här kodavsnittet anger vi platsen för vårt dokument. Ersätta`"YOUR DOCUMENTS DIRECTORY"` med den faktiska katalogen där ditt dokument är lagrat.

## Steg 2: Gå till tabellen

När dokumentet är laddat är nästa steg att komma åt tabellen som vi vill hålla ihop. I det här exemplet antar vi att tabellen är den första tabellen i dokumentet.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

 Denna kodrad hittar den första tabellen i dokumentet. De`GetChild` metod hämtar en specifik typ av nod, vilket i det här fallet är`NodeType.Table` . De`0` indikerar att vi vill ha den första tabellen och`true`flaggan ser till att vi söker rekursivt genom alla underordnade noder.

## Steg 3: Slinga genom tabellceller

Nu måste vi gå igenom varje cell i tabellen. Eftersom en tabell innehåller flera rader och varje rad innehåller flera celler, går vi igenom varje cell och säkerställer att den inte delas över sidor.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

 Här,`GetChildNodes` hämtar alla celler i tabellen, och vi går igenom var och en av dem. De`EnsureMinimum()` metod ser till att varje cell innehåller minst ett stycke, eftersom en tom cell kan orsaka problem senare.

## Steg 4: Ställ in KeepWithNext-egenskapen

 För att förhindra att tabellen delas över sidor måste vi ställa in`KeepWithNext` egenskap för varje stycke i tabellen. Den här egenskapen säkerställer att stycket förblir med nästa stycke, vilket effektivt förhindrar sidbrytningar mellan dem.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

 Denna loop kontrollerar varje stycke i varje cell. Villkoret säkerställer att vi inte tillämpar`KeepWithNext`egenskap till sista stycket i sista raden. Annars skulle egendomen inte ha någon effekt eftersom det inte finns något nästa stycke.

## Steg 5: Spara dokumentet

 Slutligen, efter att ha tillämpat`KeepWithNext` egenskap måste vi spara det ändrade dokumentet.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Den här raden sparar det uppdaterade dokumentet med ett nytt namn och bevarar originalfilen. Du kan nu öppna den resulterande filen och se att tabellen inte längre är uppdelad på två sidor!

## Slutsats

Och där har du det! Genom att följa dessa enkla steg kan du enkelt förhindra att tabeller delas över sidor i Word-dokument med Aspose.Words för .NET. Oavsett om du arbetar med rapporter, kontrakt eller andra dokument, garanterar att hålla tabellerna intakta ett mer polerat, professionellt utseende.

Det fina med Aspose.Words är dess flexibilitet och användarvänlighet, vilket gör att du kan manipulera Word-dokument programmatiskt utan att behöva Microsoft Word installerat på din maskin. Nu när du har hunnit med att hålla ihop tabeller kan du utforska andra funktioner i biblioteket för att ta dina färdigheter i dokumentbehandling till nästa nivå!

## FAQ's

### Varför delas min tabell fortfarande över sidor efter att ha använt den här koden?

 Om ditt bord fortfarande går sönder, se till att du har tillämpat`KeepWithNext` egendom korrekt. Dubbelkolla att alla stycken utom det sista i varje cell har denna egenskap.

### Kan jag bara hålla ihop specifika rader?

 Ja, du kan selektivt tillämpa`KeepWithNext` egenskap till specifika rader eller stycken i tabellen för att styra vilka delar som ska hålla ihop.

### Fungerar den här metoden med stora bord?

För mycket stora tabeller kan Word fortfarande dela upp dem över sidor om det inte finns tillräckligt med utrymme för att få plats med hela tabellen på en sida. Överväg att justera tabellens formatering eller marginaler för att passa större tabeller.

### Kan jag använda den här metoden med andra dokumentformat?

Ja! Aspose.Words för .NET stöder många format som DOC, DOCX, PDF och andra. Samma metod fungerar i alla format som stöder tabeller.

### Är Aspose.Words för .NET ett gratis bibliotek?

 Aspose.Words för .NET erbjuder en gratis provperiod, men för full tillgång till alla funktioner måste du köpa en licens. Du kan utforska licensalternativ på[Aspose köpsida](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
