---
category: general
date: 2026-09-24
description: Stel de positie van een knop in een Word‑document in met Java en Aspose.Words.
  Leer hoe je een knop invoegt, een ActiveX‑besturingselement toevoegt en een Word‑document
  maakt in Java‑stijl.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: nl
lastmod: 2026-09-24
og_description: Stel de knoppositie in een Word‑document in met Java. Deze gids laat
  zien hoe je een knop invoegt, een ActiveX‑besturingselement toevoegt en een Word‑document
  maakt met Java en Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Knoppositie instellen in een Word‑document met Java – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Hoe de positie van een knop in een Word‑document instellen met Java
url: /nl/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe de knoppositie in een Word‑document met Java in te stellen

Als je de **knoppositie** in een Word‑bestand moet **instellen**, laat deze gids je een volledige, uitvoerbare oplossing zien. Of je nu een sjabloon bouwt dat gebruikersinteractie vereist of een formulier automatiseert, je leert precies **hoe je een knop invoegt** met Aspose.Words for Java en de plaatsing ervan beheert.

De tutorial behandelt alles wat je nodig hebt om een **ActiveX‑besturingselement toevoegen** aan een Word‑document, legt uit hoe je **een knop aan Word toevoegen** en demonstreert het volledige proces om een **Word‑document in Java** te maken. Er zijn geen externe referenties nodig—kopieer, voer uit en controleer het resultaat.

## Vereisten

* Java 17 (of een Java 8+ runtime) geïnstalleerd.
* Maven of Gradle om afhankelijkheden te beheren.
* Een Aspose.Words for Java‑licentie (de gratis proefversie werkt voor evaluatie).
* Een basisbegrip van Java‑syntaxis.

> **Pro tip:** Houd je Aspose.Words‑JAR‑bestanden in een `libs/`‑map en voeg ze toe aan de classpath van je project om versieconflicten te voorkomen.

## Stap 1: Het Maven‑project opzetten

Maak een eenvoudig Maven‑project (of gebruik Gradle) en voeg de Aspose.Words‑dependency toe:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Het uitvoeren van `mvn clean compile` downloadt de bibliotheek en bereidt het build‑pad voor.

## Stap 2: Een nieuw Word‑document maken

De eerste handeling is om een **Word‑document in Java** te maken. Je maakt een `Document`‑object en een `DocumentBuilder` aan die je in staat stelt het bestand te bewerken.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

De `Document`‑klasse vertegenwoordigt het volledige .docx‑bestand, terwijl `DocumentBuilder` een vloeiende API biedt voor het invoegen van inhoud.

## Stap 3: Hoe een knop in te voegen – ActiveX‑besturingselement toevoegen

Aspose.Words biedt de `Forms2OleControl`‑klasse voor het invoegen van legacy ActiveX‑besturingselementen zoals een CommandButton. Deze stap toont de exacte manier om **een knop in te voegen** in het document.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

De `insertForms2OleControl`‑methode retourneert een `Forms2OleControl`‑instantie die je kunt configureren. Dit is de kern van het **ActiveX‑besturingselement toevoegen** proces.

## Stap 4: Knoppositie instellen

Nu stellen we daadwerkelijk de **knoppositie instellen** in. De `setLeft`‑ en `setTop`‑methoden van het besturingselement accepteren waarden in punten (1 pt = 1/72 in). Om de knop uit te lijnen met typische schermcoördinaten, kun je pixels naar punten converteren (1 px ≈ 0,75 pt). In het voorbeeld plaatsen we de knop 100 px vanaf de linkerrand en 150 px vanaf de bovengrens.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Omdat de **knoppositie instellen**‑logica hier is ingekapseld, kun je deze regels hergebruiken telkens wanneer je een besturingselement moet verplaatsen. Pas de getallen aan om aan je lay‑outvereisten te voldoen.

## Stap 5: Grootte en bijschrift definiëren

Een knop zonder label is verwarrend. Gebruik `setWidth`, `setHeight` en `setCaption` om het een zichtbare weergave te geven.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

