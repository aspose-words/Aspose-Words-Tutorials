---
title: Beställd lista
linktitle: Beställd lista
second_title: Aspose.Words Document Processing API
description: Lär dig hur du skapar ordnade listor i Word-dokument med Aspose.Words för .NET med vår steg-för-steg-guide. Perfekt för att automatisera dokumentskapande.
weight: 10
url: /sv/net/working-with-markdown/ordered-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Beställd lista

## Introduktion

Så du har bestämt dig för att dyka in i Aspose.Words för .NET för att skapa fantastiska Word-dokument programmatiskt. Fantastiskt val! Idag ska vi bryta ner hur man skapar en ordnad lista i ett Word-dokument. Vi tar det steg för steg, så oavsett om du är en nybörjare som kodar eller ett erfaret proffs, kommer du att tycka att den här guiden är väldigt användbar. Låt oss komma igång!

## Förutsättningar

Innan vi dyker in i koden finns det några saker du behöver:

1. Aspose.Words för .NET: Se till att du har Aspose.Words för .NET installerat. Om du inte gör det kan du ladda ner den[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller någon annan .NET-kompatibel IDE.
3. Grundläggande kunskaper i C#: Du bör vara bekväm med C#-grunderna för att enkelt kunna följa med.

## Importera namnområden

För att använda Aspose.Words i ditt projekt måste du importera de nödvändiga namnrymden. Det här är som att ställa in din verktygslåda innan du börjar arbeta.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

Låt oss dela upp koden i lagom stora steg och förklara varje del. Redo? Här går vi!

## Steg 1: Initiera dokumentet

Först och främst måste du skapa ett nytt dokument. Se detta som att öppna ett tomt Word-dokument på din dator.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Här initierar vi ett nytt dokument och ett DocumentBuilder-objekt. DocumentBuilder är som din penna, så att du kan skriva innehåll i dokumentet.

## Steg 2: Använd numrerad listformat

Låt oss nu tillämpa ett standardformat för numrerade listor. Det här är som att ställa in ditt Word-dokument att använda numrerade punkter.

```csharp
builder.ListFormat.ApplyNumberDefault();
```

Denna kodrad ställer in numreringen för din lista. Lätt, eller hur?

## Steg 3: Lägg till listobjekt

Låt oss sedan lägga till några objekt till vår lista. Föreställ dig att du skriver ner en inköpslista.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

Med dessa rader lägger du till de två första objekten till din lista.

## Steg 4: Dra in listan

Vad händer om du vill lägga till underobjekt under ett objekt? Låt oss göra det!

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

 De`ListIndent` metoden drar in listan och skapar en underlista. Du skapar nu en hierarkisk lista, ungefär som en kapslad att-göra-lista.

## Slutsats

Att skapa en ordnad lista i ett Word-dokument programmatiskt kan verka skrämmande till en början, men med Aspose.Words för .NET är det enkelt. Genom att följa dessa enkla steg kan du enkelt lägga till och hantera listor i dina dokument. Oavsett om du genererar rapporter, skapar strukturerade dokument eller bara automatiserar dina arbetsflöden, har Aspose.Words för .NET dig täckt. Så varför vänta? Börja koda och se magin utvecklas!

## FAQ's

### Kan jag anpassa numreringsstilen för listan?  
 Ja, du kan anpassa numreringsstilen med hjälp av`ListFormat`fastigheter. Du kan ställa in olika numreringsstilar som romerska siffror, bokstäver etc.

### Hur lägger jag till fler nivåer av indrag?  
 Du kan använda`ListIndent` metod flera gånger för att skapa djupare nivåer av underlistor. Varje samtal till`ListIndent` lägger till en nivå av indrag.

### Kan jag blanda punktlistor och numrerade listor?  
 Absolut! Du kan använda olika listformat inom samma dokument med hjälp av`ListFormat` egendom.

### Är det möjligt att fortsätta numreringen från en tidigare lista?  
Ja, du kan fortsätta numreringen genom att använda samma listformat. Aspose.Words låter dig styra listnumrering över olika stycken.

### Hur tar jag bort listformatet?  
 Du kan ta bort listformatet genom att ringa`ListFormat.RemoveNumbers()`. Detta kommer att göra om listobjekten till vanliga stycken.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
