---
title: Ange listnivå
linktitle: Ange listnivå
second_title: Aspose.Words Document Processing API
description: Lär dig hur du skapar numrerade och punktlistor på flera nivåer i Word-dokument med Aspose.Words för .NET. Steg-för-steg-guide ingår. Perfekt för .NET-utvecklare.
weight: 10
url: /sv/net/working-with-list/specify-list-level/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ange listnivå

## Introduktion

Hej där, medkodare! Om du någonsin har brottats med att skapa dynamiska och sofistikerade listor i Word-dokument med hjälp av .NET, har du en njutning. Idag dyker vi in i världen av Aspose.Words för .NET. Specifikt kommer vi att fokusera på att specificera listnivåer. Se det som en nivå på ditt dokumentspel, så att du kan skapa professionella, polerade listor utan ansträngning. I slutet av den här guiden har du en tydlig väg till att skapa både numrerade och punktlistor med flera nivåer. Redo? Låt oss hoppa direkt in!

## Förutsättningar

Innan vi dyker in i det nitty-gritty, låt oss se till att vi har allt vi behöver. Här är en snabb checklista:

1.  Aspose.Words for .NET: Se till att du har Aspose.Words for .NET-biblioteket installerat. Du kan ladda ner den[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En IDE som Visual Studio kommer att göra ditt liv enklare.
3. .NET Framework: Se till att du har .NET Framework installerat på din dator.
4. Grundläggande förståelse för C#: Denna handledning förutsätter att du är bekväm med grundläggande C#-programmering.

Har du allt? Stor! Låt oss smutsa ner händerna.

## Importera namnområden

Först och främst måste vi importera de nödvändiga namnrymden. Öppna ditt C#-projekt och lägg till följande med hjälp av direktiv:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Detta skapar förutsättningar för att arbeta med Aspose.Words i ditt projekt.

## Steg 1: Konfigurera Document and DocumentBuilder

 Låt oss börja med att skapa ett nytt dokument och ett`DocumentBuilder` objekt att arbeta med det.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Skapa en numrerad lista

 Nu skapar vi en numrerad lista baserad på en av Microsoft Word-listmallarna och tillämpar den på`DocumentBuilder`'s nuvarande paragraf.

```csharp
builder.ListFormat.List = doc.Lists.Add(ListTemplate.NumberArabicDot);
```

## Steg 3: Tillämpa flera listnivåer

Aspose.Words låter dig ange upp till nio nivåer för en lista. Låt oss tillämpa dem alla för att se hur det fungerar.

```csharp
for (int i = 0; i < 9; i++)
{
    builder.ListFormat.ListLevelNumber = i;
    builder.Writeln("Level " + i);
}
```

I den här slingan ställer vi in listnivån för varje stycke och skriver en textrad som anger nivån.

## Steg 4: Skapa en punktlista

Låt oss sedan byta växel och skapa en punktlista. Den här gången använder vi en annan listmall.

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

Och det är det! Du har precis skapat ett dokument med komplexa liststrukturer med Aspose.Words för .NET.

## Slutsats

Att skapa strukturerade listor på flera nivåer i Word-dokument kan avsevärt förbättra läsbarheten och professionaliteten. Med Aspose.Words för .NET kan du automatisera denna process, vilket sparar tid och säkerställer konsekvens. Vi hoppas att den här guiden har hjälpt dig att förstå hur du anger listnivåer effektivt. Fortsätt experimentera och se hur kraftfullt det här verktyget kan vara för dina dokumentbehandlingsbehov.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter dig skapa, redigera, konvertera och skriva ut Word-dokument programmatiskt i C#.

### Kan jag använda Aspose.Words gratis?
Aspose.Words erbjuder en gratis testversion som du kan ladda ner[här](https://releases.aspose.com/) . För en fullständig version kan du kolla in köpalternativen[här](https://purchase.aspose.com/buy).

### Hur många nivåer kan jag ange i en lista med Aspose.Words?
Du kan ange upp till nio nivåer i en lista med Aspose.Words.

### Är det möjligt att blanda numrerade och punktlistor i ett enda dokument?
Ja, du kan blanda olika typer av listor i ett enda dokument genom att byta listmallen efter behov.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
 Du kan hitta detaljerad dokumentation[här](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
