---
"description": "Lär dig hur du förhindrar att tabeller bryts över sidor i Word-dokument med hjälp av Aspose.Words för .NET. Följ vår guide för att underhålla professionella, läsbara dokument."
"linktitle": "Håll ihop bordet"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Håll ihop bordet"
"url": "/sv/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Håll ihop bordet

## Introduktion

Har du någonsin känt dig frustrerad när en tabell i ditt Word-dokument delas upp över två sidor? Det är som om din noggrant upplagda information plötsligt bestämmer sig för att ta en paus halvvägs! Att hålla tabeller samlade på en sida är avgörande för läsbarhet och presentation. Oavsett om det är för en rapport, ett projektförslag eller bara ett personligt dokument kan det vara ganska irriterande att ha tabeller delade. Som tur är för oss har Aspose.Words för .NET ett smidigt sätt att lösa problemet. I den här handledningen går vi igenom stegen för att hålla dina tabeller intakta och snygga. Nu kör vi!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET - Om du inte har installerat det än kan du ladda ner det från [här](https://releases.aspose.com/words/net/).
2. Ett Word-dokument med en tabell – Vi kommer att arbeta med ett exempeldokument som har en tabell som sträcker sig över flera sidor.
3. Grundläggande kunskaper i C# – Den här handledningen förutsätter att du har grundläggande förståelse för C#-programmering.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna. Detta ger oss tillgång till de klasser och metoder vi behöver från Aspose.Words för .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Låt oss dela upp processen i enkla, lättsmälta steg. Vi börjar med att ladda vårt dokument och avslutar med att spara det uppdaterade dokumentet där tabellen förblir sammanhållen.

## Steg 1: Ladda dokumentet

För att arbeta med ett Word-dokument måste vi först ladda det. Vi använder `Document` klass för detta.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Steg 2: Åtkomst till tabellen

Sedan behöver vi hitta den tabell vi vill hålla ihop. Vi antar att det är den första tabellen i dokumentet.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Steg 3: Ställ in KeepWithNext för stycken

För att förhindra att tabellen bryts över sidor måste vi ställa in `KeepWithNext` egenskap för varje stycke i tabellen, förutom de sista styckena på den sista raden.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Steg 4: Spara dokumentet

Slutligen sparar vi det uppdaterade dokumentet. Detta kommer att tillämpa våra ändringar och säkerställa att tabellen förblir samlad på en sida.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Slutsats

Och där har du det! Med bara några få rader kod kan du förhindra att dina tabeller delas upp över sidor i dina Word-dokument. Denna enkla men effektiva lösning säkerställer att dina tabeller förblir snygga och professionella, vilket förbättrar läsbarheten i dina dokument. Aspose.Words för .NET gör det enkelt att hantera sådana formateringsproblem, så att du kan fokusera på att skapa bra innehåll.

## Vanliga frågor

### Kan jag hålla flera tabeller tillsammans med den här metoden?  
Ja, du kan tillämpa samma logik på flera tabeller genom att iterera igenom varje tabell i ditt dokument.

### Vad händer om min tabell är för stor för att få plats på en sida?  
Om en tabell är för stor för att få plats på en enda sida, kommer den fortfarande att sträcka sig över sidor. Den här metoden säkerställer att mindre tabeller förblir intakta utan att delas.

### Finns det något sätt att automatisera detta för alla tabeller i ett dokument?  
Ja, du kan loopa igenom alla tabeller i ditt dokument och tillämpa `KeepWithNext` egenskap till varje stycke.

### Behöver jag en betald licens för Aspose.Words för .NET?  
Du kan börja med en gratis provperiod från [här](https://releases.aspose.com/), men för full funktionalitet rekommenderas en betald licens.

### Kan jag använda annan formatering på tabellen samtidigt som jag håller ihop den?  
Absolut! Du kan formatera din tabell efter behov samtidigt som du ser till att den hålls samlad på en sida.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}