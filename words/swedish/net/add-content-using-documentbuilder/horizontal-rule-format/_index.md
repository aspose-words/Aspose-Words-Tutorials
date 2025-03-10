---
title: Horisontellt regelformat i Word-dokument
linktitle: Horisontellt regelformat i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du infogar anpassningsbara horisontella regler i Word-dokument med Aspose.Words för .NET. Förbättra din dokumentautomatisering.
weight: 10
url: /sv/net/add-content-using-documentbuilder/horizontal-rule-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Horisontellt regelformat i Word-dokument

## Introduktion

När det gäller .NET-utveckling kan det vara en skrämmande uppgift att manipulera och formatera Word-dokument programmatiskt. Lyckligtvis tillhandahåller Aspose.Words för .NET en robust lösning som ger utvecklare möjlighet att automatisera dokumentskapande, redigering och hantering med lätthet. Den här artikeln fördjupar sig i en av de väsentliga funktionerna: infoga horisontella regler i Word-dokument. Oavsett om du är en erfaren utvecklare eller precis har börjat med Aspose.Words, kommer att bemästra denna förmåga att förbättra din dokumentgenereringsprocess.

## Förutsättningar

Innan du börjar implementera horisontella regler med Aspose.Words för .NET, se till att du har följande förutsättningar:

- Visual Studio: Installera Visual Studio IDE för .NET-utveckling.
- Aspose.Words for .NET: Ladda ner och installera Aspose.Words for .NET från[här](https://releases.aspose.com/words/net/).
- Grundläggande C#-kunskaper: Bekantskap med C#-programmeringsspråkets grunder.
-  DocumentBuilder Class: Förståelse av`DocumentBuilder` klass i Aspose.Words för dokumentmanipulation.

## Importera namnområden

För att börja, importera de nödvändiga namnrymden i ditt C#-projekt:

```csharp
using Aspose.Words;
using System.Drawing;
```

Dessa namnrymder ger tillgång till Aspose.Words-klasser för dokumentmanipulation och standard .NET-klasser för hantering av färger.

Låt oss dela upp processen att lägga till en horisontell regel i ett Word-dokument med Aspose.Words för .NET i omfattande steg:

## Steg 1: Initiera DocumentBuilder och Set Directory

 Initiera först a`DocumentBuilder` objekt och ange katalogsökvägen där dokumentet ska sparas.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
DocumentBuilder builder = new DocumentBuilder();
```

## Steg 2: Infoga horisontell regel

 Använd`InsertHorizontalRule()` metod för`DocumentBuilder` klass för att lägga till en horisontell regel.

```csharp
Shape shape = builder.InsertHorizontalRule();
```

## Steg 3: Anpassa horisontellt regelformat

 Få tillgång till`HorizontalRuleFormat` egenskapen för den infogade formen för att anpassa den horisontella regelns utseende.

```csharp
HorizontalRuleFormat horizontalRuleFormat = shape.HorizontalRuleFormat;
horizontalRuleFormat.Alignment = HorizontalRuleAlignment.Center;
horizontalRuleFormat.WidthPercent = 70;
horizontalRuleFormat.Height = 3;
horizontalRuleFormat.Color = Color.Blue;
horizontalRuleFormat.NoShade = true;
```

- Justering: Anger justeringen av den horisontella regeln (`HorizontalRuleAlignment.Center` i det här exemplet).
- WidthPercent: Anger bredden på den horisontella regeln som en procentandel av sidbredden (70 % i det här exemplet).
- Höjd: Definierar höjden på den horisontella regeln i punkter (3 punkter i det här exemplet).
- Färg: Ställer in färgen på den horisontella regeln (`Color.Blue` i det här exemplet).
- NoShade: Anger om den horisontella regeln ska ha en skugga (`true` i det här exemplet).

## Steg 4: Spara dokument

 Slutligen, spara det ändrade dokumentet med hjälp av`Save` metod för`Document` objekt.

```csharp
builder.Document.Save(dataDir + "AddContentUsingDocumentBuilder.HorizontalRuleFormat.docx");
```

## Slutsats

Att behärska infogningen av horisontella regler i Word-dokument med Aspose.Words för .NET förbättrar dina dokumentautomatiseringsmöjligheter. Genom att utnyttja flexibiliteten och kraften i Aspose.Words kan utvecklare effektivisera dokumentgenerering och formateringsprocesser.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att arbeta med Word-dokument programmatiskt i .NET-applikationer.

### Hur kan jag ladda ner Aspose.Words för .NET?
 Du kan ladda ner Aspose.Words för .NET från[här](https://releases.aspose.com/words/net/).

### Kan jag anpassa utseendet på horisontella regler i Aspose.Words?
Ja, du kan anpassa olika aspekter som justering, bredd, höjd, färg och skuggning av horisontella regler med Aspose.Words.

### Är Aspose.Words lämpligt för dokumentbehandling på företagsnivå?
Ja, Aspose.Words används flitigt i företagsmiljöer för sina robusta dokumenthanteringsmöjligheter.

### Var kan jag få support för Aspose.Words för .NET?
 För stöd och samhällsengagemang, besök[Aspose.Words forum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
