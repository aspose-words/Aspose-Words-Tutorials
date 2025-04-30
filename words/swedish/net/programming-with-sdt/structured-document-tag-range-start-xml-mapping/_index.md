---
"description": "Lär dig hur du dynamiskt binder XML-data till strukturerade dokumenttaggar i Word med Aspose.Words för .NET. Följ vår steg-för-steg-guide."
"linktitle": "Taggintervall för strukturerat dokument Start XML-mappning"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Taggintervall för strukturerat dokument Start XML-mappning"
"url": "/sv/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Taggintervall för strukturerat dokument Start XML-mappning

## Introduktion

Har du någonsin velat infoga XML-data dynamiskt i ett Word-dokument? Då har du tur! Aspose.Words för .NET gör den här uppgiften till en barnlek. I den här handledningen fördjupar vi oss i XML-mappning av strukturerade dokumenttaggar för startintervall. Den här funktionen låter dig binda anpassade XML-delar till innehållskontroller, vilket säkerställer att ditt dokumentinnehåll uppdateras sömlöst med dina XML-data. Redo att omvandla dina dokument till dynamiska mästerverk.

## Förkunskapskrav

Innan vi går in i kodningsdelen, låt oss se till att du har allt du behöver:

1. Aspose.Words för .NET-biblioteket: Se till att du har den senaste versionen. Du kan ladda ner den [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller annan IDE som stöder C#.
3. Grundläggande kunskaper i C#: Bekantskap med C#-programmering är ett krav.
4. Word-dokument: Ett exempel på ett Word-dokument att arbeta med.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna. Detta säkerställer att vi har tillgång till alla nödvändiga klasser och metoder i Aspose.Words för .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Steg 1: Konfigurera din dokumentkatalog

Varje projekt behöver en grund, eller hur? Här konfigurerar vi sökvägen till din dokumentkatalog.

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda Word-dokumentet

Sedan laddar vi Word-dokumentet. Det är i det här dokumentet vi ska infoga våra XML-data.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Steg 3: Lägg till anpassad XML-del

Vi behöver skapa en XML-del som innehåller de data vi vill infoga och lägga till den i dokumentets CustomXmlPart-samling. Denna anpassade XML-del kommer att fungera som datakälla för våra strukturerade dokumenttaggar.

### Skapa en XML-del

Generera först ett unikt ID för XML-delen och definiera dess innehåll.

```csharp
// Konstruera en XML-del som innehåller data och lägg till den i dokumentets CustomXmlPart-samling.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Verifiera XML-delens innehåll

För att säkerställa att XML-delen läggs till korrekt skriver vi ut dess innehåll.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Steg 4: Skapa en strukturerad dokumenttagg

En Structured Document Tag (SDT) är en innehållskontroll som kan binda till en XML-del. Här skapar vi en SDT som visar innehållet i vår anpassade XML-del.

Först, leta reda på SDT-intervallets början i dokumentet.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Steg 5: Ställ in XML-mappning för SDT:n

Nu är det dags att binda vår XML-del till SDT:n. Genom att ställa in en XML-mappning anger vi vilken del av XML-datan som ska visas i SDT:n.

XPath pekar på det specifika elementet i XML-delen som vi vill visa. Här pekar vi på det andra `<text>` elementet inom `<root>` element.

```csharp
// Ställ in en mappning för vår StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Steg 6: Spara dokumentet

Spara slutligen dokumentet för att se ändringarna i praktiken. SDT:n i Word-dokumentet visar nu det angivna XML-innehållet.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Slutsats

Och där har du det! Du har framgångsrikt mappat en XML-del till en strukturerad dokumenttagg i ett Word-dokument med hjälp av Aspose.Words för .NET. Den här kraftfulla funktionen gör att du enkelt kan skapa dynamiska och datadrivna dokument. Oavsett om du genererar rapporter, fakturor eller någon annan dokumenttyp kan XML-mappning avsevärt effektivisera ditt arbetsflöde.

## Vanliga frågor

### Vad är en tagg för en strukturerad dokument i Word?
Strukturerade dokumenttaggar, även kända som innehållskontroller, är behållare för specifika typer av innehåll i Word-dokument. De kan användas för att binda data, begränsa redigering eller vägleda användare i dokumentskapandet.

### Hur kan jag uppdatera XML-delens innehåll dynamiskt?
Du kan uppdatera XML-delens innehåll genom att ändra `xmlPartContent` strängen innan den läggs till i dokumentet. Uppdatera helt enkelt strängen med den nya informationen och lägg till den i `CustomXmlParts` samling.

### Kan jag binda flera XML-delar till olika SDT:er i samma dokument?
Ja, du kan binda flera XML-delar till olika SDT:er i samma dokument. Varje SDT kan ha sin egen unika XML-del och XPath-mappning.

### Är det möjligt att mappa komplexa XML-strukturer till SDT:er?
Absolut! Du kan mappa komplexa XML-strukturer till SDT:er genom att använda detaljerade XPath-uttryck som korrekt pekar på de önskade elementen i XML-delen.

### Hur kan jag ta bort en XML-del från ett dokument?
Du kan ta bort en XML-del genom att anropa `Remove` metod på `CustomXmlParts` samling, passerar `xmlPartId` av den XML-del du vill ta bort.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}