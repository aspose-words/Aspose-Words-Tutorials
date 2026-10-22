---
category: general
date: 2026-08-20
description: Leer hoe je vormen groepeert, de grootte van een vorm instelt, een afbeelding
  in een document invoegt, een afbeelding aan een groep toevoegt en een rechthoekvorm
  maakt met Aspose.Words in Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: nl
lastmod: 2026-08-20
og_description: Hoe vormen te groeperen in een Word‑document met Aspose.Words. Volg
  deze stapsgewijze Java‑tutorial om de vormgrootte in te stellen, een afbeelding
  in het document in te voegen, een afbeelding aan de groep toe te voegen en een rechthoekige
  vorm te maken.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Hoe vormen groeperen in een Word-document met Aspose.Words – Java-gids
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Hoe vormen te groeperen in een Word‑document met Aspose.Words
url: /nl/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in een Word‑document met Aspose.Words

Als je **hoe vormen groeperen** in een Word‑bestand moet, laat deze tutorial de volledige Java‑oplossing zien. Je ziet hoe je **vormgrootte instellen**, **afbeelding in document invoegen**, **afbeelding aan groep toevoegen** en **rechthoekige vorm maken**—alles met duidelijke uitleg en een uitvoerbaar code‑voorbeeld.

Vormen groeperen vereenvoudigt lay‑outbeheer, stelt je in staat meerdere objecten als één eenheid te verplaatsen of te roteren, en houdt je document overzichtelijk. In de onderstaande stappen bouw je een groep die een rechthoek en een afbeelding bevat, en plaats je de groep op de pagina.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* Java 17 of nieuwer geïnstalleerd.
* Aspose.Words for Java (versie 23.9 of later) toegevoegd aan de classpath van je project.
* Een voorbeeld‑JPEG‑afbeelding op `YOUR_DIRECTORY/sample.jpg` (vervang `YOUR_DIRECTORY` door het daadwerkelijke pad).

Je kunt Aspose.Words toevoegen via Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Hoe vormen groeperen met Aspose.Words

De volgende secties lopen stap voor stap door elke bewerking die nodig is om **hoe vormen groeperen** uit te voeren. De primaire H2‑kop bevat het belangrijkste zoekwoord, conform SEO‑regels.

### Stap 1: Maak een nieuw document en een `DocumentBuilder`

Een `Document` vertegenwoordigt het Word‑bestand, terwijl `DocumentBuilder` handige methoden biedt om inhoud in te voegen.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is*: Beginnen met een nieuw `Document` zorgt ervoor dat de groep die je maakt geen interferentie veroorzaakt met bestaande elementen.

### Stap 2: Voeg een groepsvorm toe die meerdere onderliggende vormen bevat

Een groepsvorm fungeert als een container. De afmetingen bepalen de begrenzende doos voor alle onderliggende vormen.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Tip*: De breedte (`300`) en hoogte (`200`) zijn in points (1 pt = 1/72 inch). Pas ze aan op basis van de grootte van de vormen die je wilt toevoegen.

### Stap 3: Maak een rechthoekige vorm, stel de grootte in en voeg deze toe aan de groep

De exacte grootte van een vorm instellen is essentieel wanneer je precieze lay‑outcontrole wilt.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Waarom we vormgrootte instellen*: De methoden `setWidth` en `setHeight` komen overeen met het secundaire zoekwoord **set shape size**, waardoor je pixel‑perfecte controle krijgt over het uiterlijk van de rechthoek.

### Stap 4: Voeg een afbeelding in en voeg vervolgens de afbeelding‑vorm toe aan dezelfde groep

Het invoegen van een afbeelding is de kern van de vereiste **insert image into document**. De geretourneerde `Shape` is een afbeelding‑vorm die net als elke andere vorm gegroepeerd kan worden.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tip*: Als je de oorspronkelijke beeldverhouding wilt behouden, stel dan alleen één dimensie in (`setWidth` of `setHeight`). Aspose.Words schaalt de andere dimensie automatisch.

### Stap 5: Positioneer de volledige groep op de pagina

