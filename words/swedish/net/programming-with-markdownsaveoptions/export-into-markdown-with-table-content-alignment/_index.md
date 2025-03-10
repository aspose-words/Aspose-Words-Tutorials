---
title: Exportera till Markdown med tabellinnehållsjustering
linktitle: Exportera till Markdown med tabellinnehållsjustering
second_title: Aspose.Words Document Processing API
description: Lär dig hur du exporterar Word-dokument till Markdown med justerade tabeller med Aspose.Words för .NET. Följ vår steg-för-steg-guide för perfekta Markdown-bord.
weight: 10
url: /sv/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportera till Markdown med tabellinnehållsjustering

## Introduktion

Hej där! Har du någonsin undrat hur du exporterar ditt Word-dokument till Markdown-format med perfekt justerade tabeller? Oavsett om du är en utvecklare som arbetar med dokumentation eller bara någon som älskar Markdown, är den här guiden för dig. Vi kommer att fördjupa oss i det smarta med att använda Aspose.Words för .NET för att uppnå detta. Är du redo att förvandla dina Word-tabeller till snyggt justerade Markdown-tabeller? Låt oss komma igång!

## Förutsättningar

Innan vi dyker in i koden finns det några saker du måste ha på plats:

1.  Aspose.Words for .NET Library: Se till att du har Aspose.Words for .NET-biblioteket. Du kan ladda ner den från[Aspose Releases Page](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Ställ in din utvecklingsmiljö. Visual Studio är ett populärt val för .NET-utveckling.
3. Grundläggande kunskaper om C#: Att förstå C# är viktigt eftersom vi kommer att skriva kod på detta språk.
4. Exempel på Word-dokument: Ha ett Word-dokument som du kan använda för att testa.

## Importera namnområden

Innan vi börjar koda, låt oss importera de nödvändiga namnrymden. Dessa ger oss tillgång till Aspose.Words-klasserna och metoderna vi kommer att använda.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Initiera Document and DocumentBuilder

Först och främst måste vi skapa ett nytt Word-dokument och initiera ett`DocumentBuilder` objekt för att börja bygga vårt dokument.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Skapa ett nytt dokument.
Document doc = new Document();

// Initiera DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga celler och justera innehåll

Därefter infogar vi några celler i vårt dokument och ställer in deras justering. Detta är avgörande för att säkerställa att Markdown-exporten behåller korrekt justering.

```csharp
// Infoga en cell och ställ in justeringen till höger.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Infoga en annan cell och ställ in justeringen till mitten.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Steg 3: Ställ in tabellinnehållsjustering för Markdown-export

 Nu är det dags att konfigurera`MarkdownSaveOptions` för att kontrollera justeringen av tabellinnehåll i den exporterade Markdown-filen. Vi sparar dokumentet med olika justeringsinställningar för att se hur det fungerar.

```csharp
// Skapa MarkdownSaveOptions-objekt.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Spara dokument med vänsterjustering.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Ändra justeringen till höger och spara.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Ändra justeringen till mitten och spara.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Steg 4: Använd automatisk justering av tabellinnehåll

 De`Auto`alignment alternativet tar justeringen från första stycket i motsvarande tabellkolumn. Detta kan vara praktiskt när du har blandade justeringar i en enda tabell.

```csharp
// Ställ in justering på Auto.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Spara dokument med automatisk justering.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Slutsats

Och där har du det! Att exportera Word-dokument till Markdown med justerade tabeller med Aspose.Words för .NET är en bris när du väl vet hur man gör. Detta kraftfulla bibliotek gör det enkelt att styra formateringen och justeringen av dina tabeller, vilket säkerställer att dina Markdown-dokument ser ut precis som du vill ha dem. Glad kodning!

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som gör det möjligt för utvecklare att skapa, ändra, konvertera och exportera Word-dokument programmatiskt.

### Kan jag ställa in olika justeringar för olika kolumner i samma tabell?
 Ja, genom att använda`Auto` justering, kan du ha olika justeringar baserat på första stycket i varje kolumn.

### Behöver jag en licens för att använda Aspose.Words för .NET?
 Ja, Aspose.Words för .NET kräver en licens för full funktionalitet. Du kan få en[tillfällig licens](https://purchase.aspose.com/temporary-license/) för utvärdering.

### Är det möjligt att exportera andra dokumentelement till Markdown med Aspose.Words?
Ja, Aspose.Words stöder export av olika element som rubriker, listor och bilder till Markdown-format.

### Var kan jag få support om jag stöter på problem?
 Du kan få stöd från[Aspose.Words Support Forum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
