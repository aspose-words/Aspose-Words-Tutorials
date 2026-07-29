---
category: general
date: 2026-07-29
description: 'Instellen van knopgrootte Java‑tutorial: leer hoe je een ActiveX‑opdrachtknop
  in een Word‑document invoegt met Java en Aspose.Words, plus het aanpassen van de
  grootte en het aanmaken van een leeg document.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: nl
lastmod: 2026-07-29
og_description: set button size java guide toont hoe je met Java een ActiveX‑opdrachtknop
  in een Word‑bestand invoegt, de grootte aanpast en het document programmeerbaar
  opslaat.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Knopgrootte instellen Java – ActiveX‑opdrachtknop toevoegen aan Word met
  Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: knopgrootte instellen java – ActiveX‑opdrachtknop in Word invoegen
url: /nl/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – ActiveX‑opdrachtknop invoegen in Word

Heb je je ooit afgevraagd **how to set button size java** wanneer je Word‑documenten automatiseert? Misschien bouw je een rapportagetool die een klikbare “Submit”-knop nodig heeft direct in het .docx‑bestand. In deze tutorial lopen we het volledige proces door – een leeg Word‑document maken, een ActiveX‑opdrachtknop invoegen, en expliciet de breedte en hoogte instellen – allemaal met Java en Aspose.Words.

We beantwoorden ook de hardnekkige “how to insert activex” vraag die bij veel ontwikkelaars opduikt. Aan het einde heb je een uitvoerbaar programma dat een Word‑bestand produceert met een perfect‑afgewerkte opdrachtknop, klaar voor verdere aanpassing.

---

## Wat je nodig hebt

