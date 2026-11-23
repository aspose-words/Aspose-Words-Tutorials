---
category: general
date: 2026-11-22
description: Voeg een rechthoekvorm toe in een Word‑document met Java, stel de vormgrootte
  in, groepeer meerdere vormen en voeg efficiënt een vorm toe aan de groep.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: nl
lastmod: 2026-11-22
og_description: Voeg een rechthoekvorm toe aan een Word‑document met Java, stel vervolgens
  de grootte van de vorm in, groepeer meerdere vormen en voeg een vorm toe aan de
  groep in één workflow.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Rechthoekvorm toevoegen en vormen groeperen in Java – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Rechthoekvorm toevoegen en vormen groeperen in Java
url: /nl/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm toevoegen en vormen groeperen in Java

Als je een **rechthoekvorm** aan een Word‑document wilt toevoegen met Java, leidt deze gids je stap voor stap door het proces. Je leert ook hoe je **de vormgrootte instelt**, **meerdere vormen groepeert**, en **een vorm aan een groep toevoegt** zonder de IDE te verlaten.

Werken met vectorafbeeldingen binnen een DOCX‑bestand voelt vaak aan als het jongleren met verschillende API’s. Aan het einde van deze tutorial heb je één zelfstandig programma dat een rechthoek, een ellips en eventuele extra vormen maakt die je nodig hebt, en ze vervolgens groepeert zodat ze zich als één object bewegen. Geen externe tools zijn nodig, behalve Aspose.Words for Java.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* Java 17 of hoger geïnstalleerd.
* Maven 3.8+ (of Gradle) om afhankelijkheden te beheren.
* Een geldige Aspose.Words for Java‑licentie (evaluatie werkt voor testen).
* Een IDE zoals IntelliJ IDEA of VS Code, hoewel elke teksteditor volstaat.

Deze vereisten zorgen ervoor dat de code kan worden gecompileerd en uitgevoerd in elke moderne ontwikkelomgeving.

## Stap 1: Het Maven‑project opzetten

Maak een nieuw Maven‑project aan of voeg de Aspose.Words‑afhankelijkheid toe aan een bestaand `pom.xml`:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

De afhankelijkheid haalt alle klassen op die nodig zijn voor documentmanipulatie, inclusief `Document`, `DocumentBuilder`, `Shape` en `GroupShape`. Maven downloadt de JAR‑bestanden automatisch wanneer je `mvn compile` uitvoert.

## Stap 2: Het document laden en een DocumentBuilder maken

Een `DocumentBuilder` biedt de fluente API voor het invoegen van inhoud. Laad een bestaand DOCX‑bestand of begin met een leeg document:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Het vroegtijdig aanmaken van de builder geeft je een cursor die zich aan het begin van het document bevindt, klaar voor het invoegen van vormen.

## Rechthoekvorm toevoegen aan een Word‑document

### Stap 3: De rechthoekvorm invoegen

De rechthoek is het eerste visuele element dat we in het document willen plaatsen. Door de `Shape`‑constructor te gebruiken met `ShapeType.RECTANGLE`, krijg je een volledig bewerkbaar object.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Het toevoegen van de rechthoek op dit moment beïnvloedt de lay‑out niet totdat de grootte is gedefinieerd en de vorm aan een container wordt toegevoegd.

### Vormgrootte en afmetingen instellen

#### Stap 4: Breedte en hoogte definiëren

