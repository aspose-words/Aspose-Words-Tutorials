---
category: general
date: 2026-07-26
description: Hoe een ActiveX‑knop in een Word‑document in te voegen met Aspose.Words
  – leer de knopbijschrift, positie en grootte in slechts een paar regels in te stellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: nl
lastmod: 2026-07-26
og_description: Hoe een ActiveX‑knop in een Word‑document in te voegen met Aspose.Words.
  Volg deze stapsgewijze tutorial om de knopbijschrift, positie en grootte in te stellen.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Hoe een ActiveX‑knop in Word in te voegen – Snelle gids
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Hoe een ActiveX‑knop in Word invoegen – Knopbijschrift instellen
url: /nl/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een ActiveX‑knop in Word in te voegen – Knopbijschrift instellen

Heb je je ooit afgevraagd **hoe je ActiveX**‑besturingselementen in een Word‑bestand kunt invoegen zonder de UI te openen? Je bent niet de enige. In veel bedrijfsapplicaties heb je een klikbare knop nodig die een macro uitvoert, en dit programmatically doen bespaart uren. Deze gids laat je precies zien **hoe je ActiveX** CommandButton kunt invoegen met Aspose.Words for Java, en—ja—hoe je **knopbijschrift instelt** zodat de gebruiker weet wat hij moet klikken.

We lopen het volledige proces door: van het instellen van de bibliotheek, het maken van een nieuw document, het plaatsen van de knop, het aanpassen van grootte en locatie, het geven van een vriendelijk bijschrift, en uiteindelijk het opslaan van het bestand. Aan het einde heb je een uitvoerbaar `.docx` dat in Word opent met een volledig functionele ActiveX‑knop die klaar is om je macro te activeren.

---

## Wat je zult leren

- Aspose.Words installeren en refereren in een Java‑project.  
- Een nieuw `Document` en `DocumentBuilder` aanmaken.  
- **ActiveX** CommandButton‑besturingselement invoegen met één regel code.  
- **Knopbijschrift instellen**, positie aanpassen en afmetingen definiëren.  
- Het document opslaan en openen in Word om het resultaat te zien.

Ervaring met ActiveX is niet vereist; alleen basiskennis van Java en een kopie van Aspose.Words.

---

## Vereisten

- Java 8 of nieuwer geïnstalleerd op je machine.  
- Maven of Gradle voor dependency‑beheer (we laten het Maven‑fragment zien).  
- Een gelicentieerde of evaluatie‑kopie van **Aspose.Words for Java** (de gratis proefversie werkt prima voor deze demo).  
- Microsoft Word (een recente versie) om het gegenereerde bestand te testen.

---

## Stap 1: Aspose.Words in je project instellen

Allereerst—voeg de Aspose.Words‑dependency toe. Als je Maven gebruikt, plaats dit in je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle‑gebruikers kunnen toevoegen:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Na een snelle `mvn clean install` (of `gradle build`) staat de bibliotheek op je classpath en kun je beginnen met coderen.

---

## Stap 2: Een nieuw document en builder aanmaken

