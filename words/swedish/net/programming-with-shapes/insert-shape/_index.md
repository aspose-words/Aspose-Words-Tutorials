---
"description": "Lär dig hur du infogar och manipulerar former i Word-dokument med Aspose.Words för .NET med vår steg-för-steg-guide."
"linktitle": "Infoga form"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Infoga form"
"url": "/sv/net/programming-with-shapes/insert-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga form

## Introduktion

När det gäller att skapa visuellt tilltalande och välstrukturerade Word-dokument kan former spela en viktig roll. Oavsett om du lägger till pilar, rutor eller till och med komplexa anpassade former, erbjuder möjligheten att manipulera dessa element programmatiskt oöverträffad flexibilitet. I den här handledningen utforskar vi hur man infogar och manipulerar former i Word-dokument med Aspose.Words för .NET.

## Förkunskapskrav

Innan du börjar med handledningen, se till att du har följande förkunskaper:

1. Aspose.Words för .NET: Ladda ner och installera den senaste versionen från [Aspose-utgåvorsida](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En lämplig .NET-utvecklingsmiljö, till exempel Visual Studio.
3. Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# och grundläggande begrepp.

## Importera namnrymder

För att komma igång måste du importera de nödvändiga namnrymderna i ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Steg 1: Konfigurera ditt projekt

Innan du kan börja infoga former måste du konfigurera ditt projekt och lägga till Aspose.Words för .NET-biblioteket.

1. Skapa ett nytt projekt: Öppna Visual Studio och skapa ett nytt C# Console Application-projekt.
2. Lägg till Aspose.Words för .NET: Installera Aspose.Words för .NET-biblioteket via NuGet Package Manager.

```bash
Install-Package Aspose.Words
```

## Steg 2: Initiera dokumentet

Först måste du initiera ett nytt dokument och en dokumentbyggare, vilket hjälper till att konstruera dokumentet.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Initiera ett nytt dokument
Document doc = new Document();

// Initiera en DocumentBuilder för att hjälpa till att bygga dokumentet
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 3: Infoga en form

Nu ska vi infoga en form i dokumentet. Vi börjar med att lägga till en enkel textruta.

```csharp
// Infoga en textruteform i dokumentet
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Rotera formen
shape.Rotation = 30.0;
```

I det här exemplet infogar vi en textruta på positionen (100, 100) med en bredd och höjd på 50 enheter vardera. Vi roterar också formen 30 grader.

## Steg 4: Lägg till en annan form

Låt oss lägga till en annan form i dokumentet, den här gången utan att ange positionen.

```csharp
// Lägg till en annan textruteform
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Rotera formen
secondShape.Rotation = 30.0;
```

Det här kodavsnittet infogar en annan textruta med samma dimensioner och rotation som den första men utan att ange dess position.

## Steg 5: Spara dokumentet

Efter att du har lagt till formerna är det sista steget att spara dokumentet. Vi kommer att använda `OoxmlSaveOptions` för att ange sparformatet.

```csharp
// Definiera sparalternativ med efterlevnad
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Spara dokumentet
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Slutsats

Och där har du det! Du har lyckats infoga och manipulera former i ett Word-dokument med Aspose.Words för .NET. Den här handledningen behandlade grunderna, men Aspose.Words erbjuder många fler avancerade funktioner för att arbeta med former, till exempel anpassade stilar, kopplingar och gruppformer.

För mer detaljerad information, besök [Aspose.Words för .NET-dokumentation](https://reference.aspose.com/words/net/).

## Vanliga frågor

### Hur infogar jag olika typer av former?
Du kan ändra `ShapeType` i `InsertShape` metod för att infoga olika typer av former som cirklar, rektanglar och pilar.

### Kan jag lägga till text inuti formerna?
Ja, du kan använda `builder.Write` metod för att lägga till text inuti formerna efter att du har infogat dem.

### Är det möjligt att styla formerna?
Ja, du kan utforma formerna genom att ange egenskaper som `FillColor`, `StrokeColor`och `StrokeWeight`.

### Hur placerar jag former i förhållande till andra element?
Använd `RelativeHorizontalPosition` och `RelativeVerticalPosition` egenskaper för att placera former i förhållande till andra element i dokumentet.

### Kan jag gruppera flera former tillsammans?
Ja, Aspose.Words för .NET låter dig gruppera former med hjälp av `GroupShape` klass.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}