Het instellen van de afmetingen van de vorm bepaalt hoe deze op de pagina verschijnt. Breedte‑ en hoogte‑waarden worden gemeten in punten (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Je kunt deze getallen aanpassen aan je ontwerpvereisten. Dezelfde methoden gelden voor elke `Shape`‑instantie, zodat je ze kunt hergebruiken voor cirkels, pijlen of aangepaste tekeningen.

#### Stap 5: De rechthoek in het document invoegen

Nu de rechthoek een grootte heeft, plaats je hem op de pagina. De `insertShape`‑methode van `DocumentBuilder` voegt de vorm toe op de huidige cursorpositie.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

Op dit moment verschijnt de rechthoek alleen op de pagina. De volgende stappen laten zien hoe je hem combineert met andere vormen.

## Meerdere vormen samen groeperen

Vormen groeperen stelt je in staat ze te verplaatsen, roteren of van grootte te veranderen als één geheel. Dit is vooral handig bij het maken van complexe diagrammen.

### Stap 6: Een groepsvorm‑container maken

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

De `insertGroupShape`‑aanroep voegt een lege container toe aan het document. Alle vormen die aan deze container worden toegevoegd, worden onderdeel van de groep.

### Vorm aan groep toevoegen

#### Stap 7: De rechthoek aan de groep toevoegen

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Door toe te voegen wordt de rechthoek van het documentgedeelte naar de interne collectie van de groep verplaatst. De rechthoek houdt nu rekening met de transformaties van de groep.

#### Stap 8: Een ellips toevoegen ter demonstratie

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

De ellips deelt dezelfde coördinatenruimte als de rechthoek, zodat je ze visueel kunt uitlijnen door hun `setLeft`‑ en `setTop`‑eigenschappen aan te passen indien nodig.

### Stap 9: Het document opslaan

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Het uitvoeren van het programma genereert `output.docx`. Open het bestand in Microsoft Word of LibreOffice; je ziet een rechthoek en een ellips die gegroepeerd zijn. Het selecteren van één van de vormen markeert de hele groep, wat bevestigt dat **een vorm aan een groep toevoegen** geslaagd is.

![Add rectangle shape example in Java](image.png){alt="Voorbeeld van een toegevoegde rechthoekvorm in Java"}

*De screenshot toont de rechthoek en ellips binnen één enkele groep, klaar voor gezamenlijke manipulatie.*

## Waarom deze aanpak belangrijk is

* **Enkele bron van waarheid** – Alle vormeigenschappen worden ingesteld voordat de groep wordt aangemaakt, waardoor lay‑outproblemen worden voorkomen.
* **Herbruikbaarheid** – Dezelfde `setWidth`/`setHeight`‑methoden werken voor elke vorm, zodat je het voorbeeld kunt uitbreiden met pijlen, sterren of aangepaste SVG‑bestanden.
* **Prestaties** – Groeperen vermindert het aantal tekenobjecten dat de Word‑renderer moet verwerken, wat de openingssnelheid van grote documenten verbetert.
* **Onderhoudbaarheid** – Door de logica voor het maken en groeperen van vormen bij elkaar te houden, kunnen toekomstige ontwikkelaars afmetingen aanpassen of nieuwe vormen toevoegen zonder door ongewenste code te zoeken.

## Veelvoorkomende variaties en randgevallen

| Scenario | Aanpassing |
|----------|------------|
| **Andere eenheden** | Gebruik `PointsToPixels`‑conversie of stel `Shape.setWrapType(WrapType.INLINE)` in voor inline plaatsing. |
| **De groep roteren** | Roep `groupShape.setRotation(45);` aan om alle onderliggende vormen met 45° te roteren. |
| **Tekst aan een vorm toevoegen** | Gebruik `Shape.setText("Label");` na het instellen van de grootte. |
| **Dynamische afmetingen** | Haal paginadimensies op via `doc.getFirstSection().getPageSetup().getPageWidth()` en bereken vormgroottes evenredig. |

Deze variaties laten zien hoe het kernpatroon — **rechthoekvorm toevoegen**, **vormgrootte instellen**, **meerdere vormen groeperen**, **vorm aan groep toevoegen** — zich aanpast aan tal van real‑world vereisten.

## Conclusie

Je weet nu hoe je **een rechthoekvorm** aan een Word‑document toevoegt met Java, **de vormgrootte instelt**, **meerdere vormen groepeert**, en **een vorm aan een groep toevoegt** op een nette, onderhoudbare manier. Het volledige voorbeeld compileert tot één uitvoerbare klasse, en het resulterende DOCX‑bestand toont de verwachte output.

Vanaf hier kun je verder gaan met:

* Tekstlabels of hyperlinks aan elke vorm toevoegen.
* Groepen nesten om hiërarchische diagrammen te bouwen.
* Het document exporteren naar PDF terwijl de vormgroepen behouden blijven.

Voel je vrij om te experimenteren met verschillende afmetingen, kleuren en extra vormtypen. Het beheersen van vormmanipulatie opent de deur naar geautomatiseerde rapportgeneratie, dynamische diagrammen en rijke documentervaringen — allemaal direct vanuit Java‑code.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Rechthoekvorm invoegen in Java – Groeperen en positioneren van vormen](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Hoe ellips‑ en rechthoekvormen te maken en in te voegen binnen een groepsvorm in een Word‑document met Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Rechthoekvorm maken in een Word‑document met Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}