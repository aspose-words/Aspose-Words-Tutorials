---
category: general
date: 2026-11-22
description: Maak een macroknop in een Word‑document met Java. Leer een opdrachtknop
  in te voegen, de knoptekst in te stellen en de macro aan de knop te koppelen voor
  interactieve documenten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: nl
lastmod: 2026-11-22
og_description: Maak een macroknop in een Word‑document met Java. Deze tutorial laat
  zien hoe je een opdrachtknop invoegt, de knoptekst instelt en de macro aan de knop
  koppelt voor volledige interactiviteit.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Maak een macro‑knop in een Word‑document met Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Hoe maak je een macroknop in een Word‑document met Aspose.Words voor Java
url: /nl/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een macroknop te maken in een Word-document met Aspose.Words voor Java

Als je een **macroknop** in een Word‑bestand moet **maken**, leidt deze gids je door de exacte benodigde stappen. Je leert hoe je een **command button** **invoegt**, **knoptekst instelt**, en **macro koppelt aan knop**, zodat het document volledig interactief wordt.

Ontwikkelaars voegen vaak OLE‑besturingselementen toe om VBA‑macro's vanuit een document te activeren. Deze tutorial behandelt de volledige workflow, van projectconfiguratie tot een uitvoerbaar Java‑voorbeeld dat een **interactieve knop** toevoegt aan een .docx‑bestand. Er zijn geen externe scripts nodig—alles draait binnen het Java‑proces.

## Vereisten

* JDK 17 of later geïnstalleerd.
* Maven 3.8+ (of Gradle) voor afhankelijkheidsbeheer.
* Aspose.Words for Java 23.9 of nieuwer – de bibliotheek biedt de `DocumentBuilder` en OLE‑control‑API's.
* Basiskennis van Java en VBA‑macro's.

Als een van deze items ontbreekt, installeer deze dan eerst; de rest van de tutorial gaat ervan uit dat ze beschikbaar zijn.

## Hoe een macroknop te maken met Aspose.Words voor Java

De kern van de oplossing bestaat uit vier acties:

1. **Insert command button** OLE‑control in het document invoegen.
2. **Set button text** (bijschrift) dat de gebruiker ziet.
3. **Link macro to button** zodat klikken de gewenste VBA‑routine uitvoert.
4. **Save the document** met de ingesloten macro.

Elke actie wordt hieronder in een eigen sectie uitgelegd.

### Stap 1: Insert command button in het document invoegen

`DocumentBuilder.insertForms2OleControl` maakt een OLE‑control van het opgegeven type. De constante `Forms2OleControlType.COMMAND_BUTTON` vertelt Aspose.Words een command button te genereren die een macro kan hosten.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Waarom dit belangrijk is:** De OLE‑control fungeert als een container voor de macro. Zonder deze in te voegen is er geen visueel element waarop de gebruiker kan klikken.

### Stap 2: Set button text (bijschrift)

Het bijschrift is het zichtbare label op de knop. Gebruik `setCaption` om te definiëren wat de gebruiker ziet.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Waarom dit belangrijk is:** Duidelijke knoptekst verbetert de bruikbaarheid. De `setCaption`‑methode werkt de `Caption`‑eigenschap van de OLE‑control bij, die Word weergeeft als het knoplabel.

### Stap 3: Link macro to button

Een macro wordt geïdentificeerd aan de hand van zijn naam, bijvoorbeeld `MyMacro`. De `setOnClick`‑methode slaat deze naam op in de `OnClick`‑eventhandler van de knop.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Waarom dit belangrijk is:** Het koppelen van een macro creëert het interactieve gedrag. Wanneer de gebruiker op de knop klikt in Word, wordt de gekoppelde VBA‑routine uitgevoerd.

### Stap 4: Voeg interactieve knop toe aan een Word-document

