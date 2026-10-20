---
category: general
date: 2026-10-20
description: Maak programmatisch een lege DOCX en voeg een commandoknop toe met Java.
  Leer de volledige code om een Word‑document te maken, op te slaan met een knop en
  het bijschrift van de commandoknop in te stellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: nl
lastmod: 2026-10-20
og_description: Maak via code een leeg DOCX‑bestand en voeg een opdrachtknop toe.
  Volg deze stapsgewijze Java‑gids om Word op te slaan met een knop en de bijschrift
  van de opdrachtknop in te stellen.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Maak een leeg DOCX-programma via code – voeg een opdrachtknop toe
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Maak een leeg DOCX‑bestand via code en voeg een opdrachtknop toe
url: /nl/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een lege DOCX programmatisch aan en voeg een commandoknop toe

Als je een **blank DOCX programmatisch wilt maken**, laat deze tutorial zien hoe je een commandoknop direct in het bestand kunt insluiten. Je krijgt de volledige *create word document code* die een Word‑document met een knop opslaat, je in staat stelt **commandoknop bijschrift in te stellen**, en werkt met de nieuwste Aspose.Words for Java‑bibliotheek.

Het insluiten van interactieve besturingselementen in een DOCX‑bestand is handig wanneer je sjablonen wilt verspreiden die macro's activeren, externe programma's starten, of simpelweg gebruikers begeleiden met een klikbare “Click Me”-knop. De onderstaande stappen behandelen alles, van het initialiseren van een leeg document tot het opslaan van het uiteindelijke bestand op schijf.

## Vereisten

* Java 17 of nieuwer geïnstalleerd.
* Maven (of je favoriete build‑tool) om afhankelijkheden te beheren.
* Aspose.Words for Java 23.9 of later. Voeg de afhankelijkheid toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Een IDE zoals IntelliJ IDEA of VS Code (elke editor die Java ondersteunt werkt).

## Maak een lege DOCX programmatisch – stap‑voor‑stap

De volgende secties splitsen het proces op in duidelijke, genummerde stappen. Elke stap legt uit **waarom** het nodig is, niet alleen **wat** je moet typen.

### Stap 1: Initialiseer een nieuw leeg document

Een leeg document is het canvas waarop je de commandoknop plaatst. Aspose.Words levert de `Document`‑klasse hiervoor.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Waarom dit belangrijk is*: Beginnen met een leeg `Document` zorgt ervoor dat er geen verborgen opmaak of bestaande besturingselementen interfereren met de knop die je later toevoegt.

### Stap 2: Stel een `DocumentBuilder` in

`DocumentBuilder` is een helper die je in staat stelt inhoud in te voegen, inclusief OLE‑besturingselementen, zonder je bezig te houden met low‑level knooppuntmanipulatie.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Waarom dit belangrijk is*: De builder behoudt de huidige cursorpositie, zodat de knop precies op de opgegeven plaats wordt geplaatst.

### Stap 3: Voeg een OLE‑commandoknop toe

Word behandelt interactieve besturingselementen als OLE (Object Linking and Embedding)‑objecten. Aspose.Words maakt `Forms2OleControl` hiervoor beschikbaar.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Waarom dit belangrijk is*: Het invoegen van het besturingselement maakt een tijdelijke aanduiding die je later kunt configureren (type, bijschrift, positie).

### Stap 4: Configureer de knop – type, bijschrift en locatie

Je moet het type van het besturingselement definiëren (`COMMANDBUTTON`), een voor de gebruiker zichtbaar bijschrift instellen, en het op de pagina plaatsen.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Waarom dit belangrijk is*:  
* **Type** vertelt Word dat het besturingselement zich gedraagt als een klikbare knop.  
* **Caption** is de tekst die de gebruiker ziet; deze wijzigen is hoe je **commandoknop bijschrift instelt**.  
* **Left** en **Top** bepalen de exacte plaatsing, wat essentieel is wanneer je **add command button word** documenten toevoegt die een precieze lay-out vereisen.

### Stap 5: Sla het document op met de ingesloten knop

