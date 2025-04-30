---
"description": "Lär dig hur du skapar ordnade listor i Word-dokument med Aspose.Words för .NET med vår steg-för-steg-guide. Perfekt för att automatisera dokumentskapandet."
"linktitle": "Ordnad lista"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ordnad lista"
"url": "/sv/net/working-with-markdown/ordered-list/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ordnad lista

## Introduktion

Så, du har bestämt dig för att börja använda Aspose.Words för .NET för att skapa fantastiska Word-dokument programmatiskt. Fantastiskt val! Idag ska vi gå igenom hur man skapar en ordnad lista i ett Word-dokument. Vi tar det steg för steg, så oavsett om du är en nybörjare inom kodning eller ett erfaret proffs, kommer du att tycka att den här guiden är superhjälpsam. Nu sätter vi igång!

## Förkunskapskrav

Innan vi går in i koden finns det några saker du behöver:

1. Aspose.Words för .NET: Se till att du har Aspose.Words för .NET installerat. Om du inte har det kan du ladda ner det. [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller annan .NET-kompatibel IDE.
3. Grundläggande kunskaper i C#: Du bör vara bekväm med grunderna i C# för att enkelt kunna följa med.

## Importera namnrymder

För att använda Aspose.Words i ditt projekt måste du importera de nödvändiga namnrymderna. Detta är som att konfigurera din verktygslåda innan du börjar arbeta.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

Låt oss dela upp koden i enkla steg och förklara varje del. Är du redo? Nu kör vi!

## Steg 1: Initiera dokumentet

Först och främst behöver du skapa ett nytt dokument. Tänk på det som att öppna ett tomt Word-dokument på din dator.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Här initierar vi ett nytt dokument och ett DocumentBuilder-objekt. DocumentBuilder är som din penna, som låter dig skriva innehåll i dokumentet.

## Steg 2: Använd numrerad listformat

Nu ska vi använda ett standardformat för numrerade listor. Det här är som att ställa in ditt Word-dokument för att använda numrerade punkter.

```csharp
builder.ListFormat.ApplyNumberDefault();
```

Den här kodraden ställer in numreringen för din lista. Enkelt, eller hur?

## Steg 3: Lägg till listobjekt

Nu ska vi lägga till några saker på vår lista. Tänk dig att du skriver en inköpslista.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

Med dessa rader lägger du till de två första punkterna i din lista.

## Steg 4: Indrag listan

Vad händer om du vill lägga till underobjekt under ett objekt? Nu gör vi det!

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

De `ListIndent` Metoden indenterar listan och skapar en underlista. Du skapar nu en hierarkisk lista, ungefär som en kapslad att-göra-lista.

## Slutsats

Att skapa en ordnad lista i ett Word-dokument programmatiskt kan verka skrämmande till en början, men med Aspose.Words för .NET är det jättekul. Genom att följa dessa enkla steg kan du enkelt lägga till och hantera listor i dina dokument. Oavsett om du genererar rapporter, skapar strukturerade dokument eller bara automatiserar dina arbetsflöden, har Aspose.Words för .NET det du behöver. Så varför vänta? Börja koda och se magin utvecklas!

## Vanliga frågor

### Kan jag anpassa numreringsstilen för listan?  
Ja, du kan anpassa numreringsstilen med hjälp av `ListFormat` egenskaper. Du kan ställa in olika numreringsstilar som romerska siffror, bokstäver etc.

### Hur lägger jag till fler nivåer av indentering?  
Du kan använda `ListIndent` metoden flera gånger för att skapa djupare nivåer av underlistor. Varje anrop till `ListIndent` lägger till en nivå av indentering.

### Kan jag blanda punktlistor och numrerade listor?  
Absolut! Du kan använda olika listformat inom samma dokument med hjälp av `ListFormat` egendom.

### Är det möjligt att fortsätta numreringen från en tidigare lista?  
Ja, du kan fortsätta numreringen genom att använda samma listformat. Aspose.Words låter dig styra listnumreringen över olika stycken.

### Hur kan jag ta bort listformatet?  
Du kan ta bort listformatet genom att anropa `ListFormat.RemoveNumbers()`Detta kommer att återställa listposterna till vanliga stycken.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}