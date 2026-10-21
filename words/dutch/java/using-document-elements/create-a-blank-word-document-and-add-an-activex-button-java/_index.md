---
category: general
date: 2026-10-16
description: Maak een leeg Word‑document met Java en leer hoe je een ActiveX‑knop
  toevoegt, de bijschrift instelt en de afmetingen aanpast met Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: nl
lastmod: 2026-10-16
og_description: Maak een leeg Word‑document met Java, voeg vervolgens een ActiveX‑knop
  toe, stel het bijschrift in en definieer de afmetingen met Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Maak een leeg Word‑document en voeg een ActiveX‑knop in – Java‑gids
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Maak een leeg Word‑document en voeg een ActiveX‑knop toe (Java)
url: /nl/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document en voeg een ActiveX‑knop toe (Java)

Als je **programmatically een leeg Word‑document wilt maken**, laat deze gids je zien hoe je dat doet met Java en Aspose.Words. Je leert ook hoe je een **ActiveX‑knop kunt toevoegen**, **de knopbijschrift kunt instellen** en **de afmetingen van de knop kunt bepalen**, zodat de besturingselement er precies uitziet zoals je verwacht.

Deze tutorial behandelt:

* Een leeg Word‑bestand initialiseren met Aspose.Words for Java.  
* Een ActiveX `CommandButton`‑besturingselement invoegen.  
* Het bijschrift en de grootte van de knop configureren.  
* Het uiteindelijke `.docx`‑bestand opslaan.

Je moet basiskennis van Java hebben en een recente versie van de Aspose.Words for Java‑bibliotheek (de code werkt met 23.9 en later). Geen extra afhankelijkheden zijn vereist.

![Maak een leeg Word‑document met een ActiveX‑knop](/images/activex-button-example.png){: .align-center alt="Maak een leeg Word‑document met een ActiveX‑knop"}

## Maak een leeg Word‑document met Aspose.Words

De eerste stap is het instantieren van een leeg `Document`‑object. Dit object vertegenwoordigt het volledige Word‑bestand in het geheugen en biedt de `DocumentBuilder`‑klasse voor bewerking.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Waarom dit belangrijk is:**  
Het maken van een leeg document geeft je een schoon canvas, waardoor verborgen stijlen of secties die later de lay-outberekeningen kunnen verstoren, worden vermeden.

## Voeg een ActiveX‑knop toe aan het document

Aspose.Words stelt je in staat legacy ActiveX‑besturingselementen in te sluiten via de `Forms2OleControl`‑klasse. De onderstaande code voegt een `CommandButton`‑besturingselement in op de huidige cursorpositie.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Tip:** De `setOleClassName`‑waarde `"Forms.CommandButton.1"` is de ProgID voor de standaard Microsoft Forms‑knop. Het gebruiken van een andere ProgID (bijv. `"Forms.CheckBox.1"`) zou een ander type besturingselement invoegen.

## Stel het knopbijschrift in

Een bijschrift is de tekst die op het knopoppervlak verschijnt. Je kunt het op elk moment vóór het opslaan van het document wijzigen.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Waarom je dit nodig hebt:** Gebruikers begrijpen een besturingselement alleen wanneer het doel duidelijk is. Het instellen van een betekenisvol bijschrift verbetert de bruikbaarheid, vooral wanneer het document in Word op Windows wordt geopend.

## Stel de afmetingen van de knop in

Positie en grootte worden gespecificeerd in points (1 point = 1/72 inch). Pas de waarden aan om ze in je lay-out te laten passen.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Veelvoorkomende variaties:**

| Scenario | Aanpassing |
|----------|------------|
| Grotere knop voor touch‑schermen | Verhoog `setWidth` en `setHeight` evenredig |
| Gecentreerde knop op de pagina | Bereken `left = (pageWidth - width) / 2` |
| Meerdere knoppen in een kolom | Verhoog `setTop` voor elke nieuwe knop |

## Sla het document met de ActiveX‑knop op

Schrijf tenslotte het document naar schijf. Het `.docx`‑formaat behoudt het ActiveX‑besturingselement voor Windows‑versies van Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Verwacht resultaat:** Het openen van `ActiveXCommandButton.docx` in Word (Windows) toont een lege pagina met een klikbare knop gelabeld **Click Me** die 100 pt van de linkermarge en 200 pt van de bovenmarge is gepositioneerd.

## Volledig, uitvoerbaar voorbeeld

Kopieer de volledige klasse hieronder naar je IDE, voeg de Aspose.Words for Java‑JAR toe aan het project‑classpath, en voer het uit.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Het uitvoeren van het programma genereert `ActiveXCommandButton.docx` in de werkmap. Open het met Microsoft Word (Windows) om te verifiëren dat de knop precies verschijnt zoals geconfigureerd.

## Waarom deze aanpak wordt aanbevolen

* **Eenvoud:** Alleen de kern‑Aspose.Words‑API wordt gebruikt; geen COM‑interop of extra bibliotheken zijn vereist.  
* **Portabiliteit:** De code draait op elk platform dat Java ondersteunt, hoewel het ActiveX‑besturingselement zelf alleen werkt op Windows‑versies van Word.  
* **Onderhoudbaarheid:** Alle eigenschappen (bijschrift, afmetingen, positie) worden ingesteld via duidelijke, zelf‑documenterende methoden, waardoor toekomstige aanpassingen eenvoudig zijn.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Valkuil | Oplossing |
|---------|------------|
| De knop verschijnt niet in Word op macOS of Linux | ActiveX‑besturingselementen zijn alleen voor Windows. Gebruik een ander besturingselement (bijv. een content‑control) voor cross‑platform documenten. |
| Bijschrift wordt afgekapt | Zorg dat de knopbreedte breed genoeg is voor de tekst; vergroot `setWidth` of gebruik een korter bijschrift. |
| Knop overlapt andere inhoud | Pas de waarden van `setTop` en `setLeft` aan, of voeg een nieuwe alinea in vóór het besturingselement om het zijn eigen ruimte te geven. |

## Volgende stappen

Nu je **een leeg Word‑document kunt maken**, **een ActiveX‑knop kunt toevoegen**, **het knopbijschrift kunt instellen**, en **de afmetingen van de knop kunt bepalen**, kun je het volgende verkennen:

* Event‑afhandelingscode toevoegen via VBA‑macro's (vereist het insluiten van een macro‑module).  
* Meerdere besturingselementen invoegen in een tabelindeling voor formulier‑achtige documenten.  
* De **FormField**‑API's van Aspose.Words gebruiken voor cross‑platform formulieroplossingen.

Experimenteer met verschillende groottes, posities en bijschriften om ze aan te passen aan je specifieke documentontwerp. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Word‑document maken Java – Rechthoekvorm toevoegen met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Een watermerk toevoegen aan een document met Aspose.Words voor Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}