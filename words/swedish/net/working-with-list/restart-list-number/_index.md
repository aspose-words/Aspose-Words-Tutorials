---
"description": "Lär dig hur du startar om listnummer i Word-dokument med Aspose.Words för .NET. Den här detaljerade guiden på 2000 ord täcker allt du behöver veta, från installation till avancerad anpassning."
"linktitle": "Starta om listnummer"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Starta om listnummer"
"url": "/sv/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Starta om listnummer

## Introduktion

Vill du bemästra konsten att manipulera listor i dina Word-dokument med Aspose.Words för .NET? Då har du kommit rätt! I den här handledningen ska vi fördjupa oss i att starta om listnummer, en smart funktion som tar dina dokumentautomatiseringsfärdigheter till nästa nivå. Spänn fast säkerhetsbältet, så sätter vi igång!

## Förkunskapskrav

Innan vi går in i koden, låt oss se till att du har allt du behöver:

1. Aspose.Words för .NET: Du måste ha Aspose.Words för .NET installerat. Om du inte har installerat det än kan du göra det [ladda ner den här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Se till att du har en lämplig utvecklingsmiljö som Visual Studio.
3. Grundläggande kunskaper i C#: Grundläggande förståelse för C# hjälper dig att följa handledningen.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna. Dessa är avgörande för att komma åt Aspose.Words-funktionerna.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Nu ska vi dela upp processen i enkla steg. Vi går igenom allt från att skapa en lista till att starta om numreringen.

## Steg 1: Konfigurera ditt dokument och din verktygsbyggare

Innan du kan börja manipulera listor behöver du ett dokument och en DocumentBuilder. DocumentBuilder är ditt bästa verktyg för att lägga till innehåll i ditt dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 2: Skapa och anpassa din första lista

Härnäst skapar vi en lista baserad på en mall och anpassar dess utseende. I det här exemplet använder vi arabiskt talformat med parenteser.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Här har vi ställt in teckenfärgen till röd och justerat texten till höger.

## Steg 3: Lägg till objekt i din första lista

När din lista är klar är det dags att lägga till några saker. DocumentBuilderns `ListFormat.List` egenskapen hjälper till att tillämpa listformatet på texten.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Steg 4: Starta om listnumreringen

För att återanvända listan och omforma numreringen måste du skapa en kopia av den ursprungliga listan. Detta gör att du kan ändra den nya listan oberoende av varandra.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

I det här exemplet börjar den nya listan på nummer 10.

## Steg 5: Lägg till objekt i den nya listan

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

Att omstarta listnummer i Word-dokument med Aspose.Words för .NET är enkelt och otroligt användbart. Oavsett om du genererar rapporter, skapar strukturerade dokument eller bara behöver bättre kontroll över dina listor, har den här tekniken det du behöver.

## Vanliga frågor

### Kan jag använda andra listmallar förutom NumberArabicParenthesis?

Absolut! Aspose.Words erbjuder olika listmallar som punkter, bokstäver, romerska siffror och mer. Du kan välja den som bäst passar dina behov.

### Hur ändrar jag listnivån?

Du kan ändra listnivån genom att modifiera `ListLevels` egendom. Till exempel, `list1.ListLevels[1]` skulle hänvisa till den andra nivån i listan.

### Kan jag starta om numreringen vid vilket nummer som helst?

Ja, du kan ställa in startnumret till vilket heltal som helst med hjälp av `StartAt` egenskapen för listnivån.

### Är det möjligt att ha olika formatering för olika listnivåer?

Javisst! Varje listnivå kan ha sina egna formateringsinställningar, såsom teckensnitt, justering och numreringsstil.

### Vad händer om jag vill fortsätta numreringen från en tidigare lista istället för att börja om?

Om du vill fortsätta numreringen behöver du inte skapa en kopia av listan. Fortsätt bara att lägga till objekt i den ursprungliga listan.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}