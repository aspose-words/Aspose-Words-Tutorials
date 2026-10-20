---
date: 2026-10-17
description: Lär dig hur du ändrar kantlinjer i tabellceller med Aspose.Words for
  Java, inklusive att ställa in cellkantstilar, tillämpa stil för första kolumnen
  och auto‑anpassa tabellinnehåll.
keywords:
- how to change borders
- apply first column style
- Aspose.Words table styling
- Java document processing
lastmod: 2026-10-17
linktitle: Hur du ändrar kantlinjer i tabellceller med Aspose.Words for Java
og_description: Hur du ändrar kantlinjer i tabellceller med Aspose.Words for Java.
  Denna guide visar hur du ställer in cellkanttjocklek, tillämpar stil för första
  kolumnen och auto‑anpassar tabeller för professionella dokument.
og_image_alt: Screenshot of a Java table with customized cell borders using Aspose.Words
og_title: Hur du ändrar kantlinjer i tabellceller – Aspose.Words for Java
schemas:
- author: Aspose
  dateModified: '2026-10-17'
  description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  headline: How to change borders in table cells using Aspose.Words for Java
  type: TechArticle
- description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  name: How to change borders in table cells using Aspose.Words for Java
  steps:
  - name: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
    text: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
    text: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
  - name: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
    text: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
  type: HowTo
