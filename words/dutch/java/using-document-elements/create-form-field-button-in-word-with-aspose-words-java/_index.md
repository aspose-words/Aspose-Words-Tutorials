---
category: general
date: 2026-10-13
description: Maak een formulierknop in Word met Aspose.Words voor Java. Leer hoe je
  een opdrachtknop in Word‑formuliervelden invoegt en de bijschrift van de opdrachtknop
  instelt in een paar eenvoudige stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: nl
lastmod: 2026-10-13
og_description: Maak een formulierknop in Word met Aspose.Words voor Java. Deze tutorial
  laat zien hoe je commandoknop‑velden invoegt en de bijschrift van de commandoknop
  snel instelt.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Formulierveldknop maken in Word – Aspose.Words Java-gids
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Formulierveldknop maken in Word met Aspose.Words Java
url: /nl/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formulierveld‑knop maken in Word met Aspose.Words Java

Als je een **formulierveld‑knop** in een Word‑document moet **maken**, leidt deze gids je stap‑voor‑stap door het volledige proces met Aspose.Words voor Java. Of je nu een invul‑formuliersjabloon bouwt of interactieve besturingselementen aan een rapport toevoegt, je leert hoe je **command button word**‑formuliervelden **invoegt** en **de caption van de command button instelt** met minimale code.

De tutorial behandelt alles van Maven‑configuratie tot een volledig uitvoerbaar voorbeeld, zodat je de code kunt kopiëren‑plakken, uitvoeren en een `.docx`‑bestand ziet met een klikbare knop die klaar is voor verdere aanpassing.

## Vereisten

Zorg ervoor dat je het volgende hebt:

- Java 17 (of nieuwer) geïnstalleerd en geconfigureerd op je machine.
- Maven 3.6+ voor afhankelijkheidsbeheer.
- Een IDE of teksteditor naar keuze (bijv. IntelliJ IDEA, VS Code).
- Een geldige Aspose.Words for Java‑licentie (de gratis proefversie werkt voor evaluatie).

## Stap 1: Voeg Aspose.Words toe aan je Maven‑project

Maak een `pom.xml` (of bewerk de bestaande) en voeg de Aspose.Words‑dependency toe:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Pro tip:** Houd het versienummer up‑to‑date. Nieuwe releases voegen ondersteuning toe voor de nieuwste Word‑functies en verbeteren de prestaties.

## Stap 2: Initialise­er een leeg document en een `DocumentBuilder`

De `DocumentBuilder`‑klasse biedt een fluente API voor het bewerken van een Word‑document. In deze stap maken we een leeg `Document` en koppelen we een builder eraan.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Het aanmaken van het document vormt de basis voor het later **maken van formulierveld‑knop**‑objecten in de tutorial.

## Stap 3: Voeg een command button‑formulierveld in

Aspose.Words biedt de `Forms2OleControl`‑klasse voor OLE‑formulierelementen. Om **command button word**‑formuliervelden **in te voegen**, roep je `insertForms2OleControl` aan met de enum‑waarde `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

De methode retourneert een `Forms2OleControl`‑instantie die we kunnen configureren voordat we opslaan.

## Stap 4: Definieer grootte en positie van de knop

Een command button heeft expliciete afmetingen en plaatsing op de pagina nodig. Pas de breedte, hoogte en coördinaten aan zodat ze passen bij je lay‑out.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Het nauwkeurig afstemmen van deze waarden zorgt ervoor dat de knop precies verschijnt waar je wilt in het uiteindelijke document.

## Stap 5: **Caption van de command button instellen**

De zichtbare tekst op de knop wordt geregeld door de `setCaption`‑methode. Hier **stellen we de caption van de command button in** om de gebruiker te begeleiden.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Je kunt `"Click Me"` vervangen door elke label die past bij de bedoeling van je formulier, zoals `"Submit"` of `"Approve"`.

## Stap 6: Sla het document op

Schrijf tenslotte het document naar schijf. Het resulterende bestand bevat de interactieve knop en kan worden geopend in Microsoft Word of LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Het uitvoeren van het programma levert `CommandButtonDemo.docx`. Als je dit in Word opent, zie je een knop met de caption **Click Me** die 50 pt van de linkerkant en 100 pt van de bovenkant van de pagina is gepositioneerd.

### Verwachte output

- Een `.docx`‑bestand met de naam `CommandButtonDemo.docx`.
- Het document bevat één pagina met een command button‑formulierveld.
- De knop toont de caption die je hebt ingesteld (bijv. **Click Me**).

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe aan te passen |
|-----------|-------------------|
| **Meerdere knoppen** | Roep `insertForms2OleControl` herhaaldelijk aan en pas `setLeft`/`setTop` voor elke nieuwe knop aan. |
| **Verschillende caption per knop** | Gebruik `setCaption` met een unieke string na elke invoeging. |
| **Knop in een tabelcel** | Verplaats de cursor naar de gewenste cel met `builder.moveTo(cell.getFirstParagraph())` voordat je het besturingselement invoegt. |
| **Legacy Word‑formaten (.doc)** | Sla op met `doc.save("Demo.doc", SaveFormat.DOC);` – de command button blijft behouden. |
| **Alleen‑lezen formulieren** | Na invoegen, stel `commandButton.setEnabled(false);` in om gebruikersinteractie te voorkomen. |

## Tips voor een robuuste implementatie

- **Afmetingen valideren**: Zeer grote breedtes kunnen ervoor zorgen dat de knop buiten de paginamarge valt.
- **Licentie‑handhaving**: Zonder een geldige licentie voegt Aspose.Words een watermerk toe aan het gegenereerde document. Pas je licentie vroegtijdig toe met `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Testen**: Open het gegenereerde bestand in Word en schakel **Design Mode** in (Developer → Design Mode) om de eigenschappen van de knop te bekijken.

## Volledige broncode‑overzicht

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Kopieer de code naar een bestand met de naam `InsertCommandButtonDemo.java`, compileer met Maven (`mvn compile`) en voer uit (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Het gegenereerde document verschijnt in de hoofdmap van je project.

## Conclusie

Je weet nu hoe je een **formulierveld‑knop** in Word maakt met Aspose.Words voor Java, hoe je **command button word**‑formuliervelden **invoegt**, en hoe je **de caption van de command button instelt** via code. Dit end‑to‑end‑voorbeeld biedt een solide basis voor het bouwen van rijkere, interactieve Word‑documenten—of je nu één enkele verzendknop nodig hebt of een volledige suite aan formulierelementen.

### Wat is de volgende stap?

- Verken andere formulierelementen zoals selectievakjes (`Forms2OleControlType.CHECKBOX`) en tekstvakken (`Forms2OleControlType.TEXTBOX`).
- Combineer formuliervelden met mail‑merge om gepersonaliseerde vragenlijsten te genereren.
- Gebruik de Aspose.Words `FormField`‑API om door de gebruiker ingevoerde gegevens te lezen nadat het document is ingevuld.

Voel je vrij om te experimenteren met verschillende groottes, captions en plaatsingen. Zodra je command buttons onder de knie hebt, wordt het toevoegen van volledige formulieren aan je Word‑automatiseringspijplijnen een eenvoudige taak. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formuliervelden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Een Combo Box‑formulierveld toevoegen aan een Word‑document met Aspose.Words voor .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Een Check Box‑formulierveld toevoegen aan een Word‑document met Aspose.Words voor .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}