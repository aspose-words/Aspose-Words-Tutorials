---
category: general
date: 2026-11-15
description: Bewerk een Word-document programmatically om een opdrachtknop in te voegen.
  Leer hoe je een knop toevoegt, de naam van de opdrachtknop instelt en in enkele
  minuten een formulierknop in Word maakt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: nl
lastmod: 2026-11-15
og_description: Bewerk een Word‑document programmatically en voeg een opdrachtknop
  toe. Deze gids laat zien hoe je een knop toevoegt, de naam van de opdrachtknop instelt
  en snel een formulierknop in Word maakt.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Bewerk Word-document programmatisch – voeg een opdrachtknop toe
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Bewerk Word-document programmatisch en voeg een opdrachtknop toe
url: /nl/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-document programmatically bewerken en een opdrachtknop toevoegen

Als je **Word-document programmatically wilt bewerken**, is de snelste manier om de Aspose.Words API te gebruiken. Deze tutorial laat je precies zien **hoe je knop**‑besturingselementen toevoegt, hun bijschrift configureert, en **de naam van de opdrachtknop instelt** zodat het document kan fungeren als een eenvoudig formulier. Aan het einde heb je een volledig bewerkbaar *.docx* dat een functionele opdrachtknop bevat, klaar voor verdere verwerking.

Je leert hoe je **command button word invoegt**, **form button word maakt**, en knop‑eigenschappen beheert zonder Word handmatig te openen. Het enige vereiste is een basis Java‑ontwikkelomgeving en de Aspose.Words for Java‑bibliotheek.

## Prerequisites

- Java 17 of hoger (de code werkt ook met Java 8+)
- Aspose.Words for Java (download van [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Een bestaand Word‑document (`input.docx`) dat je wilt aanpassen
- Bekendheid met Maven of Gradle om de Aspose.Words‑dependency toe te voegen

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Stap 1: Het Word‑document laden

De eerste handeling wanneer je **Word-document programmatically bewerkt** is het laden van het bronbestand in een `Document`‑object. Dit object vertegenwoordigt het volledige Word‑bestand in het geheugen, waardoor je de inhoud kunt manipuleren.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Waarom dit belangrijk is:** Het laden van het document creëert een DOM‑achtige structuur die Aspose.Words kan doorlopen en aanpassen. Als je deze stap overslaat, heb je geen doelwit meer voor het invoegen van de knop.

## Stap 2: Een `DocumentBuilder` maken om het document te bewerken

Een `DocumentBuilder` werkt als een cursor binnen het Word‑bestand. Het stelt je in staat om tekst, afbeeldingen en formulierbesturingselementen in te voegen op de huidige positie.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tip:** Als je de knop in een specifieke alinea nodig hebt, verplaats je de builder eerst met `builder.moveToParagraph(index, true);`.

## Stap 3: Een Forms2OleControl invoegen (opdrachtknop)

Nu beantwoorden we de centrale vraag **hoe je knop toevoegt** in een Word‑bestand. De methode `insertForms2OleControl()` maakt een legacy *Forms2.0* opdrachtknop, die het meest compatibel is met verschillende Word‑versies.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Randgeval:** Het Forms2.0‑element is alleen zichtbaar in de *Ontwerpmodus* van Word. Als je een nieuwere ActiveX‑knop nodig hebt, overweeg dan `insertOleControl()`; maar het legacy‑element werkt voor de meeste automatiseringsscenario's.

## Stap 4: De eigenschappen van de knop configureren

Na het invoegen van het element kun je **de naam van de opdrachtknop instellen** en **command button word invoegen** (bijschrift) om het gebruiksvriendelijk te maken.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Waarom deze eigenschappen?**  
> - `setName` geeft de knop een identifier die VBA of externe tools kunnen gebruiken.  
> - `setCaption` is het zichtbare label, effectief **form button word creëren** dat eindgebruikers aanklikken.

Je kunt ook de grootte, positie aanpassen of een macro toevoegen door toegang te krijgen tot het onderliggende OLE‑object, maar die onderwerpen vallen buiten de reikwijdte van deze korte gids.

## Stap 5: Het gewijzigde document opslaan

Tot slot sla je de wijzigingen op in een nieuw bestand. Deze stap **creëert form button word** in het uitvoerdocument.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Resultaat:** Bij het openen van `output.docx` in Microsoft Word zie je een knop met het label “Submit”. Wanneer je Word naar de *Ontwerpmodus* schakelt (Ontwikkelaar → Ontwerpmodus), kun je dubbelklikken op de knop om een macro toe te voegen of deze simpelweg als tijdelijke aanduiding in een formulier te gebruiken.

### Verwachte output

- Het cursor‑invoegpunt wordt vervangen door een knop.
- De knop toont het bijschrift **Submit**.
- De interne naam van de knop is **cmdSubmit**, die je kunt gebruiken in VBA of externe automatiseringsscripts.

## Veelgestelde vragen en variaties

### Hoe voeg je een knop toe aan een specifieke alinea?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Hoe een knop invoegen in een tabelcel?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Wat als ik een grotere knop nodig heb?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Hoe **command button word invoegen** met een andere taal (bijv. C#)?

Dezelfde logica geldt; vervang Java‑syntaxis door C#‑equivalenten:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Pro‑tips en valkuilen

- **Pro tip:** Roep altijd `builder.moveToDocumentEnd()` aan voordat je een knop invoegt als je deze helemaal aan het einde van het document wilt plaatsen.  
- **Let op:** Het opslaan naar hetzelfde bestand dat je hebt geopend kan het document beschadigen als er een uitzondering optreedt. Gebruik een apart uitvoerpad zoals getoond.  
- **Compatibiliteit:** De legacy Forms2.0‑knop werkt in Word 2007‑2021. Voor Word op het web, overweeg in plaats daarvan content‑controls te gebruiken.  
- **Prestaties:** Het laden van zeer grote documenten (>100 MB) kan veel geheugen verbruiken. Gebruik `Document.load(InputStream, LoadOptions)` met `LoadOptions.setLoadFormat(LoadFormat.DOCX)` om het resource‑gebruik te beperken.

## Volledig werkend voorbeeld

Hieronder staat het volledige, kant‑klaar Java‑programma. Kopieer het naar een klasse genaamd `WordButtonDemo.java`, pas de bestands‑paden aan en voer `mvn compile exec:java` uit.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Voer het programma uit en open `output.docx` om te verifiëren dat de knop verschijnt zoals verwacht.

## Conclusie

Je weet nu hoe je **Word-document programmatically kunt bewerken** om **command button word in te voegen**, **form button word te creëren**, en **de naam van de opdrachtknop in te stellen** met Aspose.Words for Java. Deze aanpak elimineert handmatig bewerken, maakt batchverwerking van formulieren mogelijk en integreert naadloos met geautomatiseerde workflows.

Vervolgens kun je verkennen:

- VBA‑macros toevoegen aan de knop (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- **Content controls** gebruiken voor rijkere formulierervaringen (`builder.insertCheckBox()` enz.)  
- Bulk‑invoeging automatiseren over meerdere documenten met een lus  

Voel je vrij om te experimenteren met de grootte, positie en gebeurtenisafhandeling van de knop om aan jouw specifieke scenario te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een opdrachtknop programmatically toevoegen in een Word‑document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Word‑document programmatically maken en ActiveX‑knop toevoegen](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Opdrachtknop toevoegen aan Word‑document met Aspose.Words – Complete gids](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}