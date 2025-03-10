---
title: Arbeta med öppen AI-modell
linktitle: Arbeta med öppen AI-modell
second_title: Aspose.Words Document Processing API
description: Lås upp effektiv dokumentsammanfattning med Aspose.Words för .NET med OpenAIs kraftfulla modeller. Dyk in i den här omfattande guiden nu.
weight: 10
url: /sv/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Arbeta med öppen AI-modell

## Introduktion

dagens digitala värld är innehåll kung. Oavsett om du är en student, en affärsman eller en ivrig författare, är förmågan att manipulera, sammanfatta och generera dokument effektivt ovärderlig. Det är här Aspose.Words för .NET-biblioteket kommer in i bilden, så att du kan hantera dokument som ett proffs. I denna omfattande handledning kommer vi att dyka in i hur man kan utnyttja Aspose.Words i kombination med OpenAI-modeller för att sammanfatta dokument effektivt. Är du redo att låsa upp din potential för dokumenthantering? Låt oss komma igång!

## Förutsättningar

Innan vi kavlar upp ärmarna och dyker in i koden, finns det några väsentliga saker du behöver ha på plats:

### .NET Framework
Se till att du kör på en version av .NET-ramverket som är kompatibel med Aspose.Words. Generellt sett bör .NET 5.0 och högre fungera perfekt.

### Aspose.Words för .NET Library
 Du måste ladda ner och installera Aspose.Words-biblioteket. Du kan ta det från[denna länk](https://releases.aspose.com/words/net/).

### OpenAI API-nyckel
För att integrera OpenAIs språkmodeller för dokumentsammanfattning behöver du en API-nyckel. Du kan få det genom att registrera dig på OpenAI-plattformen och hämta din nyckel från dina kontoinställningar.

### IDE för utveckling
Att ha en integrerad utvecklingsmiljö (IDE) som Visual Studio är perfekt för att utveckla .NET-applikationer.

### Grundläggande programmeringskunskaper
En grundläggande förståelse för C# och objektorienterad programmering hjälper dig att lättare förstå begreppen.

## Importera paket

Nu när vi har allt i ordning, låt oss importera våra paket. Öppna ditt Visual Studio-projekt och lägg till de nödvändiga biblioteken. Så här kan du göra det:

### Lägg till Aspose.Words-paketet

Du kan lägga till Aspose.Words-paketet via NuGet Package Manager. Så här gör du:
- Gå till Verktyg -> NuGet Package Manager -> Hantera NuGet-paket för lösning.
- Sök efter "Aspose.Words" och klicka på Installera.

### Lägg till systemmiljö

 Se till att inkludera`System`namnutrymme för att hantera miljövariabler:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Lägg till Aspose.Words

Inkludera sedan namnutrymmet Aspose.Words i din C#-fil:
```csharp
using Aspose.Words;
```

### Lägg till OpenAI Library

Om du använder ett bibliotek för gränssnitt med OpenAI (som en REST-klient), se till att du inkluderar det också. Du kan behöva lägga till det via NuGet på samma sätt som vi lade till Aspose.Words.

Nu när vi har förberett vår miljö och importerat de nödvändiga paketen, låt oss dela upp dokumentsammanfattningsprocessen steg för steg.

## Steg 1: Definiera dina dokumentkataloger

Innan du kan börja spela med dina dokument måste du ställa in kataloger där dina dokument och artefakter kommer att finnas:

```csharp
// Din dokumentkatalog
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Din artefakterkatalog
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Detta gör din kod mer hanterbar, eftersom du enkelt kan ändra sökvägarna om det behövs. De`MyDir` är där dina inmatningsdokument lagras, medan`ArtifactsDir` är där du kommer att spara genererade sammanfattningar.

## Steg 2: Ladda dina dokument

Därefter kommer du att ladda de dokument du vill sammanfatta. Det här är enkelt med Aspose.Words:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Se till att dina dokuments namn matchar de du tänker använda, annars kommer du att stöta på fel!

## Steg 3: Skaffa din API-nyckel

Nu när dina dokument har laddats är det dags att dra in din OpenAI API-nyckel. Du hämtar den från miljövariabler för att hålla den säker:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Det är viktigt att hantera din API-nyckel på ett säkert sätt för att hålla obehöriga användare borta.

## Steg 4: Skapa en OpenAI-modellinstans

Med din API-nyckel tillgänglig kan du nu skapa en instans av OpenAI-modellen. För dokumentsammanfattning använder vi Gpt4OMini-modellen:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Det här steget skapar i grunden den hjärnkraft som behövs för att sammanfatta dina dokument, vilket ger dig tillgång till AI-driven sammanfattning.

## Steg 5: Sammanfatta ett enda dokument

Låt oss först sammanfatta det första dokumentet. Det är här magin händer:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Här använder vi`Summarize` modellens metod. De`SummaryLength.Short`parameter anger att vi vill ha en kort sammanfattning — perfekt för en snabb överblick!

## Steg 6: Sammanfatta flera dokument

Känner du dig ambitiös? Du kan sammanfatta flera dokument samtidigt. Se bara hur lätt det är:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Denna funktion är särskilt praktisk för att jämföra flera filer. Kanske förbereder du för ett möte och behöver kortfattade anteckningar från flera långa rapporter. Det här är din nya bästa vän!

## Slutsats

Att sammanfatta dokument med Aspose.Words för .NET och OpenAI är inte bara en fördelaktig färdighet; det är ganska stärkande. Genom att följa den här guiden har du förvandlat lång, komplicerad text till kortfattade sammanfattningar, vilket sparar tid och ansträngning. Oavsett om du säkerställer tydlighet för kunder eller förbereder dig för den viktiga presentationen, har du nu verktygen för att göra det effektivt.

Så vad väntar du på? Dyk ner i dina dokument med tillförsikt och låt tekniken göra det tunga arbetet!

## FAQ's

### Vad är Aspose.Words för .NET?  
Aspose.Words för .NET är ett kraftfullt bibliotek som gör det möjligt för utvecklare att skapa, manipulera och konvertera dokument programmatiskt.

### Behöver jag en API-nyckel för OpenAI?  
Ja, du måste ha en giltig OpenAI API-nyckel för att få tillgång till sammanfattningsfunktionerna med deras modeller.

### Kan jag sammanfatta flera dokument samtidigt?  
Absolut! Du kan sammanfatta flera dokument i ett enda samtal, vilket är idealiskt för omfattande rapporter.

### Hur installerar jag Aspose.Words?  
Du kan installera det via NuGet Package Manager i Visual Studio genom att söka efter "Aspose.Words".

### Finns det en gratis provperiod för Aspose.Words?  
 Ja, du kan få tillgång till en gratis testversion av Aspose.Words genom deras[webbplats](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
