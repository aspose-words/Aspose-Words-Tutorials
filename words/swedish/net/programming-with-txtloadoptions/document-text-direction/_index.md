---
"description": "Lär dig hur du ställer in textriktningen för dokument i Word med Aspose.Words för .NET med den här steg-för-steg-guiden. Perfekt för att hantera språk som skrivs från höger till vänster."
"linktitle": "Dokumentets textriktning"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Dokumentets textriktning"
"url": "/sv/net/programming-with-txtloadoptions/document-text-direction/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentets textriktning

## Introduktion

När du arbetar med Word-dokument, särskilt de som innehåller flera språk eller har speciella formateringsbehov, kan det vara avgörande att ställa in textriktningen. Till exempel, när du arbetar med höger-till-vänster-språk som hebreiska eller arabiska, kan du behöva justera textriktningen därefter. I den här guiden går vi igenom hur du ställer in textriktningen i dokumentet med Aspose.Words för .NET. 

## Förkunskapskrav

Innan vi går in i koden, se till att du har följande:

- Aspose.Words för .NET-biblioteket: Se till att du har Aspose.Words för .NET installerat. Du kan ladda ner det från [Aspose webbplats](https://releases.aspose.com/words/net/).
- Visual Studio: En utvecklingsmiljö för att skriva och exekvera C#-kod.
- Grundläggande kunskaper i C#: Bekantskap med C#-programmering är meriterande eftersom vi kommer att skriva en del kod.

## Importera namnrymder

För att börja måste du importera de namnrymder som behövs för att arbeta med Aspose.Words i ditt projekt. Så här gör du:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

Dessa namnrymder ger åtkomst till de klasser och metoder som behövs för att manipulera Word-dokument.

## Steg 1: Definiera sökvägen till din dokumentkatalog

Först, ange sökvägen till var ditt dokument finns. Detta är avgörande för att ladda och spara filer korrekt.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där ditt dokument är lagrat.

## Steg 2: Skapa TxtLoadOptions med inställning för dokumentriktning

Nästa steg är att skapa en instans av `TxtLoadOptions` och ställ in dess `DocumentDirection` egenskap. Detta talar om för Aspose.Words hur textriktningen i dokumentet ska hanteras.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

I det här exemplet använder vi `DocumentDirection.Auto` att låta Aspose.Words automatiskt bestämma riktningen baserat på innehållet.

## Steg 3: Ladda dokumentet

Ladda nu dokumentet med hjälp av `Document` klass och den tidigare definierade `loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

Här, `"Hebrew text.txt"` är namnet på din textfil. Se till att filen finns i den angivna katalogen.

## Steg 4: Få åtkomst till och kontrollera styckets dubbelriktade formatering

För att bekräfta att textriktningen är korrekt inställd, öppna dokumentets första stycke och kontrollera dess dubbelriktade formatering.

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

Det här steget är användbart för felsökning och verifiering av att dokumentets textriktning har tillämpats som förväntat.

## Steg 5: Spara dokumentet med de nya inställningarna

Spara slutligen dokumentet för att tillämpa och behålla ändringarna.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

Här, `"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` är namnet på utdatafilen. Se till att välja ett namn som återspeglar de ändringar du har gjort.

## Slutsats

Att ställa in textriktning i Word-dokument är en enkel process med Aspose.Words för .NET. Genom att följa dessa steg kan du enkelt konfigurera hur ditt dokument hanterar text från höger till vänster eller vänster till höger. Oavsett om du arbetar med flerspråkiga dokument eller behöver formatera textriktning för specifika språk, erbjuder Aspose.Words en robust lösning som möter dina behov.

## Vanliga frågor

### Vad är `DocumentDirection` egendom som används till?

De `DocumentDirection` fastighet i `TxtLoadOptions` bestämmer textriktningen för dokumentet. Den kan ställas in på `DocumentDirection.Auto`, `DocumentDirection.LeftToRight`, eller `DocumentDirection.RightToLeft`.

### Kan jag ange textriktningen för specifika stycken istället för hela dokumentet?

Ja, du kan ange textriktning för specifika stycken med hjälp av `ParagraphFormat.Bidi` egendom, men den `TxtLoadOptions.DocumentDirection` egenskapen anger standardriktningen för hela dokumentet.

### Vilka filformat stöds för laddning med `TxtLoadOptions`?

`TxtLoadOptions` används främst för att ladda textfiler (.txt). För andra filformat, använd andra klasser som `DocLoadOptions` eller `DocxLoadOptions`.

### Hur kan jag hantera dokument med blandade textinstruktioner?

För dokument med blandade textriktningar kan du behöva hantera formateringen per stycke. Använd `ParagraphFormat.Bidi` egenskapen för att justera varje styckes riktning efter behov.

### Var kan jag hitta mer information om Aspose.Words för .NET?

För mer information, kolla in [Aspose.Words för .NET-dokumentation](https://reference.aspose.com/words/net/)Du kan också utforska ytterligare resurser som [Nedladdningslänk](https://releases.aspose.com/words/net/), [Köpa](https://purchase.aspose.com/buy), [Gratis provperiod](https://releases.aspose.com/), [Tillfällig licens](https://purchase.aspose.com/temporary-license/)och [Stöd](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}