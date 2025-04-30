---
"description": "Lär dig hur du infogar ett ASK-fält utan att använda Document Builder i Aspose.Words för .NET. Följ den här guiden för att förbättra dina Word-dokument dynamiskt."
"linktitle": "Infoga ASKField utan dokumentbyggare"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Infoga ASKField utan dokumentbyggare"
"url": "/sv/net/working-with-fields/insert-askfield-with-out-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga ASKField utan dokumentbyggare

## Introduktion

Vill du bemästra dokumentautomation med Aspose.Words för .NET? Då har du kommit till rätt ställe! Idag ska vi guida dig genom hur du infogar ett ASK-fält utan att använda en dokumentbyggare. Det här är en smidig funktion när du vill att ditt dokument ska uppmana användarna att göra specifika inmatningar, vilket gör dina Word-dokument mer interaktiva och dynamiska. Så, låt oss dyka in och göra dina dokument smartare!

## Förkunskapskrav

Innan vi börjar med lite kod, låt oss se till att vi har allt klart:

1. Aspose.Words för .NET: Se till att du har det här biblioteket installerat. Om inte kan du ladda ner det från [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En lämplig IDE som Visual Studio.
3. .NET Framework: Se till att du har .NET Framework installerat.

Toppen! Nu när vi är klara kan vi börja med att importera de nödvändiga namnrymderna.

## Importera namnrymder

Först och främst måste vi importera namnrymden Aspose.Words för att få tillgång till alla funktioner i Aspose.Words för .NET. Så här gör du:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## Steg 1: Skapa ett nytt dokument

Innan vi kan infoga ett ASK-fält behöver vi ett dokument att arbeta med. Så här skapar du ett nytt dokument:

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Dokumentskapande.
Document doc = new Document();
```

Det här kodavsnittet skapar ett nytt Word-dokument där vi lägger till vårt ASK-fält.

## Steg 2: Åtkomst till styckenoden

I ett Word-dokument är innehållet organiserat i noder. Vi behöver komma åt den första styckenoden där vi ska infoga vårt ASK-fält:

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

Den här kodraden hämtar det första stycket i dokumentet, redo för infogning av vårt ASK-fält.

## Steg 3: Infoga ASK-fältet

Nu ska vi gå vidare till huvudhändelsen – att infoga ASK-fältet. Det här fältet uppmanar användaren att göra inmatningar när dokumentet öppnas.

```csharp
// Infoga fältet FRÅGA.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

Här lägger vi till ett ASK-fält i stycket. Enkelt, eller hur?

## Steg 4: Konfigurera ASK-fältet

Vi behöver ange några egenskaper för att definiera hur ASK-fältet beter sig. Nu konfigurerar vi bokmärkets namn, prompttexten, standardsvaret och beteendet för koppling av dokument:

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- Bokmärkesnamn: En unik identifierare för ASK-fältet.
- PromptText: Texten som uppmanar användaren att göra inmatning.
- Standardsvar: Det förifyllda svaret som användaren kan ändra.
- PromptOnceOnMailMerge: Avgör om prompten bara visas en gång under en dokumentkoppling.

## Steg 5: Uppdatera fältet

Efter att ha konfigurerat ASK-fältet måste vi uppdatera det för att säkerställa att alla inställningar tillämpas korrekt:

```csharp
field.Update();
```

Det här kommandot säkerställer att vårt ASK-fält är klart och korrekt konfigurerat i dokumentet.

## Steg 6: Spara dokumentet

Slutligen, låt oss spara dokumentet i vår angivna katalog:

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

Den här raden sparar dokumentet med det infogade ASK-fältet. Och där har du det – ditt dokument är nu utrustat med ett dynamiskt ASK-fält!

## Slutsats

Grattis! Du har precis lagt till ett ASK-fält i ett Word-dokument med Aspose.Words för .NET utan dokumentbyggaren. Den här funktionen kan avsevärt förbättra användarinteraktionen med dina dokument, vilket gör dem mer flexibla och användarvänliga. Fortsätt experimentera med olika fält och egenskaper för att frigöra Aspose.Words fulla potential. Lycka till med kodningen!

## Vanliga frågor

### Vad är ett ASK-fält i Aspose.Words?
Ett ASK-fält i Aspose.Words är ett fält som uppmanar användaren att ange specifik inmatning när dokumentet öppnas, vilket möjliggör dynamisk datainmatning.

### Kan jag använda flera ASK-fält i ett enda dokument?
Ja, du kan infoga flera ASK-fält i ett dokument, vart och ett med unika frågor och svar.

### Vad är syftet med `PromptOnceOnMailMerge` egendom?
De `PromptOnceOnMailMerge` Egenskapen avgör om ASK-prompten bara visas en gång under en dokumentkoppling eller varje gång.

### Behöver jag uppdatera ASK-fältet efter att jag har ställt in dess egenskaper?
Ja, uppdatering av ASK-fältet säkerställer att alla egenskaper tillämpas korrekt och att fältet fungerar som förväntat.

### Kan jag anpassa prompttexten och standardsvaret?
Absolut! Du kan ställa in anpassad prompttext och standardsvar för att skräddarsy FRÅGA-fältet efter dina specifika behov.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}