- questions:
  - answer: Yes, you can create and apply custom styles programmatically. See the
      [Aspose.Words documentation](https://reference.aspose.com/words/java/) for details.
    question: Can I use custom table styles not included in the default options?
  - answer: Use standard Java logic to inspect cell values, then call the appropriate
      formatting methods (e.g., change background colour if a value exceeds a threshold).
    question: How can I apply conditional formatting to cells?
  - answer: Absolutely. After merging cells, apply shading or borders using the same
      `CellFormat` APIs.
    question: Is it possible to format merged cells the same way as regular cells?
  - answer: Adjust column widths or call `autoFit` again after inserting new data
      to recalculate the layout.
    question: What if I need the table to resize dynamically based on user input?
  - answer: The official [Aspose.Words API documentation](https://reference.aspose.com/words/java/)
      contains a comprehensive set of samples.
    question: Where can I find more examples of table styling?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- Aspose.Words
- Java tables
- document formatting
- border styling
title: Hur du ändrar kantlinjer i tabellceller med Aspose.Words for Java
url: /sv/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man ändrar kantramar i tabellceller med Aspose.Words för Java

## Introduktion

När du behöver presentera data i en ren, professionell layout är **ändring av cellkanter** ett av de första visuella justeringarna du gör. I Java ger Aspose.Words dig ett fullständigt API som låter dig formatera tabeller, justera enskilda cellkanter, aktivera stil för första kolumnen och automatiskt anpassa innehållet så att tabellen aldrig överskrider sidan. Denna handledning guidar dig genom varje steg, från att skapa ett dokument till att finjustera varje kant, och visar varför dessa funktioner är viktiga i verkliga rapporter och fakturor.

## Snabba svar
`DocumentBuilder`‑klassen används för att programatiskt bygga dokument och tabeller.  
- **Vad är den primära klassen för att bygga tabeller?** `DocumentBuilder` skapar tabeller och celler programatiskt.  
- **Hur ändrar jag tjockleken på en enskild cells kant?** Använd `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Kan jag tillämpa en fördefinierad tabellstil?** Ja – anropa `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Vilken metod anpassar automatiskt en tabell till dess innehåll?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Behöver jag en licens för produktion?** En giltig Aspose.Words-licens krävs för icke‑testanvändning.

## Vad innebär “hur man ändrar cellkanter” i Aspose.Words?

Att ändra cellkanter innebär att anpassa de visuella linjerna som separerar cellerna — färg, bredd och linjestil. Aspose.Words för Java erbjuder ett detaljerat API som låter dig ställa in dessa egenskaper på tabell-, rad- eller enskild‑cellnivå, vilket ger dig exakt kontroll över dokumentens utseende.

## Varför använda Aspose.Words för Java för tabellstyling?

Aspose.Words stödjer **35+ in- och utdataformat** (DOCX, PDF, HTML, ODT osv.) och kan bearbeta **500‑sidiga dokument på under 3 sekunder** på vanlig serverhårdvara utan att kräva Microsoft Word. Biblioteket fungerar konsekvent på Windows, Linux och macOS, vilket gör att du kan generera eller modifiera dokument på serversidan, tillämpa inbyggda tabellstilar såsom *första kolumnens stil*, och automatiskt anpassa tabeller till innehållet med ett enda metodanrop.

## Förutsättningar

1. **Java Development Kit (JDK) 8+** – se till att `java` finns i din PATH.  
2. **IDE** – IntelliJ IDEA, Eclipse eller någon annan editor du föredrar.  
3. **Aspose.Words for Java** – ladda ner den senaste JAR-filen från den [officiella webbplatsen](https://releases.aspose.com/words/java/).  
4. **Grundläggande Java‑kunskaper** – du bör vara bekväm med att skapa ett Maven/Gradle‑projekt och lägga till externa JAR‑filer.

## Importera paket

`Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` och relaterade klasser finns i `com.aspose.words`‑namnrymden. Att importera detta enda paket ger dig tillgång till hela verktygssatsen för tabellstyling. `DocumentBuilder`‑klassen erbjuder metoder för att programatiskt konstruera och modifiera ett dokument.

```java
import com.aspose.words.*;
```

## Hur man ändrar cellkanter

Nedan följer en kortfattad steg‑för‑steg‑guide som skapar en tabell, applicerar en global kant och sedan anpassar en enskild cells kanter.

### Direkt svar
Ett `Document` representerar Word‑filen, medan `DocumentBuilder` skapar innehåll såsom tabeller. Ladda ett nytt `Document`, infoga en `Table` med `DocumentBuilder`, sätt en 2‑punkts svart kant för hela tabellen, och öka sedan vänster-, höger-, topp- och bottenkant på den tredje cellen till 4 punkter. Detta tillvägagångssätt låter dig markera vilken cell som helst samtidigt som resten av tabellen behåller en enhetlig stil.

### Steg 1: ladda ett nytt dokument

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Steg 2: skapa tabellen och sätt globala kanter

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Steg 3: ändra kanter på en enskild cell

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Vad koden gör
- **Globala kanter** – `table.setBorders` ger hela tabellen en 2‑punkts svart linje.  
- **Cellskuggning** – Visar hur man färgar enskilda celler (röd & grön).  
- **Anpassade cellkanter** – Den tredje cellen får en 4‑punkts kant på alla sidor, vilket får den att sticka ut.

## Tillämpa tabellstilar (inklusive stil för första kolumnen)

Tabellstilar låter dig applicera ett enhetligt utseende med ett enda anrop. Vi kommer också att aktivera *första kolumnens stil* och automatiskt anpassa tabellen till dess innehåll.

### Direkt svar
`StyleIdentifier` listar inbyggda tabellstilar, och `AutoFitBehavior` styr hur en tabell anpassar sig till sitt innehåll. Skapa ett nytt `Document`, bygg en `Table`, sätt dess `StyleIdentifier` till `MEDIUM_SHADING_1_ACCENT_1`, aktivera `FirstColumn` och `RowBands`, och anropa sedan `autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` så att kolumnerna automatiskt krymper eller expanderar för att passa den infogade datan.

### Steg 4: skapa ett nytt dokument för styling

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Steg 5: tillämpa en fördefinierad stil och aktivera formatering för första kolumnen

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Steg 6: fyll tabellen med data

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Varför detta är viktigt
- **Stilidentifierare** – `MEDIUM_SHADING_1_ACCENT_1` ger tabellen ett rent, skuggat utseende.  
- **Stil för första kolumnen** – Att markera den första kolumnen förbättrar läsbarheten, särskilt i rapporter.  
- **Radband** – Växlande radfärger gör stora tabeller mer ögonvänliga.  
- **Auto‑fit** – Säkerställer att tabellens bredd anpassas till innehållet, vilket förhindrar avklippt text.

## Vanliga problem & felsökning

| Problem | Typisk orsak | Snabb lösning |
|-------|----------------|-----------|
| Kanter visas inte | Använder `clearFormatting()` efter att ha satt kanter | Sätt kanter **efter** att ha rensat formatering, eller återapplicera dem. |
| Skuggning ignoreras på sammanslagna celler | Skuggning applicerad före sammanslagning | Applicera skuggning **efter** att cellerna har slagits ihop. |
| Tabellens bredd överskrider sidmarginalerna | Ingen auto‑fit tillämpad | Anropa `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` eller sätt en fast bredd. |
| Stil tillämpas inte | Fel `StyleIdentifier`‑värde | Verifiera att identifieraren finns i den version av Aspose.Words du använder. |

## Vanliga frågor

**Q: Kan jag använda anpassade tabellstilar som inte ingår i standardalternativen?**  
A: Ja, du kan skapa och tillämpa anpassade stilar programatiskt. Se den [Aspose.Words-dokumentationen](https://reference.aspose.com/words/java/) för detaljer.

**Q: Hur kan jag tillämpa villkorlig formatering på celler?**  
A: Använd standard Java‑logik för att inspektera cellvärden, och anropa sedan lämpliga formateringsmetoder (t.ex. ändra bakgrundsfärg om ett värde överstiger ett tröskelvärde).

**Q: Är det möjligt att formatera sammanslagna celler på samma sätt som vanliga celler?**  
A: Absolut. Efter att ha slagit ihop celler, applicera skuggning eller kanter med samma `CellFormat`‑API:er.

**Q: Vad händer om jag behöver att tabellen ändrar storlek dynamiskt baserat på användarens inmatning?**  
A: Justera kolumnbredder eller anropa `autoFit` igen efter att ha infogat ny data för att omberäkna layouten.

**Q: Var kan jag hitta fler exempel på tabellstyling?**  
A: Den officiella [Aspose.Words API-dokumentationen](https://reference.aspose.com/words/java/) innehåller ett omfattande urval av exempel.

## Slutsats

Du har nu en komplett verktygslåda för **hur man ändrar kanter** i tabellceller, tillämpa *första kolumnens stil*, och **auto‑fit tabellinnehåll** med Aspose.Words för Java. Genom att behärska dessa tekniker kan du skapa dokument som både är datarika och visuellt polerade — idealiska för rapporter, fakturor och alla affärskritiska utskrifter.

---


**Last Updated:** 2026-10-17  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose

## Relaterade handledningar

- [Aspose.Words Java Formaterings‑ & Stilstutorialer – Förbättra dina dokument](/words/java/formatting-styles/)
- [Avancerade dokumentkanter med Aspose.Words för Java: En omfattande guide](/words/java/headers-footers-page-setup/advanced-document-borders-aspose-words-java/)
- [Lägg till ett vattenmärke i ett dokument med Aspose.Words för Java](/words/java/document-conversion-and-export/using-watermarks-to-documents/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}