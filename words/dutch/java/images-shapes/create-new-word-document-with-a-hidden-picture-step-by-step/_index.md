---
category: general
date: 2026-09-27
description: Maak een nieuw Word‑document en voeg een afbeeldingsvorm in die verborgen
  blijft. Leer hoe je de vorm kunt verbergen en een verborgen afbeelding kunt toevoegen
  met Aspose.Words voor Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert image shape
- how to hide shape
- how to insert image
- add hidden picture
language: nl
lastmod: 2026-09-27
og_description: Maak een nieuw Word‑document en voeg een afbeeldingvorm toe die verborgen
  blijft. Leer hoe je de vorm kunt verbergen en een verborgen afbeelding kunt toevoegen
  met Aspose.Words voor Java.
og_image_alt: Screenshot showing a Word document with a hidden picture inserted using
  Java
og_title: Maak een nieuw Word‑document met een verborgen afbeelding – Java‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create new Word document and insert an image shape that stays hidden.
    Learn how to hide shape and add hidden picture using Aspose.Words for Java.
  headline: Create new Word document with a hidden picture – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- hidden image
title: Maak een nieuw Word‑document met een verborgen afbeelding – stapsgewijze handleiding
url: /nl/java/images-shapes/create-new-word-document-with-a-hidden-picture-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een nieuw Word‑document met een verborgen afbeelding – stapsgewijze handleiding

Als je een **create new Word document** moet maken die een logo bevat maar je wilt niet dat het logo de paginalay‑out beïnvloedt, laat deze gids je precies zien hoe je dit doet. Je leert hoe je een **insert image shape** toevoegt, begrijpt **how to hide shape**, en uiteindelijk **add hidden picture** aan het bestand zonder visuele impact.

De tutorial behandelt alles van projectopzet tot de laatste verificatiestap. Aan het einde heb je een volledig functioneel Java‑programma dat een Word‑bestand maakt, een afbeelding‑vorm invoegt, deze verbergt en het resultaat opslaat. Er is geen extra gereedschap nodig naast de Aspose.Words for Java‑bibliotheek.

## Vereisten

* Java 17 (of nieuwer) geïnstalleerd.
* Een Maven‑ of Gradle‑project waarin je afhankelijkheden kunt toevoegen.
* Aspose.Words for Java 23.9 (of de nieuwste versie) – zie de officiële Maven‑repository voor de juiste coördinaten.
* Een afbeeldingsbestand (bijv. `logo.png`) geplaatst in een map die je vanuit je code kunt refereren.

> **Pro tip:** Houd de afbeelding in dezelfde directory als je bronbestand tijdens ontwikkeling; dit vereenvoudigt het padbeheer.

## Stap 1: Zet het project op en importeer Aspose.Words

Voeg de Aspose.Words‑afhankelijkheid toe aan je `pom.xml` (Maven) of `build.gradle` (Gradle). Hieronder staat het Maven‑fragment:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Maak nu een Java‑klasse genaamd `HiddenPictureDemo`. De eerste regels importeren de benodigde klassen en **create new Word document**:

```java
import com.aspose.words.*;

public class HiddenPictureDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder
        Document doc = new Document();               // creates new Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is:* `Document` vertegenwoordigt het volledige `.docx`‑bestand, terwijl `DocumentBuilder` een fluente API biedt om inhoud toe te voegen zoals alinea's, tabellen en vormen.

## Stap 2: Voeg een afbeelding‑vorm toe aan het Word‑document

De volgende bewerking demonstreert **how to insert image** als een vorm. Het gebruik van `DocumentBuilder.insertImage` retourneert een `Shape`‑object dat je verder kunt manipuleren.

```java
        // Step 2: Insert an image shape (the picture will act as a shape)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");
        // Optional: set the shape size if needed
        imageShape.setWidth(100);
        imageShape.setHeight(50);
```

*Waarom je een vorm gebruikt:* Een afbeelding die als vorm wordt ingevoegd geeft je toegang tot lay‑out‑eigenschappen zoals zichtbaarheid, omloop en positionering, die essentieel zijn om de afbeelding later te verbergen.

## Stap 3: Verberg de vorm zodat deze niet in de lay‑out verschijnt

Nu beantwoorden we **how to hide shape**. Het instellen van de `Hidden`‑eigenschap op `true` verwijdert de vorm uit de visuele lay‑out terwijl deze in de documentstructuur behouden blijft.

```java
        // Step 3: Hide the shape – this is the core of "add hidden picture"
        imageShape.setHidden(true);
        // You can also set the shape's wrap type to NONE to avoid affecting surrounding text
        imageShape.setWrapType(WrapType.NONE);
