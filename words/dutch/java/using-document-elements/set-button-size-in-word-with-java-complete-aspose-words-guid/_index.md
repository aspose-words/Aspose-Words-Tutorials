---
category: general
date: 2026-07-16
description: Stel de knopgrootte programmeringsmatig in een Word‑document in met Aspose.Words
  voor Java. Leer hoe je een ActiveX‑knop invoegt, de knoplocatie instelt en meer.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: nl
lastmod: 2026-07-16
og_description: Stel de knopgrootte in een Word‑document in met Java. Deze stapsgewijze
  handleiding laat zien hoe je een ActiveX‑knop invoegt, de knoplocatie instelt en
  de knop via code toevoegt.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Stel de knopgrootte in Word in met Java – Volledige Aspose.Words‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Knopgrootte instellen in Word met Java – Complete Aspose.Words‑gids
url: /nl/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Stel knopgrootte in Word met Java – Complete Aspose.Words-gids

Heb je je ooit afgevraagd hoe je **knopgrootte instelt** in een Word‑bestand zonder de UI te openen? Je bent niet de enige. Wanneer je een formulier‑gevuld document on‑the‑fly moet genereren — bijvoorbeeld een onboarding‑pakket met een “Submit”-knop — bespaar je uren handmatig werk door dit programmatisch te doen.

In deze tutorial lopen we stap voor stap door hoe je een **ActiveX‑knop invoegt**, de afmetingen aanpast, deze correct positioneert, en uiteindelijk het bestand opslaat. Aan het einde kun je **programmatically add button**‑besturingselementen toevoegen aan elk Word‑document met Aspose.Words voor Java.

## Vereisten – Wat je nodig hebt voordat je begint

- **Java Development Kit (JDK) 8+** – de code draait op elke recente JDK.
- **Aspose.Words for Java** bibliotheek (download de nieuwste JAR van de officiële site).  
- Een **IDE** naar keuze — IntelliJ IDEA, Eclipse, of zelfs een eenvoudige teksteditor werkt.
- Basiskennis van Java‑syntaxis; geen diepgaande Word‑automatiseringskennis vereist.

> *Pro tip:* Houd de Aspose.Words JAR op het classpath van je project, anders krijg je een `ClassNotFoundException` op het moment dat je `com.aspose.words.*` probeert te importeren.

## Stap 1: Maak een nieuw Word‑document

Het eerste wat we doen is een leeg document en een `DocumentBuilder` aanmaken. Beschouw de builder als een pen waarmee we alles in het bestand kunnen tekenen.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Waarom dit belangrijk is:** Het `Document`‑object vertegenwoordigt het volledige .docx‑bestand, terwijl de `DocumentBuilder` de werkpaard is die ons in staat stelt alinea's, tabellen en — ja — ActiveX‑besturingselementen in te voegen.

## Stap 2: ActiveX‑knop invoegen – Het “Insert ActiveX Button”‑moment

Nu voegen we daadwerkelijk een **activex button** toe aan het document. Aspose.Words biedt een handige methode `insertForms2OleControl` die een `Forms2OleControl`‑object retourneert.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Wat gebeurt er onder de motorkap?* `Forms2OleControlType.COMMAND_BUTTON` vertelt Word dat we een klassieke CommandButton willen, hetzelfde type dat je vanuit het tabblad Developer in de UI zou slepen.

## Stap 3: Knopgrootte en locatie instellen – De kernlogica van “Set Button Size”

Hier komt het belangrijkste trefwoord tot zijn recht. We zullen **set button size** en ook **set button location** instellen zodat het besturingselement precies verschijnt waar we het op de pagina willen hebben.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Waarom dit belangrijk is:** Points zijn de native meeteenheid in Word (1 point = 1/72 inch). Door `setLeft`, `setTop`, `setWidth` en `setHeight` aan te passen, krijg je pixel‑perfecte controle — geen “het ziet er goed uit op mijn scherm maar niet op de printer” meer.

