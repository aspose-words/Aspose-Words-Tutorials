---
title: Structured Document Tag Range Starta XML-mappning
linktitle: Structured Document Tag Range Starta XML-mappning
second_title: Aspose.Words Document Processing API
description: Lär dig hur du dynamiskt binder XML-data till strukturerade dokumenttaggar i Word med Aspose.Words för .NET. Följ vår steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Structured Document Tag Range Starta XML-mappning

## Introduktion

Har du någonsin velat infoga XML-data dynamiskt i ett Word-dokument? Nåväl, du har tur! Aspose.Words för .NET gör denna uppgift till en lek. I den här handledningen dyker vi djupt in i strukturerat dokumenttaggintervall för start av XML-mappning. Den här funktionen låter dig binda anpassade XML-delar till innehållskontroller, vilket säkerställer att ditt dokumentinnehåll uppdateras sömlöst med dina XML-data. Redo att förvandla dina dokument till dynamiska mästerverk.

## Förutsättningar

Innan vi går in i kodningsdelen, låt oss se till att du har allt du behöver:

1.  Aspose.Words för .NET Library: Se till att du har den senaste versionen. Du kan ladda ner den[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller någon annan IDE som stöder C#.
3. Grundläggande kunskaper i C#: Bekantskap med C#-programmering är ett måste.
4. Word-dokument: Ett exempel på Word-dokument att arbeta med.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Detta kommer att säkerställa att vi har tillgång till alla nödvändiga klasser och metoder i Aspose.Words för .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Steg 1: Konfigurera din dokumentkatalog

Varje projekt behöver en grund, eller hur? Här ställer vi in sökvägen till din dokumentkatalog.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda Word-dokumentet

Därefter laddar vi Word-dokumentet. Det här är dokumentet där vi kommer att infoga vår XML-data.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Steg 3: Lägg till anpassad XML-del

Vi måste konstruera en XML-del som innehåller den data vi vill infoga och lägga till den i dokumentets CustomXmlPart-samling. Denna anpassade XML-del kommer att fungera som datakälla för våra strukturerade dokumenttaggar.

### Skapa en XML-del

Skapa först ett unikt ID för XML-delen och definiera dess innehåll.

```csharp
// Konstruera en XML-del som innehåller data och lägg till den i dokumentets CustomXmlPart-samling.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Verifiera XML-delens innehåll

För att säkerställa att XML-delen är korrekt tillagd skriver vi ut dess innehåll.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Steg 4: Skapa en strukturerad dokumenttagg

En SDT (Structured Document Tag) är en innehållskontroll som kan binda till en XML-del. Här skapar vi en SDT som visar innehållet i vår anpassade XML-del.

Leta först upp SDT-intervallets start i dokumentet.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Steg 5: Ställ in XML-mappning för SDT

Nu är det dags att binda vår XML-del till SDT. Genom att ställa in en XML-mappning anger vi vilken del av XML-datan som ska visas i SDT.

 XPath pekar på det specifika elementet i XML-delen som vi vill visa. Här pekar vi på det andra`<text>` element inom`<root>` element.

```csharp
// Ställ in en mappning för vår StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Steg 6: Spara dokumentet

Slutligen, spara dokumentet för att se ändringarna i handling. SDT i Word-dokumentet kommer nu att visa det angivna XML-innehållet.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Slutsats

Och där har du det! Du har framgångsrikt mappat en XML-del till en strukturerad dokumenttagg i ett Word-dokument med Aspose.Words för .NET. Denna kraftfulla funktion gör att du kan skapa dynamiska och datadrivna dokument utan ansträngning. Oavsett om du genererar rapporter, fakturor eller någon annan dokumenttyp kan XML-mappning avsevärt effektivisera ditt arbetsflöde.

## FAQ's

### Vad är en strukturerad dokumenttagg i Word?
Strukturerade dokumenttaggar, även kända som innehållskontroller, är behållare för specifika typer av innehåll i Word-dokument. De kan användas för att binda data, begränsa redigering eller vägleda användare i dokumentskapandet.

### Hur kan jag uppdatera XML-delens innehåll dynamiskt?
 Du kan uppdatera XML-delens innehåll genom att ändra`xmlPartContent` sträng innan du lägger till den i dokumentet. Uppdatera helt enkelt strängen med den nya datan och lägg till den i`CustomXmlParts` samling.

### Kan jag binda flera XML-delar till olika SDT i samma dokument?
Ja, du kan binda flera XML-delar till olika SDT i samma dokument. Varje SDT kan ha sin egen unika XML-del och XPath-mappning.

### Är det möjligt att mappa komplexa XML-strukturer till SDT?
Absolut! Du kan mappa komplexa XML-strukturer till SDT:er genom att använda detaljerade XPath-uttryck som exakt pekar på de önskade elementen i XML-delen.

### Hur kan jag ta bort en XML-del från ett dokument?
 Du kan ta bort en XML-del genom att anropa`Remove` metod på`CustomXmlParts` samling, passerar`xmlPartId` av XML-delen du vill ta bort.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