```

*Uitleg:* `setHidden(true)` vertelt Word de vorm als onzichtbaar te behandelen. De extra `setWrapType(WrapType.NONE)` zorgt ervoor dat de verborgen afbeelding geen ruimte reserveert, waardoor de oorspronkelijke documentstroom behouden blijft.

## Stap 4: Sla het document op en verifieer de verborgen afbeelding

Sla tenslotte het bestand op schijf op. De verborgen afbeelding blijft deel van het document, maar wordt niet weergegeven wanneer het bestand wordt geopend in Microsoft Word.

```java
        // Step 4: Save the document with the hidden shape
        doc.save("YOUR_DIRECTORY/HiddenShape.docx");
        System.out.println("Document created successfully with a hidden picture.");
    }
}
```

Wanneer je `HiddenShape.docx` in Word opent, zie je een normale, schone pagina zonder zichtbaar logo, maar de afbeelding is wel opgeslagen in het bestand. Je kunt de aanwezigheid verifiëren door het `.docx`‑bestand als zip‑archief te openen en de `word/media`‑map te inspecteren.

### Verwachte output

Het uitvoeren van het programma geeft het volgende weer:

```
Document created successfully with a hidden picture.
```

Het openen van het gegenereerde `HiddenShape.docx` toont een lege pagina (of welke inhoud je elders hebt toegevoegd) en geen zichtbare afbeelding. Als je het `.docx`‑bestand uitpakt, vind je `logo.png` in `word/media`, wat bevestigt dat de afbeelding correct **add hidden picture** is toegevoegd.

## Hoe afbeelding in andere contexten in te voegen

Als je een **insert image shape** in een specifieke alinea wilt invoegen in plaats van op de huidige cursorpositie, kun je eerst de builder verplaatsen:

```java
builder.moveToParagraph(0, 0); // moves to the first paragraph
Shape anotherShape = builder.insertImage("YOUR_DIRECTORY/banner.jpg");
anotherShape.setHidden(true);
```

Dit patroon werkt voor kopteksten, voetteksten of tabellen — verplaats de builder gewoon naar het doel‑knooppunt voordat je `insertImage` aanroept.

## Veelvoorkomende variaties en randgevallen

| Scenario | Wat aan te passen |
|----------|-------------------|
| **Meerdere verborgen afbeeldingen** | Herhaal stappen 2‑3 voor elke afbeelding. Elke `Shape` kan onafhankelijk worden verborgen. |
| **Verschillende afbeeldingsformaten** | Aspose.Words ondersteunt PNG, JPEG, BMP, GIF en TIFF. Gebruik de juiste bestandsextensie in het pad. |
| **Grote documenten** | Maak het document één keer aan en hergebruik vervolgens dezelfde `DocumentBuilder` om verborgen afbeeldingen op verschillende locaties in te voegen. |
| **Voorwaardelijke zichtbaarheid** | Gebruik `shape.setVisible(false)` samen met `shape.setHidden(true)` als je later de zichtbaarheid via Word‑macro's wilt schakelen. |
| **Compatibiliteit met oudere Word‑versies** | Sla op als `doc.save("file.doc", SaveFormat.DOC)` als je Word 2003‑2007 moet ondersteunen. Verborgen vormen gedragen zich op dezelfde manier. |

## Praktische tips uit ervaring

* **Padafhandeling:** Gebruik `Paths.get("...").toAbsolutePath().toString()` om verrassingen met relatieve paden te vermijden wanneer je vanuit een IDE draait versus een verpakte JAR.
* **Prestaties:** Het invoegen van veel grote afbeeldingen kan het geheugenverbruik verhogen. Overweeg de afbeelding te schalen (`setWidth`/`setHeight`) voordat je deze verbergt.
* **Testen:** Automatiseer een snelle controle door het opgeslagen document te laden en `doc.getChildNodes(NodeType.SHAPE, true).getCount()` aan te roepen om te verzekeren dat het verwachte aantal vormen bestaat, zelfs als ze verborgen zijn.

## Conclusie

Je weet nu hoe je een **create new Word document**, een **insert image shape** kunt toevoegen, en **how to hide shape** zodat de afbeelding onzichtbaar blijft — effectief **add hidden picture** aan elk Word‑bestand met Aspose.Words for Java. Deze techniek is nuttig voor het insluiten van watermerken, branding‑assets of metadata‑afbeeldingen die de documentlay‑out niet mogen verstoren.

### Volgende stappen

* Verken andere vorm‑eigenschappen zoals rotatie, randen en hyperlinks.
* Combineer verborgen afbeeldingen met aangepaste documenteigenschappen om extra metadata op te slaan.
* Kijk naar **how to insert image** in kopteksten of voetteksten voor consistente branding over pagina's.

Voel je vrij om te experimenteren met verschillende afbeeldingsgroottes, posities en zichtbaarheidinstellingen. Als je tegen problemen aanloopt, biedt de Aspose.Words for Java‑documentatie gedetailleerde API‑referenties en voorbeeldprojecten. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekige vorm maken in Word met Java – volledige gids](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Schaduw toevoegen aan vorm in Word – volledige Aspose.Words‑gids](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}