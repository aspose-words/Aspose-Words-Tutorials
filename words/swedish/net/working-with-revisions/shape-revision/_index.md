---
title: Formrevision
linktitle: Formrevision
second_title: Aspose.Words Document Processing API
description: Lär dig hur du hanterar formrevisioner i Word-dokument med Aspose.Words för .NET med den här omfattande guiden. Bemästra spåra ändringar, infoga former och mer.
weight: 10
url: /sv/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formrevision

## Introduktion

Att redigera Word-dokument programmatiskt kan vara en skrämmande uppgift, särskilt när det gäller att hantera former. Oavsett om du skapar rapporter, designar mallar eller helt enkelt automatiserar dokumentskapandet, är förmågan att spåra och hantera formrevisioner avgörande. Aspose.Words för .NET erbjuder ett kraftfullt API för att göra denna process sömlös och effektiv. I den här självstudien kommer vi att dyka ner i detaljerna för att revidera former i Word-dokument, och se till att du har verktygen och kunskapen för att hantera dina dokument med lätthet.

## Förutsättningar

Innan vi dyker in i koden, låt oss se till att du har allt du behöver:

-  Aspose.Words för .NET: Se till att du har Aspose.Words-biblioteket installerat. Du kan[ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Du bör ha en utvecklingsmiljö inrättad, som Visual Studio.
- Grundläggande förståelse för C#: Bekantskap med programmeringsspråket C# och grundläggande begrepp inom objektorienterad programmering.
- Word-dokument: Ett Word-dokument att arbeta med, eller så kan du skapa ett under handledningen.

## Importera namnområden

Låt oss först importera de nödvändiga namnrymden. Dessa ger oss tillgång till de klasser och metoder som krävs för att hantera Word-dokument och former.

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

Låt oss skapa ett nytt Word-dokument där vi infogar och reviderar former.

```csharp
Document doc = new Document();
```

## Steg 3: Infoga en inline-form

Vi börjar med att infoga en inline-form i vårt dokument utan att spåra revisioner. En inlineform är en som flyter med texten.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Steg 4: Börja spåra revisioner

För att spåra ändringar i vårt dokument måste vi aktivera revisionsspårning. Detta är viktigt för att identifiera modifieringar av former.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Steg 5: Infoga en annan form med revisioner

Nu när revisionsspårning är aktiverad, låt oss infoga en annan form. Den här gången kommer alla ändringar att spåras.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Steg 6: Hämta och ändra former

Vi kan hämta alla former i dokumentet och modifiera dem efter behov. Här tar vi formerna och tar bort den första.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Steg 7: Spara dokumentet

Efter att ha gjort våra ändringar måste vi spara dokumentet. Detta säkerställer att alla revisioner och ändringar lagras.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Steg 8: Hantera Shape Move-revisioner

När en form flyttas spårar Aspose.Words detta som en revision. Det betyder att det kommer att finnas två instanser av formen: en på sin ursprungliga plats och en på sin nya plats.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Slutsats

Och där har du det! Du har framgångsrikt lärt dig hur du hanterar formrevisioner i Word-dokument med Aspose.Words för .NET. Oavsett om du hanterar dokumentmallar, automatiserar rapporter eller helt enkelt håller reda på ändringar, är dessa färdigheter ovärderliga. Genom att följa denna steg-för-steg-guide har du inte bara bemästrat grunderna utan också fått insikt i mer avancerade dokumenthanteringstekniker.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, modifiera och konvertera Word-dokument programmatiskt med C#.

### Kan jag spåra ändringar som gjorts i andra element i ett Word-dokument?
Ja, Aspose.Words för .NET stöder spårning av ändringar av olika element, inklusive text, tabeller och mer.

### Hur kan jag få en gratis provversion av Aspose.Words för .NET?
 Du kan få en gratis provversion av Aspose.Words för .NET[här](https://releases.aspose.com/).

### Är det möjligt att acceptera eller avvisa ändringar programmatiskt?
Ja, Aspose.Words för .NET tillhandahåller metoder för att acceptera eller avvisa ändringar programmatiskt.

### Kan jag använda Aspose.Words för .NET med andra .NET-språk än C#?
Absolut! Aspose.Words för .NET kan användas med alla .NET-språk, inklusive VB.NET och F#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
