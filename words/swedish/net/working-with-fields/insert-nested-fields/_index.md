---
"description": "Lär dig hur du infogar kapslade fält i Word-dokument med Aspose.Words för .NET med vår steg-för-steg-guide. Perfekt för utvecklare som vill automatisera dokumentskapandet."
"linktitle": "Infoga kapslade fält"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Infoga kapslade fält"
"url": "/sv/net/working-with-fields/insert-nested-fields/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga kapslade fält

## Introduktion

Har du någonsin behövt infoga kapslade fält i dina Word-dokument programmatiskt? Kanske vill du vill visa olika texter villkorligt baserat på sidnummer? Då har du tur! Den här handledningen guidar dig genom processen att infoga kapslade fält med Aspose.Words för .NET. Nu kör vi!

## Förkunskapskrav

Innan vi börjar finns det några saker du behöver:

1. Aspose.Words för .NET: Se till att du har biblioteket Aspose.Words för .NET. Du kan ladda ner det från [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En IDE som Visual Studio.
3. Grundläggande kunskaper i C#: Förståelse för programmeringsspråket C#.

## Importera namnrymder

Se först till att importera de nödvändiga namnrymderna i ditt projekt. Dessa namnrymder innehåller klasser som du behöver för att interagera med Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.HeaderFooter;
```

## Steg 1: Initiera dokumentet

Det första steget är att skapa ett nytt dokument och ett DocumentBuilder-objekt. DocumentBuilder-klassen hjälper till att bygga och modifiera Word-dokument.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Skapa dokumentet och DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Infoga sidbrytningar

Härnäst infogar vi några sidbrytningar i dokumentet. Detta gör att vi kan demonstrera de kapslade fälten effektivt.

```csharp
// Infoga sidbrytningar.
for (int i = 0; i < 5; i++)
{
    builder.InsertBreak(BreakType.PageBreak);
}
```

## Steg 3: Flytta till sidfot

Efter att vi har infogat sidbrytningar måste vi gå till dokumentets sidfot. Det är här vi infogar vårt kapslade fält.

```csharp
// Flytta till sidfot.
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);
```

## Steg 4: Infoga kapslat fält

Nu ska vi infoga det kapslade fältet. Vi använder OM-fältet för att villkorligt visa text baserat på det aktuella sidnumret.

```csharp
// Infoga kapslat fält.
Field field = builder.InsertField(@"IF ");
builder.MoveTo(field.Separator);
builder.InsertField("PAGE");
builder.Write(" <> ");
builder.InsertField("NUMPAGES");
builder.Write(" \"See next page\" \"Last page\" ");
```

I det här steget infogar vi först OM-fältet, flyttar det till dess avgränsare och infogar sedan fälten PAGE och NUMPAGES. OM-fältet kontrollerar om det aktuella sidnumret (PAGE) inte är lika med det totala antalet sidor (NUMPAGES). Om det är sant visas "Se nästa sida", annars visas "Sista sidan".

## Steg 5: Uppdatera fältet

Slutligen uppdaterar vi fältet för att säkerställa att det visar rätt text.

```csharp
// Uppdatera fältet.
field.Update();
```

## Steg 6: Spara dokumentet

Det sista steget är att spara dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "InsertNestedFields.docx");
```

## Slutsats

Och där har du det! Du har lyckats infoga kapslade fält i ett Word-dokument med hjälp av Aspose.Words för .NET. Detta kraftfulla bibliotek gör det otroligt enkelt att manipulera Word-dokument programmatiskt. Oavsett om du genererar rapporter, skapar mallar eller automatiserar dokumentarbetsflöden, har Aspose.Words det du behöver.

## Vanliga frågor

### Vad är ett kapslat fält i Word-dokument?
Ett kapslat fält är ett fält som innehåller andra fält. Det möjliggör mer komplext och villkorligt innehåll i dokument.

### Kan jag använda andra fält inom OM-fältet?
Ja, du kan kapsla olika fält som DATUM, TID och FÖRFATTARE i OM-fältet för att skapa dynamiskt innehåll.

### Är Aspose.Words för .NET gratis?
Aspose.Words för .NET är ett kommersiellt bibliotek, men du kan få en [gratis provperiod](https://releases.aspose.com/) att prova det.

### Kan jag använda Aspose.Words med andra .NET-språk?
Ja, Aspose.Words stöder alla .NET-språk, inklusive VB.NET och F#.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
Du kan hitta detaljerad dokumentation [här](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}