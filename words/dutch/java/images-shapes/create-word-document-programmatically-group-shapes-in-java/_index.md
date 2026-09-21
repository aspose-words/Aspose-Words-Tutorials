---
category: general
date: 2026-09-21
description: Maak een Word‑document programmatisch aan met Java. Leer hoe je vormen
  groepeert in Word, een rechthoekvorm invoegt, de vormgrootte instelt en vormen toevoegt
  aan een Word‑document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: nl
lastmod: 2026-09-21
og_description: 'Maak een Word-document programmatically met Java: deze gids laat
  zien hoe je vormen groepeert in Word, rechthoekige vormen invoegt, de grootte van
  vormen instelt en vormen toevoegt aan een Word-document.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Maak een Word-document programmatically, groepeer vormen in Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Maak een Word‑document programmatisch, groepeer vormen in Java
url: /nl/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Word-document programmatisch, groepeer vormen in Java

Als je **een Word-document programmatisch wilt maken**, leidt deze gids je door een volledige oplossing. Je zult zien hoe je **vormen in Word groepeert**, een rechthoek invoegt, de grootte instelt en andere vormen toevoegt — allemaal met Java en de Aspose.Words for Java bibliotheek.

De tutorial behandelt elke stap, van het opzetten van het project tot het opslaan van het uiteindelijke .docx‑bestand. Aan het einde kun je een Word‑document genereren dat een rechthoek en een afbeelding bevat, samengevoegd in één groep, waardoor ze gemakkelijk samen verplaatst of van grootte kunnen worden gewijzigd. Er is geen voorafgaande ervaring met de Aspose.Words‑API vereist, maar je moet wel een basis Java‑ontwikkelomgeving hebben.

## Vereisten

* Java Development Kit (JDK) 8 of nieuwer  
* Maven of Gradle voor afhankelijkheidsbeheer  
* Aspose.Words for Java 23.9 (of de nieuwste versie) – de bibliotheek is gratis voor evaluatie  
* Een afbeeldingsbestand (bijv. `sample.jpg`) geplaatst in een bekende map  

Het hebben van deze items zorgt ervoor dat de code zonder extra configuratie draait.

## Stap 1: Het project opzetten en Aspose.Words importeren

Maak een Maven‑project (of voeg de afhankelijkheid toe aan je bestaande `pom.xml`):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Als je liever Gradle gebruikt, voeg dan het volgende toe aan `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Nadat de afhankelijkheid is opgelost, importeer je de benodigde klassen in je Java‑bronbestand:

```java
import com.aspose.words.*;
import java.io.File;
```

## Stap 2: Het Word-document programmatisch maken

De eerste handeling in elk automatiseringsscenario is het instantieren van een `Document`‑object en een `DocumentBuilder`. De builder vereenvoudigt het invoegen van tekst, afbeeldingen en vormen.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Op dit moment bestaat het document alleen in het geheugen. Je kunt nu beginnen met het toevoegen van vormen.

## Stap 3: Een rechthoekvorm invoegen – hoe een rechthoekvorm in te voegen

Een rechthoek is een basis‑`Shape` met `ShapeType.RECTANGLE`. Je regelt de afmetingen met `setWidth`, `setHeight` en positioneert deze met `setTop` en `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Why this matters:** Het expliciet instellen van grootte en positie (`set shape size word`) garandeert dat de rechthoek precies op de verwachte plek verschijnt, ongeacht de standaardlay-out van het document.

## Stap 4: Een afbeelding invoegen – vormen toevoegen aan Word-document

De `DocumentBuilder` kan een afbeelding direct vanuit een bestandspad invoegen. Na het invoegen kun je de afbeelding opnieuw positioneren, net als elke andere vorm.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Zowel de rechthoek als de afbeelding zijn nu onafhankelijke vormen binnen het document.

## Stap 5: De vormen groeperen – hoe vormen in Word te groeperen

Vormen groeperen is handig wanneer je ze als één eenheid wilt verplaatsen of van grootte wilt wijzigen. Aspose.Words biedt een `GroupShape`‑container voor dit doel.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Wanneer de groep wordt opgeslagen, behandelt Word de twee kinderen als één logisch object. Later kun je de groep selecteren en slepen; zowel de rechthoek als de afbeelding volgen dan.

## Stap 6: Het document opslaan

Schrijf tenslotte het document naar schijf. Het pad moet schrijfbaar zijn voor het Java‑proces.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Het uitvoeren van de `main`‑methode produceert een bestand met de naam **GroupShapeExample.docx**. Open het in Microsoft Word om een rechthoek en een afbeelding te zien die samen in één groep zijn vergrendeld. Het selecteren van de groep laat je beide objecten tegelijk verplaatsen, wat bevestigt dat de groepering geslaagd is.

## Verwachte output

* Een Word‑bestand (`GroupShapeExample.docx`) geplaatst in de map die je hebt opgegeven.  
* In het bestand verschijnt een rechthoek (lichtgrijze vulling) in de linkerbovenhoek, en de afbeelding staat er direct onder.  
* Beide objecten maken deel uit van één enkele groep, zodat het slepen van één object het andere verplaatst.

## Veelvoorkomende variaties en randgevallen

| Situatie | Aanbeveling |
|-----------|----------------|
| **Verschillende afbeeldingsformaten** | Aspose.Words ondersteunt PNG, BMP, GIF en TIFF. Gebruik de juiste bestandsextensie in `insertImage`. |
| **Negatieve afmetingen** | De API gooit `ArgumentException`. Valideer altijd breedte en hoogte voordat je `setWidth` / `setHeight` aanroept. |
| **Grote documenten** | Het groeperen van veel vormen kan de bestandsgrootte vergroten. Overweeg om vormen te combineren tot één afbeelding wanneer prestaties belangrijk zijn. |
| **Compatibiliteit met Word‑versies** | GroupShape werkt met Word 2007 (`.docx`) en later. Voor oudere `.doc`‑bestanden wordt de groep afgevlakt. |
| **Dynamische positionering** | Gebruik berekeningen op basis van paginagrootte (`doc.getFirstSection().getPageSetup().getPageWidth()`) als je een adaptieve plaatsing nodig hebt. |

**Pro tip:** Na het maken van de groep kun je wijzigen


## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak Word-document Java – Voeg rechthoekvorm toe met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Maak rechthoekvorm in Word met Java – volledige gids](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Maak groepsvorm in Word-document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}