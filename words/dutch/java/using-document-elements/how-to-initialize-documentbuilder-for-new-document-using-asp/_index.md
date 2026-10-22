---
category: general
date: 2026-10-04
description: Leer hoe u DocumentBuilder initialiseert voor een nieuw document en een
  ActiveX‑knop toevoegt met Aspose.Words in Java. Stapsgewijze handleiding met volledige
  code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: nl
lastmod: 2026-10-04
og_description: Initialiseer DocumentBuilder voor een nieuw document en voeg een ActiveX‑opdrachtknop
  in met behulp van de Aspose.Words Java API. Volg deze beknopte tutorial.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: DocumentBuilder initialiseren voor een nieuw document – volledige Aspose.Words-gids
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Hoe DocumentBuilder initialiseren voor een nieuw document met Aspose.Words
url: /nl/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe DocumentBuilder te initialiseren voor een nieuw document met Aspose.Words

Als je **DocumentBuilder voor een nieuw document** moet initialiseren in een Java‑project, laat deze tutorial je de exacte stappen zien. Je ziet hoe je een leeg Word‑bestand maakt, een ActiveX‑opdrachtknop toevoegt en het resultaat opslaat — alles met één zelf‑containende code‑voorbeeld.

Werken met Word‑documenten via code betekent vaak dat je low‑level details moet afhandelen, zoals formulierelementen. Aan het einde van deze gids kun je een ActiveX‑knop insluiten zonder je IDE te verlaten, wat handig is voor het genereren van sjablonen, geautomatiseerde rapporten of interactieve formulieren.

## Vereisten

Zorg ervoor dat je het volgende hebt:

* Java 17 of hoger geïnstalleerd  
* Maven 3.8+ (of Gradle als je dat liever gebruikt)  
* Een Aspose.Words for Java‑licentie (de gratis proefversie werkt voor testen)  
* Basiskennis van Java‑syntaxis  

Als je nieuw bent met Aspose.Words, biedt de bibliotheek een high‑level API voor het maken, bewerken en opslaan van Word‑documenten. De `DocumentBuilder`‑klasse is het primaire toegangspunt voor het opbouwen van documentinhoud.

## Stap 1: Het Maven‑project opzetten

Maak een nieuw Maven‑project (of voeg toe aan een bestaand project) en voeg de Aspose.Words‑dependency toe:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Houd de bibliotheekversie up‑to‑date; nieuwere releases voegen ondersteuning toe voor extra formulierelementen en verbeteren de prestaties.

## Stap 2: `DocumentBuilder` initialiseren voor nieuw document

De kern van de tutorial is de **initialize DocumentBuilder for new document**‑operatie. Je maakt eerst een lege `Document`‑instantie, en geeft die vervolgens door aan de `DocumentBuilder`‑constructor.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is:* Het initialiseren van `DocumentBuilder` koppelt de builder aan een specifiek `Document`‑object, zodat je alinea’s, tabellen of formulierelementen direct aan dat document kunt toevoegen. Zonder deze stap zou de builder geen doel hebben om op te werken.

## Stap 3: Een ActiveX‑opdrachtknop invoegen

Aspose.Words biedt de `Forms2OleControl`‑klasse om legacy ActiveX‑besturingselementen in te sluiten. De volgende code voegt een **Forms2OleControl‑opdrachtknop** toe op de huidige cursorpositie.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Wat is een ActiveX‑opdrachtknop?

Een ActiveX‑opdrachtknop is een legacy UI‑element dat macro’s kan uitvoeren of gebeurtenissen kan activeren wanneer een gebruiker erop klikt binnen een Word‑document. Hoewel moderne Office‑versies de voorkeur geven aan Content Controls, vertrouwen veel enterprise‑sjablonen nog steeds op ActiveX voor achterwaartse compatibiliteit.

## Stap 4: Het document opslaan

Na het invoegen van het besturingselement roep je simpelweg `save` aan. Het bestand zal de ActiveX‑knop bevatten en kan worden geopend in Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Wanneer je `ActiveXButton.docx` in Word opent, zie je een knop met de tekst **Click Me**. Klikken op de knop doet niets tenzij je een macro koppelt, maar het besturingselement zelf is volledig functioneel.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het complete programma dat je kunt kopiëren‑plakken naar `src/main/java/com/example/ActiveXButtonDemo.java`. Het bevat alle imports en foutafhandeling die nodig zijn voor een snelle test.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Verwachte output**

```
Document saved to output/ActiveXButton.docx
```

Open het gegenereerde bestand in Microsoft Word 2016 of later; je zou een knop met de tekst *Click Me* bovenaan de eerste pagina moeten zien.

## Veelvoorkomende variaties en randgevallen

| Scenario | Aanpassing |
|----------|------------|
| **De knop toevoegen aan een specifieke alinea** | Verplaats de cursor van de builder met `builder.moveToParagraph(index, NodeType.PARAGRAPH);` voordat je `insertForms2OleControl` aanroept. |
| **Knopgrootte instellen** | Gebruik `commandButton.setWidth(100);` en `commandButton.setHeight(30);` om de afmetingen in punten te definiëren. |
| **Een macro aan de knop toevoegen** | Sla het document op, open het in Word, schakel het tabblad Ontwikkelaar in en koppel handmatig een VBA‑macro aan de knop (ActiveX‑besturingselementen kunnen niet direct vanuit Aspose.Words worden gescript). |
| **Doel .doc (binair) formaat** | Verander `doc.save(outputPath, SaveFormat.DOC);` om een legacy Word 97‑2003‑bestand te produceren. |
| **Uitvoeren op Android** | Gebruik Aspose.Words for Android via de Java‑API; dezelfde code werkt zolang de bibliotheek in de APK is opgenomen. |

## Tips voor probleemoplossing

* **`java.lang.NoClassDefFoundError`** – Zorg ervoor dat de Aspose.Words‑JAR op het classpath staat. Maven voegt deze automatisch toe; bij handmatige builds plaats je de JAR in `libs/` en voeg je deze toe aan de bibliotheken van je IDE.  
* **Knop verschijnt niet in Word** – Controleer of de optie *Show legacy forms* is ingeschakeld in het Trust Center van Word (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **Licentie‑exception** – Als je de code zonder geldige licentie uitvoert, voegt Aspose.Words een watermerk toe. Registreer een gratis proefversie of koop een licentie om dit te verwijderen.

## Conclusie

Je weet nu hoe je **initialize DocumentBuilder for new document**, een ActiveX‑opdrachtknop kunt invoegen en het resultaat kunt opslaan met Aspose.Words for Java. Dit patroon stelt je in staat om interactief Word‑sjablonen programmatisch te genereren, wat vooral handig is voor geautomatiseerde rapportage of formulier‑gedreven workflows.

Vanaf hier kun je extra formulierelementen verkennen (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, enz.), de knop combineren met aangepaste VBA‑macro’s, of volledige documenten genereren met tabellen, afbeeldingen en opmaak — alles met dezelfde `DocumentBuilder`‑workflow.

---

*Klaar om complexere Word‑automatisering te bouwen? Bekijk onze handleidingen over **insert table with DocumentBuilder**, **apply styles programmatically**, en **export to PDF with Aspose.Words**.*

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Add a watermark to a document using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}