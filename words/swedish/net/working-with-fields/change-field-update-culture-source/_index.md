---
title: Ändra fältuppdateringskulturkälla
linktitle: Ändra fältuppdateringskulturkälla
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ändrar fältuppdateringskulturkällan i Aspose.Words för .NET med den här guiden. Styr datumformatering baserat på olika kulturer enkelt.
weight: 10
url: /sv/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ändra fältuppdateringskulturkälla

## Introduktion

I den här handledningen kommer vi att dyka in i Aspose.Words-världen för .NET och utforska hur man ändrar källan för fältuppdateringskulturen. Om du har att göra med Word-dokument som innehåller datumfält och du behöver kontrollera hur dessa datum formateras utifrån olika kulturer, är den här guiden för dig. Låt oss gå igenom processen steg-för-steg, så att du förstår varje koncept och kan tillämpa det effektivt i dina projekt.

## Förutsättningar

Innan vi hoppar in i koden, se till att du har följande:

-  Aspose.Words för .NET: Du kan ladda ner det från[här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Alla .NET-kompatibla IDE (t.ex. Visual Studio).
- Grundläggande kunskaper om C#: Denna handledning förutsätter att du har en grundläggande förståelse för C#-programmering.

## Importera namnområden

Låt oss först importera de nödvändiga namnrymden för vårt projekt. Detta kommer att säkerställa att vi har tillgång till alla nödvändiga klasser och metoder som tillhandahålls av Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Låt oss nu dela upp exemplet i flera steg för att hjälpa dig förstå hur du ändrar fältuppdateringskulturkällan i Aspose.Words för .NET.

## Steg 1: Initiera dokumentet

 Det första steget är att skapa en ny instans av`Document` klass och a`DocumentBuilder`. Detta lägger grunden för att bygga och manipulera vårt Word-dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga fält med specifik plats

Därefter måste vi infoga fält i dokumentet. För det här exemplet kommer vi att infoga två datumfält. Vi ställer in teckensnittets språkläge till tyska (LocaleId = 1031) för att visa hur kulturen påverkar datumformatet.

```csharp
builder.Font.LocaleId = 1031; // tyska
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Steg 3: Ställ in fältuppdateringskulturkälla

 För att kontrollera kulturen som används vid uppdatering av fälten ställer vi in`FieldUpdateCultureSource` egendom av`FieldOptions`klass. Denna egenskap avgör om kulturen är hämtad från fältkoden eller dokumentet.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Steg 4: Kör sammanfogning

Vi behöver nu köra en sammanslagning för att fylla fälten med faktiska data. I det här exemplet kommer vi att ställa in det andra datumfältet (`Date2`) till 1 januari 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Steg 5: Spara dokumentet

Slutligen sparar vi dokumentet i den angivna katalogen. Detta steg avslutar processen med att ändra källan för fältuppdateringskulturen.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Slutsats

Och där har du det! Du har framgångsrikt ändrat fältuppdateringskulturkällan i Aspose.Words för .NET. Genom att följa dessa steg kan du säkerställa att dina Word-dokument visar datum och andra fältvärden enligt de angivna kulturinställningarna. Detta kan vara särskilt användbart när du skapar dokument för en internationell publik.

## FAQ's

###  Vad är syftet med att ställa in`LocaleId`?
 De`LocaleId` anger kulturinställningarna för texten, vilket påverkar hur datum och andra lokalitetskänsliga data formateras.

### Kan jag använda en annan plats än tyska?
 Ja, du kan ställa in`LocaleId`till valfri giltig lokalidentifierare. Till exempel 1033 för engelska (USA).

###  Vad händer om jag inte ställer in`FieldUpdateCultureSource` property?
Om den här egenskapen inte är inställd kommer dokumentets standardkulturinställningar att användas vid uppdatering av fält.

### Är det möjligt att uppdatera fält baserat på dokumentets kultur istället för fältkoden?
 Ja, du kan ställa in`FieldUpdateCultureSource` till`FieldUpdateCultureSource.Document` att använda dokumentets kulturinställningar.

### Hur formaterar jag datum i ett annat mönster?
 Du kan ändra datumformatmönstret i`InsertField` metod genom att modifiera`\\@` växla värde.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
