---
category: general
date: 2026-07-20
description: Hoe voeg je een knop toe aan een Word‑document met Aspose.Words. Leer
  in enkele minuten een Forms2OleControl‑knop in te voegen met DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: nl
lastmod: 2026-07-20
og_description: Hoe een knop aan een Word‑document toe te voegen met Aspose.Words.
  Volg deze praktische gids om een Forms2OleControl‑CommandButton in te sluiten met
  Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Hoe een knop toevoegen aan Word-document – Complete Aspose.Words-tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Hoe een knop aan een Word‑document toe te voegen – Stapsgewijze handleiding
url: /nl/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een knop toe te voegen aan Word-document – Complete Aspose.Words tutorial

Heb je je ooit afgevraagd **hoe je een knop aan een Word-document kunt toevoegen** zonder de UI te openen en te klikken? Je bent niet de enige. Veel ontwikkelaars moeten programmatisch interactieve besturingselementen insluiten—denk aan een “Submit” knop in een sjabloon die later door een eindgebruiker wordt ingevuld. Het goede nieuws? Met Aspose.Words for Java kun je dit in een handvol regels doen.

In deze tutorial lopen we de exacte stappen door om een `Forms2OleControl` van het type **CommandButton** in te voegen met behulp van de `DocumentBuilder`. Aan het einde heb je een kant‑klaar `.docx`‑bestand dat een klikbare knop toont met het label “Click Me”. Geen mysterie, alleen duidelijke code en de reden achter elke regel.

## Wat je zult leren

- Hoe je een nieuw Word-document vanaf nul maakt.
- Hoe je **DocumentBuilder** gebruikt om een **Forms2OleControl** te plaatsen.
- Waarom je de knopbijschrift en -grootte op de manier die we doen moet instellen.
- Hoe je het resultaat opslaat en verifieert.
- Veelvoorkomende valkuilen (bijv. ontbrekende libraries, niet‑ondersteunde besturingselementtypen) en hoe je ze kunt vermijden.

**Prerequisites** – Je hebt Java 8+ (of nieuwer) en de Aspose.Words for Java‑bibliotheek (versie 23.12 of later) nodig. Een IDE zoals IntelliJ IDEA of Eclipse maakt het makkelijker, maar elke teksteditor werkt.

---

## Stap 1: Stel je project in en importeer afhankelijkheden

Voordat er code wordt uitgevoerd, moet Maven (of Gradle) weten waar Aspose.Words te halen is. Voeg dit fragment toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Als je Gradle verkiest, is het equivalent:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Gebruik de nieuwste release; oudere versies kunnen de `Forms2OleControl`‑API missen.

Zodra de afhankelijkheid is opgelost, ben je klaar om Java‑code te schrijven.

## Stap 2: Maak een nieuw document en verkrijg een DocumentBuilder

De `Document`‑klasse vertegenwoordigt het volledige `.docx`‑pakket, terwijl `DocumentBuilder` het penseel is dat je gebruikt om er inhoud op te schilderen. Beschouw `DocumentBuilder` als de “cursor” die weet waar het volgende element moet komen.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** Een nieuw `Document` initialiseren geeft je een schoon canvas. De builder wijst automatisch naar de eerste alinea, zodat je secties of pagina's niet handmatig hoeft te beheren.

## Stap 3: Voeg een Forms2OleControl van type CommandButton in

Nu komt de ster van de show: `insertForms2OleControl`. Deze methode maakt een OLE (Object Linking and Embedding)‑controle aan die Word als een formelement beschouwt. We geven drie argumenten door:

1. `Forms2OleControlType.COMMANDBUTTON` – vertelt Word dat we een knop willen.
2. `100` – breedte in punten (≈1,39 inch).
3. `30` – hoogte in punten (≈0,42 inch).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**How it works:** Intern maakt Aspose.Words de juiste XML aan in het `word/document.xml`‑deel, met een verwijzing naar het OLE‑object. De afmetingen die je opgeeft worden gerespecteerd door de lay-outengine van Word, zodat de knop precies verschijnt waar de cursor van de builder staat.

## Stap 4: Stel de bijschrift (tekst) van de knop in

