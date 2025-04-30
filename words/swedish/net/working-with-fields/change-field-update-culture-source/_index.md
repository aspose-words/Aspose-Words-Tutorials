---
"description": "Lär dig hur du ändrar källan för fältuppdateringskultur i Aspose.Words för .NET med den här guiden. Kontrollera enkelt datumformatering baserat på olika kulturer."
"linktitle": "Ändra fältuppdateringskulturkälla"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ändra fältuppdateringskulturkälla"
"url": "/sv/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ändra fältuppdateringskulturkälla

## Introduktion

I den här handledningen ska vi dyka ner i Aspose.Words värld för .NET och utforska hur man ändrar källan för fältuppdateringskulturen. Om du arbetar med Word-dokument som innehåller datumfält och behöver kontrollera hur dessa datum formateras baserat på olika kulturer, är den här guiden för dig. Låt oss gå igenom processen steg för steg, så att du förstår varje koncept och kan tillämpa det effektivt i dina projekt.

## Förkunskapskrav

Innan vi går in i koden, se till att du har följande:

- Aspose.Words för .NET: Du kan ladda ner det från [här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Valfri .NET-kompatibel IDE (t.ex. Visual Studio).
- Grundläggande kunskaper i C#: Den här handledningen förutsätter att du har en grundläggande förståelse för C#-programmering.

## Importera namnrymder

Först, låt oss importera de namnrymder som behövs för vårt projekt. Detta säkerställer att vi har tillgång till alla nödvändiga klasser och metoder som tillhandahålls av Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Nu ska vi dela upp exemplet i flera steg för att hjälpa dig förstå hur du ändrar källan för fältuppdateringskultur i Aspose.Words för .NET.

## Steg 1: Initiera dokumentet

Det första steget är att skapa en ny instans av `Document` klass och en `DocumentBuilder`Detta lägger grunden för att bygga och manipulera vårt Word-dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga fält med specifik språkinställning

Nästa steg är att infoga fält i dokumentet. I det här exemplet infogar vi två datumfält. Vi ställer in teckensnittets språkinställning på tyska (LocaleId = 1031) för att visa hur kulturen påverkar datumformatet.

```csharp
builder.Font.LocaleId = 1031; // Tyska
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Steg 3: Ange kulturkälla för fältuppdatering

För att styra kulturen som används vid uppdatering av fälten ställer vi in `FieldUpdateCultureSource` egendomen tillhörande `FieldOptions` klass. Den här egenskapen avgör om kulturen hämtas från fältkoden eller dokumentet.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Steg 4: Kör dokumentkoppling

Vi behöver nu köra en dokumentkoppling för att fylla fälten med faktiska data. I det här exemplet kommer vi att ställa in det andra datumfältet (`Date2`) till och med den 1 januari 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Steg 5: Spara dokumentet

Slutligen sparar vi dokumentet i den angivna katalogen. Detta steg slutför processen att ändra källan för fältuppdateringskulturen.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Slutsats

Och där har du det! Du har framgångsrikt ändrat kulturkällan för fältuppdateringen i Aspose.Words för .NET. Genom att följa dessa steg kan du säkerställa att dina Word-dokument visar datum och andra fältvärden enligt de angivna kulturinställningarna. Detta kan vara särskilt användbart när du genererar dokument för en internationell publik.

## Vanliga frågor

### Vad är syftet med att sätta `LocaleId`?
De `LocaleId` anger kulturinställningarna för texten, vilket påverkar hur datum och annan språkkänslig data formateras.

### Kan jag använda en annan språkinställning än tyska?
Ja, du kan ställa in `LocaleId` till valfri giltig språkidentifierare. Till exempel 1033 för engelska (USA).

### Vad händer om jag inte ställer in `FieldUpdateCultureSource` egendom?
Om den här egenskapen inte är inställd kommer dokumentets standardinställningar för kultur att användas vid uppdatering av fält.

### Är det möjligt att uppdatera fält baserat på dokumentets kultur istället för fältkoden?
Ja, du kan ställa in `FieldUpdateCultureSource` till `FieldUpdateCultureSource.Document` för att använda dokumentets kulturinställningar.

### Hur formaterar jag datum i ett annat mönster?
Du kan ändra datumformatmönstret i `InsertField` metoden genom att modifiera `\\@` växlingsvärde.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}