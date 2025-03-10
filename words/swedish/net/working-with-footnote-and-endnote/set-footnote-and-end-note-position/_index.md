---
title: Ställ in fotnots- och slutnotposition
linktitle: Ställ in fotnots- och slutnotposition
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in fotnots- och slutnotspositioner i Word-dokument med Aspose.Words för .NET med denna detaljerade steg-för-steg-guide.
weight: 10
url: /sv/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in fotnots- och slutnotposition

## Introduktion

Om du arbetar med Word-dokument och behöver hantera fotnoter och slutnoter effektivt, är Aspose.Words för .NET ditt favoritbibliotek. Den här handledningen går igenom hur du ställer in fotnots- och slutnotpositioner i ett Word-dokument med Aspose.Words för .NET. Vi kommer att dela upp varje steg för att göra det enkelt att följa och implementera.

## Förutsättningar

Innan du dyker in i handledningen, se till att du har följande:

-  Aspose.Words för .NET Library: Du kan ladda ner det från[här](https://releases.aspose.com/words/net/).
- Visual Studio: Alla nyare versioner fungerar bra.
- Grundläggande kunskaper om C#: Att förstå grunderna hjälper dig att enkelt följa med.

## Importera namnområden

Importera först de nödvändiga namnrymden i ditt C#-projekt:

```csharp
using System;
using Aspose.Words;
```

## Steg 1: Ladda Word-dokumentet

För att börja måste du ladda ditt Word-dokument i Aspose.Words Document-objektet. Detta gör att du kan manipulera dokumentets innehåll.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 den här koden, ersätt`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där ditt dokument finns.

## Steg 2: Ställ in fotnotsposition

Därefter ställer du in positionen för fotnoterna. Aspose.Words för .NET låter dig placera fotnoter antingen längst ner på sidan eller under texten.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

 Här har vi angett att fotnoterna ska visas under texten. Om du föredrar dem längst ner på sidan, använd`FootnotePosition.BottomOfPage`.

## Steg 3: Ställ in slutnotposition

På samma sätt kan du ställa in slutnoternas position. Slutnoter kan placeras antingen i slutet av avsnittet eller i slutet av dokumentet.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

 I det här exemplet placeras slutnoter i slutet av varje avsnitt. För att placera dem i slutet av dokumentet, använd`EndnotePosition.EndOfDocument`.

## Steg 4: Spara dokumentet

Spara slutligen dokumentet för att tillämpa ändringarna. Se till att du anger rätt sökväg och namn för utdatadokumentet.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Den här raden sparar det ändrade dokumentet i din angivna katalog.

## Slutsats

Att ställa in fotnots- och slutnotspositioner i Word-dokument med Aspose.Words för .NET är enkelt när du känner till stegen. Genom att följa den här guiden kan du anpassa dina dokument så att de passar dina behov, och se till att fotnoter och slutnoter placeras exakt där du vill ha dem.

## FAQ's

### Kan jag ställa in olika positioner för enskilda fotnoter eller slutnoter?

Nej, Aspose.Words för .NET ställer in positionen för alla fotnoter och slutnoter i ett dokument enhetligt.

### Är Aspose.Words för .NET kompatibelt med alla versioner av Word-dokument?

Ja, Aspose.Words för .NET stöder ett brett utbud av Word-dokumentformat, inklusive DOC, DOCX, RTF och mer.

### Kan jag använda Aspose.Words för .NET med andra programmeringsspråk?

Aspose.Words för .NET är designat för .NET-applikationer, men du kan använda det med alla .NET-stödda språk som C#, VB.NET, etc.

### Finns det en gratis testversion tillgänglig för Aspose.Words för .NET?

 Ja, du kan få en gratis provperiod[här](https://releases.aspose.com/).

### Var kan jag hitta mer detaljerad dokumentation för Aspose.Words för .NET?

 Detaljerad dokumentation finns tillgänglig[här](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
