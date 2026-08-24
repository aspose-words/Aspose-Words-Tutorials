---
category: general
date: 2026-08-23
description: Maak een leeg Word‑document met Aspose.Words voor Java, leer hoe je vormen
  groepeert, een rechthoekvorm kleurt en het document in enkele minuten opslaat als docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: nl
lastmod: 2026-08-23
og_description: Maak een leeg Word‑document met Aspose.Words voor Java, en ontdek
  vervolgens hoe je vormen groepeert, een rechthoekvorm kleurt en het document efficiënt
  opslaat als docx.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Maak een leeg Word‑document en groepeer vormen in Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Maak een leeg Word‑document en groepeer vormen in Java
url: /nl/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document en groepeer vormen in Java

Als je **een leeg Word‑document** programmatically wilt **maken**, maakt Aspose.Words for Java het eenvoudig. Deze tutorial laat je precies zien hoe je **een leeg Word‑document** maakt, een **groepering van vormen in Word** invoegt, een **kleurige rechthoekvorm** toepast, en uiteindelijk **het document opslaat als docx**. Aan het einde heb je een herbruikbare code‑snippet die je in elk Java‑project kunt gebruiken.

Je leert:

* De benodigde Maven/Gradle‑dependency voor Aspose.Words.
* Hoe je een leeg document en een `DocumentBuilder` instantiate.
* De exacte stappen **hoe je vormen groepeert** binnen een `GroupShape`.
* Hoe je vulkleuren instelt op rechthoekvormen.
* De best practice voor **document opslaan als docx** en waar je het uitvoerbestand vindt.

Er wordt geen voorafgaande ervaring met Aspose.Words verondersteld, maar je moet vertrouwd zijn met basis‑Java‑ontwikkeling en een JDK 8 of nieuwer geïnstalleerd hebben.

---

## Vereisten

| Vereiste | Versie / Detail |
|----------|-----------------|
| Java Development Kit | 8 of hoger |
| Buildtool | Maven 3+ of Gradle 6+ |
| Aspose.Words for Java | 23.12 of later (de nieuwste versie op het moment van schrijven) |
| IDE (optioneel) | IntelliJ IDEA, Eclipse, VS Code, of elke Java‑compatibele editor |

---

## Stap 1: Voeg Aspose.Words toe aan je project

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Als je een corporate proxy gebruikt, configureer Maven/Gradle om het pakket van de Aspose‑repository te halen zoals beschreven in de officiële documentatie.

---

## Stap 2: **Maak een leeg Word‑document** met een builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

De `Document`‑constructor maakt een lege `.docx`‑container in het geheugen. De `DocumentBuilder` biedt een fluïde API om inhoud toe te voegen, inclusief vormen.

---

## Stap 3: Voeg een **groepering van vormen in Word** toe

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

Een `GroupShape` werkt als een mini‑canvas. Alle vormen die eraan worden toegevoegd bewegen samen, wat precies **hoe je vormen groepeert** voor consistente lay-out betekent.

---

## Stap 4: Voeg de eerste **kleurige rechthoekvorm** toe (rood)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

De constante `ShapeType.RECTANGLE` maakt een eenvoudige rechthoek. Door `getFill().setForeColor(...)` aan te roepen, beheer je de **kleurige rechthoekvorm**. Je kunt `java.awt.Color.RED` vervangen door elke andere `java.awt.Color`‑constante of een aangepaste RGB‑waarde.

---

## Stap 5: Voeg de tweede **kleurige rechthoekvorm** toe (groen) en positioneer deze

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Het instellen van `setLeft` (of `setTop`) verplaatst de vorm relatief ten opzichte van de linkerbovenhoek van de **groepering van vormen in Word** container. Dit demonstreert **hoe je vormen groepeert** met precieze positionering.

---

## Stap 6: **Sla het document op als docx** en controleer het resultaat

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

De `save`‑methode schrijft automatisch een `.docx`‑bestand omdat de bestandsextensie `.docx` is. Als je een ander formaat nodig hebt (bijv. PDF), geef je de juiste `SaveFormat`‑enum door.

> **Tip:** Zorg ervoor dat de doelmap (`output/` in dit voorbeeld) bestaat of maak deze programmatically aan met `new File("output").mkdirs();`.

---

## Volledige broncode voor snel kopiëren‑plakken

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Verwacht resultaat:** Het openen van `GroupShapeDemo.docx` in Microsoft Word toont één pagina met twee gekleurde rechthoeken (rood links, groen rechts) die samen bewegen wanneer je de groep selecteert.

---

## Veelgestelde vragen en edge‑case handling

| Vraag | Antwoord |
|-------|----------|
| *Kan ik meer dan twee vormen aan dezelfde groep toevoegen?* | Ja. Roep `groupShape.appendChild(yourShape)` aan voor elke extra vorm. De groep past zich automatisch aan de uiterste extents aan, of je kunt handmatig de breedte/hoogte aanpassen. |
| *Wat als ik een ander type vorm nodig heb (bijv. ellips)?* | Vervang `ShapeType.RECTANGLE` door `ShapeType.ELLIPSE`. Dezelfde vul‑kleurlogica geldt. |
| *Moet ik het `Document`‑object zelf vrijgeven?* | Aspose.Words beheert native resources intern. Bij het afsluiten van de JVM worden resources vrijgegeven. Voor langdurige applicaties kun je `doc.dispose();` aanroepen als je de **Aspose.Words for Java (Native)** versie gebruikt. |
| *Hoe wijzig ik de Z‑order zodat één rechthoek bovenop staat?* | Gebruik `groupShape.insertAfter(shape, referenceShape);` of `groupShape.insertBefore(shape, referenceShape);` om kinderen binnen de groep te herschikken. |
| *Kan ik vormen groeperen over verschillende secties heen?* | Nee. Een `GroupShape` moet zich binnen één alinea of vormcontainer bevinden. Om over secties te groeperen, maak je afzonderlijke groepen in elke sectie. |

---

## Conclusie

Je weet nu hoe je **een leeg Word‑document** maakt met Aspose.Words for Java, **vormen groepeert in Word**, **kleurige rechthoekvormen** stylet, en **het document opslaat als docx**. Dit patroon schaalt naar complexere lay-outs — voeg gewoon extra vormen toe, pas offsets aan, en voeg eventueel tekst, afbeeldingen of hyperlinks toe binnen de groep.

**Volgende stappen** die je kunt verkennen:

* Gebruik **groepering van vormen in Word** om flowcharts of UI‑mock‑ups te bouwen.
* Experimenteer met **document opslaan als docx** gecombineerd met PDF‑conversie (`doc.save("out.pdf")`).
* Pas verlopen of patronen toe op de **kleurige rechthoekvorm** voor een rijkere visuele vormgeving.
* Combineer gegroepeerde vormen met tabellen of grafieken voor geavanceerde rapportagedocumenten.

Voel je vrij om de afmetingen, kleuren of vormtypen aan te passen aan de branding van je project. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}