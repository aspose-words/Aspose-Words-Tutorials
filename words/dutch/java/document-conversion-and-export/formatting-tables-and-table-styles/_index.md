---
date: 2026-10-17
description: Leer hoe u de randen in tabelcellen wijzigt met Aspose.Words for Java,
  inclusief het instellen van celrandstijlen, het toepassen van de eerste kolomstijl
  en het automatisch aanpassen van tabelinhoud.
keywords:
- how to change borders
- apply first column style
- Aspose.Words table styling
- Java document processing
lastmod: 2026-10-17
linktitle: Hoe de randen in tabelcellen wijzigen met Aspose.Words for Java
og_description: Hoe de randen in tabelcellen wijzigen met Aspose.Words for Java. Deze
  gids laat zien hoe u de dikte van celranden instelt, de eerste kolomstijl toepast
  en tabellen automatisch aanpast voor professionele documenten.
og_image_alt: Screenshot of a Java table with customized cell borders using Aspose.Words
og_title: Hoe de randen in tabelcellen – Aspose.Words for Java
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
title: Hoe de randen in tabelcellen wijzigen met Aspose.Words for Java
url: /nl/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe randen in tabelcellen wijzigen met Aspose.Words voor Java

## Inleiding

Wanneer je gegevens moet presenteren in een nette, professionele lay-out, is **celranden wijzigen** een van de eerste visuele aanpassingen die je toepast. In Java biedt Aspose.Words een volledig uitgeruste API waarmee je tabellen kunt stylen, individuele celranden kunt aanpassen, de eerste‑kolom‑stijl kunt inschakelen en de inhoud automatisch kunt laten passen zodat de tabel nooit over de pagina heen loopt. Deze tutorial leidt je stap voor stap door het proces, van het maken van een document tot het fijn afstellen van elke rand, en laat zien waarom deze functies belangrijk zijn in rapporten en facturen uit de praktijk.

