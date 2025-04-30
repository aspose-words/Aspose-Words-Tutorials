---
"description": "Lär dig hur du hanterar formändringar i Word-dokument med Aspose.Words för .NET med den här omfattande guiden. Bemästra spårning av ändringar, infogning av former och mer."
"linktitle": "Formrevision"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Formrevision"
"url": "/sv/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formrevision

## Introduktion

Att redigera Word-dokument programmatiskt kan vara en svår uppgift, särskilt när det gäller att hantera former. Oavsett om du skapar rapporter, designar mallar eller helt enkelt automatiserar dokumentskapandet är möjligheten att spåra och hantera formändringar avgörande. Aspose.Words för .NET erbjuder ett kraftfullt API för att göra denna process sömlös och effektiv. I den här handledningen går vi in på detaljerna kring att revidera former i Word-dokument, så att du har verktygen och kunskapen för att hantera dina dokument med lätthet.

## Förkunskapskrav

Innan vi går in i koden, låt oss se till att du har allt du behöver:

- Aspose.Words för .NET: Se till att du har Aspose.Words-biblioteket installerat. Du kan [ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Du bör ha en utvecklingsmiljö konfigurerad, till exempel Visual Studio.
- Grundläggande förståelse för C#: Bekantskap med programmeringsspråket C# och grundläggande koncept inom objektorienterad programmering.
- Word-dokument: Ett Word-dokument att arbeta med, eller så kan du skapa ett under handledningen.

## Importera namnrymder

Först importerar vi de nödvändiga namnrymderna. Dessa ger oss tillgång till de klasser och metoder som krävs för att hantera Word-dokument och former.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Steg 1: Konfigurera din dokumentkatalog

Innan vi börjar arbeta med former måste vi definiera sökvägen till vår dokumentkatalog. Det är här vi sparar våra modifierade dokument.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Skapa ett nytt dokument

Nu skapar vi ett nytt Word-dokument där vi ska infoga och redigera former.

```csharp
Document doc = new Document();
```

## Steg 3: Infoga en inbäddad form

Vi börjar med att infoga en inbäddad form i vårt dokument utan att spåra ändringar. En inbäddad form är en som flyter med texten.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Steg 4: Börja spåra revisioner

För att spåra ändringar i vårt dokument måste vi aktivera revisionsspårning. Detta är viktigt för att identifiera ändringar som gjorts i former.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Steg 5: Infoga en annan form med revideringar

Nu när revisionsspårning är aktiverad, låt oss infoga en annan form. Den här gången kommer alla ändringar att spåras.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Steg 6: Hämta och modifiera former

Vi kan hämta alla former i dokumentet och ändra dem efter behov. Här hämtar vi formerna och tar bort den första.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Steg 7: Spara dokumentet

Efter att vi har gjort våra ändringar måste vi spara dokumentet. Detta säkerställer att alla revideringar och ändringar lagras.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Steg 8: Hantera revideringar av formflyttningar

När en form flyttas, spårar Aspose.Words detta som en revision. Det betyder att det kommer att finnas två instanser av formen: en på dess ursprungliga plats och en på dess nya plats.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Slutsats

Och där har du det! Du har framgångsrikt lärt dig hur man hanterar formändringar i Word-dokument med hjälp av Aspose.Words för .NET. Oavsett om du hanterar dokumentmallar, automatiserar rapporter eller helt enkelt håller reda på ändringar är dessa färdigheter ovärderliga. Genom att följa den här steg-för-steg-guiden har du inte bara bemästrat grunderna utan också fått insikt i mer avancerade dokumenthanteringstekniker.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, modifiera och konvertera Word-dokument programmatiskt med hjälp av C#.

### Kan jag spåra ändringar som gjorts i andra element i ett Word-dokument?
Ja, Aspose.Words för .NET stöder spårning av ändringar i olika element, inklusive text, tabeller med mera.

### Hur kan jag få en gratis provversion av Aspose.Words för .NET?
Du kan få en gratis provversion av Aspose.Words för .NET [här](https://releases.aspose.com/).

### Är det möjligt att acceptera eller avvisa revisioner programmatiskt?
Ja, Aspose.Words för .NET tillhandahåller metoder för att acceptera eller avvisa revisioner programmatiskt.

### Kan jag använda Aspose.Words för .NET med andra .NET-språk förutom C#?
Absolut! Aspose.Words för .NET kan användas med alla .NET-språk, inklusive VB.NET och F#.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}