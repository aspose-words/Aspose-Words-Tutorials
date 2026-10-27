---
category: general
date: 2026-08-14
description: Maak een docx ActiveX‑knop in Java met Aspose.Words. Leer hoe je een
  formulierknop in Word via code kunt toevoegen en het document opslaan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: nl
lastmod: 2026-08-14
og_description: Maak een docx ActiveX‑knop in Java met Aspose.Words. Deze gids laat
  zien hoe je een formulierknop in Word toevoegt, deze configureert en het bestand
  opslaat.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Docx ActiveX‑knop maken in Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Maak docx ActiveX‑knop in Java – volledige programmeergids
url: /nl/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak docx ActiveX‑knop in Java – volledige programmeergids

Als je een **docx ActiveX‑knop** in Java moet maken, leidt deze gids je door het volledige proces. Je ziet hoe je een formulierknop in Word toevoegt, de eigenschappen configureert en een kant‑klaar .docx‑bestand produceert.

Werken met ActiveX‑besturingselementen is een veelvoorkomende eis bij het automatiseren van legacy Word‑formulieren. In deze tutorial leer je **form button word** documenten toe te voegen met de Aspose.Words for Java‑bibliotheek, zodat je interactieve besturingselementen kunt insluiten zonder handmatig bewerken.

## Wat je nodig hebt

* Java 17 of hoger (de code compileert met eerdere versies, maar Java 17 wordt aanbevolen).
* Aspose.Words for Java 23.10 of nieuwer – download de JAR van de Aspose‑website of voeg de Maven‑dependency toe.
* Een IDE (IntelliJ IDEA, Eclipse of VS Code) of een eenvoudige teksteditor en command‑line build‑tools.
* Basiskennis van Java‑syntaxis en object‑georiënteerd programmeren.

## Hoe een docx ActiveX‑knop te maken met Aspose.Words

De volgende stappen tonen de exacte volgorde die nodig is om **docx ActiveX‑knop**‑objecten te maken en in een Word‑document in te sluiten.

### Stap 1: Het project opzetten en Aspose.Words importeren

Voeg de Aspose.Words‑dependency toe aan je `pom.xml` als je Maven gebruikt:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Of, als je Gradle verkiest:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Nadat de dependency is opgehaald, importeer je de benodigde klassen in je Java‑bronbestand:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Deze imports geven je toegang tot `Document`, `DocumentBuilder` en de `Forms2OleControl`‑API die wordt gebruikt om ActiveX‑besturingselementen in te voegen.

### Stap 2: Maak een nieuw leeg document

Instantieer een `Document`‑object, dat een leeg Word‑bestand vertegenwoordigt dat klaar is om inhoud te ontvangen.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Het eerst aanmaken van het document zorgt ervoor dat de daaropvolgende builder werkt op een schoon canvas.

### Stap 3: Initialiseer een DocumentBuilder

`DocumentBuilder` biedt een vloeiende interface voor het invoegen van tekst, afbeeldingen en besturingselementen. Koppel het aan het document dat je zojuist hebt gemaakt.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

De builder houdt de huidige cursorpositie in het document bij, zodat de volgende invoeging precies gebeurt waar je het nodig hebt.

### Stap 4: Voeg een ActiveX CommandButton‑besturingselement in

Gebruik de `insertForms2OleControl`‑methode om een ActiveX `CommandButton` in te sluiten. Deze methode retourneert een `Forms2OleControl`‑instantie die je verder kunt configureren.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

Op dit moment bevat het .docx‑bestand een tijdelijke aanduiding voor een knop, maar heeft nog geen visueel bijschrift of grootte.

### Stap 5: Configureer de eigenschappen van de knop

Stel de naam, het bijschrift en de lay‑out‑attributen van het besturingselement in. Deze waarden bepalen hoe de knop in Word verschijnt en hoe je er later naar kunt verwijzen via VBA of automatiseringsscripts.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Pro tip:** Word meet posities in punten (1 pt ≈ 1/72 in). Pas `setTop` en `setLeft` aan om de knop uit te lijnen met de omliggende inhoud.

### Stap 6: Sla het document op

Schrijf tenslotte het document naar schijf. Gebruik de `.docx`‑extensie om het bestand in het moderne Office Open XML‑formaat te behouden.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Wanneer je het resulterende bestand opent in Microsoft Word, zie je een **Submit**‑knop op de door jou opgegeven coördinaten. Klikken op de knop in Word zal geen actie uitvoeren tenzij je VBA‑code toevoegt, maar het besturingselement is volledig functioneel voor formulier‑gebaseerde workflows.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Heb ik een speciale Word‑versie nodig?** | ActiveX‑besturingselementen worden ondersteund in de desktopversie van Microsoft Word op Windows. Ze zijn niet beschikbaar in Word voor Mac of Word Online. |
| **Kan ik dit gebruiken met `.doc`‑bestanden?** | Ja. Sla het document op met een `.doc`‑extensie (`document.save("ActiveXButton.doc")`). dezelfde API werkt voor het oudere binaire formaat. |
| **Wat als de knop niet verschijnt?** | Zorg ervoor dat **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** ActiveX‑besturingselementen toestaat. Controleer ook of het document niet geopend is in “Protected View”. |
| **Kan ik andere ActiveX‑besturingselementen toevoegen?** | Zeker. Vervang `Forms2OleControlType.COMMAND_BUTTON` door `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, enz. |
| **Is er een grootte‑limiet?** | De grootte van het besturingselement wordt alleen beperkt door de paginalay‑out. Zeer grote afmetingen kunnen een lay‑out‑overflow veroorzaken. |

## Volledig, uitvoerbaar voorbeeld

Hieronder staat een volledige Java‑klasse die je kunt kopiëren, compileren en uitvoeren. Het bevat alle imports, de main‑methode en inline‑commentaren voor duidelijkheid.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Verwacht resultaat:** Na het uitvoeren van het programma verschijnt `ActiveXButton.docx` in de werkmap. Het openen in Microsoft Word toont een klikbare **Submit**‑knop die zich dicht bij de linkerbovenhoek van de eerste pagina bevindt.

## Conclusie

Je weet nu hoe je **docx ActiveX‑knop**‑objecten in Java kunt maken met Aspose.Words, en je hebt gezien hoe je **form button word**‑documenten programmatisch kunt toevoegen. De stappen—het opzetten van het project, een document maken, het besturingselement invoegen, de eigenschappen configureren en opslaan—dekken de volledige workflow van begin tot eind.

Vervolgens kun je verkennen:

* Het toevoegen van VBA‑macro's die reageren op de knop‑klik.
* Het insluiten van andere ActiveX‑besturingselementen zoals selectievakjes of lijstvakken.
* Het automatiseren van de generatie van meer‑pagina‑formulieren met meerdere interactieve elementen.

Voel je vrij om te experimenteren met groottes, posities en bijschriften om aan je specifieke formulier‑ontwerpvereisten te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hoe HTML te laden en op te slaan als DOCX met Aspose.Words voor Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Hoe PDF‑documenten te maken met Aspose.Words voor Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}