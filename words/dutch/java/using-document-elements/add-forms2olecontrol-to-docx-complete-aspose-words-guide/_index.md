---
category: general
date: 2026-07-23
description: Leer hoe u Forms2OleControl aan een DOCX kunt toevoegen met Aspose.Words.
  Deze stapsgewijze handleiding laat zien hoe u een ActiveX CommandButton‑besturingselement
  in Java invoegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add forms2olecontrol to docx
- insert ActiveX control in DOCX
- Aspose.Words Forms2OleControl example
- embed CommandButton in Word document
- Java DocumentBuilder ActiveX
language: nl
lastmod: 2026-07-23
og_description: Voeg Forms2OleControl direct toe aan DOCX. Volg deze praktische gids
  om een ActiveX CommandButton in te sluiten met Aspose.Words voor Java.
og_image_alt: Screenshot of Java code that adds Forms2OleControl to DOCX using Aspose.Words
og_title: Forms2OleControl toevoegen aan DOCX – Volledige Aspose.Words‑handleiding
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  headline: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  name: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  steps:
  - name: Using a Different ActiveX Control
    text: 'If you want a checkbox instead of a button, just change the control type:'
  - name: Embedding Multiple Controls
    text: Call `builder.insertForms2OleControl()` multiple times, moving the cursor
      with `builder.moveTo()` or inserting text between calls. Each call adds a new
      OLE container, so you can build complex forms inside a single DOCX.
  - name: Working with .NET
    text: The same logic applies to C#—the method names are identical (`DocumentBuilder.InsertForms2OleControl()`).
      If you’re on .NET, replace the Java syntax with its C# counterpart, but the
      **embed CommandButton in Word document** concept stays unchanged.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Java
- DOCX
title: Forms2OleControl toevoegen aan DOCX – Complete Aspose.Words-gids
url: /nl/java/using-document-elements/add-forms2olecontrol-to-docx-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Forms2OleControl toevoegen aan DOCX – Complete Aspose.Words-gids

Heb je je ooit afgevraagd hoe je **Forms2OleControl aan DOCX kunt toevoegen** zonder je haar uit te trekken? Je bent niet de enige. Of je nu een sjabloon‑gedreven rapport bouwt of een klikbare knop in een Word‑bestand nodig hebt, het insluiten van een ActiveX‑besturingselement is het geheime ingrediënt.

In deze tutorial lopen we een concreet voorbeeld door dat **Forms2OleControl aan DOCX toevoegt** met Aspose.Words for Java. Je ziet de volledige code, begrijpt waarom elke regel belangrijk is, en krijgt tips voor het omgaan met de eigenaardigheden die ontwikkelaars vaak tegenkomen.

## Wat je zult leren

- Hoe je Aspose.Words instelt in een Java‑project  
- De exacte stappen om **een ActiveX‑besturingselement in DOCX in te voegen** (ja, het primaire trefwoord nogmaals)  
- Het configureren van de eigenschappen van een CommandButton zodat deze zich gedraagt als een echt UI‑element  
- Het opslaan van het document en verifiëren dat het besturingselement daadwerkelijk is ingesloten  

Ervaring met ActiveX is niet vereist, maar een basisbegrip van Java en Maven/Gradle maakt de reis soepeler. Klaar? Laten we erin duiken.

## Stap 1: Aspose.Words instellen in je project

Voordat je **Forms2OleControl aan DOCX kunt toevoegen**, heb je de Aspose.Words‑bibliotheek op het classpath nodig. De gemakkelijkste manier is via Maven:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Als je Gradle gebruikt, is het equivalent `implementation 'com.aspose:aspose-words:24.9'`.

Waarom dit belangrijk is: Aspose.Words biedt de `DocumentBuilder.insertForms2OleControl()`‑methode die we zullen gebruiken om **een ActiveX‑besturingselement in DOCX in te voegen**. Zonder de bibliotheek zou de compiler geen idee hebben wat een `Forms2OleControl` is.

## Stap 2: Forms2OleControl toevoegen aan DOCX

Nu volgt de kern van de tutorial—hier **voegen we Forms2OleControl aan DOCX toe**. We maken een nieuw document, starten een `DocumentBuilder` en roepen de invoegmethode aan.

