---
title: Få tillgång till reviderad version
linktitle: Få tillgång till reviderad version
second_title: Aspose.Words Document Processing API
description: Lär dig hur du kommer åt och visar den reviderade versionen av ett dokument med Aspose.Words för .NET. Följ vår steg-för-steg-guide för sömlös dokumenthantering.
weight: 10
url: /sv/net/working-with-revisions/access-revised-version/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Få tillgång till reviderad version

## Introduktion

Har du någonsin behövt få åtkomst till den reviderade versionen av ett dokument programmatiskt? Oavsett om du arbetar med samarbetsprojekt eller helt enkelt behöver hantera dokumentrevisioner, är Aspose.Words för .NET ditt bästa verktyg. Den här handledningen går igenom hela processen, från att ställa in din miljö till att komma åt och visa versioner i ett Word-dokument. Så, låt oss dyka direkt in!

## Förutsättningar

Innan vi börjar behöver du några saker:

1.  Aspose.Words för .NET Library: Du kan ladda ner det[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller någon annan IDE som stöder .NET.
3. Grundläggande kunskaper om C#: Detta hjälper dig att följa med i kodningsdelen.

Se till att du har löst dessa förutsättningar innan du fortsätter till nästa steg.

## Importera namnområden

Först och främst måste du importera de nödvändiga namnrymden. Detta är ett avgörande steg för att säkerställa att din kod känner igen Aspose.Words for .NET-biblioteket.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Låt oss dela upp processen i enkla steg som är lätta att följa.

## Steg 1: Konfigurera dokumentsökvägen

Innan du kan arbeta med dokumentet måste du ange sökvägen där ditt dokument finns. Detta är viktigt för att koden ska hitta och manipulera filen.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda dokumentet

 Därefter ska du ladda dokumentet i din ansökan. Detta steg innebär att skapa en ny`Document` objekt och initialisera det med sökvägen till ditt dokument.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

## Steg 3: Uppdatera listetiketter

Om ditt dokument innehåller listor är det viktigt att uppdatera listetiketterna. Detta säkerställer att alla listobjekt är korrekt numrerade och formaterade.

```csharp
doc.UpdateListLabels();
```

## Steg 4: Byt till den reviderade versionen

Låt oss nu byta till den reviderade versionen av dokumentet. Detta steg är avgörande om du vill komma åt och visa versionerna.

```csharp
doc.RevisionsView = RevisionsView.Final;
```

## Steg 5: Iteration genom revisioner

 För att komma åt revisionerna måste du iterera dig igenom`Revisions` insamling av dokumentet. Detta steg innebär att använda en`foreach` loop för att gå igenom varje revision.

```csharp
foreach (Revision revision in doc.Revisions)
{
    // Ytterligare kod kommer hit
}
```

## Steg 6: Kontrollera överordnad nodtyp

 För varje revision, kontrollera om den överordnade noden är av typen`Paragraph`. Detta är viktigt eftersom vi vill komma åt stycket som innehåller revideringen.

```csharp
if (revision.ParentNode.NodeType == NodeType.Paragraph)
{
    // Ytterligare kod kommer hit
}
```

## Steg 7: Få åtkomst till stycket

 När du har bekräftat att den överordnade noden är ett stycke, casta den till en`Paragraph` objekt. Detta steg låter dig arbeta med stycket och dess egenskaper.

```csharp
Paragraph paragraph = (Paragraph)revision.ParentNode;
```

## Steg 8: Kontrollera om stycket är ett listobjekt

Kontrollera sedan om stycket är ett listobjekt. Detta är viktigt eftersom listobjekt har specifika egenskaper som vi behöver komma åt.

```csharp
if (paragraph.IsListItem)
{
    // Ytterligare kod kommer hit
}
```

## Steg 9: Visa listans etikett och nivå

Visa slutligen listetiketten och listnivån för stycket. Det här steget ger användbar information om listobjektet, till exempel dess numrering och indragsnivå.

```csharp
Console.WriteLine(paragraph.ListLabel.LabelString);
Console.WriteLine(paragraph.ListFormat.ListLevel);
```

## Slutsats

Och där har du det! Du har lyckats komma åt den reviderade versionen av ett dokument med Aspose.Words för .NET. Genom att följa dessa steg kan du hantera och visa dokumentrevisioner med lätthet. Oavsett om du har att göra med samarbetsprojekt eller helt enkelt behöver hålla reda på förändringar, har Aspose.Words för .NET dig täckt.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek som låter dig skapa, redigera och manipulera Word-dokument programmatiskt.

### Kan jag komma åt versioner i alla Word-dokument?
Ja, så länge dokumentet innehåller revisioner kan du komma åt dem med Aspose.Words för .NET.

### Behöver jag en licens för att använda Aspose.Words för .NET?
 Ja, du kan få en licens från[här](https://purchase.aspose.com/buy) . De erbjuder också en[gratis provperiod](https://releases.aspose.com/) och a[tillfällig licens](https://purchase.aspose.com/temporary-license/).

### Är Aspose.Words for .NET kompatibelt med alla .NET-versioner?
Aspose.Words för .NET är kompatibel med ett brett utbud av .NET-versioner. Du kan hitta mer information i[dokumentation](https://reference.aspose.com/words/net/).

### Var kan jag få support för Aspose.Words för .NET?
 Du kan få stöd från Aspose-communityt på deras[forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