- **Java Development Kit (JDK) 8 of nieuwer** – de code compileert met elke recente JDK.  
- **Aspose.Words for Java** (de nieuwste versie vanaf juli 2026). Haal de JAR op van de [Aspose website](https://products.aspose.com/words/java) of via Maven:  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Een IDE of eenvoudige teksteditor – IntelliJ IDEA, Eclipse of VS Code volstaat.  
- Een map waarin je het gegenereerde **CommandButton.docx** wilt opslaan.

Dat is alles. Geen extra Office‑interop‑bibliotheken, geen COM‑trucs, alleen pure Java.

---

## Stapsgewijze implementatie

We splitsen de oplossing op in vijf logische stappen. Elke stap heeft een eigen H2‑kop; één van hen bevat ons **primaire trefwoord** voor SEO.

### 1. Project opzetten en Aspose.Words importeren

Maak eerst een nieuw Maven‑ (of Gradle‑) project aan en voeg de Aspose.Words‑dependency toe zoals hierboven weergegeven. Importeer vervolgens de benodigde klassen in je Java‑bronbestand:

```java
import com.aspose.words.*;
```

> **Pro tip:** Als je een IDE gebruikt, laat die de klassen automatisch importeren. Het bespaart veel typen en voorkomt typefouten.

### 2. java create blank word Document

Nu maken we daadwerkelijk een **java create blank word** document. Dit vormt de basis waarop we later **insert command button word** gaan plaatsen.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

Het `Document`‑object vertegenwoordigt het volledige Word‑bestand in het geheugen. Op dit moment heeft het bestand nog geen pagina’s, geen tekst – alleen een schone lei.

### 3. DocumentBuilder initialiseren en de ActiveX‑besturingselement invoegen

De `DocumentBuilder` is een helper die ons in staat stelt inhoud, alinea’s, tabellen en, ja, ActiveX‑besturingselementen toe te voegen. Hier beantwoorden we **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` is Aspose’s wrapper rond een OLE‑object. Door `COMMANDBUTTON` te specificeren vertellen we Word een klassieke ActiveX‑opdrachtknop in te sluiten.

### 4. How to Set Button Size Java – Breedte en hoogte aanpassen

Nu volgt het hart van de tutorial: **how to set button size java**. Het besturingselement biedt verschillende lay‑out‑eigenschappen – `Left`, `Top`, `Width` en `Height`. Door ze direct in te stellen bepaal je hoe de knop er op de pagina uitziet.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Waarom deze getallen? In Word is één punt gelijk aan 1/72 van een inch. Een breedte van `120` punten komt dus overeen met ongeveer 1,67 inch – groot genoeg voor een leesbaar label, maar niet overweldigend. Pas de waarden aan naar jouw layout; dezelfde eigenschappen beantwoorden ook de **how to set button**‑vraag die je misschien hebt.

> **Opmerking:** Als je een ander knop‑type nodig hebt (bijv. een selectievakje), vervang dan `Forms2OleControlType.COMMANDBUTTON` door de juiste enum‑waarde.

### 5. Document opslaan

Sla tenslotte het document op schijf op:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Vervang `YOUR_DIRECTORY` door een absoluut of relatief pad op jouw machine. Na het uitvoeren van het programma open je het gegenereerde bestand in Microsoft Word. Je ziet een knop met de tekst “Click Me” die 100 pts vanaf de linkerkant en 200 pts vanaf de bovenkant staat, exact in de afmetingen die we hebben ingesteld.

---

## Volledig werkend voorbeeld

Hieronder staat de complete, kant‑klaar Java‑klasse. Kopieer‑en‑plak deze in `CommandButtonActiveX.java`, pas het uitvoerpad aan, en klik op **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Verwachte output:** Het openen van `CommandButton.docx` in Word toont één pagina met een klikbare “Click Me”‑knop ongeveer in het midden van de pagina. De afmetingen van de knop komen overeen met de waarden die je hebt opgegeven, wat bevestigt dat **set button size java** werkt zoals bedoeld.

---

## Veelgestelde vragen & randgevallen

### Wat als de knop niet verschijnt in Word?

- **Controleer de Word‑versie.** ActiveX‑besturingselementen vereisen de desktop‑versie van Word; Word Online verwijdert ze.  
- **Zorg ervoor dat de Aspose.Words‑licentie is toegepast** (als je een betaalde editie gebruikt). Een niet‑gelicentieerde evaluatie‑versie kan een watermerk toevoegen, maar toont het besturingselement nog steeds.

### Kan ik het lettertype of de kleur van de knop wijzigen?

Ja. Na het invoegen van het besturingselement kun je toegang krijgen tot het onderliggende OLE‑object en de VBA‑eigenschappen manipuleren. Dat is een geavanceerder onderwerp – kijk bijvoorbeeld naar `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` voor een rode caption.

### Hoe verwerk ik het klik‑event van de knop?

ActiveX‑opdrachtknoppen genereren een VBA `Click`‑event. Om de knop functioneel te maken, moet je een macro in hetzelfde document embedden. Aspose.Words kan een macro‑module toevoegen via de `Document.getMacros()`‑API, maar de macro‑code zelf moet in VBA geschreven worden.

### Wat betreft verschillende knop‑types?

Aspose.Words ondersteunt vele `Forms2OleControlType`‑waarden: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX`, enz. Vervang de enum‑constante in de `insertForms2OleControl`‑aanroep om te experimenteren.

---

## Pro‑tips voor productie‑klare code

1. **Gebruik constanten voor lay‑out‑waarden** – maakt toekomstige aanpassingen eenvoudiger.  
2. **Wrap het opslaan‑pad in een `Path`‑object** om platform‑specifieke scheidingstekens te vermijden.  
3. **Dispose van het Document** (of gebruik try‑with‑resources) als je veel bestanden in een lus verwerkt.  
4. **Valideer de output‑map** vóór het aanroepen van `save` om `FileNotFoundException` te voorkomen.

---

## Conclusie

Je hebt zojuist **set button size java** geleerd door een leeg Word‑bestand te maken, een ActiveX‑opdrachtknop in te voegen en de afmetingen nauwkeurig te configureren – allemaal met een paar regels Java‑code. Dit behandelt de kern van **how to insert activex**, **how to set button**, **java create blank word**, en **insert command button word** in één zelf‑containend voorbeeld.

Volgende stappen? Probeer de caption van de knop aan te passen, een macro toe te voegen die reageert op klikken, of meerdere besturingselementen op dezelfde pagina te plaatsen. Je kunt ook onderzoeken hoe je het resulterende .docx naar PDF converteert met Aspose.Words, waarbij de knop als statische afbeelding behouden blijft.

Experimenteer gerust, en als je tegen een probleem aanloopt, laat dan een reactie achter. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hoe Word‑documenten te laden met Aspose.Words Java: uitgebreide gids](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Hoe een document op te slaan als pdf met Aspose.Words voor Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}