```java
import com.aspose.words.*;

public class ActiveXExample {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2.2: Insert an ActiveX Forms2OleControl (CommandButton)
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Step 2.3: Configure the CommandButton properties
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setName("MyButton");
        commandButton.setCaption("Click Me");

        // Step 2.4: Save the document with the embedded control
        String outPath = "output/ActiveXButton.docx";
        document.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**What’s happening here?**  

- `new Document()` geeft ons een schoon canvas. Beschouw het als een vers vel papier klaar voor **een ActiveX‑besturingselement in DOCX in te voegen**.  
- `builder.insertForms2OleControl()` maakt de low‑level OLE‑container die Aspose.Words *Forms2OleControl* noemt. Dit is de enige API‑aanroep die daadwerkelijk **Forms2OleControl aan DOCX toevoegt**.  
- Het instellen van `OleControlType.COMMANDBUTTON` vertelt Word dat het OLE‑object zich moet gedragen als een klassieke CommandButton—exact hetzelfde als de knop die je in de UI‑designer op een formulier zou plaatsen.  
- Ten slotte schrijft `document.save(...)` het .docx‑bestand weg, waardoor de ingesloten ActiveX wordt bewaard.

## Stap 3: De eigenschappen van de CommandButton configureren (Waarom het belangrijk is)

Alleen het invoegen van het besturingselement geeft je een lege tijdelijke aanduiding. Om het bruikbaar te maken, moet je een paar eigenschappen instellen:

| Eigenschap | Doel | Typische waarde |
|------------|------|-----------------|
| `setOleControlType` | Definieert het type ActiveX‑besturingselement (Button, CheckBox, etc.) | `OleControlType.COMMANDBUTTON` |
| `setName` | Interne identifier die door Word‑macro's of VBA‑scripts wordt gebruikt | `"MyButton"` |
| `setCaption` | De tekst die op het knopoppervlak wordt weergegeven | `"Click Me"` |

Als je deze overslaat, verschijnt de knop met een generieke naam en zonder label—niets wat een gebruiker zou klikken. Vergeet ook niet dat ActiveX‑besturingselementen **platform‑specifiek** zijn; ze werken alleen op Windows‑machines met de juiste COM‑bibliotheken geïnstalleerd.

> **Let op:** Wanneer je het gegenereerde DOCX opent op een niet‑Windows platform (bijv. macOS), zal Word een tijdelijke afbeelding tonen in plaats van een echte knop. Dit is een normale beperking van ActiveX, geen bug in je code.

## Stap 4: Het document opslaan en verifiëren

De aanroep `document.save(...)` schrijft een standaard DOCX‑bestand dat elke moderne versie van Microsoft Word kan openen. Na het uitvoeren van het programma, open `ActiveXButton.docx`:

1. Zoek de “Click Me”‑knop op de plek waar je deze hebt ingevoegd.  
2. Klik met de rechtermuisknop op de knop → **Properties** om de naam en caption te bevestigen.  
3. Klik op de knop; Word toont een eenvoudig berichtvenster als je een macro hebt gekoppeld (buiten de reikwijdte van deze gids).

Als de knop ontbreekt, controleer dan dubbel of je het **Aspose.Words Forms2OleControl‑voorbeeld** correct hebt gebruikt en of de output‑map bestaat.

> **Randgeval:** Als je wilt dat de knop een macro activeert, moet je VBA‑code aan het document toevoegen nadat het is opgeslagen. Aspose.Words kan VBA injecteren via de `Document.getBuiltInDocumentProperties()`‑API, maar dat is een eigen tutorial.

## Veelvoorkomende variaties & valkuilen

### Een ander ActiveX‑besturingselement gebruiken

Als je een checkbox in plaats van een knop wilt, wijzig dan simpelweg het besturingselementtype:

```java
commandButton.setOleControlType(OleControlType.CHECKBOX);
commandButton.setCaption("Accept Terms");
```

### Meerdere besturingselementen insluiten

Roep `builder.insertForms2OleControl()` meerdere keren aan, verplaats de cursor met `builder.moveTo()` of voeg tekst in tussen de aanroepen. Elke aanroep voegt een nieuwe OLE‑container toe, zodat je complexe formulieren kunt bouwen binnen één DOCX.

### Werken met .NET

Dezelfde logica geldt voor C#—de methodenamen zijn identiek (`DocumentBuilder.InsertForms2OleControl()`). Als je op .NET werkt, vervang je de Java‑syntaxis door de C#‑equivalent, maar het concept van **een CommandButton in een Word‑document insluiten** blijft ongewijzigd.

## Conclusie

Je hebt nu een werkend, end‑to‑end voorbeeld dat **Forms2OleControl aan DOCX toevoegt** met Aspose.Words for Java. Door een leeg document te maken, het ActiveX‑besturingselement in te voegen, de eigenschappen te configureren en het bestand op te slaan, heb je de essentiële stappen beheerst om **een ActiveX‑besturingselement in DOCX in te voegen** en kun je dit patroon uitbreiden naar andere besturingselementtypen.

Wat nu? Probeer deze techniek te combineren met Aspose.Words mail‑merge om gepersonaliseerde formulieren te genereren, of verken het toevoegen van VBA‑macro's zodat de knop daadwerkelijk iets doet. De mogelijkheden zijn eindeloos wanneer je **Aspose.Words Forms2OleControl‑voorbeeld** code combineert met je eigen bedrijfslogica.

Veel plezier met coderen, en voel je vrij om een reactie achter te laten als je ergens tegenaan loopt!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe je formuliervelden maakt en inhoud toevoegt met DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Bladwijzers toevoegen in Word met Aspose.Words for Java – Invoegen, bijwerken, verwijderen](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)
- [Hoe je een watermerk toevoegt aan documenten met Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}