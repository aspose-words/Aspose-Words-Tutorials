---
category: general
date: 2026-08-23
description: Leer hoe u een opdrachtknop in een Word‑document kunt invoegen met Java
  en Aspose.Words. Deze gids laat zien hoe u een formulierbesturingselement toevoegt,
  de knopnaam instelt en een ActiveX‑knop insluit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: nl
lastmod: 2026-08-23
og_description: Voeg een opdrachtknop toe in een Word‑document met Java. Volg deze
  gids om een formulierbesturingselement toe te voegen, de knopnaam in te stellen
  en een ActiveX‑knop in te sluiten met Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Opdrachtknop invoegen in Word met Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Hoe een opdrachtknop in een Word‑document in te voegen met Java
url: /nl/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een commandoknop in een Word‑document invoegen met Java

Als je een **command button** in een Word‑bestand moet invoegen, toont deze tutorial een volledige oplossing met Aspose.Words for Java. Je ziet hoe je een form control toevoegt, de bijschrift configureert en de knopnaam instelt zonder je IDE te verlaten.

De gids behandelt alles wat je nodig hebt om een `.docx` te maken die een ActiveX‑knop bevat, klaar voor gebruik in Microsoft Word. Er is geen extra tooling vereist, en het voorbeeld draait op Java 8+.

## Wat je zult leren

* Hoe een form control van het type **CommandButton** aan een Word‑document toe te voegen.  
* De exacte stappen om **set button name** en **add activex button** eigenschappen toe te voegen.  
* Hoe het document op te slaan zodat de knop correct wordt weergegeven wanneer het in Word wordt geopend.  

Je moet een basis Java‑ontwikkelomgeving hebben en een Maven‑ of Gradle‑project dat de Aspose.Words‑bibliotheek kan importeren.

## Vereisten

| Vereiste | Reden |
|-------------|--------|
| Java 8 of nieuwer | Aspose.Words for Java draait op Java 8+. |
| Maven‑ of Gradle‑buildtool | Vereenvoudigt het toevoegen van de Aspose.Words‑dependency. |
| Aspose.Words for Java-licentie (of gratis proefversie) | Vereist voor de volledige functionaliteit; de API werkt in evaluatiemodus. |
| Een IDE zoals IntelliJ IDEA of Eclipse | Maakt het bewerken en uitvoeren van het voorbeeld gemakkelijker. |

## Stap 1: Voeg Aspose.Words toe aan je project

Voor Maven, voeg de volgende dependency toe aan `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Voor Gradle, plaats deze regel in `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Nadat de dependency is opgehaald, kun je de bibliotheekklassen importeren in je Java‑bronbestand.

## Stap 2: Commandoknop invoegen – de kerncode

Maak een nieuwe Java‑klasse genaamd `InsertCommandButtonDemo`. De onderstaande code voert alle vier acties uit die nodig zijn om een **command button** in te voegen:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Waarom elke regel belangrijk is

* **Document & DocumentBuilder** – Ze bieden de in‑memory representatie van een Word‑bestand en de API om de inhoud te wijzigen.  
* **insertForms2OleControl** – Deze methode **voegt form control toe** van het type `COMMAND_BUTTON`. Het geretourneerde `Forms2OleControl`‑object vertegenwoordigt de ActiveX‑control.  
* **setName** – Wijs een programmatische identifier toe (`btnSubmit`). Word‑macro's of VBA kunnen later naar deze naam verwijzen.  
* **setCaption** – Definieert de tekst die de gebruiker op de knop ziet, waarmee de vraag “hoe voeg je een knop toe” wordt beantwoord.  
* **save** – Schrijft de `.docx` naar schijf, waarbij de ingebedde ActiveX‑knop behouden blijft.  

Het uitvoeren van het programma maakt `CommandButtonDemo.docx` aan in de werkmap. Het openen van het bestand in Microsoft Word toont een knop met het label **Submit** die je kunt klikken (er wordt een standaard ActiveX‑dialoog weergegeven in evaluatiemodus).

## Stap 3: Controleer de ingevoegde knop in Word

1. Open `CommandButtonDemo.docx` met Microsoft Word (2016 of later).  
2. De **Submit**‑knop verschijnt op de plaats waar de cursor tijdens het invoegen stond.  
3. Klik met de rechtermuisknop op de knop en kies **Properties** om te zien dat het **Name**‑veld `btnSubmit` bevat.  

Als de knop niet verschijnt, zorg er dan voor dat **ActiveX‑controls** zijn ingeschakeld in de Trust Center‑instellingen van Word.

## Stap 4: De knop aanpassen (optioneel)

Je kunt de knop verder aanpassen door de grootte, positie aan te passen of een VBA‑macro toe te voegen. De `Forms2OleControl`‑klasse biedt extra eigenschappen zoals `setWidth`, `setHeight` en `setLeft`. Hieronder staat een voorbeeld dat de knop groter maakt:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Deze regels kunnen na de `setCaption`‑aanroep worden geplaatst. Ze demonstreren **add activex button**‑aanpassing buiten de basisinvoeging.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Symptoom | Oorzaak | Oplossing |
|---------|-------|-----|
| Knop verschijnt niet in Word | Document opgeslagen voordat de control werd toegevoegd | Zorg ervoor dat `insertForms2OleControl` wordt aangeroepen vóór `doc.save`. |
| Knopbijschrift is leeg | `setCaption` niet aangeroepen of aangeroepen met een lege string | Geef een niet‑lege string op, bijv. `"Submit"`. |
| VBA kan de knop niet vinden | Naamverschil tussen VBA‑code en `setName`‑waarde | Houd de naam consistent; gebruik `setName("btnSubmit")` en verwijs naar `btnSubmit` in VBA. |
| Beveiligingswaarschuwing bij openen van het bestand | De macro‑beveiliging van Word blokkeert ActiveX‑controls | Pas Trust Center > Macro‑instellingen aan, of onderteken het document met een vertrouwd certificaat. |

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige bronbestand, klaar om te kopiëren en plakken in je IDE. Het bevat de import‑statements, foutafhandeling en een commentaarblok dat elke belangrijke stap uitlegt.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Verwacht resultaat:** Na het uitvoeren van het programma bevat `CommandButtonDemo.docx` een enkele **Submit**‑knop. Het openen van het bestand in Word toont de knop precies op de plek waar de `DocumentBuilder`‑cursor zich bevond.

## Volgende stappen

* **Voeg meer form controls toe** – Gebruik `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` of `TEXT_BOX` om volledige Word‑formulieren te bouwen.  
* **Combineer met mail‑merge** – Voeg knoppen in een mail‑merged document in om gepersonaliseerde interactieve formulieren te maken.  
* **Voeg VBA‑macro's toe** – Programmeer VBA in die reageert op het `Click`‑event van de knop voor geavanceerde automatisering.  

Deze onderwerpen breiden de **add form control**‑techniek die je zojuist hebt beheerst, natuurlijk uit.

---

### Samenvatting

Je weet nu hoe je een **command button** in een Word‑document kunt **invoegen** met Java, hoe je **form control** kunt **toevoegen**, hoe je **button name** kunt **instellen**, en hoe je **add activex button**‑aanpassingen kunt doen. Het volledige voorbeeld werkt direct, en je kunt het aanpassen aan elke document‑generatie‑workflow. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formuliervelden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Combo‑box formveld invoegen in Word‑document](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Selectievakje formveld invoegen in Word‑document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}