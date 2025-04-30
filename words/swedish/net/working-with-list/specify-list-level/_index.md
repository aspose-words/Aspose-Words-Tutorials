---
"description": "Lär dig hur du skapar numrerade listor och punktlistor i flera nivåer i Word-dokument med Aspose.Words för .NET. Steg-för-steg-guide ingår. Perfekt för .NET-utvecklare."
"linktitle": "Ange listnivå"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ange listnivå"
"url": "/sv/net/working-with-list/specify-list-level/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ange listnivå

## Introduktion

Hej där, kodare! Om du någonsin har brottats med att skapa dynamiska och sofistikerade listor i Word-dokument med hjälp av .NET, har du något att vänta dig. Idag dyker vi ner i Aspose.Words värld för .NET. Vi kommer specifikt att fokusera på att specificera listnivåer. Tänk på det som att höja nivån på ditt dokumentkunskap, så att du enkelt kan skapa professionella, polerade listor. I slutet av den här guiden har du en tydlig väg att skapa både numrerade och punktlistor med flera nivåer. Är du redo? Nu kör vi!

## Förkunskapskrav

Innan vi går in på detaljerna, låt oss se till att vi har allt vi behöver. Här är en snabb checklista:

1. Aspose.Words för .NET: Se till att du har Aspose.Words för .NET-biblioteket installerat. Du kan ladda ner det [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En IDE som Visual Studio kommer att göra ditt liv enklare.
3. .NET Framework: Se till att du har .NET Framework installerat på din dator.
4. Grundläggande förståelse för C#: Den här handledningen förutsätter att du är bekant med grundläggande C#-programmering.

Har du allt? Toppen! Nu smutsar vi ner händerna.

## Importera namnrymder

Först och främst behöver vi importera de nödvändiga namnrymderna. Öppna ditt C#-projekt och lägg till följande med hjälp av direktiv:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Detta banar väg för att arbeta med Aspose.Words i ditt projekt.

## Steg 1: Konfigurera dokumentet och DocumentBuilder

Låt oss börja med att skapa ett nytt dokument och ett `DocumentBuilder` motsätta sig att arbeta med det.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Skapa en numrerad lista

Nu ska vi skapa en numrerad lista baserad på en av listmallarna i Microsoft Word och tillämpa den på `DocumentBuilder`s nuvarande stycke.

```csharp
builder.ListFormat.List = doc.Lists.Add(ListTemplate.NumberArabicDot);
```

## Steg 3: Tillämpa flera listnivåer

Med Aspose.Words kan du ange upp till nio nivåer för en lista. Låt oss tillämpa alla för att se hur det fungerar.

```csharp
for (int i = 0; i < 9; i++)
{
    builder.ListFormat.ListLevelNumber = i;
    builder.Writeln("Level " + i);
}
```

I den här loopen ställer vi in listnivån för varje stycke och skriver en textrad som anger nivån.

## Steg 4: Skapa en punktlista

Nu ska vi byta växel och skapa en punktlista. Den här gången använder vi en annan listmall.

```csharp
builder.ListFormat.List = doc.Lists.Add(ListTemplate.BulletDiamonds);
```

## Steg 5: Tillämpa flera nivåer på punktlistan

Precis som med den numrerade listan kommer vi att tillämpa flera nivåer på vår punktlista.

```csharp
for (int i = 0; i < 9; i++)
{
    builder.ListFormat.ListLevelNumber = i;
    builder.Writeln("Level " + i);
}
```

## Steg 6: Stoppa listformatering

Slutligen, låt oss se hur vi kan stoppa listformateringen för att återgå till normal text.

```csharp
builder.ListFormat.List = null;
```

## Steg 7: Spara dokumentet

Efter allt det hårda arbetet är det dags att spara vårt dokument. Låt oss spara det med ett meningsfullt namn.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.SpecifyListLevel.docx");
```

Och det var allt! Du har just skapat ett dokument med komplexa liststrukturer med hjälp av Aspose.Words för .NET.

## Slutsats

Att skapa strukturerade listor med flera nivåer i Word-dokument kan avsevärt förbättra läsbarheten och professionalismen. Med Aspose.Words för .NET kan du automatisera denna process, vilket sparar tid och säkerställer konsekvens. Vi hoppas att den här guiden har hjälpt dig att förstå hur du anger listnivåer effektivt. Fortsätt experimentera och se hur kraftfullt det här verktyget kan vara för dina dokumentbehandlingsbehov.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter dig skapa, redigera, konvertera och skriva ut Word-dokument programmatiskt i C#.

### Kan jag använda Aspose.Words gratis?
Aspose.Words erbjuder en gratis testversion som du kan ladda ner [här](https://releases.aspose.com/)För en fullständig version kan du se köpalternativen [här](https://purchase.aspose.com/buy).

### Hur många nivåer kan jag ange i en lista med Aspose.Words?
Du kan ange upp till nio nivåer i en lista med Aspose.Words.

### Är det möjligt att blanda numrerade och punktlistor i ett enda dokument?
Ja, du kan blanda olika typer av listor i ett enda dokument genom att byta listmall efter behov.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
Du kan hitta detaljerad dokumentation [här](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}