Tot slot schrijf je het bestand naar schijf. Het resulterende bestand kan worden geopend in Microsoft Word, waar de knop volledig functioneel zal zijn.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Waarom dit belangrijk is*: Deze stap **slaat Word op met knop** zodat het besturingselement op verschillende machines behouden blijft. Het bestand kan worden verspreid als een sjabloon of worden gebruikt in geautomatiseerde rapportgeneratie‑pijplijnen.

## Volledig werkend voorbeeld

Kopieer de volledige klasse hieronder naar een bestand genaamd `CommandButtonDemo.java`, pas `YOUR_DIRECTORY` aan naar een echt pad, en voer het uit met `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Verwacht resultaat

Wanneer je `CommandButton.docx` opent in Microsoft Word:

* Het document is volledig leeg, behalve een knop met het label **Click Me**.
* Klikken op de knop toont het standaard Word‑gedrag (het doet niets tenzij er een macro aan is gekoppeld), wat bevestigt dat het OLE‑besturingselement correct is ingesloten.

## Veelgestelde vragen & randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Kan ik de knopgrootte wijzigen?** | Ja. Gebruik `commandButton.setWidth(double)` en `commandButton.setHeight(double)` om de afmetingen in punten aan te passen. |
| **Wat als ik een macro aan de knop moet koppelen?** | De knop zelf is slechts een OLE‑besturingselement. Je moet handmatig of via de Aspose.Words `Document`‑API's `addMacro`‑hulpmiddelen een VBA‑macro aan het document toevoegen. |
| **Zal de knop werken in LibreOffice?** | LibreOffice ondersteunt beperkte OLE‑besturingselementen. De knop verschijnt, maar het klikgedrag kan verschillen. |
| **Hoe voeg ik meerdere knoppen toe?** | Herhaal Stappen 3‑4 met een nieuwe `Forms2OleControl`‑instantie. Pas `setLeft`/`setTop` voor elke knop aan om overlapping te voorkomen. |
| **Is de code compatibel met .NET?** | Dezelfde logica geldt, maar je zou `Aspose.Words` voor .NET‑klassen (`Document`, `DocumentBuilder`, `Forms2OleControl`) gebruiken. |

## Tips uit de praktijk

* **Pro tip:** Gebruik `builder.moveToDocumentEnd()` vóór het invoegen van de knop als je deze helemaal aan het einde van het document wilt, ongeacht eerdere inhoud.
* **Let op:** Zeer kleine `Left`/`Top`‑waarden kunnen de knop buiten het afdrukbare gebied plaatsen, waardoor deze onzichtbaar wordt in de lay-outweergave van Word.
* **Prestatienota:** Het invoegen van veel OLE‑besturingselementen kan de bestandsgrootte vergroten. Als je alleen een visuele aanwijzing nodig hebt, overweeg dan een gewone `Shape` met een hyperlink te gebruiken.

## Conclusie

Je weet nu hoe je **een lege DOCX programmatisch kunt maken** en een volledig functionele commandoknop kunt insluiten met Java. De tutorial behandelde de volledige *create word document code* workflow, toonde hoe je **Word opslaat met knop**, liet de juiste manier zien om **add command button word**‑elementen toe te voegen, en legde uit hoe je **commandoknop bijschrift instelt**.

Vanaf hier kun je:

* Meer OLE‑besturingselementen (checkboxes, comboboxen) toevoegen voor rijkere formulieren.
* VBA‑macro's koppelen om de knop aangepaste acties te laten uitvoeren.
* Deze techniek combineren met document‑mail‑merge voor dynamische, interactieve sjablonen.

Voel je vrij om te experimenteren met knopstijlen, posities en extra besturingselementen om aan je specifieke bedrijfsvereisten te voldoen. Veel programmeerplezier

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak een leeg Word‑document met een commandoknop – stap‑voor‑stap gids](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Hoe een ActiveX‑knop in Word in te voegen – knopbijschrift instellen](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Maak een leeg Word‑document met Java – volledige Aspose.Words‑gids](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}