> *Veelvoorkomende valkuil:* Als je vergeet zowel breedte als hoogte in te stellen, blijft de knop op de standaardgrootte, die te klein kan zijn om op te klikken. Specificeer altijd beide.

## Stap 4: Document opslaan – “Create Word Document Button” voltooid

Tot slot schrijven we het bestand naar schijf. De naam suggereert dat we een **creating a Word document button** binnen een .docx aanmaken.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Wanneer je `CommandButtonDemo.docx` opent in Microsoft Word, zie je een **Submit**‑knop geplaatst 100 pt vanaf de linkerrand en 150 pt vanaf de bovenkant, met een grootte van 80 × 30 pt. Klikken erop in de UI activeert het standaard ActiveX‑gedrag (dat je later kunt koppelen met VBA indien nodig).

### Verwachte output screenshot

![Word-document dat de ingevoegde knop toont met de ingestelde knopgrootte](https://example.com/images/set-button-size.png "Screenshot van een Word‑bestand waarin de knopgrootte is ingesteld met Aspose.Words voor Java")

*Alt‑tekst:* knopgrootte instellen in een Word‑document met Java

## Stap 5 (Optioneel): Meer besturingselementen toevoegen of de knop stijlen

Als je meer **programmatically add button**‑besturingselementen nodig hebt dan één Submit‑knop, herhaal dan gewoon het invoegblok met nieuwe namen en bijschriften. Je kunt ook lettertype, achtergrondkleur aanpassen, of later VBA‑macro's koppelen.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tip:* Houd alle knopafmetingen consistent voor een professionele uitstraling. Een snelle manier is om breedte/hoogte in constanten op te slaan.

## Veelgestelde vragen & randgevallen

### “Kan ik de knopgrootte instellen met centimeters in plaats van points?”

De API van Word accepteert alleen points, maar je kunt centimeters omrekenen naar points (`points = cm * 28.3465`). Schrijf een kleine hulpfunctie als je liever metrische eenheden gebruikt.

### “Wat als ik wil dat de knop op een specifieke pagina verschijnt?”

Na het invoegen van de knop kun je de cursor naar een bepaalde pagina verplaatsen met `builder.moveToPage(pageNumber)`. Voeg het besturingselement direct na de verplaatsing in, en stel vervolgens de locatie in zoals hierboven getoond.

### “Werkt dit met .doc (Word 97‑2003) bestanden?”

Ja — Aspose.Words verwerkt automatisch oudere formaten. Verander gewoon de bestandsextensie in `doc.save("Demo.doc")`.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een Java‑klasse en direct kunt uitvoeren (ervan uitgaande dat de Aspose.Words JAR op het classpath staat).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Voer het programma uit, open het gegenereerde `CommandButtonDemo.docx`, en je zult twee netjes geschaalde knoppen zien die klaar zijn voor interactie.

## Conclusie – Je hebt het instellen van knopgrootte in Word onder de knie

We hebben zojuist een volledige, end‑to‑end‑oplossing doorgenomen voor **set button size** en **set button location** met Aspose.Words voor Java. Door de stappen te volgen kun je **insert activex button**, **programmatically add button**‑besturingselementen toevoegen, en uiteindelijk **create word document button**‑elementen maken die precies zo werken als je nodig hebt.  
Wat nu? Probeer de knop in een tabelcel te embedden, of voeg een VBA‑macro toe die formulier‑velden valideert vóór verzending. Hetzelfde patroon werkt voor andere ActiveX‑besturingselementen zoals selectievakjes of keuzelijsten — vervang gewoon `Forms2OleControlType.COMMAND_BUTTON` door de juiste enum‑waarde.

Als je ergens tegenaan loopt, laat dan een reactie achter hieronder. Veel plezier met coderen, en geniet van de kracht van geautomatiseerde Word‑documentcreatie!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe LoadOptions in te stellen in Aspose.Words voor Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Hoe voetteksten uit Word‑documenten te verwijderen met Aspose.Words voor Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java: Uitgebreide gids voor Word‑documentverwerking](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}