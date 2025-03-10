---
title: Ställ in alternativa teckensnittsinställningar
linktitle: Ställ in alternativa teckensnittsinställningar
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in Font Fallback Settings i Aspose.Words för .NET. Den här omfattande guiden säkerställer att alla tecken i dina dokument visas korrekt.
weight: 10
url: /sv/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in alternativa teckensnittsinställningar

## Introduktion

När du arbetar med dokument som innehåller olika textelement, till exempel olika språk eller specialtecken, är det avgörande att se till att dessa element visas korrekt. Aspose.Words för .NET erbjuder en kraftfull funktion som kallas Font Fallback Settings, som hjälper till att definiera regler för att ersätta teckensnitt när det ursprungliga teckensnittet inte stöder vissa tecken. I den här guiden kommer vi att undersöka hur du ställer in Font Fallback Settings med Aspose.Words för .NET i en steg-för-steg handledning.

## Förutsättningar

Innan du dyker in i handledningen, se till att du har följande förutsättningar på plats:

- Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# och .NET framework.
-  Aspose.Words för .NET: Ladda ner och installera från[nedladdningslänk](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: En inställning som Visual Studio för att skriva och köra din kod.
-  Exempeldokument: Ha ett exempeldokument (t.ex.`Rendering.docx`) redo för testning.
- Font Fallback Rules XML: Förbered en XML-fil som definierar typsnittets reservregler.

## Importera namnområden

För att använda Aspose.Words måste du importera de nödvändiga namnrymden. Detta ger tillgång till olika klasser och metoder som krävs för dokumentbehandling.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Steg 1: Definiera dokumentkatalogen

Först definierar du katalogen där ditt dokument lagras. Detta är viktigt för att hitta och bearbeta ditt dokument.

```csharp
// Sökvägen till dokumentkatalogen
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda dokumentet

 Ladda ditt dokument i en Aspose.Words`Document` objekt. Detta steg låter dig arbeta med dokumentet programmatiskt.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Konfigurera teckensnittsinställningar

 Skapa en ny`FontSettings` objekt och läs in alternativa teckensnittsinställningar från en XML-fil. Den här XML-filen innehåller reglerna för reservtypsnitt.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Steg 4: Tillämpa teckensnittsinställningar på dokumentet

 Tilldela den konfigurerade`FontSettings`till dokumentet. Detta säkerställer att reservreglerna för teckensnitt tillämpas när dokumentet renderas.

```csharp
doc.FontSettings = fontSettings;
```

## Steg 5: Spara dokumentet

Slutligen, spara dokumentet. Fallback-inställningarna för teckensnitt kommer att användas under sparandet för att säkerställa korrekt teckensnittsersättning.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML-fil: Font Fallback Rules

Här är ett exempel på hur din XML-fil som definierar teckensnittets reservregler ska se ut:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Slutsats

Genom att följa dessa steg kan du effektivt ställa in och använda Font Fallback Settings i Aspose.Words för .NET. Detta säkerställer att dina dokument visar alla tecken korrekt, även om det ursprungliga teckensnittet inte stöder vissa tecken. Genom att implementera dessa inställningar förbättras kvaliteten och läsbarheten av dina dokument avsevärt.

## FAQ's

### F1: Vad är Font Fallback?

Font Fallback är en funktion som tillåter ersättning av teckensnitt när det ursprungliga teckensnittet inte stöder vissa tecken, vilket säkerställer korrekt visning av alla textelement.

### F2: Kan jag ange flera reservteckensnitt?

Ja, du kan ange flera reservteckensnitt i XML-reglerna. Aspose.Words kommer att kontrollera varje typsnitt i angiven ordning tills det hittar ett som stöder tecknet.

### F3: Var kan jag ladda ner Aspose.Words för .NET?

 Du kan ladda ner den från[Aspose nedladdningssida](https://releases.aspose.com/words/net/).

### F4: Hur skapar jag XML-filen för alternativa teckensnittsregler?

XML-filen kan skapas med vilken textredigerare som helst. Det bör följa strukturen som visas i exemplet i denna handledning.

### F5: Finns det stöd tillgängligt för Aspose.Words?

 Ja, du kan hitta support på[Aspose.Words supportforum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
