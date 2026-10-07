---
category: general
date: 2026-10-07
description: Maak een ActiveX‑opdrachtknop in Java en voeg de opdrachtknop programmatisch
  toe aan Word‑documenten. Leer hoe je de linker‑bovenpositie van de knop instelt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: nl
lastmod: 2026-10-07
og_description: Maak een ActiveX-opdrachtknop in Java om interactieve besturingselementen
  in uw Word‑documenten in te sluiten. Leer hoe u programmatisch een opdrachtknop
  toevoegt, de positie instelt en het uiterlijk aanpast.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: ActiveX‑opdrachtknop maken in Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Hoe maak je een ActiveX‑commando‑knop in Java
url: /nl/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een ActiveX‑opdrachtknop in Java

Als je een **ActiveX‑opdrachtknop** in een Word‑document wilt maken met Java, laat deze gids je precies zien hoe. Je ziet een volledig, uitvoerbaar voorbeeld dat **programmeer­matig een opdrachtknop toevoegt**, positioneert met `setLeft` en `setTop`, en het resultaat opslaat als een `.docx`‑bestand.

Het insluiten van een interactieve knop stelt je in staat formulieren te bouwen, workflows te automatiseren of gebruikersinvoer direct binnen een Word‑bestand te verzamelen. De onderstaande stappen behandelen alles van projectopzet tot eindcontrole, zodat je de code kunt kopiëren naar je eigen project zonder iets te missen.

## Vereisten

Voor je begint, zorg dat je het volgende hebt:

- JDK 17 of nieuwer geïnstalleerd  
- Maven 3.8+ (of je favoriete build‑tool)  
- Aspose.Words for Java 23.9 of later – de bibliotheek die `DocumentBuilder` en OLE‑controlondersteuning biedt  
- Basiskennis van Java‑syntaxis en object‑georiënteerde concepten  

Als je Maven gebruikt, voeg dan de afhankelijkheid toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Pro tip:** Gebruik de nieuwste Aspose.Words‑versie om te profiteren van bugfixes en nieuwe OLE‑functies.

## Stap 1: Maak een nieuw leeg document en een DocumentBuilder

De eerste stap om een **ActiveX‑opdrachtknop** te maken is het instantieren van een leeg `Document` en een `DocumentBuilder`. De builder biedt een vloeiende API voor het invoegen van inhoud, inclusief OLE‑controls.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` vertegenwoordigt het Word‑bestand in het geheugen, terwijl `DocumentBuilder` fungeert als een cursor waarmee je elementen precies kunt plaatsen waar je ze nodig hebt.

## Stap 2: Voeg een OLE‑opdrachtknop‑control toe

ActiveX‑controls worden ingevoegd als OLE‑objecten. Aspose.Words levert de `Forms2OleControl`‑klasse hiervoor.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Wanneer je `insertForms2OleControl()` aanroept, maakt Aspose automatisch een placeholder‑shape aan die de ActiveX‑knop zal hosten.

## Stap 3: Configureer de eigenschappen van de knop

Nu voeg je **programmeer­matig opdrachtknop**‑details toe, zoals de ProgID, bijschrift en grootte. De meest voorkomende ProgID voor een opdrachtknop is `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Hoe de linkerbovenhoek van de knop instellen

Het positioneren van de knop is waar het secundaire trefwoord **how to set button left top** relevant wordt. De methoden `setLeft` en `setTop` accepteren waarden gemeten in punten (1 punt = 1/72 in).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Pas deze getallen aan om ze in je lay‑out te laten passen. Bijvoorbeeld, om de knop uit te lijnen met een tabelcel, bereken je de coördinaten van de cel en geef je die door aan `setLeft`/`setTop`.

## Stap 4: Sla het document op

Schrijf tenslotte het document naar schijf. Het bestand zal de ActiveX‑knop bevatten, klaar voor interactie wanneer het wordt geopend in Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Het uitvoeren van de `main`‑methode levert `CommandButton.docx` op. Open het bestand in Word, schakel de inhoud in indien gevraagd, en je ziet een klikbare knop met het label **Click Me** gepositioneerd op de door jou opgegeven coördinaten.

![ActiveX‑opdrachtknop maken in Java](/images/activex-button-screenshot.png){.center width=600 alt="ActiveX‑opdrachtknop maken in Java screenshot showing the button inside the Word document"}

## Veelvoorkomende variaties en randgevallen

### Meerdere knoppen toevoegen

Als je meerdere knoppen nodig hebt, herhaal je **Stap 2** en **Stap 3** voor elke control. Vergeet niet `setLeft` en `setTop` aan te passen zodat de knoppen elkaar niet overlappen.

### Het gedrag van de knop wijzigen

ActiveX‑knoppen kunnen VBA‑macro's uitvoeren bij een klik. Om een macro toe te wijzen, stel je de eigenschap `setOnAction` in met de macro‑naam:

```java
commandButton.setOnAction("MyMacro");
```

Zorg ervoor dat het doel‑document de bijbehorende VBA‑module bevat; anders geeft Word een foutmelding.

### Compatibiliteitsopmerkingen

- De knop werkt alleen in desktop‑versies van Word die ActiveX ondersteunen (bijv. Word voor Windows). In Word voor Mac of online editors verschijnt hij als een statisch beeld.  
- Als je een gemengde omgeving target, overweeg dan het gebruik van een **content control** (`RichTextContentControl`) in plaats van een ActiveX‑control.

## Volledige broncode ter referentie

Hieronder vind je het complete, zelfstandige voorbeeld dat je kunt kopiëren naar een nieuw Maven‑project en direct kunt uitvoeren.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Verwachte output:** Na uitvoering vind je `CommandButton.docx` in de werkmap van je project. Het openen van het bestand in Microsoft Word toont een knop op de opgegeven locatie met het bijschrift “Click Me”.

## Conclusie

Je weet nu hoe je een **ActiveX‑opdrachtknop** in Java kunt **programmeer­matig een opdrachtknop** aan een Word‑document kunt toevoegen, en hoe je de lay‑out nauwkeurig kunt regelen met **how to set button left top**‑methoden. Deze techniek opent de deur naar rijke, interactieve Word‑formulieren die macro's kunnen activeren, externe applicaties kunnen starten of gebruikersinvoer direct in het document kunnen verzamelen.

### Volgende stappen

- Verken andere ActiveX‑controls zoals `Forms.TextBox.1` of `Forms.CheckBox.1`.  
- Combineer meerdere controls met een VBA‑module om volledig uitgeruste formulieren te implementeren.  
- Vervang ActiveX door content controls als je cross‑platform compatibiliteit nodig hebt.  

Voel je vrij te experimenteren met grootte, bijschrift en positionering om je UI‑ontwerp te matchen. Als je tegen problemen aanloopt, controleer dan dubbel of de Aspose.Words‑versie die je gebruikt OLE‑controls ondersteunt, en verifieer dat de beveiligingsinstellingen van Word de uitvoering van ActiveX toestaan. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [OLE‑objecten en ActiveX‑controls insluiten in Word‑documenten](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Hoe formuliervelden maken en inhoud toevoegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Rechthoekige vorm maken in Word met Java – volledige gids](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}