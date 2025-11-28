---
date: 2025-11-28
description: Leer hoe u celranden kunt wijzigen en tabellen kunt opmaken met Aspose.Words
  for Java. Deze stapsgewijze gids behandelt het instellen van randen, het toepassen
  van de eerste kolomstijl, het automatisch aanpassen van tabelinhoud en het toepassen
  van tabelstijlen.
language: nl
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Hoe celranden in tabellen te wijzigen – Aspose.Words voor Java
url: /java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe celranden in tabellen te wijzigen – Aspose.Words voor Java

## Inleiding

Als het gaat om documentopmaak, spelen tabellen een cruciale rol, en **weten hoe je celranden wijzigt** is essentieel voor het creëren van duidelijke, professionele lay-outs. Als je ontwikkelt met Java en Aspose.Words, heb je al een krachtig gereedschap tot je beschikking. In deze tutorial lopen we stap voor stap het volledige proces door: tabellen opmaken, celranden wijzigen, de *eerste kolom stijl* toepassen en *auto‑fit tabelinhoud* gebruiken zodat je documenten er gepolijst uitzien.

## Snelle antwoorden
- **Wat is de primaire klasse voor het bouwen van tabellen?** `DocumentBuilder` maakt tabellen en cellen programmatisch aan.  
- **Hoe wijzig ik de lijndikte van één cel?** Gebruik `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Kan ik een vooraf gedefinieerde tabelstijl toepassen?** Ja – roep `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)` aan.  
- **Welke methode past een tabel automatisch aan de inhoud aan?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Heb ik een licentie nodig voor productie?** Een geldige Aspose.Words‑licentie is vereist voor niet‑trial gebruik.

## Wat betekent “hoe celranden te wijzigen” in Aspose.Words?

Celranden wijzigen betekent het aanpassen van de visuele lijnen die cellen scheiden—kleur, breedte en lijntype. Aspose.Words biedt een rijke API waarmee je deze eigenschappen kunt aanpassen op tabel‑, rij‑ of individuele‑celniveau, waardoor je fijne controle hebt over het uiterlijk van je documenten.

## Waarom Aspose.Words voor Java gebruiken voor tabelstyling?

- **Consistente uitstraling op alle platforms** – dezelfde stylingcode werkt op Windows, Linux en macOS.  
- **Geen afhankelijkheid van Microsoft Word** – genereer of wijzig documenten server‑side.  
- **Rijke stijlbibliotheek** – ingebouwde tabelstijlen (bijv. *eerste kolom stijl*) en volledige auto‑fit‑mogelijkheden.  

## Voorvereisten

1. **Java Development Kit (JDK) 8+** – zorg dat `java` in je PATH staat.  
2. **IDE** – IntelliJ IDEA, Eclipse of een andere editor naar keuze.  
3. **Aspose.Words voor Java** – download de nieuwste JAR van de [officiële site](https://releases.aspose.com/words/java/).  
4. **Basiskennis van Java** – je moet vertrouwd zijn met het aanmaken van een Maven/Gradle‑project en het toevoegen van externe JAR‑bestanden.

## Importeren van pakketten

Om met tabellen te werken, heb je de kernklassen van Aspose.Words nodig:

```java
import com.aspose.words.*;
```

Deze enkele import geeft je toegang tot `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` en vele andere hulpprogramma’s.

## Hoe celranden te wijzigen

Hieronder maken we een eenvoudige tabel, wijzigen we de algemene randen en passen we vervolgens individuele cellen aan.

### Stap 1: Een nieuw document laden

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Stap 2: De tabel maken en globale randen instellen

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

### Stap 3: Randen van één cel wijzigen

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
- **Celshading** – Toont hoe je individuele cellen kunt kleuren (rood & groen).  
- **Aangepaste celranden** – De derde cel krijgt een rand van 4 punt aan alle zijden, waardoor hij opvalt.

## Toepassen van tabelstijlen (inclusief eerste kolom stijl)

Tabelstijlen laten je met één aanroep een consistente look toepassen. We laten ook zien hoe je de *eerste kolom stijl* inschakelt en de tabel automatisch aan de inhoud laat aanpassen.

### Stap 4: Een nieuw document maken voor styling

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Stap 5: Een vooraf gedefinieerde stijl toepassen en eerste kolom‑formattering inschakelen

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Stap 6: De tabel vullen met gegevens

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
- **Style identifier** – `MEDIUM_SHADING_1_ACCENT_1` geeft de tabel een nette, schaduwachtige uitstraling.  
- **Eerste kolom stijl** – Het markeren van de eerste kolom verbetert de leesbaarheid, vooral in rapporten.  
- **Rij‑banden** – Afwisselende rij‑kleuren maken grote tabellen makkelijker te bekijken.  
- **Auto‑fit** – Zorgt ervoor dat de tabelbreedte zich aanpast aan de inhoud, zodat tekst niet wordt afgekapt.

## Veelvoorkomende problemen & probleemoplossing

| Probleem | Typische oorzaak | Snelle oplossing |
|----------|-------------------|-------------------|
| Randen verschijnen niet | `clearFormatting()` gebruiken na het instellen van randen | Stel randen **na** het wissen van opmaak in, of pas ze opnieuw toe. |
| Shading wordt genegeerd bij samengevoegde cellen | Shading toegepast vóór het samenvoegen | Pas shading **na** het samenvoegen van de cellen toe. |
| Tabelbreedte overschrijdt paginamarges | Geen auto‑fit toegepast | Roep `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` aan of stel een vaste breedte in. |
| Stijl wordt niet toegepast | Verkeerde `StyleIdentifier`‑waarde | Controleer of de identifier bestaat in de versie van Aspose.Words die je gebruikt. |

## Veelgestelde vragen

**V: Kan ik aangepaste tabelstijlen gebruiken die niet in de standaardopties staan?**  
A: Ja, je kunt programmatically aangepaste stijlen maken en toepassen. Zie de [Aspose.Words‑documentatie](https://reference.aspose.com/words/java/) voor details.

**V: Hoe kan ik voorwaardelijke opmaak op cellen toepassen?**  
A: Gebruik standaard Java‑logica om celwaarden te inspecteren en roep vervolgens de juiste opmaak‑methoden aan (bijv. achtergrondkleur wijzigen als een waarde een drempel overschrijdt).

**V: Is het mogelijk om samengevoegde cellen op dezelfde manier te formatteren als gewone cellen?**  
A: Absoluut. Na het samenvoegen van cellen kun je shading of randen toepassen met dezelfde `CellFormat`‑API’s.

**V: Wat als de tabel dynamisch moet schalen op basis van gebruikersinvoer?**  
A: Pas kolombreedtes aan of roep `autoFit` opnieuw aan nadat je nieuwe gegevens hebt ingevoegd om de lay‑out te herberekenen.

**V: Waar vind ik meer voorbeelden van tabelstyling?**  
A: De officiële [Aspose.Words API‑documentatie](https://reference.aspose.com/words/java/) bevat een uitgebreide verzameling voorbeelden.

## Conclusie

Je beschikt nu over een complete toolbox voor **hoe celranden te wijzigen**, het toepassen van de *eerste kolom stijl* en **auto‑fit tabelinhoud** met Aspose.Words voor Java. Door deze technieken te beheersen kun je documenten produceren die zowel data‑rijk als visueel aantrekkelijk zijn—perfect voor rapporten, facturen en elke andere zakelijke output.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Laatst bijgewerkt:** 2025-11-28  
**Getest met:** Aspose.Words voor Java 24.12 (latest at time of writing)  
**Auteur:** Aspose