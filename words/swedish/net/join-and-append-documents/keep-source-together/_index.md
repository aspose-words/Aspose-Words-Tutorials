---
"description": "Lär dig hur du förhindrar att tabeller bryts över sidor med Aspose.Words för .NET med den här steg-för-steg-guiden. Säkerställ snygga, professionella Word-dokument."
"linktitle": "Håll ihop bordet"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Håll ihop bordet"
"url": "/sv/net/join-and-append-documents/keep-source-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Håll ihop bordet

## Introduktion

Tabeller är en viktig del av många Word-dokument, men ibland kan det hända att tabellen delas upp över två sidor. Detta kan störa dokumentets flöde och påverka dess läsbarhet. Skulle det inte vara trevligt om det fanns ett sätt att hålla hela tabellen samlad på en sida? Med Aspose.Words för .NET finns det en enkel lösning på problemet! I den här handledningen går vi igenom hur du förhindrar att tabeller delas upp över sidor, vilket säkerställer att ditt dokument ser snyggt och professionellt ut.

## Förkunskapskrav

Innan vi börjar med handledningen, låt oss se till att du har allt du behöver för att följa den smidigt.

### Aspose.Words för .NET-biblioteket

Först måste du ha Aspose.Words för .NET installerat. Detta är det kraftfulla biblioteket som låter dig arbeta med Word-dokument programmatiskt.

- [Ladda ner Aspose.Words för .NET](https://releases.aspose.com/words/net/)

### Utvecklingsmiljö

Du bör ha en utvecklingsmiljö konfigurerad för att köra C#-kod, till exempel:

- Visual Studio (alla nyare versioner)
- .NET Framework 2.0 eller senare

### Ett Word-dokument med en tabell

Du behöver ett Word-dokument som innehåller en tabell. I den här handledningen kommer vi att arbeta med ett exempeldokument som heter `"Table spanning two pages.docx"`Den här filen innehåller en tabell som för närvarande sträcker sig över två sidor.

### Tillfällig licens (valfritt)

Även om Aspose.Words har en gratis provperiod kanske du vill använda en [tillfällig licens](https://purchase.aspose.com/temporary-license/) för att frigöra bibliotekets fulla potential.

## Importera paket

Innan vi skriver någon kod måste vi importera de namnrymder som krävs för att arbeta med Aspose.Words för .NET. Lägg till följande importfiler högst upp i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dessa namnrymder ger dig tillgång till klasser som `Document`, `Table`, `Cell`och andra som vi kommer att använda i den här handledningen.

## Steg 1: Ladda dokumentet

Det första vi behöver göra är att ladda Word-dokumentet som innehåller tabellen. För detta använder vi `Document` klassen från Aspose.Words. Den här klassen låter dig öppna och manipulera Word-filer programmatiskt.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

I det här kodavsnittet anger vi platsen för vårt dokument. Ersätt `"YOUR DOCUMENTS DIRECTORY"` med den faktiska katalogen där ditt dokument är lagrat.

## Steg 2: Åtkomst till tabellen

När dokumentet har laddats är nästa steg att komma åt tabellen som vi vill hålla ihop. I det här exemplet antar vi att tabellen är den första tabellen i dokumentet.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Den här kodraden hittar den första tabellen i dokumentet. `GetChild` metoden hämtar en specifik typ av nod, vilket i detta fall är `NodeType.Table`Den `0` indikerar att vi vill ha den första tabellen, och `true` flaggan säkerställer att vi söker rekursivt igenom alla underordnade noder.

## Steg 3: Loopa igenom tabellceller

Nu behöver vi loopa igenom varje cell i tabellen. Eftersom en tabell innehåller flera rader och varje rad innehåller flera celler, kommer vi att iterera igenom varje cell och se till att den inte bryts över sidor.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

Här, `GetChildNodes` hämtar alla celler i tabellen, och vi loopar igenom var och en av dem. `EnsureMinimum()` Metoden ser till att varje cell innehåller minst ett stycke, eftersom en tom cell kan orsaka problem senare.

## Steg 4: Ställ in egenskapen KeepWithNext

För att förhindra att tabellen bryts över sidor måste vi ställa in `KeepWithNext` egenskap för varje stycke i tabellen. Den här egenskapen säkerställer att stycket stannar kvar i nästa stycke, vilket effektivt förhindrar sidbrytningar mellan dem.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

Den här loopen kontrollerar varje stycke i varje cell. Villkoret säkerställer att vi inte tillämpar `KeepWithNext` egenskapen till det sista stycket på den sista raden. Annars skulle egenskapen inte ha någon effekt eftersom det inte finns något nästa stycke.

## Steg 5: Spara dokumentet

Slutligen, efter att ha applicerat `KeepWithNext` egenskapen måste vi spara det ändrade dokumentet.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Den här raden sparar det uppdaterade dokumentet med ett nytt namn, och bevarar originalfilen. Du kan nu öppna den resulterande filen och se att tabellen inte längre är uppdelad på två sidor!

## Slutsats

Och där har du det! Genom att följa dessa enkla steg kan du enkelt förhindra att tabeller bryts över sidor i Word-dokument med hjälp av Aspose.Words för .NET. Oavsett om du arbetar med rapporter, kontrakt eller andra dokument, ger det ett mer polerat och professionellt utseende att behålla tabellerna intakta.

Det fina med Aspose.Words är dess flexibilitet och användarvänlighet, vilket gör att du kan manipulera Word-dokument programmatiskt utan att behöva Microsoft Word installerat på din dator. Nu när du har fått kläm på att hålla ihop tabeller kan du utforska andra funktioner i biblioteket för att ta dina dokumentbehandlingsfärdigheter till nästa nivå!

## Vanliga frågor

### Varför bryts min tabell fortfarande över olika sidor efter att jag har använt den här koden?

Om ditt bord fortfarande går sönder, se till att du har applicerat `KeepWithNext` egenskapen korrekt. Dubbelkolla att alla stycken utom det sista i varje cell har den här egenskapen inställd.

### Kan jag bara hålla ihop specifika rader?

Ja, du kan selektivt tillämpa `KeepWithNext` egenskapen till specifika rader eller stycken i tabellen för att styra vilka delar som ska hållas ihop.

### Fungerar den här metoden med stora tabeller?

För mycket stora tabeller kan Word fortfarande dela upp dem över sidor om det inte finns tillräckligt med utrymme för att få plats med hela tabellen på en sida. Överväg att justera tabellens formatering eller marginaler för att anpassa den till större tabeller.

### Kan jag använda den här metoden med andra dokumentformat?

Ja! Aspose.Words för .NET stöder många format som DOC, DOCX, PDF och andra. Samma metod fungerar i alla format som stöder tabeller.

### Är Aspose.Words för .NET ett gratis bibliotek?

Aspose.Words för .NET erbjuder en gratis provperiod, men för fullständig åtkomst till alla funktioner måste du köpa en licens. Du kan utforska licensalternativ på [Aspose köpsida](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}