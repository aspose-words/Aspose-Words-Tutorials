---
"description": "Upptäck hur du använder Aspose.Words för .NET för att upptäcka numrering med blanksteg i klartextdokument och säkerställa att dina listor känns igen korrekt."
"linktitle": "Identifiera numrering med mellanslag"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Identifiera numrering med mellanslag"
"url": "/sv/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Identifiera numrering med mellanslag

## Introduktion

Aspose.Words för .NET-entusiaster! Idag dyker vi ner i en fascinerande funktion som kan göra det enkelt att hantera listor i klartextdokument. Har du någonsin hanterat textfiler där vissa rader ska vara listor, men de ser helt enkelt inte riktigt rätt ut när de laddas in i ett Word-dokument? Vi har ett smart knep i rockärmen: att upptäcka numrering med mellanslag. Den här handledningen går igenom hur du använder... `DetectNumberingWithWhitespaces` alternativet i Aspose.Words för .NET för att säkerställa att dina listor känns igen korrekt, även när det finns mellanslag mellan siffrorna och texten.

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

- Aspose.Words för .NET: Du kan ladda ner det från [Aspose-utgåvor](https://releases.aspose.com/words/net/) sida.
- Utvecklingsmiljö: Visual Studio eller annan C# IDE.
- .NET Framework installerat på din dator.
- Grundläggande kunskaper i C#: Att förstå grunderna hjälper dig att följa exemplen.

## Importera namnrymder

Innan du börjar med koden, se till att du har importerat de nödvändiga namnrymderna till ditt projekt. Här är ett snabbt utdrag för att komma igång:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Låt oss dela upp processen i enkla, hanterbara steg. Varje steg guidar dig genom den nödvändiga koden och förklarar vad som händer.

## Steg 1: Definiera din dokumentkatalog

Först och främst, låt oss ställa in sökvägen till din dokumentkatalog. Det är här dina in- och utdatafiler kommer att lagras.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Skapa ett klartextdokument

Härnäst skapar vi ett klartextdokument som en sträng. Detta dokument kommer att innehålla delar som kan tolkas som listor.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Steg 3: Konfigurera LoadOptions

För att upptäcka numrering med mellanslag måste vi ställa in `DetectNumberingWithWhitespaces` alternativ till `true` i en `TxtLoadOptions` objekt.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Steg 4: Ladda dokumentet

Nu ska vi ladda dokumentet med hjälp av `TxtLoadOptions` som en parameter. Detta säkerställer att den fjärde listan (med mellanslag) detekteras korrekt.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Steg 5: Spara dokumentet

Spara slutligen dokumentet i den angivna katalogen. Detta skapar ett Word-dokument med korrekt identifierade listor.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Slutsats

Och där har du det! Med bara några få rader kod har du bemästrat konsten att upptäcka numrering med mellanslag i klartextdokument med hjälp av Aspose.Words för .NET. Den här funktionen kan vara otroligt praktisk när du hanterar olika textformat och säkerställer att dina listor representeras korrekt i dina Word-dokument. Så nästa gång du stöter på de där knepiga listorna vet du exakt vad du ska göra.

## Vanliga frågor

### Vad är `DetectNumberingWithWhitespaces` i Aspose.Words för .NET?
`DetectNumberingWithWhitespaces` är ett alternativ i `TxtLoadOptions` som gör att Aspose.Words kan känna igen listor även när det finns mellanslag mellan numreringen och listobjektets text.

### Kan jag använda den här funktionen för andra avgränsare som punkter och hakparenteser?
Ja, Aspose.Words identifierar automatiskt listor med vanliga avgränsare som punkter och hakparenteser. `DetectNumberingWithWhitespaces` hjälper specifikt till med listor som innehåller blanksteg.

### Vad händer om jag inte använder `DetectNumberingWithWhitespaces`?
Utan det här alternativet kanske listor med blanksteg mellan numreringen och texten inte känns igen som listor, och objekten kan visas som vanliga stycken.

### Finns den här funktionen i andra Aspose-produkter?
Den här specifika funktionen är skräddarsydd för Aspose.Words för .NET, utformad för att hantera Word-dokumentbehandling.

### Hur kan jag få en tillfällig licens för Aspose.Words för .NET?
Du kan få en tillfällig licens från [Aspose tillfällig licens](https://purchase.aspose.com/temporary-license/) sida.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}