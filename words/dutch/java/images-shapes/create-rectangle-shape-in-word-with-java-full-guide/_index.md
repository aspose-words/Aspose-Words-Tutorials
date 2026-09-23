---
category: general
date: 2026-02-10
description: Maak een rechthoekvorm in een Word‑document met Aspose.Words voor Java.
  Leer hoe je de schaduwkleur instelt, hoe je een schaduw toevoegt en hoe je een Word‑document
  programmeermatig maakt.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: nl
og_description: Maak een rechthoekvorm in een Word‑document met Aspose.Words voor
  Java. Volg deze stapsgewijze tutorial om de schaduwkleur in te stellen, een schaduw
  toe te voegen en een Word‑document te maken.
og_title: Rechthoekvorm maken in Word met Java – Volledige gids
tags:
- Aspose.Words
- Java
- Document Automation
title: Rechthoekvorm maken in Word met Java – Volledige gids
url: /nl/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken in Word met Java – Volledige gids

Heb je ooit **een rechthoekvorm** moeten maken in een Word‑document, maar wist je niet waar te beginnen? Je bent niet de enige—veel ontwikkelaars lopen tegen die muur aan wanneer ze voor het eerst proberen grafische elementen programmatisch te tekenen in Word. Het goede nieuws? Met Aspose.Words for Java kun je een rechthoek op een pagina plaatsen, er een mooie schaduw aan geven en het bestand binnen enkele seconden opslaan. In deze tutorial lopen we stap voor stap door **hoe je een schaduw toevoegt**, **hoe je de schaduwkleur instelt**, en **hoe je een Word‑document** vanaf nul maakt.  

We behandelen alles wat je nodig hebt: de vereiste bibliotheken, elke regel code, waarom bepaalde instellingen belangrijk zijn, en een paar trucjes die je misschien niet in de officiële documentatie vindt. Aan het einde heb je een kant‑klaar voorbeeld dat een rechthoekvorm met een zachte grijze schaduw maakt, opgeslagen als *Shadow.docx*.

## Vereisten – Wat je nodig hebt voordat je begint

Voordat we in de code duiken, zorg dat je het volgende hebt:

| Vereiste | Reden |
|----------|-------|
| Java Development Kit (JDK) 8 of nieuwer | Aspose.Words draait op elke moderne JDK. |
| Maven of Gradle (optioneel) | Vereenvoudigt het toevoegen van de Aspose.Words‑dependency. |
| Aspose.Words for Java‑licentie (of een gratis proefversie) | De bibliotheek is commercieel; een proefversie werkt voor testen. |
| Een IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Helpt je het voorbeeld snel uit te voeren en te debuggen. |

Als je al een Java‑project hebt, voeg dan gewoon de Maven‑coördinaat toe:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Geen ingewikkelde setup nodig—een eenvoudige `public static void main`‑methode volstaat.

