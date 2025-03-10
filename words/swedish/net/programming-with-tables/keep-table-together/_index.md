---
title: Håll ihop bordet
linktitle: Håll ihop bordet
second_title: Aspose.Words Document Processing API
description: Lär dig hur du förhindrar att tabeller delas över sidor i Word-dokument med Aspose.Words för .NET. Följ vår guide för att underhålla professionella, läsbara dokument.
weight: 10
url: /sv/net/programming-with-tables/keep-table-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Håll ihop bordet

## Introduktion

Har du någonsin varit frustrerad när en tabell i ditt Word-dokument är uppdelad på två sidor? Det är som att din noggrant upplagda information plötsligt bestämde sig för att ta en paus halvvägs! Att hålla ihop tabeller på en sida är avgörande för läsbarhet och presentation. Oavsett om det är för en rapport, ett projektförslag eller bara ett personligt dokument, kan det vara ganska jobbigt att ha uppdelade tabeller. Tur för oss, Aspose.Words för .NET har ett smart sätt att lösa detta problem. I den här handledningen går vi igenom stegen för att hålla dina bord intakta och ser skarpa ut. Låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande:

1.  Aspose.Words för .NET - Om du inte har installerat det ännu kan du ladda ner det från[här](https://releases.aspose.com/words/net/).
2. Ett Word-dokument med en tabell - Vi kommer att arbeta med ett exempeldokument som har en tabell som spänner över flera sidor.
3. Grundläggande kunskaper om C# - Denna handledning förutsätter att du har en grundläggande förståelse för C#-programmering.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Detta ger oss tillgång till de klasser och metoder vi behöver från Aspose.Words för .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Låt oss dela upp processen i lättsmälta steg. Vi börjar med att ladda vårt dokument och avslutar med att spara det uppdaterade dokumentet där tabellen stannar ihop.

## Steg 1: Ladda dokumentet

 För att arbeta med ett Word-dokument måste vi först ladda det. Vi kommer att använda`Document` klass för detta.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Steg 2: Gå till tabellen

Därefter måste vi få det bord vi vill hålla ihop. Vi antar att det är den första tabellen i dokumentet.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Steg 3: Ställ in KeepWithNext för stycken

 För att förhindra att tabellen delas över sidor måste vi ställa in`KeepWithNext` egenskap för varje stycke i tabellen, förutom de sista styckena i den sista raden.

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

Slutligen sparar vi det uppdaterade dokumentet. Detta kommer att tillämpa våra ändringar och säkerställa att tabellen förblir tillsammans på en sida.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Slutsats

Och där har du det! Med bara några rader kod kan du förhindra att dina tabeller delas över sidor i dina Word-dokument. Denna enkla men effektiva lösning säkerställer att dina bord förblir snygga och professionella, vilket förbättrar läsbarheten för dina dokument. Aspose.Words för .NET gör det enkelt att hantera sådana formateringsproblem, vilket gör att du kan fokusera på att skapa bra innehåll.

## FAQ's

### Kan jag hålla flera tabeller tillsammans med den här metoden?  
Ja, du kan tillämpa samma logik på flera tabeller genom att iterera genom varje tabell i ditt dokument.

### Vad händer om mitt bord är för stort för att få plats på en sida?  
Om en tabell är för stor för att få plats på en enda sida spänner den fortfarande över sidorna. Denna metod säkerställer att mindre bord förblir intakta utan att delas.

### Finns det något sätt att automatisera detta för alla tabeller i ett dokument?  
 Ja, du kan gå igenom alla tabeller i ditt dokument och använda`KeepWithNext` egendom till varje stycke.

### Behöver jag en betald licens för Aspose.Words för .NET?  
Du kan börja med en gratis provperiod från[här](https://releases.aspose.com/), men för full funktionalitet rekommenderas en betald licens.

### Kan jag använda annan formatering på tabellen samtidigt som jag håller ihop den?  
Absolut! Du kan formatera din tabell efter behov samtidigt som du ser till att den förblir ihop på en sida.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
