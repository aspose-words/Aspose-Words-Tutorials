---
"description": "Lär dig hur du lägger till gruppformer i Word-dokument med Aspose.Words för .NET med den här omfattande steg-för-steg-handledningen."
"linktitle": "Lägg till gruppform"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Lägg till gruppform"
"url": "/sv/net/programming-with-shapes/add-group-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till gruppform

## Introduktion

Att skapa komplexa dokument med rika visuella element kan ibland vara en skrämmande uppgift, särskilt när man arbetar med gruppformer. Men frukta inte! Aspose.Words för .NET förenklar processen och gör det hur enkelt som helst. I den här handledningen guidar vi dig genom stegen för att lägga till gruppformer i dina Word-dokument. Redo att dyka in? Nu sätter vi igång!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET: Du kan ladda ner det från [Aspose-utgåvorsida](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller annan IDE kompatibel med .NET.
3. Grundläggande förståelse för C#: Kunskap om C#-programmering är meriterande.

## Importera namnrymder

För att börja behöver vi importera de nödvändiga namnrymderna i vårt projekt. Dessa namnrymder ger åtkomst till de klasser och metoder som krävs för att manipulera Word-dokument med Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Steg 1: Initiera dokumentet

Först och främst, låt oss initiera ett nytt Word-dokument. Tänk på detta som att skapa en tom arbetsyta där vi lägger till våra gruppformer.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

Här, `EnsureMinimum()` lägger till en minimal uppsättning noder som krävs för dokumentet.

## Steg 2: Skapa GroupShape-objektet

Nästa steg är att skapa en `GroupShape` objekt. Detta objekt kommer att fungera som en behållare för andra former, vilket gör att vi kan gruppera dem tillsammans.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Steg 3: Lägg till former i gruppformen

Nu ska vi lägga till individuella former till vår `GroupShape` behållare. Vi börjar med en accentkantform och lägger sedan till en åtgärdsknappsform.

### Lägga till en accentkantform

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

Det här kodavsnittet skapar en accentkantform med en bredd och höjd på 100 enheter och lägger till den i `GroupShape`.

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

Här skapar vi en åtgärdsknappsform, placerar den och lägger till den i vår `GroupShape`.

## Steg 4: Definiera GroupShape-dimensionerna

För att säkerställa att våra former passar bra inom gruppen måste vi ange måtten på `GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

Detta definierar bredden och höjden på `GroupShape` som 200 enheter och ställer in koordinatstorleken därefter.

## Steg 5: Infoga gruppformen i dokumentet

Nu ska vi lägga in vår `GroupShape` in i dokumentet med hjälp av `DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` ger ett enkelt sätt att lägga till noder, inklusive former, i dokumentet.

## Steg 6: Spara dokumentet

Slutligen, spara dokumentet i den angivna katalogen.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

Och där har du det! Ditt dokument med gruppformer är klart.

## Slutsats

Att lägga till gruppformer i dina Word-dokument behöver inte vara en komplicerad process. Med Aspose.Words för .NET kan du enkelt skapa och manipulera former, vilket gör dina dokument mer visuellt tilltalande och funktionella. Följ stegen som beskrivs i den här handledningen, så blir du ett proffs på nolltid!

## Vanliga frågor

### Kan jag lägga till fler än två former i en gruppform?
Ja, du kan lägga till så många former du behöver `GroupShape`Använd bara `AppendChild` metod för varje form.

### Är det möjligt att formatera formerna inom en GroupShape?
Absolut! Varje form kan utformas individuellt med hjälp av de egenskaper som finns i `Shape` klass.

### Hur placerar jag gruppformen i dokumentet?
Du kan placera `GroupShape` genom att sätta dess `Left` och `Top` egenskaper.

### Kan jag lägga till text i formerna i gruppformen?
Ja, du kan lägga till text i former med hjälp av `AppendChild` metod för att lägga till en `Paragraph` innehållande `Run` noder med text.

### Är det möjligt att gruppera former dynamiskt baserat på användarinmatning?
Ja, du kan dynamiskt skapa och gruppera former baserat på användarinmatning genom att justera egenskaper och metoder därefter.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}