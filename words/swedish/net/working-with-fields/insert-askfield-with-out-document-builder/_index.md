---
title: Infoga ASKField Without Document Builder
linktitle: Infoga ASKField Without Document Builder
second_title: Aspose.Words Document Processing API
description: Lär dig hur du infogar ett ASK-fält utan att använda Document Builder i Aspose.Words för .NET. Följ den här guiden för att förbättra dina Word-dokument dynamiskt.
weight: 10
url: /sv/net/working-with-fields/insert-askfield-with-out-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga ASKField Without Document Builder

## Introduktion

Vill du behärska dokumentautomatisering med Aspose.Words för .NET? Du har kommit till rätt ställe! Idag går vi igenom hur du infogar ett Frågefält utan att använda en Document Builder. Det här är en snygg funktion när du vill att ditt dokument ska uppmana användarna till specifik input, vilket gör dina Word-dokument mer interaktiva och dynamiska. Så låt oss dyka in och göra dina dokument smartare!

## Förutsättningar

Innan vi smutsar ner händerna med lite kod, låt oss se till att vi har allt inställt:

1.  Aspose.Words för .NET: Se till att du har det här biblioteket installerat. Om inte kan du ladda ner den från[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En lämplig IDE som Visual Studio.
3. .NET Framework: Se till att du har .NET Framework installerat.

Stor! Nu när vi är klara, låt oss börja med att importera de nödvändiga namnrymden.

## Importera namnområden

Först och främst måste vi importera Aspose.Words-namnområdet för att komma åt alla funktioner i Aspose.Words för .NET. Så här gör du:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## Steg 1: Skapa ett nytt dokument

Innan vi kan infoga ett ASK-fält behöver vi ett dokument att arbeta med. Så här skapar du ett nytt dokument:

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Skapande av dokument.
Document doc = new Document();
```

Det här kodavsnittet skapar ett nytt Word-dokument där vi lägger till vårt ASK-fält.

## Steg 2: Gå till paragrafnoden

I ett Word-dokument är innehållet organiserat i noder. Vi måste komma åt noden första stycket där vi infogar vårt ASK-fält:

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

Denna kodrad hämtar det första stycket i dokumentet, redo för vårt ASK-fältinfogning.

## Steg 3: Infoga ASK-fältet

Låt oss nu komma till huvudevenemanget – infoga ASK-fältet. Detta fält kommer att uppmana användaren att skriva in när dokumentet öppnas.

```csharp
// Infoga fältet FRÅGA.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

Här lägger vi till ett ASK-fält till stycket. Enkelt, eller hur?

## Steg 4: Konfigurera ASK-fältet

Vi måste ställa in några egenskaper för att definiera hur ASK-fältet beter sig. Låt oss konfigurera bokmärkets namn, prompttext, standardsvar och kopplingsfunktion:

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: En unik identifierare för ASK-fältet.
- PromptText: Texten som uppmanar användaren att skriva in.
- DefaultResponse: Det förifyllda svaret som användaren kan ändra.
- PromptOnceOnMailMerge: Bestämmer om prompten endast visas en gång under en e-postsammanfogning.

## Steg 5: Uppdatera fältet

Efter att ha konfigurerat ASK-fältet måste vi uppdatera det för att säkerställa att alla inställningar tillämpas korrekt:

```csharp
field.Update();
```

Detta kommando ser till att vårt ASK-fält är klart och korrekt inställt i dokumentet.

## Steg 6: Spara dokumentet

Slutligen, låt oss spara dokumentet i vår specificerade katalog:

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

Denna rad sparar dokumentet med det infogade ASK-fältet. Och där har du det – ditt dokument är nu utrustat med ett dynamiskt ASK-fält!

## Slutsats

Grattis! Du har precis lagt till ett ASK-fält i ett Word-dokument med Aspose.Words för .NET utan Document Builder. Den här funktionen kan avsevärt förbättra användarinteraktionen med dina dokument, vilket gör dem mer flexibla och användarvänliga. Fortsätt att experimentera med olika fält och egenskaper för att låsa upp Aspose.Words fulla potential. Glad kodning!

## FAQ's

### Vad är ett ASK-fält i Aspose.Words?
Ett ASK-fält i Aspose.Words är ett fält som ber användaren om specifik inmatning när dokumentet öppnas, vilket möjliggör dynamisk datainmatning.

### Kan jag använda flera ASK-fält i ett enda dokument?
Ja, du kan infoga flera ASK-fält i ett dokument, vart och ett med unika uppmaningar och svar.

###  Vad är syftet med`PromptOnceOnMailMerge` property?
 De`PromptOnceOnMailMerge` egenskapen avgör om ASK-prompten endast visas en gång under en kopplingsoperation eller varje gång.

### Behöver jag uppdatera fältet ASK efter att ha ställt in dess egenskaper?
Ja, uppdatering av ASK-fältet säkerställer att alla egenskaper tillämpas korrekt och att fältet fungerar som förväntat.

### Kan jag anpassa uppmaningstexten och standardsvaret?
Absolut! Du kan ställa in anpassad prompttext och standardsvar för att skräddarsy FRÅGA-fältet efter dina specifika behov.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
