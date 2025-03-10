---
title: Lägg till gruppform
linktitle: Lägg till gruppform
second_title: Aspose.Words Document Processing API
description: Lär dig hur du lägger till gruppformer i Word-dokument med Aspose.Words för .NET med denna omfattande, steg-för-steg-handledning.
weight: 10
url: /sv/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till gruppform

## Introduktion

Att skapa komplexa dokument med rika visuella element kan ibland vara en svår uppgift, särskilt när man hanterar gruppformer. Men frukta inte! Aspose.Words för .NET förenklar denna process, vilket gör det lätt som en plätt. I den här handledningen går vi igenom stegen för att lägga till gruppformer i dina Word-dokument. Redo att dyka i? Låt oss komma igång!

## Förutsättningar

Innan vi börjar, se till att du har följande:

1.  Aspose.Words för .NET: Du kan ladda ner det från[Aspose releaser sida](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller någon annan IDE-kompatibel med .NET.
3. Grundläggande förståelse för C#: Bekantskap med C#-programmering är ett plus.

## Importera namnområden

För att börja måste vi importera de nödvändiga namnrymden i vårt projekt. Dessa namnrymder ger åtkomst till de klasser och metoder som krävs för att manipulera Word-dokument med Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Steg 1: Initiera dokumentet

Först till kvarn, låt oss initiera ett nytt Word-dokument. Se det här som att skapa en tom duk där vi lägger till våra gruppformer.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 Här,`EnsureMinimum()` lägger till en minimal uppsättning noder som krävs för dokumentet.

## Steg 2: Skapa GroupShape-objektet

 Därefter måste vi skapa en`GroupShape`objekt. Detta objekt kommer att fungera som en behållare för andra former, vilket gör att vi kan gruppera dem tillsammans.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Steg 3: Lägg till former i GroupShape

 Låt oss nu lägga till individuella former till vår`GroupShape` behållare. Vi börjar med en kantform med accent och lägger sedan till en åtgärdsknappsform.

### Lägga till en accentkantsform

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 Detta kodavsnitt skapar en kantform med accent med en bredd och höjd på 100 enheter och lägger till den i`GroupShape`.

### Lägga till en åtgärdsknappsform

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

 Här skapar vi en åtgärdsknappsform, placerar den och lägger till den i vår`GroupShape`.

## Steg 4: Definiera GroupShape-dimensionerna

 För att säkerställa att våra former passar bra inom gruppen måste vi ställa in måtten på`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 Detta definierar bredden och höjden på`GroupShape` som 200 enheter och ställer in koordinatstorleken därefter.

## Steg 5: Infoga GroupShape i dokumentet

 Nu, låt oss infoga vår`GroupShape` in i dokumentet med hjälp av`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` ger ett enkelt sätt att lägga till noder, inklusive former, till dokumentet.

## Steg 6: Spara dokumentet

Slutligen, spara dokumentet i din angivna katalog.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

Och där har du det! Ditt dokument med gruppformer är klart.

## Slutsats

Att lägga till gruppformer i dina Word-dokument behöver inte vara en komplicerad process. Med Aspose.Words för .NET kan du skapa och manipulera former med lätthet, vilket gör dina dokument mer visuellt tilltalande och funktionella. Följ stegen som beskrivs i den här handledningen och du kommer att bli ett proffs på nolltid!

## FAQ's

### Kan jag lägga till mer än två former i en GroupShape?
 Ja, du kan lägga till så många former som du behöver till en`GroupShape` . Använd bara`AppendChild` metod för varje form.

### Är det möjligt att styla formerna inom en GroupShape?
 Absolut! Varje form kan stylas individuellt med hjälp av egenskaperna som finns tillgängliga i`Shape` klass.

### Hur placerar jag GroupShape i dokumentet?
 Du kan placera`GroupShape` genom att ställa in dess`Left` och`Top` fastigheter.

### Kan jag lägga till text till formerna i GroupShape?
 Ja, du kan lägga till text till former med hjälp av`AppendChild` metod för att lägga till en`Paragraph` innehållande`Run` noder med text.

### Är det möjligt att gruppera former dynamiskt baserat på användarinmatning?
Ja, du kan dynamiskt skapa och gruppera former baserat på användarinmatning genom att justera egenskaperna och metoderna därefter.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
