---
title: Infoga fält Inkludera text utan dokumentbyggare
linktitle: Infoga FieldIncludeText utan dokumentbyggare
second_title: Aspose.Words Document Processing API
description: Lär dig hur du infogar en FieldIncludeText utan att använda DocumentBuilder i Aspose.Words för .NET med vår detaljerade steg-för-steg-guide.
weight: 10
url: /sv/net/working-with-fields/insert-field-include-text-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga fält Inkludera text utan dokumentbyggare

## Introduktion

I en värld av dokumentautomation och manipulation står Aspose.Words för .NET som ett kraftfullt verktyg. Idag dyker vi ner i en detaljerad guide om hur man infogar en FieldIncludeText utan att använda DocumentBuilder. Den här handledningen går igenom processen steg-för-steg, och säkerställer att du förstår varje del av koden och dess syfte.

## Förutsättningar

Innan vi dyker in i koden, låt oss se till att du har allt du behöver:

1.  Aspose.Words för .NET: Se till att du har den senaste versionen installerad. Du kan ladda ner den från[här](https://releases.aspose.com/words/net/).
2. .NET-utvecklingsmiljö: Alla .NET-kompatibla IDE som Visual Studio.
3. Grundläggande kunskaper i C#: Bekantskap med C#-programmering hjälper dig att följa med.

## Importera namnområden

Först och främst måste vi importera de nödvändiga namnrymden. Dessa namnrymder ger åtkomst till de klasser och metoder som krävs för att manipulera Word-dokument.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

Låt oss nu dela upp exemplet i flera steg. Varje steg kommer att förklaras i detalj för att säkerställa tydlighet.

## Steg 1: Ställ in katalogsökvägen

Det första steget är att definiera sökvägen till din dokumentkatalog. Det är här dina Word-dokument kommer att lagras och nås.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Steg 2: Skapa dokumentet och stycket

Därefter skapar vi ett nytt dokument och ett stycke i det dokumentet. Detta stycke kommer att innehålla fältet FieldIncludeText.

```csharp
// Skapa dokumentet och stycket.
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## Steg 3: Infoga FieldIncludeText-fältet

Nu infogar vi fältet FieldIncludeText i stycket. Detta fält låter dig inkludera text från ett annat dokument.

```csharp
// Infoga fältet FieldIncludeText.
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## Steg 4: Ställ in fältegenskaper

Vi måste ange egenskaperna för fältet FieldIncludeText. Detta inkluderar att ställa in bokmärkets namn och källdokumentets fullständiga sökväg.

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## Steg 5: Lägg till stycke till dokument

Med fältet inställt lägger vi till stycket i dokumentets första avsnittskropp.

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## Steg 6: Uppdatera fält

Innan vi sparar dokumentet måste vi uppdatera FieldIncludeText för att säkerställa att det hämtar in rätt innehåll från källdokumentet.

```csharp
fieldIncludeText.Update();
```

## Steg 7: Spara dokumentet

Slutligen sparar vi dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt infoga en FieldIncludeText utan att använda DocumentBuilder i Aspose.Words för .NET. Detta tillvägagångssätt ger ett strömlinjeformat sätt att inkludera innehåll från ett dokument till ett annat, vilket gör dina dokumentautomatiseringsuppgifter mycket enklare.

## FAQ's

### Vad är Aspose.Words för .NET?  
Aspose.Words för .NET är ett kraftfullt bibliotek för att arbeta med Word-dokument i .NET-applikationer. Det gör det möjligt att skapa, redigera och konvertera dokument programmatiskt.

### Varför använda FieldIncludeText?  
FieldIncludeText är användbart för att dynamiskt inkludera innehåll från ett dokument till ett annat, vilket möjliggör mer modulära och underhållbara dokument.

### Kan jag använda den här metoden för att inkludera text från andra filformat?  
FieldIncludeText fungerar specifikt med Word-dokument. För andra format kan du behöva andra metoder eller klasser som tillhandahålls av Aspose.Words.

### Är Aspose.Words for .NET kompatibelt med .NET Core?  
Ja, Aspose.Words för .NET stöder .NET Framework, .NET Core och .NET 5/6.

### Hur kan jag få en gratis provversion av Aspose.Words för .NET?  
 Du kan få en gratis provperiod från[här](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
