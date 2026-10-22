---
category: general
date: 2026-09-27
description: Maak een docx met ActiveX in Java met behulp van Aspose.Words. Leer stap
  voor stap een ActiveX‑opdrachtknop in te voegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: nl
lastmod: 2026-09-27
og_description: Maak een docx met ActiveX in Java met Aspose.Words. Volg deze gids
  om een ActiveX-opdrachtknop in te voegen en het document op te slaan.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Maak een docx met ActiveX in Java – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Hoe een docx met ActiveX te maken met Java en Aspose.Words
url: /nl/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een docx met ActiveX met Java en Aspose.Words

Als je een **docx met ActiveX moet maken**, laat deze gids je een complete oplossing zien. Je leert hoe je een **ActiveX-opdrachtknop** in een Word‑bestand kunt invoegen met Aspose.Words voor Java, en vervolgens het resultaat opslaat als een .docx die geopend kan worden in Microsoft Word.

Het programmatisch genereren van een Word‑document bespaart je handmatig bewerken en garandeert consistentie in rapporten, contracten of formuliertemplates. De onderstaande stappen behandelen alles, van projectopzet tot het omgaan met veelvoorkomende valkuilen, zodat je de techniek in elke Java‑applicatie kunt integreren.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* Java Development Kit (JDK) 8 of nieuwer geïnstalleerd.
* Maven 3.6+ (of een ander build‑tool dat je verkiest).
* Een Aspose.Words for Java‑licentiebestand (de gratis evaluatie werkt voor testen).
* Microsoft Word geïnstalleerd op de doelmachine als je de ActiveX‑besturingselement visueel wilt verifiëren.

Deze items zijn vereist omdat Aspose.Words de API levert die het document maakt, terwijl Word nodig is om het ActiveX‑besturingselement weer te geven.

## Stap 1: Stel het Maven‑project in

Maak een nieuw Maven‑project aan of voeg de Aspose.Words‑dependency toe aan een bestaande `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Houd de Aspose.Words‑versie gesynchroniseerd met de officiële release‑notes om te profiteren van bug‑fixes en nieuwe ActiveX‑functies.

## Stap 2: Schrijf de Java‑code die het document maakt

Maak een klasse genaamd `ActiveXDocxCreator`. De onderstaande code bevat alle benodigde imports, een `main`‑methode en gedetailleerde commentaren die elke bewerking uitleggen.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Waarom elke regel belangrijk is

* `Document` is de container voor alle Word‑inhoud. Het maken van een nieuw exemplaar geeft je een schoon canvas.
* `DocumentBuilder` biedt een vloeiende API om elementen in te voegen; het houdt automatisch de invoegpositie bij.
* `insertForms2OleControl()` maakt een generieke OLE‑besturingselement‑placeholder. Aspose.Words behandelt dit als een ActiveX‑container.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` vertelt Word dat de placeholder moet worden weergegeven als een CommandButton.
* `setCaption("Click Me")` definieert de tekst die op de knop wordt weergegeven.
* `setLeft` en `setTop` plaatsen de knop relatief ten opzichte van de paginamarges. Pas deze waarden aan om bij je lay‑out te passen.
* `setWidth` en `setHeight` zijn optioneel maar verbeteren het uiterlijk van de knop, vooral wanneer de standaardgrootte te klein is.
* `doc.save` schrijft de in‑memory‑structuur naar een fysiek .docx‑bestand dat Word kan openen.

## Stap 3: Verifieer het gegenereerde document

Open `output/ActiveXCommandButton.docx` in Microsoft Word:

1. Het document moet één pagina tonen met een knop gelabeld **Click Me** die zich dicht bij de linkerbovenhoek bevindt.
2. Als de knop niet verschijnt, controleer dan of **ActiveX‑besturingselementen zijn ingeschakeld** in het Trust Center van Word (File → Options → Trust Center → Trust Center Settings → ActiveX Settings).
3. De knop werkt alleen in Windows‑versies van Word die ActiveX ondersteunen. Op macOS of web‑gebaseerde Word wordt het besturingselement weergegeven als een statische afbeelding.

## Stap 4: Veelvoorkomende randgevallen afhandelen

| Situation | Reason | Recommended action |
|-----------|--------|--------------------|
| De knop ontbreekt na het openen van het bestand | Word‑beveiligingsinstellingen blokkeren ActiveX | Schakel “Run all controls without restrictions” in voor vertrouwde locaties. |
| Het gegenereerde .docx kan niet worden geopend | Incompatibele Aspose.Words‑versie | Upgrade naar de nieuwste Aspose.Words‑release; oudere versies kunnen de benodigde OLE‑onderdelen mogelijk niet correct insluiten. |
| Je wilt dat de knop een macro uitvoert | ActiveX alleen bevat geen macro‑code | Combineer het ActiveX‑besturingselement met een VBA‑macro die het `Click`‑event afhandelt. Gebruik de `DocumentBuilder.insertOleObject`‑methode om een macro‑ingeschakeld sjabloon in te sluiten. |
| De lay‑out is verkeerd bij verschillende paginagroottes | Coördinaten zijn absolute punten | Gebruik `builder.getPageSetup().setPageWidth` en `setPageHeight` om de paginagrootte te standaardiseren voordat je het besturingselement positioneert. |

## Stap 5: De oplossing uitbreiden

Je kunt andere ActiveX‑besturingselementen invoegen door de `ControlType`‑enum te wijzigen:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words ondersteunt ook het invoegen van **ActiveX‑tekstvakken**, **listboxen** en **comboboxen**. Dezelfde positioneringsmethoden (`setLeft`, `setTop`, `setWidth`, `setHeight`) zijn van toepassing.

Als je meerdere besturingselementen moet plaatsen, roep dan herhaaldelijk `builder.insertForms2OleControl()` aan en pas de coördinaten van elk besturingselement dienovereenkomstig aan.

## Volledige broncode

Hieronder staat het volledige `ActiveXDocxCreator.java`‑bestand, klaar om te kopiëren en plakken:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Het uitvoeren van dit programma produceert een **docx met ActiveX** die je kunt distribueren naar eindgebruikers die interactieve formulieren nodig hebben.

## Conclusie

Je weet nu hoe je **docx met ActiveX** kunt maken met Java en Aspose.Words, en hoe je **ActiveX‑opdrachtknop** programmatisch kunt invoegen. De tutorial besprak projectopzet, volledige broncode, verificatiestappen en strategieën voor het omgaan met typische problemen.

Vanaf hier kun je verder verkennen:

* Het toevoegen van VBA‑macro's om te reageren op de knop‑klik.
* Het insluiten van andere ActiveX‑besturingselementen zoals selectievakjes of comboboxen.
* Het automatiseren van het genereren van meer‑pagina‑formulieren met dynamische gegevens.

Experimenteer met verschillende coördinaten, groottes en besturingselementtypen om aan je specifieke documentlay‑out te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}