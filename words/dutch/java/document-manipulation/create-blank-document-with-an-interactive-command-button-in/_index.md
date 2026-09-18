---
category: general
date: 2026-09-18
description: Maak een leeg document in Java en voeg een ActiveX‑knop toe. Leer hoe
  je een opdrachtknop invoegt, een interactief formulier bouwt en een Word‑document
  opslaat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: nl
lastmod: 2026-09-18
og_description: Maak een leeg document in Java en voeg een ActiveX‑opdrachtknop toe.
  Volg deze stapsgewijze handleiding om een interactief formulier te bouwen en het
  Word‑bestand op te slaan.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Maak een leeg document met een interactieve opdrachtknop in Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Maak een leeg document met een interactieve opdrachtknop in Word met Java
url: /nl/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg document met een interactieve opdrachtknop in Word met Java

Als je een **leeg document** moet maken die een klikbare knop bevat, laat deze gids je precies zien hoe je dat doet met Aspose.Words for Java. Je leert een interactieve vorm te bouwen, een ActiveX‑knop toe te voegen, en uiteindelijk het Word‑bestand op te slaan — in een paar beknopte stappen.

Het insluiten van een opdrachtknop verandert een statische .docx in een functioneel formulier waarmee eindgebruikers direct in Microsoft Word kunnen interageren. Deze tutorial behandelt ook **hoe een opdrachtknop in te voegen**, het omgaan met veelvoorkomende valkuilen, en het uitbreiden van de oplossing voor complexere formulieren.

## Vereisten

* Java 17 of hoger (de code compileert met JDK 17+)
* Aspose.Words for Java 23.9 of nieuwer – de bibliotheek biedt `Document`, `DocumentBuilder` en `Forms2OleControl`.
* Een IDE of build‑tool (Maven/Gradle) die de Aspose.Words‑dependency kan toevoegen.
* Basiskennis van Java‑syntaxis en Word‑documentconcepten.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Stap 1: Maak een leeg document

De eerste handeling is het instantieren van een nieuw `Document`‑object. Dit object vertegenwoordigt een leeg Word‑bestand dat klaar is voor inhoud.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Het maken van een leeg document geeft je een schoon canvas, wat essentieel is wanneer je programmatically een **Word‑document maken** zonder een vooraf bestaand sjabloon.

## Stap 2: Initialiseert een DocumentBuilder

`DocumentBuilder` is de primaire klasse voor het toevoegen van tekst, tabellen en formulierbesturingselementen. Het werkt op het `Document` dat je zojuist hebt aangemaakt.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

De builder houdt de huidige invoegpositie bij, zodat volgende commando's de juiste locatie in het bestand beïnvloeden.

## Stap 3: Voeg een Forms2Ole‑opdrachtknop‑control toe

Aspose.Words biedt de `Forms2OleControl`‑klasse voor ActiveX‑besturingselementen. Om een **ActiveX‑knop toe te voegen**, vraag je een `COMMANDBUTTON`‑type op bij de builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

De methode `insertForms2OleControl` voegt de control toe op de huidige cursorpositie van de builder. Omdat de control een ActiveX‑object is, werkt het alleen in de desktop‑versie van Microsoft Word, niet in Word Online.

## Stap 4: Configureer het uiterlijk en de positie van de knop

Je kunt de bijschrift, grootte en locatie van de knop instellen via de setters van de control. Positiewaarden worden gemeten in points (1 point = 1/72 inch).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Waarom deze eigenschappen configureren?* Het instellen van `Top` en `Left` zorgt ervoor dat de knop verschijnt waar je verwacht op de pagina, terwijl `Caption` het voor de gebruiker zichtbare label definieert. Als je breedte/hoogte overslaat, kent Word standaardafmetingen toe, die mogelijk niet overeenkomen met je ontwerp.

### Pro‑tip
Als je van plan bent meerdere controls toe te voegen, roep dan `builder.moveToDocumentEnd()` aan vóór elke invoeging om overlappende objecten te voorkomen.

