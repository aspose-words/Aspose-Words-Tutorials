---
"description": "Upptäck hur du får fram de faktiska formgränspunkterna i Word-dokument med Aspose.Words för .NET. Lär dig exakt formmanipulation med den här detaljerade guiden."
"linktitle": "Hämta faktiska formgränspunkter"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Hämta faktiska formgränspunkter"
"url": "/sv/net/programming-with-shapes/get-actual-shape-bounds-points/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hämta faktiska formgränspunkter

## Introduktion

Har du någonsin försökt manipulera former i dina Word-dokument och undrat över deras exakta mått? Att känna till de exakta gränserna för former kan vara avgörande för olika dokumentredigerings- och formateringsuppgifter. Oavsett om du skapar en detaljerad rapport, ett fint nyhetsbrev eller en sofistikerad flyer, säkerställer förståelse för formens mått att din design ser helt rätt ut. I den här guiden går vi in på hur man får de faktiska gränserna för former i punkter med Aspose.Words för .NET. Redo att göra dina former bildperfekta? Nu sätter vi igång!

## Förkunskapskrav

Innan vi går in på detaljerna, låt oss se till att du har allt du behöver:

1. Aspose.Words för .NET: Se till att du har Aspose.Words för .NET-biblioteket installerat. Om inte kan du ladda ner det. [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Du bör ha en utvecklingsmiljö konfigurerad, till exempel Visual Studio.
3. Grundläggande kunskaper i C#: Den här guiden förutsätter att du har grundläggande förståelse för C#-programmering.

## Importera namnrymder

Låt oss först importera de nödvändiga namnrymderna. Detta är avgörande eftersom det ger oss åtkomst till klasserna och metoderna som tillhandahålls av Aspose.Words för .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Steg 1: Skapa ett nytt dokument

För att börja behöver vi skapa ett nytt dokument. Det här dokumentet kommer att fungera som arbetsytan där vi infogar och manipulerar våra former.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Här skapar vi en instans av `Document` klass och en `DocumentBuilder` för att hjälpa oss att infoga innehåll i dokumentet.

## Steg 2: Infoga en bildform

Nu ska vi infoga en bild i dokumentet. Den här bilden kommer att fungera som vår form, och vi kommer senare att hämta dess gränser.

```csharp
Shape shape = builder.InsertImage("YOUR DOCUMENT DIRECTORY/Transparent background logo.png");
```

Ersätta `"YOUR DOCUMENT DIRECTORY/Transparent background logo.png"` med sökvägen till din bildfil. Den här raden infogar bilden i dokumentet som en form.

## Steg 3: Lås upp bildförhållandet

I det här exemplet låser vi upp bildförhållandet för formen. Det här steget är valfritt men användbart om du planerar att ändra storlek på formen.

```csharp
shape.AspectRatioLocked = false;
```

Genom att låsa upp bildförhållandet kan vi ändra storlek på formen fritt utan att behålla dess ursprungliga proportioner.

## Steg 4: Hämta formgränserna

Nu kommer den spännande delen – att hämta formens faktiska gränser i punkter. Denna information kan vara avgörande för exakt positionering och layout.

```csharp
Console.Write("\nGets the actual bounds of the shape in points: ");
Console.WriteLine(shape.GetShapeRenderer().BoundsInPoints);
```

De `GetShapeRenderer` Metoden tillhandahåller en renderare för formen, och `BoundsInPoints` ger oss de exakta måtten.

## Slutsats

Och där har du det! Du har lyckats hämta de faktiska gränserna för en form i punkter med hjälp av Aspose.Words för .NET. Denna kunskap ger dig möjlighet att manipulera och placera former med precision, vilket säkerställer att dina dokument ser ut exakt som du föreställer dig dem. Oavsett om du designar komplexa layouter eller bara behöver justera ett element, är förståelsen av formgränser revolutionerande.

## Vanliga frågor

### Varför är det viktigt att känna till gränserna för en form?
Att känna till gränserna hjälper till att placera och justera former exakt i dokumentet, vilket säkerställer ett professionellt utseende.

### Kan jag använda andra typer av former förutom bilder?
Absolut! Du kan använda vilken form som helst, till exempel rektanglar, cirklar och anpassade teckningar.

### Vad händer om min bild inte visas i dokumentet?
Se till att filsökvägen är korrekt och att bilden finns på den platsen. Dubbelkolla om det finns stavfel eller felaktiga katalogreferenser.

### Hur kan jag bibehålla bildförhållandet för min form?
Uppsättning `shape.AspectRatioLocked = true;` för att bibehålla de ursprungliga proportionerna vid storleksändring.

### Är det möjligt att få gränser i andra enheter än poäng?
Ja, du kan konvertera punkter till andra enheter som tum eller centimeter med hjälp av lämpliga konverteringsfaktorer.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}