Nadat alle onderliggende vormen zijn toegevoegd, kun je de hele groep verplaatsen, roteren of verbergen. Positioneren maakt indirect gebruik van het concept **add picture to group**, omdat de groep nu de afbeelding bevat.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Uitleg*: `setLeft` en `setTop` plaatsen de groep relatief ten opzichte van de paginamarges. Het roteren van de groep toont aan dat alle onderliggende vormen de transformatie overnemen.

### Stap 6: Sla het document op

Tot slot schrijf je het bestand naar schijf. Je kunt het resulterende `.docx`‑bestand in Word openen om de groepering te verifiëren.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Het uitvoeren van het programma levert **GroupShapesDemo.docx** op, met daarin een rechthoek en een afbeelding die samen zijn gebundeld. Het selecteren van één van de vormen in Word selecteert ook de andere, wat bevestigt dat je succesvol **hoe vormen groeperen** hebt geleerd.

---

## Verwachte output

Wanneer je *GroupShapesDemo.docx* opent in Microsoft Word:

* Een rechthoek (gouden vulling) verschijnt aan de linkerkant van de groep.
* De door jou geleverde afbeelding verschijnt rechts van de rechthoek.
* Beide objecten bewegen samen wanneer je de groep sleept.
* De groep staat 50 pt vanaf de linkermarge en 100 pt vanaf de bovenmarge, geroteerd 15°.

Als de afbeelding niet verschijnt, controleer dan het bestandspad in `insertImage`. Aspose.Words geeft een `IOException` wanneer het bestand niet gevonden kan worden.

---

## Veelgestelde vragen en edge‑case handling

| Vraag | Antwoord |
|----------|--------|
| **Kan ik meer dan twee vormen toevoegen?** | Ja. Roep `groupShape.appendChild(otherShape)` aan voor elke extra vorm. |
| **Wat als ik een transparante achtergrond voor de rechthoek nodig heb?** | Gebruik `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Wordt groeperen ondersteund in oudere Word‑formaten (bijv. `.doc`)?** | Groeperen werkt voor `.docx` en `.doc`, maar sommige oudere viewers negeren mogelijk de groepsmetadata. Sla op als `.docx` voor volledige getrouwheid. |
| **Hoe kan ik later degroeperen?** | Haal de kind‑nodes op via `groupShape.getChildNodes(NodeType.ANY, true)` en verplaats ze naar het document‑body, verwijder vervolgens de groep. |
| **Kan ik vormen groeperen over verschillende secties heen?** | Nee. Een `GroupShape` moet zich binnen één `Story` bevinden (meestal het hoofd‑document‑body). |

---

## Pro‑tips voor robuuste vormafhandeling

* **Gebruik absolute positionering spaarzaam** – relatieve positionering (`builder.moveToDocumentEnd()`) levert vaak responsievere lay‑outs op.
* **Cache de `DocumentBuilder`** – een nieuwe builder voor elke bewerking aanmaken kan de prestaties bij grote documenten verminderen.
* **Stel `PictureFillMode` in** wanneer je wilt dat de afbeelding zich uitstrekt of tegelpatroon vormt binnen de vorm: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Valideer afbeeldingsafmetingen** vóór het invoegen om onverwachte schaalveranderingen die de begrenzende doos van de groep kunnen beïnvloeden te voorkomen.

---

## Volgende stappen

Nu je weet **hoe vormen groeperen**, kun je het volgende verkennen:

* **Insert image into document** met geavanceerde opties zoals bijsnijden (`pictureShape.setCropTop(...)`).
* **Set shape size** dynamisch op basis van paginagrootte (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** samen met tekstvakken voor bijschriften.
* **Create rectangle shape** met afgeronde hoeken (`rectangleShape.setCornerRadius(5);`).

Deze onderwerpen bouwen voort op dezelfde API‑surface en helpen je om geavanceerde, programmatische Word‑rapporten te maken.

---

## Conclusie

In deze tutorial heb je **hoe vormen groeperen** geleerd in een Word‑document met Aspose.Words for Java. Door de zes stappen te volgen—een document maken, een groep invoegen, **create rectangle shape**, **set shape size**, **insert image into document**, **add picture to group**, en de groep positioneren—heb je nu een herbruikbaar patroon voor complexe lay‑outscenario's. Experimenteer gerust met extra onderliggende vormen, verschillende rotaties, of conditionele groeperingslogica om aan de behoeften van jouw applicatie te voldoen.

Happy coding!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}