![voorbeeld van rechthoekvorm](https://example.com/rectangle-shadow.png "rechthoekvorm met schaduw in Word")

*Afbeeldings‑alt‑tekst: voorbeeld van rechthoekvorm dat een cyaan rechthoek met een grijze schaduw toont.*

## Stap 1 – Een nieuw Word‑document maken

Het eerste wat we moeten doen is een leeg document aanmaken. Beschouw het als het openen van een nieuw Word‑bestand waarop je later gaat tekenen.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Waarom beginnen met een lege `Document`? Omdat Aspose.Words de `Document`‑klasse beschouwt als het canvas voor alle daaropvolgende bewerkingen—het toevoegen van alinea’s, tabellen of vormen. Als je deze stap overslaat, krijg je een `NullPointerException` op het moment dat je iets probeert in te voegen.

## Stap 2 – Een DocumentBuilder instellen

Een `DocumentBuilder` is je vriendelijke pen die in het `Document` schrijft. Het is de aanbevolen manier om inhoud toe te voegen omdat het automatisch de cursorpositie beheert.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Je vraagt je misschien af: “Waarom niet direct met het document werken?” Het antwoord: de builder abstraheert low‑level details zoals sectiebeheer, waardoor de code schoner en minder foutgevoelig wordt.

## Stap 3 – De rechthoekvorm invoegen

Nu komt het leuke deel—**hoe je een vorm maakt**. We voegen een rechthoek van 100 × 50 punten toe en geven deze een cyaan vulling zodat je hem daadwerkelijk kunt zien.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Een paar opmerkingen:

* `ShapeType.RECTANGLE` vertelt Aspose dat we een rechthoek willen; je kunt dit vervangen door `OVAL`, `LINE`, etc.
* De afmetingen worden uitgedrukt in punten (1 pt ≈ 1/72 in). Pas ze aan naar jouw lay‑out.
* Zonder vullingskleur zou de vorm onzichtbaar zijn tegen een witte pagina—vandaar de cyaan.

## Stap 4 – Een schaduw toevoegen en **schaduwkleur instellen**

Hier beantwoorden we het **hoe je een schaduw toevoegt** deel van de puzzel. Het `ShadowFormat`‑object regelt elk visueel aspect van de schaduw, van kleur tot vervagingsradius.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Waarom juist deze waarden?

* **Zichtbaarheid** – Zonder `setVisible(true)` worden de overige instellingen genegeerd.
* **Kleur** – Grijs is een neutrale keuze die zowel op lichte als donkere achtergronden werkt. Vervang gerust `java.awt.Color.GRAY` door elke gewenste `java.awt.Color`.
* **Vervagingsradius** – Een waarde van `5.0` geeft een zachte veder; hogere getallen maken de schaduw meer diffuus.
* **OffsetX/Y** – Offsets verschuiven de schaduw naar rechts en naar beneden, alsof het licht van links‑boven komt.
* **Transparantie** – Een half‑transparante schaduw mengt zich beter met de pagina, vooral bij afdrukken.

Als je een scherpere look wilt, zet de vervagingsradius op `0` en vergroot de offset. Experimenteren wordt aangemoedigd—schaduwen zijn sterk visueel, en de juiste instellingen hangen af van het ontwerp van je document.

## Stap 5 – Het document opslaan

Tot slot slaan we alles op in een `.docx`‑bestand. Je kunt elk pad kiezen dat je wilt; zorg er alleen voor dat de map bestaat.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Wanneer je *Shadow.docx* opent in Microsoft Word, zie je een cyaan rechthoek met een subtiele grijze schaduw die 4 pts naar rechts en naar beneden zweeft. Dat is de volledige **create word document**‑workflow.

### Verwacht resultaat

| Element | Uiterlijk |
|---------|-----------|
| Rechthoek | Cyaan vulling, 100 × 50 pt grootte |
| Schaduw | Grijs, 30 % transparant, 5 pt vervaging, offset (4, 4) |
| Bestand | `Shadow.docx` opgeslagen op het opgegeven pad |

Als de vorm niet verschijnt, controleer dan of de vullingskleur niet gelijk is aan de paginabackground en of de schaduw op zichtbaar staat.

## Pro‑tips & Veelvoorkomende valkuilen

* **Pro tip:** Gebruik `rectangle.setStrokeColor(java.awt.Color.BLACK);` als je een rand rond de vorm wilt. Dit laat de rechthoek beter opvallen op een afgedrukte pagina.
* **Let op:** Opslaan in een alleen‑lezen map veroorzaakt een `IOException`. Kies een schrijfbare locatie of pas de bestandsrechten aan.
* **Randgeval:** Als je een transparante vulling (geen kleur) nodig hebt, roep dan `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);` aan. De vorm zal nog steeds een schaduw werpen, wat handig kan zijn voor watermerk‑achtige graphics.
* **Prestatie‑opmerking:** Het toevoegen van honderden vormen in een lus kan het geheugenverbruik verhogen. Roep `document.save` slechts één keer aan nadat alle vormen zijn toegevoegd.

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een Java‑klasse genaamd `ShadowDemo`. Het compileert en draait direct (mits je de Aspose.Words‑JAR op het classpath hebt).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Voer het programma uit, open het resulterende *Shadow.docx*, en je ziet de rechthoek met zijn schaduw precies zoals beschreven.

## Wat als je meer vormen nodig hebt?

Je vraagt je misschien af: “Kan ik **rechthoekvorm maken** meerdere keren of andere vormen gebruiken?” Absoluut. Loop gewoon over de invoegcode en pas de coördinaten aan met `builder.moveTo` of `builder.insertParagraph`. Dezelfde schaduwinstellingen kun je hergebruiken door ze in een hulpfunctie te plaatsen:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Roep `applyStandardShadow(rectangle);` aan na elke vorminvoeging om je code DRY (Don’t Repeat Yourself) te houden.

## Volgende stappen – Verder gaan dan de basis

Nu je weet **hoe je een schaduw toevoegt**, overweeg dan deze gerelateerde onderwerpen:

* **Hoe je schaduwkleur instelt** voor tekst‑runs – geeft titels een subtiele lift.
* **Create word document** met tabellen en afbeeldingen – combineer vormen met andere inhoud.
* **Hoe je vorm‑animaties maakt** met de ingebouwde mogelijkheden van Word

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}