De grootte wordt ook uitgedrukt in punten, dus we converteren van pixels voor consistentie.

## Stap 6: Document opslaan – voltooi de workflow voor het maken van een Word‑document in Java

Ten slotte sla je het bestand op schijf op. Het pad kan absoluut zijn of relatief ten opzichte van de project‑root.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Het uitvoeren van het programma genereert `CommandButtonDemo.docx` in de `output`‑map. Het openen van het bestand in Microsoft Word toont een klikbare knop die precies op de door jou ingestelde positie staat.

### Verwachte output

* Een `.docx`‑bestand met de naam **CommandButtonDemo.docx**.
* In het document verschijnt een **CommandButton** met het label “Click Me” 100 px vanaf de linkermarge en 150 px vanaf de bovengrens.
* De knop reageert op klikken wanneer het document in Word wordt geopend (het zal een standaard ActiveX‑bericht weergeven tenzij je aangepaste VBA‑code toevoegt).

## Stap 7: Veelvoorkomende variaties en randgevallen

### Meerdere knoppen toevoegen

Als je **een knop aan Word wilt toevoegen** meer dan één keer, herhaal dan stap 3‑5 met elke keer een nieuwe `Forms2OleControl`‑instantie. Vergeet niet de `setTop`‑waarde aan te passen zodat knoppen elkaar niet overlappen.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Werken zonder licentie

Aspose.Words voegt een watermerk toe wanneer het zonder licentie wordt gebruikt. Voor productiecodel, koop een licentie en pas deze toe aan het begin van `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Compatibiliteit met oudere Office‑versies

ActiveX‑besturingselementen worden ondersteund in het `.doc`‑formaat (Word 97‑2003). Om een legacy‑bestand te maken, wijzig je het opslagformaat:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Volledige broncode (uitvoerbaar)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Sla het bestand op als `src/main/java/CommandButtonDemo.java`, voer `mvn exec:java -Dexec.mainClass=CommandButtonDemo` uit, en open het gegenereerde document om het resultaat te zien.

## Veelgestelde vragen

**Q: Werkt dit met OpenJDK?**  
A: Ja. Aspose.Words is pure Java en draait op elke JDK 8+ implementatie, inclusief OpenJDK.

**Q: Kan ik het lettertype of de kleur van de knop wijzigen?**  
A: Het uiterlijk van een ActiveX‑knop wordt bepaald door de host‑applicatie (Word). Je kunt VBA‑code toevoegen om eigenschappen tijdens runtime te wijzigen, maar het statische uiterlijk is beperkt tot de standaardstijl.

**Q: Wat als ik de knop in een tabelcel moet plaatsen?**  
A: Verplaats de cursor van `DocumentBuilder` naar de cel voordat je `insertForms2OleControl` aanroept. Het besturingselement erft de lay‑out van de cel, en je kunt nog steeds `setLeft`/`setTop` gebruiken voor fijne afstemming.

## Conclusie

Je weet nu hoe je de **knoppositie** in een Word‑document met Java kunt **instellen**, hoe je **een knop kunt invoegen**, hoe je een **ActiveX‑besturingselement toevoegt**, en hoe je **een knop aan Word toevoegt** terwijl je de best practices voor **Word‑documenten maken in Java** projecten volgt. Het volledige voorbeeld demonstreert de volledige workflow—van projectopzet tot een opgeslagen `.docx`‑bestand dat een functionele CommandButton bevat.

### Volgende stappen

* Verken andere `Forms2OleControl.ControlType`‑waarden (bijv. `CHECKBOX`, `TEXTBOX`) om rijkere formulieren te bouwen.
* Combineer de knop met VBA‑macro’s voor aangepaste klikafhandeling.
* Gebruik de mail‑merge‑functie van Aspose.Words om gepersonaliseerde documenten te genereren die al interactieve besturingselementen bevatten.

Veel plezier met coderen, en geniet van het automatiseren van Word‑documenten met Java!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Een Combo‑box formulier‑veld toevoegen aan een Word‑document met Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Hoe Word‑documenten te laden met Aspose.Words Java: uitgebreide gids](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}