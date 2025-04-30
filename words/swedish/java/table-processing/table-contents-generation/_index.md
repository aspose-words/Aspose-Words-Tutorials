---
"description": "Lär dig hur du skapar dynamiska innehållsförteckningar med Aspose.Words för Java. Bemästra innehållsförteckningsgenerering med steg-för-steg-vägledning och exempel på källkod."
"linktitle": "Generering av innehållsförteckning"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Generering av innehållsförteckning"
"url": "/sv/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generering av innehållsförteckning

## Introduktion

Har du någonsin kämpat med att skapa en dynamisk och professionell innehållsförteckning (TOC) i dina Word-dokument? Leta inte längre! Med Aspose.Words för Java kan du automatisera hela processen, vilket sparar tid och säkerställer noggrannhet. Oavsett om du skapar en omfattande rapport eller en akademisk uppsats, kommer den här handledningen att guida dig genom att generera en innehållsförteckning programmatiskt med Java. Redo att dyka in? Nu sätter vi igång!

## Förkunskapskrav

Innan vi börjar koda, se till att du har följande:

1. Java Development Kit (JDK): Installerat på ditt system. Du kan ladda ner det från [Oracles webbplats](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words för Java-biblioteket: Ladda ner den senaste versionen från [släppsida](https://releases.aspose.com/words/java/).
3. Integrerad utvecklingsmiljö (IDE): Såsom IntelliJ IDEA, Eclipse eller NetBeans.
4. Aspose tillfällig licens: För att undvika utvärderingsbegränsningar, skaffa en [tillfällig licens](https://purchase.aspose.com/temporary-license/).

## Importera paket

För att använda Aspose.Words för Java effektivt, se till att du importerar de obligatoriska klasser. Här är importerna:

```java
import com.aspose.words.*;
```

Följ dessa steg för att generera en dynamisk innehållsförteckning i ditt Word-dokument.

## Steg 1: Initiera dokumentet och DocumentBuilder

Det första steget är att skapa ett nytt dokument och använda `DocumentBuilder` klass för att manipulera den.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`Representerar Word-dokumentet.
- `DocumentBuilder`En hjälpklass som möjliggör enkel manipulation av dokumentet.

## Steg 2: Infoga innehållsförteckningen

Nu infogar vi innehållsförteckningen i början av dokumentet.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`Infogar ett innehållsförteckningsfält. Parametrarna anger:
  - `\o "1-3"`Inkludera rubriker från nivå 1 till 3.
  - `\h`Skapa poster som hyperlänkar.
  - `\z`: Undertryck sidnummer för webbdokument.
  - `\u`Bevara stilar för hyperlänkar.
- `insertBreak`Lägger till en sidbrytning efter innehållsförteckningen.

## Steg 3: Lägg till rubriker för att fylla i innehållsförteckningen

FÖR att fylla i innehållsförteckningen måste du lägga till stycken med rubrikformat.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`: Ställer in styckeformatet till en specifik rubriknivå (t.ex. `HEADING_1`, `HEADING_2`).
- `writeln`Lägger till text i dokumentet med den angivna stilen.

## Steg 4: Lägg till kapslade rubriker

För att demonstrera innehållsförteckningsnivåer, inkludera kapslade rubriker.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Lägg till rubriker på djupare nivåer för att visa hierarkin i innehållsförteckningen.

## Steg 5: Uppdatera innehållsförteckningsfält

Innehållsförteckningsfältet måste uppdateras för att visa de senaste rubrikerna.


```java
doc.updateFields();
```

- `updateFields`Uppdaterar alla fält i dokumentet och säkerställer att innehållsförteckningen återspeglar de tillagda rubrikerna.

## Steg 6: Spara dokumentet

Slutligen, spara dokumentet i önskat format.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`Exporterar dokumentet till en `.docx` fil. Du kan ange andra format som t.ex. `.pdf` eller `.txt` om det behövs.

## Slutsats

Grattis! Du har skapat en dynamisk innehållsförteckning i ett Word-dokument med hjälp av Aspose.Words för Java. Med bara några få rader kod har du automatiserat en uppgift som annars skulle kunna ta timmar. Så, vad händer nu? Försök att experimentera med olika rubrikstilar och format för att skräddarsy din innehållsförteckning efter specifika behov.

## Vanliga frågor

### Kan jag anpassa innehållsförteckningsformatet ytterligare?
Absolut! Du kan justera innehållsförteckningsparametrar, som att inkludera sidnummer, justera text eller använda anpassade rubrikformat.

### Är en licens obligatorisk för Aspose.Words för Java?
Ja, en licens krävs för full funktionalitet. Du kan börja med en [tillfällig licens](https://purchase.aspose.com/temporary-license/).

### Kan jag generera en innehållsförteckning för ett befintligt dokument?
Ja! Ladda dokumentet till en `Document` objektet och följ samma steg för att infoga och uppdatera innehållsförteckningen.

### Fungerar detta för PDF-export?
Ja, innehållsförteckningen visas i PDF-filen om du sparar dokumentet i `.pdf` formatera.

### Var kan jag hitta mer dokumentation?
Kolla in [Aspose.Words för Java-dokumentation](https://reference.aspose.com/words/java/) för fler exempel och detaljer.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}