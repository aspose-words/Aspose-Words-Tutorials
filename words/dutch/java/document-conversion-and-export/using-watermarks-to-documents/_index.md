---
date: 2026-02-19
description: Leer hoe je een document met watermerk maakt met Aspose.Words voor Java
  en een afbeeldingwatermerk toevoegt in Java voor professioneel uitziende documenten.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Document maken met watermerk met Aspose.Words voor Java
url: /nl/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Document maken met watermerk met Aspose.Words voor Java

In deze tutorial **maak je een document met watermerk** met behulp van de Aspose.Words for Java API. Watermerken—of het nu tekst of afbeeldingen zijn—helpen je een bestand te labelen als vertrouwelijk, concept of goedgekeurd, en ze kunnen programmatisch worden toegepast op elk Word‑document. We lopen door het instellen van de bibliotheek, het toevoegen van zowel tekst‑ als afbeelding‑watermerken, het aanpassen van hun uiterlijk, en zelfs het verwijderen ervan wanneer ze niet meer nodig zijn.

## Snelle antwoorden
- **Wat doet een watermerk?** Het legt tekst of een afbeelding over elke pagina om een status of branding weer te geven.  
- **Welke bibliotheek voegt watermerken toe in Java?** Aspose.Words for Java biedt ingebouwde watermerkondersteuning.  
- **Kan ik een afbeelding‑watermerk toevoegen?** Ja—gebruik de `Shape`‑klasse en de `add image watermark java`‑aanpak.  
- **Is het watermerk semi‑transparant?** Je kunt de opacity regelen via `setSemitransparent` voor tekst‑watermerken.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor testen; een commerciële licentie is vereist voor productie.

## Wat is een watermerk en waarom gebruiken?

Een watermerk is een subtiele overlay—tekstueel of grafisch—die aan elke pagina van een document wordt toegevoegd. Het wordt vaak gebruikt om **vertrouwelijkheid**, **conceptstatus** of **branding** aan te geven zonder de onderliggende inhoud te wijzigen. Watermerken programmatisch toevoegen zorgt voor consistentie over grote aantallen bestanden en bespaart tijd vergeleken met handmatige bewerking.

## Aspose.Words for Java instellen

Voordat we watermerken gaan toevoegen, zorg ervoor dat de bibliotheek klaar is in je project:

1. Download Aspose.Words for Java van [hier](https://releases.aspose.com/words/java/).  
2. Voeg de gedownloade JAR (of Maven/Gradle‑dependency) toe aan de classpath van je project.  
3. Importeer de benodigde klassen in je Java‑bronbestand:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Nu de bibliotheek is ingesteld, duiken we in de daadwerkelijke watermerkcode.

## Hoe een tekst‑watermerk toe te voegen

Tekst‑watermerken zijn ideaal om een document te labelen als “CONFIDENTIAL” of “DRAFT”. Het volgende fragment toont een nette manier om **document met watermerk** te **creëren** met `TextWatermarkOptions`.

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

### Het tekst‑watermerk aanpassen
- **Lettertype & grootte** – wijzig `setFontFamily` en `setFontSize`.  
- **Kleur** – gebruik elke `java.awt.Color`.  
- **Lay-out** – kies `HORIZONTAL`, `DIAGONAL`, enz.  
- **Transparantie** – schakel `setSemitransparent(true)` in voor een lichtere uitstraling.

## Hoe een afbeelding‑watermerk toe te voegen (add image watermark java)

Afbeelding‑watermerken zijn perfect voor logo’s of aangepaste graphics. Hieronder staat het **add image watermark java**‑voorbeeld dat een PNG in het midden van elke pagina invoegt.

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

### Tips voor afbeelding‑watermerken
- **Formaat aanpassen** met `setWidth` / `setHeight` zodat het op de pagina past.  
- **Positie** kan gecentreerd zijn of uitgelijnd op een willekeurige marge met `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Transparantie** kan worden toegepast door het alfa‑kanaal van de afbeelding aan te passen vóór het laden.

## Hoe watermerken te verwijderen

Wanneer een document geen watermerk meer nodig heeft, kun je het programmatisch verwijderen. De onderstaande code doorloopt alle shapes en verwijdert degene die “Watermark” in hun naam bevatten.

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

## Veelvoorkomende valkuilen en probleemoplossing

- **Watermerk ontbreekt na opslaan** – zorg ervoor dat je `doc.save()` aanroept na het instellen van het watermerk.  
- **Afbeelding verschijnt niet** – controleer of het afbeeldingspad correct is en of het bestand een ondersteund formaat heeft (PNG, JPEG, BMP).  
- **Transparantie niet toegepast** – `setSemitransparent(true)` werkt alleen voor tekst‑watermerken; voor afbeeldingen moet je het alfa‑kanaal van de PNG bewerken.  
- **Meerdere secties** – als je document meerdere secties heeft, voeg het watermerk toe aan het body‑object van elke sectie of gebruik `doc.getWatermark().setText(...)` voor een globale toepassing.

## Veelgestelde vragen

**V: Hoe kan ik het lettertype van een tekst‑watermerk wijzigen?**  
A: Pas de eigenschap `setFontFamily` aan in `TextWatermarkOptions`, bijvoorbeeld `options.setFontFamily("Times New Roman");`.

**V: Kan ik meerdere watermerken aan één document toevoegen?**  
A: Ja. Maak meerdere `Shape`‑objecten (voor afbeeldingen) of roep `doc.getWatermark().setText(...)` aan met verschillende opties voor elk watermerk.

**V: Is het mogelijk een watermerk te roteren?**  
A: Voor afbeelding‑watermerken stel je de rotatie in op het `Shape`‑object met `watermark.setRotation(angle)`. Voor tekst‑watermerken gebruik je de eigenschap `setLayout` (bijv. `WatermarkLayout.DIAGONAL`).

**V: Hoe kan ik een watermerk semi‑transparant maken?**  
A: Stel `options.setSemitransparent(true)` in bij `TextWatermarkOptions`. Voor afbeeldingen pas je de opacity van de afbeelding aan vóór het laden.

**V: Kan ik watermerken toevoegen aan specifieke secties van een document?**  
A: Ja. Doorloop `doc.getSections()` en voeg het watermerk alleen toe aan de gewenste secties.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Laatst bijgewerkt:** 2026-02-19  
**Getest met:** Aspose.Words for Java 24.12 (latest)  
**Auteur:** Aspose