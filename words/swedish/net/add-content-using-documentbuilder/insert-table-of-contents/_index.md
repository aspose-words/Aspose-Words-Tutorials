---
title: Infoga innehållsförteckning i Word-dokument
linktitle: Infoga innehållsförteckning i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du infogar en innehållsförteckning i Word med Aspose.Words för .NET. Följ vår steg-för-steg-guide för sömlös dokumentnavigering.
weight: 10
url: /sv/net/add-content-using-documentbuilder/insert-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga innehållsförteckning i Word-dokument

## Introduktion
den här handledningen lär du dig hur du effektivt lägger till en innehållsförteckning (TOC) till dina Word-dokument med Aspose.Words för .NET. Den här funktionen är viktig för att organisera och navigera i långa dokument, förbättra läsbarheten och ge en snabb överblick över dokumentavsnitt.

## Förutsättningar

Innan du börjar, se till att du har följande:

- Grundläggande förståelse för C# och .NET framework.
- Visual Studio installerat på din dator.
-  Aspose.Words för .NET-bibliotek. Om du inte har installerat det ännu kan du ladda ner det från[här](https://releases.aspose.com/words/net/).

## Importera namnområden

För att komma igång, importera de nödvändiga namnrymden i ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

Låt oss dela upp processen i tydliga steg:

## Steg 1: Initiera Aspose.Words Document and DocumentBuilder

 Initiera först en ny Aspose.Words`Document` föremål och ett`DocumentBuilder` att arbeta med:

```csharp
// Initiera Document och DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga innehållsförteckningen

 Infoga nu innehållsförteckningen med hjälp av`InsertTableOfContents` metod:

```csharp
// Infoga innehållsförteckning
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## Steg 3: Starta dokumentinnehåll på en ny sida

För att säkerställa korrekt formatering, starta det faktiska dokumentinnehållet på en ny sida:

```csharp
// Infoga en sidbrytning
builder.InsertBreak(BreakType.PageBreak);
```

## Steg 4: Strukturera ditt dokument med rubriker

Organisera ditt dokumentinnehåll med lämpliga rubrikstilar:

```csharp
// Ställ in rubrikstilar
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## Steg 5: Uppdatera och fyll i innehållsförteckningen

Uppdatera innehållsförteckningen för att återspegla dokumentstrukturen:

```csharp
// Uppdatera innehållsförteckningsfälten
doc.UpdateFields();
```

## Steg 6: Spara dokumentet

Slutligen, spara ditt dokument i en angiven katalog:

```csharp
// Spara dokumentet
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## Slutsats

Att lägga till en innehållsförteckning med Aspose.Words för .NET är enkelt och förbättrar användbarheten av dina dokument avsevärt. Genom att följa dessa steg kan du effektivt organisera och navigera genom komplexa dokument.

## FAQ's

### Kan jag anpassa utseendet på innehållsförteckningen?
Ja, du kan anpassa utseendet och beteendet hos innehållsförteckningen med Aspose.Words för .NET API:er.

### Stöder Aspose.Words att uppdatera fält automatiskt?
Ja, Aspose.Words låter dig uppdatera fält som innehållsförteckning dynamiskt baserat på dokumentändringar.

### Kan jag skapa flera innehållsförteckningar i ett enda dokument?
Aspose.Words stöder generering av flera innehållsförteckningar med olika inställningar i ett enda dokument.

### Är Aspose.Words kompatibel med olika versioner av Microsoft Word?
Ja, Aspose.Words säkerställer kompatibilitet med olika versioner av Microsoft Word-format.

### Var kan jag hitta mer hjälp och support för Aspose.Words?
 För mer hjälp, besök[Aspose.Words Forum](https://forum.aspose.com/c/words/8) eller kolla in[officiell dokumentation](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