## Snelle antwoorden
De `DocumentBuilder`‑klasse wordt gebruikt om programmatisch documenten en tabellen te bouwen.  
- **Wat is de primaire klasse voor het bouwen van tabellen?** `DocumentBuilder` maakt tabellen en cellen programmatisch.  
- **Hoe wijzig ik de dikte van de rand van één cel?** Gebruik `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Kan ik een vooraf gedefinieerde tabelstijl toepassen?** Ja – roep `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)` aan.  
- **Welke methode past een tabel automatisch aan de inhoud aan?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Heb ik een licentie nodig voor productie?** Een geldige Aspose.Words‑licentie is vereist voor niet‑trial gebruik.

## Wat betekent “celranden wijzigen” in Aspose.Words?

Celranden wijzigen betekent het aanpassen van de visuele lijnen die cellen scheiden—kleur, breedte en lijntype. Aspose.Words for Java biedt een gedetailleerde API waarmee je deze eigenschappen kunt instellen op tabel‑, rij‑ of individueel‑celniveau, waardoor je nauwkeurige controle hebt over het uiterlijk van je documenten.

## Waarom Aspose.Words voor Java gebruiken voor tabelstyling?

Aspose.Words ondersteunt **35+ invoer‑ en uitvoerformaten** (DOCX, PDF, HTML, ODT, enz.) en kan **500‑pagina‑documenten verwerken in minder dan 3 seconden** op typische serverhardware zonder Microsoft Word te vereisen. De bibliotheek werkt consistent op Windows, Linux en macOS, waardoor je documenten server‑side kunt genereren of aanpassen, ingebouwde tabelstijlen zoals *first column style* kunt toepassen, en tabellen automatisch kunt laten passen met één methode‑aanroep.

## Voorvereisten

1. **Java Development Kit (JDK) 8+** – zorg ervoor dat `java` in je PATH staat.  
2. **IDE** – IntelliJ IDEA, Eclipse of een andere editor naar keuze.  
3. **Aspose.Words for Java** – download de nieuwste JAR van de [official site](https://releases.aspose.com/words/java/).  
4. **Basiskennis van Java** – je moet vertrouwd zijn met het maken van een Maven/Gradle‑project en het toevoegen van externe JAR‑bestanden.

## Importeer pakketten

De `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` en gerelateerde klassen bevinden zich in de `com.aspose.words`‑namespace. Het importeren van dit enkele pakket geeft je toegang tot de volledige toolkit voor tabelstyling. De `DocumentBuilder`‑klasse biedt methoden om een document programmatisch te construeren en te wijzigen.

```java
import com.aspose.words.*;
```

## Hoe celranden wijzigen

Hieronder vind je een beknopte, stapsgewijze gids die een tabel maakt, een globale rand toepast en vervolgens de randen van één cel aanpast.

### Direct antwoord
Een `Document` vertegenwoordigt het Word‑bestand, terwijl `DocumentBuilder` inhoud zoals tabellen creëert. Laad een nieuw `Document`, voeg een `Table` in met `DocumentBuilder`, stel een zwarte rand van 2 punt in voor de hele tabel, en vergroot vervolgens de linker‑, rechter‑, boven‑ en onderrand van de derde cel tot 4 punt. Deze aanpak laat je elke cel accentueren terwijl de rest van de tabel uniform gestyled blijft.

### Stap 1: laad een nieuw document

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Stap 2: maak de tabel en stel globale randen in

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

### Stap 3: wijzig de randen van één cel

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

#### Wat de code doet
- **Globale randen** – `table.setBorders` geeft de hele tabel een zwarte lijn van 2 punt.  
- **Celshading** – Laat zien hoe individuele cellen te kleuren (rood & groen).  
- **Aangepaste celranden** – De derde cel krijgt een rand van 4 punt aan alle zijden, waardoor hij opvalt.

## Tabelstijlen toepassen (inclusief eerste kolom stijl)

Tabelstijlen laten je een consistente uitstraling met één aanroep toepassen. We schakelen ook de *first column style* in en passen auto‑fit toe zodat de tabel zich aan de inhoud aanpast.

### Direct antwoord
`StyleIdentifier` somt ingebouwde tabelstijlen op, en `AutoFitBehavior` bepaalt hoe een tabel zich aanpast aan de inhoud. Maak een nieuw `Document`, bouw een `Table`, stel `StyleIdentifier` in op `MEDIUM_SHADING_1_ACCENT_1`, schakel `FirstColumn` en `RowBands` in, en roep `autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` aan zodat de kolommen automatisch krimpen of groeien om de ingevoerde gegevens te passen.

### Stap 4: maak een nieuw document voor styling

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Stap 5: pas een vooraf gedefinieerde stijl toe en schakel eerste‑kolom opmaak in

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Stap 6: vul de tabel met gegevens

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

#### Waarom dit belangrijk is
- **Stijl‑identifier** – `MEDIUM_SHADING_1_ACCENT_1` geeft de tabel een nette, schaduwachtige uitstraling.  
- **Eerste kolom stijl** – Het markeren van de eerste kolom verbetert de leesbaarheid, vooral in rapporten.  
- **Rij‑banden** – Afwisselende rij‑kleuren maken grote tabellen gemakkelijker leesbaar.  
- **Auto‑fit** – Zorgt ervoor dat de tabelbreedte zich aanpast aan de inhoud, waardoor afgekapt tekst wordt voorkomen.

## Veelvoorkomende problemen & foutopsporing

| Probleem | Typische oorzaak | Snelle oplossing |
|----------|------------------|------------------|
| Randen verschijnen niet | `clearFormatting()` gebruiken na het instellen van randen | Stel randen **na** het wissen van opmaak in, of pas ze opnieuw toe. |
| Shading wordt genegeerd bij samengevoegde cellen | Shading toegepast vóór het samenvoegen | Pas shading **na** het samenvoegen van de cellen toe. |
| Tabelbreedte overschrijdt paginamarges | Geen auto‑fit toegepast | Roep `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` aan of stel een vaste breedte in. |
| Stijl niet toegepast | Verkeerde `StyleIdentifier`‑waarde | Controleer of de identifier bestaat in de versie van Aspose.Words die je gebruikt. |

## Veelgestelde vragen

**Q: Kan ik aangepaste tabelstijlen gebruiken die niet in de standaardopties zitten?**  
A: Ja, je kunt aangepaste stijlen programmatically maken en toepassen. Zie de [Aspose.Words‑documentatie](https://reference.aspose.com/words/java/) voor details.

**Q: Hoe kan ik voorwaardelijke opmaak op cellen toepassen?**  
A: Gebruik standaard Java‑logica om celwaarden te inspecteren, en roep vervolgens de juiste opmaak‑methoden aan (bijv. achtergrondkleur wijzigen als een waarde een drempel overschrijdt).

**Q: Is het mogelijk om samengevoegde cellen op dezelfde manier op te maken als gewone cellen?**  
A: Absoluut. Na het samenvoegen van cellen kun je shading of randen toepassen met dezelfde `CellFormat`‑API’s.

**Q: Wat als ik de tabel dynamisch moet laten schalen op basis van gebruikersinvoer?**  
A: Pas kolombreedtes aan of roep `autoFit` opnieuw aan na het invoegen van nieuwe gegevens om de lay-out opnieuw te berekenen.

**Q: Waar kan ik meer voorbeelden van tabelstyling vinden?**  
A: De officiële [Aspose.Words API‑documentatie](https://reference.aspose.com/words/java/) bevat een uitgebreide set voorbeelden.

## Conclusie

Je beschikt nu over een volledige toolbox voor **celranden wijzigen** in tabelcellen, het toepassen van de *first column style* en **auto‑fit van tabelinhoud** met Aspose.Words for Java. Door deze technieken te beheersen kun je documenten produceren die zowel data‑rijk als visueel gepolijst zijn—ideaal voor rapporten, facturen en elke zakelijke output.

---

**Laatste update:** 2026-10-17  
**Getest met:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Auteur:** Aspose

## Gerelateerde tutorials

- [Aspose.Words Java Formatting & Styles Tutorials - Verbeter je documenten](/words/java/formatting-styles/)
- [Geavanceerde documentranden met Aspose.Words for Java: Een uitgebreide gids](/words/java/headers-footers-page-setup/advanced-document-borders-aspose-words-java/)
- [Een watermerk toevoegen aan een document met Aspose.Words for Java](/words/java/document-conversion-and-export/using-watermarks-to-documents/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}