## Stap 5: Sla het document op met de ingesloten opdrachtknop

Schrijf tenslotte het document naar schijf. De bestandsextensie moet `.docx` zijn (of `.doc` voor oudere Word‑versies) om de ActiveX‑control te behouden.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Wanneer je `CommandButton.docx` opent in Microsoft Word, zie je een knop met het label **Click Me**. Als je erop klikt, wordt de standaard ActiveX‑actie geactiveerd (die standaard niets doet). Later kun je een macro of VBA‑script koppelen om aangepast gedrag te definiëren.

## Hoe een opdrachtknop in een bestaand formulier in te voegen (optioneel)

Als je al een formulier met tekstvelden hebt en een **interactief formulier** wilt **maken** dat een knop bevat, volg dan deze extra stappen:

1. Laad het bestaande document: `Document doc = new Document("ExistingForm.docx");`
2. Verplaats de builder naar de gewenste locatie: `builder.moveToParagraph(5, 0); // 6e alinea, eerste node`
3. Voeg de knop in zoals getoond in Stap 3.
4. Pas de `Top`/`Left` van de knop aan op basis van de lay-out van de alinea.

Deze aanpak stelt je in staat elk vooraf gebouwd Word‑sjabloon te verrijken met een ActiveX‑knop zonder het hele bestand opnieuw te maken.

## Randgevallen en probleemoplossing

| Situatie | Wat te controleren | Aanbevolen oplossing |
|----------|--------------------|----------------------|
| Knop verschijnt niet in Word | Zorg ervoor dat je het bestand opent in de desktop‑versie van Word (Word Online verwijdert ActiveX). | Open het bestand in Word 2016+ desktop. |
| Bijschrift is afgekapt | Controleer of de breedte van de knop groot genoeg is om de tekst te bevatten. | Verhoog `setWidth` totdat het bijschrift past. |
| Opslaan geeft `IOException` | Bevestig dat de uitvoermap bestaat en je schrijfrechten hebt. | Maak de map aan of voer het programma uit met verhoogde rechten. |
| Meerdere knoppen overlappen | De cursor van de builder is mogelijk niet verplaatst na de vorige invoeging. | Roep `builder.moveToDocumentEnd()` aan vóór het invoegen van elke nieuwe control. |

## Volledig uitvoerbaar voorbeeld

Hieronder staat een compleet, zelfstandig Java‑programma dat je kunt kopiëren, compileren en uitvoeren. Het demonstreert **leeg document maken**, **ActiveX‑knop toevoegen**, en **Word‑document opslaan** in één stroom.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Verwachte output**

```
Document created: CommandButton.docx
```

Het openen van `CommandButton.docx` toont één pagina met een knop gelabeld **Click Me** die 100 pt van de boven‑ en linkerrand is gepositioneerd.

## Conclusie

Je weet nu hoe je een **leeg document** maakt, een **ActiveX‑knop** insluit, en een gewoon Word‑bestand omzet in een **interactief formulier**. Door **hoe een opdrachtknop in te voegen** onder de knie te krijgen, kun je dit patroon uitbreiden met selectievakjes, keuzelijsten, of zelfs aangepaste VBA‑gedreven logica.

Bekijk vervolgens deze gerelateerde onderwerpen:

* **Interactief formulier maken** met tekstvelden (`builder.insertField`)  
* **ActiveX‑knop toevoegen** die een VBA‑macro uitvoert (`builder.insertOleObject`)  
* **Word‑document maken** vanuit een sjabloon met `Document(docTemplatePath)`  
* Het geconverteerde .docx naar PDF omzetten terwijl de knop behouden blijft (opmerking: PDF zal de knop weergeven als een statisch beeld).

Voel je vrij om te experimenteren met de grootte, positie en het bijschrift van de knop om deze aan je UI‑ontwerp aan te passen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formuliervelden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [VBA‑project maken in Word‑document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Nieuw Word‑document maken](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}