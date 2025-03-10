---
title: Generering av innehållsförteckning
linktitle: Generering av innehållsförteckning
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du skapar dynamisk innehållsförteckning med Aspose.Words för Java. Master TOC-generering med steg-för-steg-vägledning och källkodsexempel.
weight: 14
url: /sv/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generering av innehållsförteckning

## Introduktion

Har du någonsin kämpat med att skapa en dynamisk och professionellt utseende innehållsförteckning (TOC) i dina Word-dokument? Leta inte längre! Med Aspose.Words för Java kan du automatisera hela processen, spara tid och säkerställa noggrannhet. Oavsett om du bygger en omfattande rapport eller en akademisk uppsats, kommer den här handledningen att leda dig genom att generera en innehållsförteckning programmatiskt med Java. Redo att dyka i? Låt oss komma igång!

## Förutsättningar

Innan vi börjar koda, se till att du har följande:

1.  Java Development Kit (JDK): Installerat på ditt system. Du kan ladda ner den från[Oracles hemsida](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Aspose.Words for Java Library: Ladda ner den senaste versionen från[släpp sida](https://releases.aspose.com/words/java/).
3. Integrated Development Environment (IDE): Som IntelliJ IDEA, Eclipse eller NetBeans.
4.  Aspose Temporary License: För att undvika utvärderingsbegränsningar, skaffa en[tillfällig licens](https://purchase.aspose.com/temporary-license/).

## Importera paket

För att använda Aspose.Words för Java effektivt, se till att du importerar de obligatoriska klasserna. Här är importen:

```java
import com.aspose.words.*;
```

Följ dessa steg för att skapa en dynamisk innehållsförteckning i ditt Word-dokument.

## Steg 1: Initiera Document and DocumentBuilder

 Det första steget är att skapa ett nytt dokument och använda`DocumentBuilder` klass för att manipulera det.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Representerar Word-dokumentet.
- `DocumentBuilder`: En hjälpklass som möjliggör enkel manipulering av dokumentet.

## Steg 2: Infoga innehållsförteckningen

Låt oss nu infoga innehållsförteckningen i början av dokumentet.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Infogar ett TOC-fält. Parametrarna specificerar:
  - `\o "1-3"`: Inkludera rubriker för nivå 1 till 3.
  - `\h`: Gör inlägg hyperlänkar.
  - `\z`: Dämpa sidnummer för webbdokument.
  - `\u`: Bevara stilar för hyperlänkar.
- `insertBreak`: Lägger till en sidbrytning efter innehållsförteckningen.

## Steg 3: Lägg till rubriker för att fylla i innehållsförteckningen

FÖR att fylla i innehållsförteckningen måste du lägga till stycken med rubrikstilar.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : Ställer in styckeformatet till en specifik rubriknivå (t.ex.`HEADING_1`, `HEADING_2`).
- `writeln`: Lägger till text i dokumentet med den angivna stilen.

## Steg 4: Lägg till kapslade rubriker

Inkludera kapslade rubriker för att visa innehållsförteckningsnivåer.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Lägg till rubriker på djupare nivåer för att visa hierarki i innehållsförteckningen.

## Steg 5: Uppdatera innehållsförteckningsfält

TOC-fältet måste uppdateras för att visa de senaste rubrikerna.


```java
doc.updateFields();
```

- `updateFields`: Uppdaterar alla fält i dokumentet och säkerställer att innehållsförteckningen återspeglar de tillagda rubrikerna.

## Steg 6: Spara dokumentet

Slutligen sparar du dokumentet i önskat format.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Exporterar dokumentet till en`.docx` fil. Du kan ange andra format som t.ex`.pdf` eller`.txt` om det behövs.

## Slutsats

Grattis! Du har framgångsrikt skapat en dynamisk innehållsförteckning i ett Word-dokument med Aspose.Words för Java. Med bara några rader kod har du automatiserat en uppgift som annars kan ta timmar. Så, vad händer härnäst? Prova att experimentera med olika rubrikstilar och format för att skräddarsy din innehållsförteckning efter specifika behov.

## FAQ's

### Kan jag anpassa TOC-formatet ytterligare?
Absolut! Du kan justera TOC-parametrar som att inkludera sidnummer, justera text eller använda anpassade rubrikstilar.

### Är en licens obligatorisk för Aspose.Words för Java?
 Ja, en licens krävs för full funktionalitet. Du kan börja med en[tillfällig licens](https://purchase.aspose.com/temporary-license/).

### Kan jag skapa en innehållsförteckning för ett befintligt dokument?
 Ja! Ladda dokumentet i en`Document` objekt och följ samma steg för att infoga och uppdatera innehållsförteckningen.

### Fungerar detta för PDF-export?
 Ja, innehållsförteckningen visas i PDF-filen om du sparar dokumentet i`.pdf` formatera.

### Var kan jag hitta mer dokumentation?
 Kolla in[Aspose.Words för Java-dokumentation](https://reference.aspose.com/words/java/) för fler exempel och detaljer.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
