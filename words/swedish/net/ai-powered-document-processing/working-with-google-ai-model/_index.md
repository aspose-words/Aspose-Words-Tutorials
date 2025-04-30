---
"description": "Förbättra din dokumenthantering med Aspose.Words för .NET och Google AI för att enkelt skapa koncisa sammanfattningar."
"linktitle": "Arbeta med Googles AI-modell"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Arbeta med Googles AI-modell"
"url": "/sv/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Arbeta med Googles AI-modell

## Introduktion

I den här artikeln utforskar vi hur man sammanfattar dokument med hjälp av Aspose.Words och Googles AI-modeller steg för steg. Oavsett om du vill kondensera en lång rapport eller utvinna insikter från flera källor, har vi det du behöver.

## Förkunskapskrav

Innan vi går in i den praktiska delen, låt oss se till att du är redo för att lyckas. Här är vad du behöver:

1. Grundläggande kunskaper i C# och .NET: Bekantskap med programmeringskoncept hjälper dig att förstå exemplen bättre.
   
2. Aspose.Words för .NET-biblioteket: Detta kraftfulla bibliotek låter dig skapa och manipulera Word-dokument sömlöst. Du kan [ladda ner den här](https://releases.aspose.com/words/net/).

3. API-nyckel för Google AI-modellen: För att använda AI-modellerna behöver du en API-nyckel för autentisering. Lagra den säkert i dina miljövariabler.

4. Utvecklingsmiljö: Se till att du har en fungerande .NET-miljö konfigurerad (Visual Studio eller annan IDE).

5. Exempeldokument: Du behöver exempel på Word-dokument (t.ex. "Big document.docx", "Document.docx") för att testa sammanfattningen.

Nu när vi har gått igenom grunderna, låt oss dyka ner i koden!

## Importera paket

För att arbeta med Aspose.Words och integrera Googles AI-modeller måste du importera de nödvändiga namnrymderna. Så här gör du det:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Nu när du har importerat de nödvändiga paketen, låt oss gå igenom processen för att sammanfatta dokument steg för steg.

## Steg 1: Konfigurera din dokumentkatalog

Innan vi kan bearbeta dokument måste vi ange var våra filer finns. Detta steg är avgörande för att säkerställa att Aspose.Words kan komma åt dokumenten.

```csharp
// Din dokumentkatalog
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Din ArtifactsDir-katalog
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

Ersätta `"YOUR_DOCUMENT_DIRECTORY"` och `"YOUR_ARTIFACTS_DIRECTORY"` med de faktiska sökvägarna på ditt system där dina dokument lagras. Detta kommer att fungera som baslinje för att läsa och spara dokument.

## Steg 2: Ladda dokumenten

Nästa steg är att ladda de dokument som vi vill sammanfatta. I det här fallet laddar du två dokument som vi angav tidigare.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

De `Document` Klassen från Aspose.Words låter dig ladda Word-filer till minnet. Se till att filnamnen matchar de faktiska dokumenten i din katalog, annars kommer du att stöta på felmeddelandet "filen hittades inte"!

## Steg 3: Hämta API-nyckeln

För att använda AI-modellen måste du hämta din API-nyckel. Denna fungerar som din åtkomstkod till Googles AI-tjänster.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Den här kodraden hämtar API-nyckeln som du har lagrat i dina miljövariabler. Det är bra att hålla känslig information som API-nycklar borta från din kod av säkerhetsskäl.

## Steg 4: Skapa en AI-modellinstans

Nu är det dags att skapa en instans av AI-modellen. Här kan du välja vilken modell du vill använda – i det här exemplet väljer vi GPT-4 Mini-modellen.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

Den här raden konfigurerar den AI-modell du kommer att använda för dokumentsammanfattning. Se till att konsultera [dokumentationen](https://reference.aspose.com/words/net/) för detaljer om olika modeller och deras kapacitet.

## Steg 5: Sammanfatta ett enda dokument

Låt oss fokusera på att sammanfatta det första dokumentet. Vi kan välja att göra en kort sammanfattning här.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

I det här steget använder vi `Summarize` metod från AI-modellinstansen för att få en kondensering av det första dokumentet. Sammanfattningslängden är inställd på kort, men du kan anpassa detta beroende på dina behov. Slutligen sparas det sammanfattade dokumentet i din artefaktkatalog.

## Steg 6: Sammanfattning av flera dokument

Vill du sammanfatta flera dokument samtidigt? Aspose.Words gör även detta enkelt!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

Här ringer vi till `Summarize` metoden igen, men den här gången med en array av dokument. Detta ger dig en lång sammanfattning som sammanfattar essensen av båda filerna. Precis som tidigare sparas resultatet i den angivna artefaktkatalogen.

## Slutsats

Och där har du det! Du har framgångsrikt skapat en miljö för att sammanfatta dokument med hjälp av Aspose.Words för .NET och Googles AI-modeller. Från att läsa in dokument till att skapa koncisa sammanfattningar ger dessa steg en effektiv metod för att hantera stora textvolymer.

## Vanliga frågor

### Vad är Aspose.Words?
Aspose.Words är ett kraftfullt bibliotek för att skapa, modifiera och konvertera Word-dokument med hjälp av .NET.

### Hur får jag en API-nyckel för Google AI?
Du kan vanligtvis få en API-nyckel genom att registrera dig för Google Cloud och aktivera de nödvändiga API-tjänsterna.

### Kan jag sammanfatta flera dokument samtidigt?
Ja! Som visats kan du skicka en array av dokument till sammanfattningsmetoden.

### Vilka typer av sammanfattningar kan jag skapa?
Du kan välja mellan korta, medellånga och långa sammanfattningar baserat på dina behov.

### Var kan jag hitta fler Aspose.Words-resurser?
Kolla in [dokumentation](https://reference.aspose.com/words/net/) för fler exempel och vägledning.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}