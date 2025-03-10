---
title: Ange standardteckensnitt vid rendering
linktitle: Ange standardteckensnitt vid rendering
second_title: Aspose.Words Document Processing API
description: Lär dig hur du anger ett standardteckensnitt när du renderar Word-dokument med Aspose.Words för .NET. Säkerställ konsekvent dokumentutseende på alla plattformar.
weight: 10
url: /sv/net/working-with-fonts/specify-default-font-when-rendering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ange standardteckensnitt vid rendering

## Introduktion

Att se till att dina Word-dokument återges korrekt på olika plattformar kan vara en utmaning, särskilt när det gäller teckensnittskompatibilitet. Ett sätt att bibehålla ett konsekvent utseende är att ange ett standardteckensnitt när du renderar dina dokument till PDF eller andra format. I den här handledningen kommer vi att utforska hur du ställer in ett standardteckensnitt med Aspose.Words för .NET, så att dina dokument ser bra ut oavsett var de visas.

## Förutsättningar

Innan vi dyker in i koden, låt oss täcka vad du behöver följa tillsammans med denna handledning:

- Aspose.Words för .NET: Se till att du har den senaste versionen installerad. Du kan ladda ner den[här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Visual Studio eller någon annan .NET-utvecklingsmiljö.
- Grundläggande kunskaper om C#: Denna handledning förutsätter att du är bekväm med C#-programmering.

## Importera namnområden

För att komma igång måste du importera de nödvändiga namnrymden. Dessa ger dig tillgång till de klasser och metoder som krävs för att arbeta med Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Låt oss nu dela upp processen för att ange ett standardteckensnitt i lätta att följa steg.

## Steg 1: Konfigurera din dokumentkatalog

Definiera först sökvägen till din dokumentkatalog. Det är här dina in- och utdatafiler kommer att lagras.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda ditt dokument

Ladda sedan dokumentet du vill rendera. I det här exemplet använder vi en fil med namnet "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Konfigurera teckensnittsinställningar

 Skapa en instans av`FontSettings` och ange standardteckensnittet. Om det definierade typsnittet inte kan hittas under renderingen kommer Aspose.Words att använda det närmast tillgängliga teckensnittet på maskinen.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Steg 4: Tillämpa teckensnittsinställningar på dokumentet

Tilldela de konfigurerade teckensnittsinställningarna till ditt dokument.

```csharp
doc.FontSettings = fontSettings;
```

## Steg 5: Spara dokumentet

Slutligen sparar du dokumentet i önskat format. I det här fallet sparar vi den som en PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Slutsats

Genom att följa dessa steg kan du se till att dina Word-dokument återges med ett specificerat standardteckensnitt, vilket bibehåller konsistens över olika plattformar. Detta kan vara särskilt användbart för dokument som delas brett eller visas på system med varierande teckensnittstillgänglighet.


## FAQ's

### Varför ange ett standardteckensnitt i Aspose.Words?
Genom att ange ett standardteckensnitt säkerställer du att ditt dokument ser konsekvent ut på olika plattformar, även om de ursprungliga teckensnitten inte är tillgängliga.

### Vad händer om standardteckensnittet inte hittas under renderingen?
Aspose.Words kommer att använda det närmast tillgängliga teckensnittet på maskinen för att bibehålla dokumentets utseende så nära som möjligt.

### Kan jag ange flera standardteckensnitt?
 Nej, du kan bara ange ett standardteckensnitt. Du kan dock hantera teckensnittsersättning för specifika fall med hjälp av`FontSettings` klass.

### Är Aspose.Words för .NET kompatibelt med alla versioner av Word-dokument?
Ja, Aspose.Words för .NET stöder ett brett utbud av Word-dokumentformat, inklusive DOC, DOCX, RTF och mer.

### Var kan jag få support om jag stöter på problem?
 Du kan få stöd från Aspose-communityt och utvecklare på[Aspose.Words Support Forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