Een `Document` vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` je toestaat het te bewerken. Beschouw de builder als een pen die op een leeg canvas tekent.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Waarom beginnen met een leeg document? Het garandeert dat je volledige controle hebt over elk element dat je toevoegt, en er is geen verborgen opmaak die je later verrast.

---

## Stap 3: Het ActiveX CommandButton‑besturingselement invoegen

Nu het middelpunt van de show. Aspose.Words biedt `insertForms2OleControl` waarmee je elk ActiveX‑besturingselement kunt plaatsen dat je opgeeft. Hier vragen we om een **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

De methode retourneert een `Forms2OleControl`‑object, waarmee je programmatisch toegang krijgt tot de eigenschappen van de knop. Dit is waar **hoe je ActiveX invoegt** een één‑regelige operatie wordt—geen gedoe met low‑level COM‑API’s.

---

## Stap 4: Positie, grootte en knopbijschrift instellen

Een knop die midden op de pagina zweeft is niet erg bruikbaar. Je wilt hem plaatsen waar gebruikers hem verwachten, een redelijke grootte geven, en—het belangrijkste—**knopbijschrift instellen** zodat ze weten wat er gebeurt bij een klik.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Waarom deze getallen?** Word gebruikt punten (1 pt ≈ 1/72 inch). `100 pt` ≈ 1,4 in vanaf de linkerkant, `150 pt` ≈ 2,1 in vanaf de bovenkant—ongeveer het midden van een standaard A4‑pagina. Pas ze aan naar jouw lay‑out.

Het bijschrift instellen is cruciaal; zonder bijschrift ziet de knop eruit als een lege rechthoek. De `setCaption`‑methode accepteert elke string, zodat je later kunt lokaliseren indien nodig.

---

## Stap 5: Het document opslaan

Tot slot schrijf je het document naar schijf. Je kunt elke gewenste map kiezen; zorg er alleen voor dat het pad bestaat.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Wanneer je `ActiveXButton.docx` in Word opent, zie je een mooi geplaatste knop met het label **“Click Me.”** Als je erop dubbelklikt, vraagt Word je om macro’s in te schakelen (omdat ActiveX‑besturingselementen als macro‑enabled worden beschouwd). Vanaf daar kun je een VBA‑routine aan het `Click`‑event van de knop koppelen.

---

## Randgevallen & Tips die je kunt missen

- **Macro‑enabled formaat**: Word schakelt ActiveX‑besturingselementen uit in gewone `.docx`‑bestanden tenzij de gebruiker macro’s inschakelt. Als je wilt dat de knop direct werkt, overweeg dan op te slaan als `.docm` (macro‑enabled) met `doc.save(outputPath, SaveFormat.DOCM);`.
- **Compatibiliteit**: Oudere versies van Word (pre‑2007) gebruiken het binaire `.doc`‑formaat. Aspose.Words kan naar dat formaat opslaan, maar de eigenschappen van het besturingselement kunnen iets anders worden weergegeven.
- **Beveiligingsinstellingen**: Sommige bedrijfsomgevingen blokkeren ActiveX. Als je knop niet verschijnt, controleer dan Word’s Trust Center → ActiveX Settings.
- **Meerdere knoppen**: Wil je er meer dan één? Herhaal simpelweg de `insertForms2OleControl`‑aanroep en pas de `Left`/`Top`‑waarden van elke knop aan. Houd de geretourneerde objecten bij zodat je individuele bijschriften kunt instellen.
- **Stijlen voor het bijschrift**: Het bijschrift erft het standaardlettertype. Om dit te wijzigen, moet je de onderliggende XML bewerken of een Word‑stijl toepassen na invoegen—buiten het bereik van deze snelle gids, maar wel mogelijk met Aspose.Words’ `ParagraphFormat`‑API.

---

## Volledig werkend voorbeeld

Hieronder vind je de complete, kant‑en‑klaar Java‑klasse. Kopieer‑plak hem in je IDE, pas het output‑pad aan, en druk op **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Verwacht resultaat**: Na uitvoering print de console de opslaglocatie. Het openen van het gegenereerde bestand in Word toont een knop ongeveer in het midden van de pagina, gelabeld “Click Me”. Klikken zal het standaard ActiveX‑klik‑event activeren (je moet een VBA‑macro koppelen om te reageren).

---

## Conclusie

Je weet nu **hoe je ActiveX** CommandButton‑besturingselementen programmatically in een Word‑document kunt invoegen met Aspose.Words, en je hebt precies gezien hoe je **knopbijschrift instelt**, de positie en grootte van het element bepaalt. Deze aanpak elimineert handmatig UI‑werk, integreert naadloos in geautomatiseerde rapportgeneratoren, en geeft je volledige controle over de

## Wat kun je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}