---
title: Starta om listnummer
linktitle: Starta om listnummer
second_title: Aspose.Words Document Processing API
description: Lär dig hur du startar om listnummer i Word-dokument med Aspose.Words för .NET. Denna detaljerade guide på 2000 ord täcker allt du behöver veta, från installation till avancerad anpassning.
weight: 10
url: /sv/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Starta om listnummer

## Introduktion

Vill du behärska konsten att manipulera listor i dina Word-dokument med Aspose.Words för .NET? Nåväl, du är på rätt plats! I den här handledningen kommer vi att dyka djupt in i att starta om listnummer, en snygg funktion som tar dina färdigheter i dokumentautomatisering till nästa nivå. Spänn fast och låt oss börja!

## Förutsättningar

Innan vi hoppar in i koden, låt oss se till att du har allt du behöver:

1.  Aspose.Words för .NET: Du måste ha Aspose.Words för .NET installerat. Om du inte har installerat det än kan du göra det[ladda ner den här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Se till att du har en lämplig utvecklingsmiljö som Visual Studio.
3. Grundläggande kunskaper om C#: En grundläggande förståelse av C# hjälper dig att följa handledningen.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Dessa är avgörande för att få tillgång till Aspose.Words-funktionerna.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Låt oss nu dela upp processen i lätta att följa steg. Vi kommer att täcka allt från att skapa en lista till att starta om dess numrering.

## Steg 1: Konfigurera ditt dokument och Builder

Innan du kan börja manipulera listor behöver du ett dokument och en DocumentBuilder. DocumentBuilder är ditt go-to-verktyg för att lägga till innehåll i ditt dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Skapa och anpassa din första lista

Därefter skapar vi en lista baserad på en mall och anpassar dess utseende. I det här exemplet använder vi det arabiska talformatet med parenteser.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Här har vi ställt in teckensnittsfärgen till röd och justerat texten till höger.

## Steg 3: Lägg till objekt till din första lista

 Med din lista klar är det dags att lägga till några objekt. Dokumentbyggarens`ListFormat.List` egenskapen hjälper till att tillämpa listformatet på texten.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Steg 4: Starta om listnumrering

För att återanvända listan och starta om dess numrering måste du skapa en kopia av den ursprungliga listan. Detta gör att du kan ändra den nya listan oberoende.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

I det här exemplet börjar den nya listan på nummer 10.

## Steg 5: Lägg till objekt till den nya listan

Precis som tidigare, lägg till objekt i din nya lista. Detta visar att listan startar om vid det angivna numret.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Steg 6: Spara ditt dokument

Slutligen, spara ditt dokument i din angivna katalog.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Slutsats

Att starta om listnummer i Word-dokument med Aspose.Words för .NET är enkelt och otroligt användbart. Oavsett om du genererar rapporter, skapar strukturerade dokument eller bara behöver bättre kontroll över dina listor, har den här tekniken dig täckt.

## FAQ's

### Kan jag använda andra listmallar förutom NumberArabicParenthesis?

Absolut! Aspose.Words erbjuder olika listmallar som kulor, bokstäver, romerska siffror och mer. Du kan välja den som bäst passar dina behov.

### Hur ändrar jag listnivån?

 Du kan ändra listnivån genom att ändra`ListLevels` egendom. Till exempel,`list1.ListLevels[1]` skulle hänvisa till den andra nivån i listan.

### Kan jag starta om numrering på vilket nummer som helst?

 Ja, du kan ställa in startnumret till vilket heltalsvärde som helst med hjälp av`StartAt` egenskapen för listnivån.

### Är det möjligt att ha olika formatering för olika listnivåer?

Verkligen! Varje listnivå kan ha sina egna formateringsinställningar, såsom teckensnitt, justering och numreringsstil.

### Vad händer om jag vill fortsätta numreringen från en tidigare lista istället för att starta om?

Om du vill fortsätta numreringen behöver du inte skapa en kopia av listan. Fortsätt bara att lägga till objekt till den ursprungliga listan.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
