---
"description": "Lär dig hur du infogar en innehållsförteckning i Word med Aspose.Words för .NET. Följ vår steg-för-steg-guide för smidig dokumentnavigering."
"linktitle": "Infoga innehållsförteckning i Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Infoga innehållsförteckning i Word-dokument"
"url": "/sv/net/add-content-using-documentbuilder/insert-table-of-contents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga innehållsförteckning i Word-dokument

## Introduktion
den här handledningen lär du dig hur du effektivt lägger till en innehållsförteckning (TOC) i dina Word-dokument med hjälp av Aspose.Words för .NET. Den här funktionen är viktig för att organisera och navigera i långa dokument, förbättra läsbarheten och ge en snabb översikt över dokumentavsnitt.

## Förkunskapskrav

Innan du börjar, se till att du har följande:

- Grundläggande förståelse för C# och .NET framework.
- Visual Studio installerat på din dator.
- Aspose.Words för .NET-biblioteket. Om du inte har installerat det än kan du ladda ner det från [här](https://releases.aspose.com/words/net/).

## Importera namnrymder

För att komma igång, importera de nödvändiga namnrymderna i ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

Låt oss dela upp processen i tydliga steg:

## Steg 1: Initiera Aspose.Words-dokumentet och DocumentBuilder

Först, initiera en ny Aspose.Words `Document` objekt och ett `DocumentBuilder` att arbeta med:

```csharp
// Initiera dokument och DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga innehållsförteckningen

Infoga nu innehållsförteckningen med hjälp av `InsertTableOfContents` metod:

```csharp
// Infoga innehållsförteckning
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## Steg 3: Starta dokumentinnehållet på en ny sida

För att säkerställa korrekt formatering, börja själva dokumentinnehållet på en ny sida:

```csharp
// Infoga en sidbrytning
builder.InsertBreak(BreakType.PageBreak);
```

## Steg 4: Strukturera ditt dokument med rubriker

Organisera ditt dokumentinnehåll med lämpliga rubrikformat:

```csharp
// Ange rubrikformat
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

Uppdatera innehållsförteckningen så att den återspeglar dokumentstrukturen:

```csharp
// Uppdatera fälten i innehållsförteckningen
doc.UpdateFields();
```

## Steg 6: Spara dokumentet

Slutligen, spara ditt dokument till en angiven katalog:

```csharp
// Spara dokumentet
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## Slutsats

Att lägga till en innehållsförteckning med Aspose.Words för .NET är enkelt och förbättrar användbarheten hos dina dokument avsevärt. Genom att följa dessa steg kan du effektivt organisera och navigera genom komplexa dokument.

## Vanliga frågor

### Kan jag anpassa utseendet på innehållsförteckningen?
Ja, du kan anpassa utseendet och beteendet för innehållsförteckningen med hjälp av Aspose.Words för .NET API:er.

### Stöder Aspose.Words automatisk uppdatering av fält?
Ja, Aspose.Words låter dig uppdatera fält som innehållsförteckning dynamiskt baserat på dokumentändringar.

### Kan jag generera flera innehållsförteckningar i ett enda dokument?
Aspose.Words stöder generering av flera innehållsförteckningar med olika inställningar i ett enda dokument.

### Är Aspose.Words kompatibelt med olika versioner av Microsoft Word?
Ja, Aspose.Words garanterar kompatibilitet med olika versioner av Microsoft Word-format.

### Var kan jag hitta mer hjälp och support för Aspose.Words?
För mer hjälp, besök [Aspose.Words Forum](https://forum.aspose.com/c/words/8) eller kolla in [officiell dokumentation](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}