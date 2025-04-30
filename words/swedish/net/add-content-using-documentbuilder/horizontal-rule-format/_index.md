---
"description": "Lär dig hur du infogar anpassningsbara horisontella linjer i Word-dokument med Aspose.Words för .NET. Förbättra din dokumentautomation."
"linktitle": "Horisontellt regelformat i Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Horisontellt regelformat i Word-dokument"
"url": "/sv/net/add-content-using-documentbuilder/horizontal-rule-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Horisontellt regelformat i Word-dokument

## Introduktion

Inom .NET-utveckling kan det vara en svår uppgift att manipulera och formatera Word-dokument programmatiskt. Lyckligtvis erbjuder Aspose.Words för .NET en robust lösning som ger utvecklare möjlighet att automatisera skapande, redigering och hantering av dokument med lätthet. Den här artikeln fördjupar sig i en av de viktigaste funktionerna: att infoga horisontella regler i Word-dokument. Oavsett om du är en erfaren utvecklare eller precis har börjat använda Aspose.Words, kommer att bemästra denna funktion att förbättra din dokumentgenereringsprocess.

## Förkunskapskrav

Innan du börjar implementera horisontella regler med Aspose.Words för .NET, se till att du har följande förutsättningar:

- Visual Studio: Installera Visual Studio IDE för .NET-utveckling.
- Aspose.Words för .NET: Ladda ner och installera Aspose.Words för .NET från [här](https://releases.aspose.com/words/net/).
- Grundläggande C#-kunskaper: Bekantskap med grunderna i programmeringsspråket C#.
- DocumentBuilder-klassen: Förståelse av `DocumentBuilder` klass i Aspose. Ord för dokumentmanipulation.

## Importera namnrymder

För att börja, importera de nödvändiga namnrymderna i ditt C#-projekt:

```csharp
using Aspose.Words;
using System.Drawing;
```

Dessa namnrymder ger åtkomst till Aspose.Words-klasser för dokumenthantering och standard .NET-klasser för hantering av färger.

Låt oss dela upp processen för att lägga till en horisontell regel i ett Word-dokument med Aspose.Words för .NET i omfattande steg:

## Steg 1: Initiera DocumentBuilder och ange katalog

Först, initiera en `DocumentBuilder` objektet och ange sökvägen till katalogen där dokumentet ska sparas.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
DocumentBuilder builder = new DocumentBuilder();
```

## Steg 2: Infoga horisontell linje

Använd `InsertHorizontalRule()` metod för `DocumentBuilder` klass för att lägga till en horisontell regel.

```csharp
Shape shape = builder.InsertHorizontalRule();
```

## Steg 3: Anpassa horisontellt regelformat

Åtkomst till `HorizontalRuleFormat` egenskapen för den infogade formen för att anpassa den horisontella regelns utseende.

```csharp
HorizontalRuleFormat horizontalRuleFormat = shape.HorizontalRuleFormat;
horizontalRuleFormat.Alignment = HorizontalRuleAlignment.Center;
horizontalRuleFormat.WidthPercent = 70;
horizontalRuleFormat.Height = 3;
horizontalRuleFormat.Color = Color.Blue;
horizontalRuleFormat.NoShade = true;
```

- Justering: Anger justeringen av den horisontella linjen (`HorizontalRuleAlignment.Center` i det här exemplet).
- WidthPercent: Anger bredden på den horisontella linjen som en procentandel av sidbredden (70 % i det här exemplet).
- Höjd: Definierar höjden på den horisontella linjalen i punkter (3 punkter i det här exemplet).
- Färg: Anger färgen på den horisontella linjen (`Color.Blue` i det här exemplet).
- Ingen skugga: Anger om den horisontella linjen ska ha en skugga (`true` i det här exemplet).

## Steg 4: Spara dokument

Spara slutligen det ändrade dokumentet med hjälp av `Save` metod för `Document` objekt.

```csharp
builder.Document.Save(dataDir + "AddContentUsingDocumentBuilder.HorizontalRuleFormat.docx");
```

## Slutsats

Att bemästra infogning av horisontella linjer i Word-dokument med Aspose.Words för .NET förbättrar dina dokumentautomatiseringsmöjligheter. Genom att utnyttja flexibiliteten och kraften i Aspose.Words kan utvecklare effektivisera dokumentgenerering och formateringsprocesser.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att arbeta med Word-dokument programmatiskt i .NET-applikationer.

### Hur kan jag ladda ner Aspose.Words för .NET?
Du kan ladda ner Aspose.Words för .NET från [här](https://releases.aspose.com/words/net/).

### Kan jag anpassa utseendet på horisontella linjer i Aspose.Words?
Ja, du kan anpassa olika aspekter som justering, bredd, höjd, färg och skuggning av horisontella linjer med hjälp av Aspose.Words.

### Är Aspose.Words lämpligt för dokumenthantering på företagsnivå?
Ja, Aspose.Words används flitigt i företagsmiljöer för sina robusta dokumenthanteringsfunktioner.

### Var kan jag få support för Aspose.Words för .NET?
För stöd och samhällsengagemang, besök [Aspose.Words-forum](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}