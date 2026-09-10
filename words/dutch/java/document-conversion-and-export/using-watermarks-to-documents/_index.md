---
date: 2025-12-18
description: Leer hoe je een watermerk aan documenten kunt toevoegen met Aspose.Words
  voor Java, inclusief voorbeeld van een afbeeldingwatermerk, wijzig de kleur van
  het watermerk, stel de transparantie van het watermerk in en verwijder het watermerk
  uit het document.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Hoe watermerk aan documenten toevoegen met Aspose.Words voor Java
url: /nl/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Watermerk toe te voegen aan Documenten met Aspose.Words voor Java

## Introductie tot het toevoegen van watermerken aan documenten in Aspose.Words voor Java

In deze tutorial leer je **hoe je een watermerk** toevoegt aan Word‑documenten met Aspose.Words voor Java. Watermerken zijn een snelle manier om een bestand te labelen als vertrouwelijk, concept of goedgekeurd, en ze kunnen tekst‑gebaseerd of afbeelding‑gebaseerd zijn. We lopen door het instellen van de bibliotheek, het maken van tekst‑ en afbeelding‑watermerken, het aanpassen van hun uiterlijk (inclusief het wijzigen van de watermerk‑kleur en het instellen van watermerk‑transparantie), en zelfs het verwijderen van een watermerk uit een document wanneer het niet meer nodig is.

## Snelle antwoorden
- **Wat is een watermerk?** Een semi‑transparante overlay (tekst of afbeelding) die achter de hoofdinhoud van het document verschijnt.  
- **Kan ik meerdere watermerken toevoegen?** Ja – maak meerdere `Shape`‑objecten aan en voeg elk toe aan de gewenste secties.  
- **Hoe wijzig ik de kleur van een watermerk?** Pas de `Color`‑eigenschap aan in `TextWatermarkOptions`.  
- **Is er een voorbeeld van een afbeelding‑watermerk?** Zie de sectie “Afbeelding‑watermerken toevoegen” hieronder.  
- **Heb ik een licentie nodig om een watermerk te verwijderen?** Een geldige Aspose.Words‑licentie is vereist voor productiegebruik.

## Aspose.Words voor Java instellen

Voordat we beginnen met het toevoegen van watermerken aan documenten, moeten we Aspose.Words voor Java instellen. Volg deze stappen om te beginnen:

1. Download Aspose.Words voor Java van [hier](https://releases.aspose.com/words/java/).  
2. Voeg de Aspose.Words voor Java‑bibliotheek toe aan je Java‑project.  
3. Importeer de benodigde klassen in je Java‑code.

Nu de bibliotheek is ingesteld, duiken we in de daadwerkelijke creatie van watermerken.

## Tekst‑watermerken toevoegen

Tekst‑watermerken zijn een veelgebruikte keuze wanneer je tekstuele informatie aan je documenten wilt toevoegen. Hier zie je hoe je een tekst‑watermerk kunt toevoegen met Aspose.Words voor Java:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Waarom dit belangrijk is:** Door `setFontFamily`, `setFontSize` en `setColor` aan te passen kun je **de watermerk‑kleur** wijzigen om bij je huisstijl te passen, en `setSemitransparent(true)` stelt je in staat **de watermerk‑transparantie** in te stellen voor een subtiel effect.

## Afbeelding‑watermerken toevoegen

Naast tekst‑watermerken kun je ook afbeelding‑watermerken aan je documenten toevoegen. Hieronder staat een **voorbeeld van een afbeelding‑watermerk** dat laat zien hoe je een PNG‑logo of -stempel kunt insluiten:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Je kunt dit blok herhalen met verschillende afbeeldingen of posities om **meerdere watermerken** aan één bestand toe te voegen.

## Watermerken aanpassen

Je kunt watermerken aanpassen door hun uiterlijk en positie te wijzigen. Voor tekst‑watermerken kun je het lettertype, de grootte, de kleur en de lay-out aanpassen. Voor afbeelding‑watermerken kun je grootte, rotatie en uitlijning wijzigen zoals getoond in de vorige voorbeelden.

## Watermerken verwijderen

Als je de **watermerk‑inhoud** uit een document moet verwijderen, doorloopt de volgende code alle shapes en verwijdert diegene die als watermerken zijn geïdentificeerd:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Veelvoorkomende gebruikssituaties & tips

- **Vertrouwelijke concepten:** Pas een semi‑transparant tekst‑watermerk toe zoals “CONFIDENTIAL”.  
- **Branding:** Gebruik een afbeelding‑watermerk dat je bedrijfslogo bevat.  
- **Sectiespecifieke watermerken:** Loop door `doc.getSections()` en voeg een watermerk alleen toe aan de secties die je kiest.  
- **Prestatie‑tip:** Hergebruik dezelfde `TextWatermarkOptions`‑instantie bij het toepassen van hetzelfde watermerk op veel documenten.

## Veelgestelde vragen

### Hoe kan ik het lettertype van een tekst‑watermerk wijzigen?

Om het lettertype van een tekst‑watermerk te wijzigen, pas je de `setFontFamily`‑eigenschap aan in de `TextWatermarkOptions`. Bijvoorbeeld:

```java
options.setFontFamily("Times New Roman");
```

### Kan ik meerdere watermerken aan één document toevoegen?

Ja, je kunt meerdere watermerken aan een document toevoegen door meerdere `Shape`‑objecten met verschillende instellingen te maken en ze aan het document toe te voegen.

### Is het mogelijk een watermerk te roteren?

Ja, je kunt een watermerk roteren door de `setRotation`‑eigenschap in het `Shape`‑object in te stellen. Positieve waarden roteren het watermerk met de klok mee, en negatieve waarden roteren het tegen de klok in.

### Hoe kan ik een watermerk semi‑transparant maken?

Om een watermerk semi‑transparant te maken, stel je de `setSemitransparent`‑eigenschap in op `true` in de `TextWatermarkOptions`.

### Kan ik watermerken toevoegen aan specifieke secties van een document?

Ja, je kunt watermerken toevoegen aan specifieke secties van een document door door de secties te itereren en het watermerk toe te voegen aan de gewenste secties.

---

**Laatst bijgewerkt:** 2025-12-18  
**Getest met:** Aspose.Words voor Java 24.12  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}