Een knop zonder label is verwarrend—stel je een stille liftknop voor. De `setCaption`‑methode stelt de zichtbare tekst in:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Je kunt het bijschrift naar alles wijzigen: “Submit”, “Approve”, of zelfs een gelokaliseerde string. Het bijschrift wordt opgeslagen in de eigenschappen van het OLE‑object, zodat Word het native weergeeft.

## Stap 5: Sla het document op en controleer het resultaat

Tot slot schrijf je het bestand naar schijf. Kies een map waar je schrijfrechten voor hebt; anders krijg je een `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Open `button-demo.docx` in Microsoft Word. Je zou een knop met het label **Click Me** bovenaan het document moeten zien. Als je erop klikt in Word, wordt het standaard OLE‑gedrag geactiveerd (meestal een placeholder‑bericht, tenzij je een macro bindt).

## Veelvoorkomende randgevallen en hoe ze op te lossen

| Situatie | Waarom het gebeurt | Oplossing |
|-----------|--------------------|-----------|
| **Ontbrekend `Forms2OleControl`‑type** | Oudere Aspose.Words‑versies exposeerden deze enum niet. | Upgrade naar 23.12+ of later. |
| **Knop verschijnt als een afbeelding** | De beveiligingsinstellingen van Word blokkeren OLE‑besturingselementen. | Schakel “Trust access to the VBA project object model” in het Trust Center in, of gebruik een macro‑enabled `.docm`. |
| **Onjuiste grootte** | Verwarring tussen punten en pixels. | Onthoud dat 1 punt = 1/72 inch. Pas de getallen dienovereenkomstig aan. |
| **Opslaan veroorzaakt `FileNotFoundException`** | Pad bestaat niet. | Zorg ervoor dat de map (`output/`) bestaat voordat `doc.save` wordt aangeroepen. Gebruik `new File("output").mkdirs();`. |

## Voorbeeld uitbreiden: meerdere knoppen of andere besturingselementen toevoegen

Als je meer dan één knop nodig hebt, verplaats je simpelweg de cursor van de builder met `builder.moveTo` of `builder.writeln()` voordat je `insertForms2OleControl` opnieuw aanroept.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Je kunt ook een **CheckBox**, **ComboBox**, of **ListBox** invoegen door `Forms2OleControlType.COMMANDBUTTON` te vervangen door de juiste enum‑waarde (`CHECKBOX`, `COMBOBOX`, etc.). Dezelfde breedte/hoogte‑parameters zijn van toepassing.

## Hoe dit past in grotere Word‑automatiseringsworkflows

- **Template Generation:** Bouw een contracttemplate die een “Approve” knop bevat voor downstream goedkeuring.
- **Reporting:** Genereer een dagelijks rapport met een “Refresh Data” knop die een macro activeert.
- **Form Distribution:** Verstuur een vragenlijst met vooraf ingevulde interactieve besturingselementen.

Al deze scenario's profiteren van de **Word‑automatisering**‑aanpak die we hebben gedemonstreerd. Door besturingselementen programmatisch in te sluiten, elimineer je handmatige bewerkingen en verminder je menselijke fouten.

## Volledige broncode (klaar om te kopiëren en plakken)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Expected output:** Wanneer je `output/button-demo.docx` opent in Microsoft Word, zie je twee knoppen—“Click Me” en “Submit”—verticaal gestapeld bovenaan het bestand.

## Conclusie

We hebben **hoe je een knop aan een Word-document kunt toevoegen** beantwoord met Aspose.Words for Java, stap voor stap. Beginnend met een leeg `Document` hebben we **DocumentBuilder** gebruikt om een `Forms2OleControl` van type **CommandButton** in te voegen, een vriendelijk bijschrift ingesteld en het resultaat opgeslagen. De aanpak schaalt naar meerdere besturingselementen en integreert naadloos in bredere **Word‑automatisering**‑pijplijnen.

Klaar voor de volgende uitdaging? Probeer de knop te vervangen door een **CheckBox**, of bind een macro die reageert wanneer de gebruiker op de knop klikt in een `.docm`‑bestand. Hetzelfde patroon geldt—verander gewoon de enum en pas het bijschrift aan.

Als je tegen problemen aanloopt, controleer dan je bibliotheekversie en de rechten van de output‑map. Laat gerust een reactie achter met vragen of deel je eigen use‑case. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formulier velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Inline afbeelding invoegen in Word-document met Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Groepvorm maken in Word-document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}