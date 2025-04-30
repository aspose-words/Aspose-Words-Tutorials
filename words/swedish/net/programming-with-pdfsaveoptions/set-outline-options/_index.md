---
"description": "Lär dig hur du ställer in dispositionsalternativ i ett PDF-dokument med Aspose.Words för .NET. Förbättra PDF-navigering genom att konfigurera rubriknivåer och utökade dispositioner."
"linktitle": "Ange dispositionsalternativ i ett PDF-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ange dispositionsalternativ i ett PDF-dokument"
"url": "/sv/net/programming-with-pdfsaveoptions/set-outline-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ange dispositionsalternativ i ett PDF-dokument

## Introduktion

När du arbetar med dokument, särskilt för professionella eller akademiska ändamål, är det avgörande att organisera ditt innehåll effektivt. Ett sätt att förbättra användbarheten hos dina PDF-dokument är att ställa in dispositionsalternativ. Dispositioner, eller bokmärken, låter användare navigera effektivt genom dokumentet, precis som kapitel i en bok. I den här guiden går vi in på hur du kan ställa in dessa alternativ med Aspose.Words för .NET, vilket säkerställer att dina PDF-filer är välorganiserade och användarvänliga.

## Förkunskapskrav

Innan du börjar finns det några saker du behöver se till att du har:

1. Aspose.Words för .NET: Se till att du har Aspose.Words för .NET installerat. Om inte, kan du [ladda ner den senaste versionen här](https://releases.aspose.com/words/net/).
2. En .NET-utvecklingsmiljö: Du behöver en fungerande .NET-utvecklingsmiljö, till exempel Visual Studio.
3. Grundläggande förståelse för C#: Bekantskap med programmeringsspråket C# hjälper dig att enkelt följa med.
4. Ett Word-dokument: Ha ett Word-dokument redo som du kan konvertera till en PDF.

## Importera namnrymder

Först måste du importera de nödvändiga namnrymderna. Det är här du inkluderar Aspose.Words-biblioteket för att interagera med ditt dokument. Så här konfigurerar du det:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Definiera dokumentsökvägen

För att börja måste du ange sökvägen till ditt Word-dokument. Det här är filen du vill konvertera till en PDF med dispositionsalternativ. 

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

I kodavsnittet ovan, ersätt `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentkatalog. Detta anger var programmet hittar Word-dokumentet.

## Steg 2: Konfigurera PDF-sparalternativ

Nästa steg är att konfigurera alternativen för att spara PDF-filen. Detta inkluderar att ställa in hur konturer ska hanteras i PDF-utdata. Du kommer att använda `PdfSaveOptions` klass för att göra detta.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
```

Nu ska vi ställa in konturalternativen. 

### Ange rubriker, dispositionsnivåer

De `HeadingsOutlineLevels` Egenskapen definierar hur många rubriknivåer som ska inkluderas i PDF-dispositionen. Om du till exempel ställer in den på 3, kommer upp till tre rubriknivåer att inkluderas i PDF-dispositionen.

```csharp
saveOptions.OutlineOptions.HeadingsOutlineLevels = 3;
```

### Ställ in utökade dispositionsnivåer

De `ExpandedOutlineLevels` Egenskapen styr hur många nivåer av dispositionen som standard ska expanderas när PDF-filen öppnas. Om du ställer in detta på 1 expanderas rubrikerna på den översta nivån, vilket ger en tydlig bild av huvudavsnitten.

```csharp
saveOptions.OutlineOptions.ExpandedOutlineLevels = 1;
```

## Steg 3: Spara dokumentet som PDF

Med alternativen konfigurerade är du redo att spara dokumentet som en PDF. Använd `Save` metod för `Document` klass och skicka in filsökvägen och spara-alternativen.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SetOutlineOptions.pdf", saveOptions);
```

Den här kodraden sparar ditt Word-dokument som en PDF och tillämpar de dispositionsalternativ du konfigurerade. 

## Slutsats

Att ange dispositionsalternativ i ett PDF-dokument kan avsevärt förbättra dess navigerbarhet, vilket gör det enklare för användare att hitta och komma åt de avsnitt de behöver. Med Aspose.Words för .NET kan du enkelt konfigurera dessa inställningar så att de passar dina behov och säkerställa att dina PDF-dokument är så användarvänliga som möjligt.

## Vanliga frågor

### Vad är syftet med att ange dispositionsalternativ i en PDF?

Att ange dispositionsalternativ hjälper användare att navigera i stora PDF-dokument enklare genom att tillhandahålla en strukturerad, klickbar innehållsförteckning.

### Kan jag ange olika rubriknivåer för olika avsnitt i mitt dokument?

Nej, dispositionsinställningarna gäller globalt för hela dokumentet. Du kan dock strukturera dokumentet med lämpliga rubriknivåer för att uppnå en liknande effekt.

### Hur kan jag förhandsgranska ändringarna innan jag sparar PDF-filen?

Du kan använda PDF-läsare som stöder dispositionsnavigering för att kontrollera hur dispositionen ser ut. Vissa program erbjuder en förhandsgranskningsfunktion för detta.

### Är det möjligt att ta bort konturen efter att man har sparat PDF-filen?

Ja, du kan ta bort konturer med PDF-redigeringsprogram, men detta är inte direkt möjligt med Aspose.Words när PDF-filen har skapats.

### Vilka andra PDF-sparalternativ kan jag konfigurera med Aspose.Words?

Aspose.Words erbjuder olika alternativ, till exempel att ställa in PDF-efterlevnadsnivå, bädda in teckensnitt och justera bildkvaliteten.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}