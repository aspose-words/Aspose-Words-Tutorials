---
"description": "Lär dig hur du läser ActiveX-kontrollegenskaper från Word-filer med Aspose.Words för .NET i en steg-för-steg-guide. Förbättra dina kunskaper inom dokumentautomation."
"linktitle": "Läs Active XControl-egenskaper från Word-fil"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Läs Active XControl-egenskaper från Word-fil"
"url": "/sv/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Läs Active XControl-egenskaper från Word-fil

## Introduktion

dagens digitala tidsålder är automatisering nyckeln till att öka produktiviteten. Om du arbetar med Word-dokument som innehåller ActiveX-kontroller kan du behöva läsa deras egenskaper för olika ändamål. ActiveX-kontroller, som kryssrutor och knappar, kan innehålla viktig data. Med Aspose.Words för .NET kan du effektivt extrahera och manipulera dessa data programmatiskt.

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET-biblioteket: Du kan ladda ner det från [här](https://releases.aspose.com/words/net/).
2. Visual Studio eller valfri C# IDE: För att skriva och exekvera din kod.
3. Ett Word-dokument med ActiveX-kontroller: Till exempel "ActiveX controls.docx".
4. Grundläggande kunskaper i C#: Bekantskap med C#-programmering är nödvändig för att följa med.

## Importera namnrymder

Låt oss först importera de namnrymder som behövs för att fungera med Aspose.Words för .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Steg 1: Ladda Word-dokumentet

För att börja måste du ladda Word-dokumentet som innehåller ActiveX-kontrollerna.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Steg 2: Initiera en sträng för att hålla egenskaper

Initiera sedan en tom sträng för att lagra egenskaperna för ActiveX-kontrollerna.

```csharp
string properties = "";
```

## Steg 3: Iterera genom former i dokumentet

Vi måste iterera igenom alla former i dokumentet för att hitta ActiveX-kontrollerna.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Bearbeta ActiveX-kontrollen
    }
}
```

## Steg 4: Extrahera egenskaper från ActiveX-kontroller

Kontrollera i loopen om kontrollen är en Forms2OleControl. Om den är det, omforma den och extrahera egenskaperna.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Steg 5: Räkna totalt antal ActiveX-kontroller

Efter att ha itererat igenom alla former, räkna det totala antalet ActiveX-kontroller som hittats.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Steg 6: Visa egenskaperna

Slutligen, skriv ut de extraherade egenskaperna till konsolen.

```csharp
Console.WriteLine("\n" + properties);
```

## Slutsats

Och där har du det! Du har framgångsrikt lärt dig hur man läser ActiveX-kontrollegenskaper från ett Word-dokument med hjälp av Aspose.Words för .NET. Den här handledningen behandlade hur man laddar ett dokument, itererar genom former och extraherar egenskaper från ActiveX-kontroller. Genom att följa dessa steg kan du automatisera extraheringen av viktig data från dina Word-dokument och därmed förbättra effektiviteten i ditt arbetsflöde.

## Vanliga frågor

### Vad är ActiveX-kontroller i Word-dokument?
ActiveX-kontroller är interaktiva objekt som är inbäddade i Word-dokument, till exempel kryssrutor, knappar och textfält, som används för att skapa formulär och automatisera uppgifter.

### Kan jag ändra egenskaperna för ActiveX-kontroller med hjälp av Aspose.Words för .NET?
Ja, Aspose.Words för .NET låter dig ändra egenskaperna för ActiveX-kontroller programmatiskt.

### Är Aspose.Words för .NET gratis att använda?
Aspose.Words för .NET erbjuder en gratis provperiod, men du måste köpa en licens för fortsatt användning. Du kan få en gratis provperiod. [här](https://releases.aspose.com/).

### Kan jag använda Aspose.Words för .NET med andra .NET-språk förutom C#?
Ja, Aspose.Words för .NET kan användas med alla .NET-språk, inklusive VB.NET och F#.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
Du kan hitta detaljerad dokumentation [här](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}