Na het configureren van de OLE‑control wil je deze mogelijk positioneren, van grootte wijzigen, of omringende tekst toevoegen. De `DocumentBuilder` blijft op het document werken, zodat je alinea's vóór of na de knop kunt invoegen.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Waarom dit belangrijk is:** Opslaan als `.docm` behoudt de macrocode. Als je opslaat als `.docx`, gaat de macro‑referentie verloren.

## Volledig uitvoerbaar voorbeeld

Hieronder staat het volledige Java‑programma, inclusief imports, foutafhandeling en commentaren die elke stap uitleggen. Kopieer de code naar een Maven‑project met de Aspose.Words‑dependency en voer het uit.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Verwachte output

Het uitvoeren van het programma genereert `MacroButtonDemo.docm`. Het openen van het bestand in Microsoft Word toont:

* Een alinea die *“Press the button to execute the macro:”* bevat.
* Een knop met het label **Run Report** direct onder de alinea.
* Wanneer je op de knop klikt, probeert Word de macro `MyMacro` uit te voeren. (Je moet de daadwerkelijke VBA‑code handmatig of via een andere automatisatiestap aan het document toevoegen.)

Als de macro niet bestaat, toont Word een beveiligingswaarschuwing, wat standaardgedrag is voor macro‑ingeschakelde documenten.

## Veelvoorkomende variaties en randgevallen

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Andere knopbijschrift** | Verander de string die aan `setCaption` wordt doorgegeven. |
| **Meerdere knoppen** | Roep `insertForms2OleControl` herhaaldelijk aan, elk met zijn eigen `setCaption` en `setOnClick`. |
| **Aangepaste macro‑namen** | Vervang `"MyMacro"` door een geldige VBA‑procedurenaam, bijv. `"ExportToExcel"`. |
| **Knopgrootte‑beperkingen** | Pas de waarden van `setWidth` en `setHeight` aan; Word respecteert de opgegeven punten. |
| **Macro programmatically insluiten** | Gebruik `Document.getBuiltInDocumentProperties().add("Macros", …)` of een aparte VBA‑injectiestap; Aspose.Words schrijft zelf geen VBA‑code. |

**Pro tip:** Test altijd het gegenereerde `.docm` op een machine met macro‑beveiliging ingesteld op *Enable all macros* tijdens ontwikkeling. In productie onderteken je de macro met een vertrouwd certificaat om beveiligingsmeldingen te vermijden.

## Checklist voor probleemoplossing

* **Knop verschijnt niet** – Controleer of het document is opgeslagen als `.docm` en geopend in een Word‑versie die OLE‑controls ondersteunt.
* **Macro wordt niet uitgevoerd** – Zorg ervoor dat de macro‑naam exact overeenkomt, inclusief hoofdletters, en dat de macro bestaat in het VBA‑project van het document.
* **Knopbijschrift wordt afgekapt** – Vergroot de knopbreedte met `setWidth` om langere tekst te accommoderen.
* **Onverwachte lay-outverschuiving** – Gebruik `builder.moveTo` om de cursor precies te positioneren vóór het invoegen van de control.

## Conclusie

Je weet nu hoe je een **macroknop** in een Word‑document kunt **maken** met Java, een **command button** **invoegt**, **knoptekst instelt**, en een **macro koppelt aan knop** voor volledige interactiviteit. Het volledige voorbeeld toont elke benodigde API‑aanroep, legt uit waarom elke stap belangrijk is, en biedt richtlijnen voor veelvoorkomende variaties.

Vervolgens kun je verkennen:

* **Add interactive button** aan bestaande sjablonen in plaats van een nieuw document.
* **Programmatically inject VBA code** met behulp van de Open XML SDK of een secundaire automatisatietool.
* **Combine multiple OLE controls** (checkboxes, list boxes) om rijke formulieren te bouwen.

Experimenteer met verschillende bijschriften, macro‑namen en knopgroottes om aan je specifieke gebruikssituatie te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een command button in een Word-document in te voegen met Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Hoe de knoppositie in een Word-document in te stellen met Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Hoe een ActiveX‑knop in Word in te voegen – Knopbijschrift instellen](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}