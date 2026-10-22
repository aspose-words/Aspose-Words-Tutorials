---
category: general
date: 2026-10-04
description: Maak een Word-document met Java dat een platte‑tekst‑inhoudsbesturingselement
  en een placeholder bevat. Leer hoe je een placeholder aan een tag toevoegt en hoe
  je een sdt invoegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: nl
lastmod: 2026-10-04
og_description: Maak een Word‑document met een platte‑tekstinhoudsbesturingselement
  en een plaatsaanduiding. Deze tutorial laat zien hoe je een plaatsaanduiding aan
  een tag toevoegt en hoe je een sdt invoegt met Aspose.Words voor Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Maak een Word‑document met inhoudsbesturing – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: Maak een Word‑document met een platte‑tekstinhoudsbesturingselement
url: /nl/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een Word-document met een platte‑tekst content control

Als je een **Word-document** moet maken dat een door de gebruiker bewerkbaar gebied bevat, is een platte‑tekst content control de meest betrouwbare aanpak. Deze tutorial laat precies zien hoe je een Structured Document Tag (SDT) invoegt, een placeholder instelt, en het resultaat opslaat als een **docx met placeholder**. Je ziet een volledig, uitvoerbaar Java‑voorbeeld dat werkt met Aspose.Words for Java 23.8.

De gids behandelt alle vereisten, legt uit waarom elke API‑aanroep belangrijk is, en biedt tips voor het omgaan met randgevallen zoals meertalige placeholders of geneste tags. Aan het einde kun je een Word‑bestand genereren dat gebruikers vraagt “Enter text…” direct in het document in te voeren.

## Vereisten

* Java 17 (of later) geïnstalleerd en geconfigureerd in je PATH.  
* Maven 3.8+ om afhankelijkheden te beheren.  
* Een Aspose.Words for Java‑licentie (evaluatie werkt voor testen).  
* Een ontwikkel‑IDE (IntelliJ IDEA, Eclipse, of VS Code).

Voeg Aspose.Words toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Maak Word-document met een platte‑tekst content control

De kernworkflow bestaat uit vier logische stappen. Elke stap is verpakt in een duidelijk benoemde methode zodat je de logica kunt hergebruiken in grotere projecten.

### Stap 1: Initialiseer het document en de builder

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**Waarom dit belangrijk is:** `Document` vertegenwoordigt het in‑memory Word‑bestand. `DocumentBuilder` is de fluente API die je in staat stelt alinea's, tabellen en SDT's in te voegen. Beginnen met een leeg document zorgt ervoor dat de placeholder helemaal aan het begin verschijnt, wat handig is voor sjablonen.

### Stap 2: Voeg een platte‑tekst Structured Document Tag (SDT) toe

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Waarom dit belangrijk is:** `StructuredDocumentTagType.PLAIN_TEXT` maakt een content control die alleen platte tekens accepteert, waardoor per ongeluk opmaken wordt voorkomen. De `setPlaceholderName`‑aanroep vult de grijze hinttekst in die gebruikers zien voordat ze typen — dit is de **add placeholder to tag**‑operatie die het document als een formulier laat aanvoelen.

### Stap 3: Voeg reguliere inhoud toe na de SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Waarom dit belangrijk is:** Inhoud toevoegen na de controlle controleert dat de SDT niet de volledige documentstroom opeet. Het toont ook hoe je gestructureerde tags kunt combineren met gewone alinea's, een veelvoorkomende eis bij het bouwen van sjablonen.

### Stap 4: Sla het resulterende bestand op

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Waarom dit belangrijk is:** De `save`‑methode schrijft het in‑memory model naar een fysiek **docx met placeholder**‑bestand. Het gegenereerde bestand kan worden geopend in Microsoft Word, LibreOffice, of elke bibliotheek die het OpenXML‑formaat ondersteunt.

## Volledige broncode

Door de onderdelen samen te voegen krijg je een zelfstandige applicatie die je kunt compileren en uitvoeren:

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Verwachte output

Het uitvoeren van het programma maakt `SdtDemo.docx`. Het openen van het bestand in Word toont:

* Een grijze placeholder “Enter text…” binnen een platte‑tekst content control met het label **MyTag**.  
* De regel **After SDT** direct onder de control.

De placeholder verdwijnt zodra de gebruiker typt, waardoor de oorspronkelijke opmaak behouden blijft.

## Veelvoorkomende variaties en randgevallen

| Scenario | Aanbevolen wijziging |
|----------|----------------------|
| **Meertalige placeholder** | Gebruik Unicode‑tekens in `setPlaceholderName`, bijv. `sdt.setPlaceholderName("Введите текст…");`. |
| **Geneste content controls** | Voeg een tweede SDT toe binnen de eerste door `builder.moveTo(sdt.getParagraph());` aan te roepen vóór de tweede `insertStructuredDocumentTag`. |
| **Alleen‑lezen control** | Roep `sdt.setLockContentControl(true);` aan om te voorkomen dat gebruikers de tag verwijderen. |
| **Rich‑text in plaats van platte tekst** | Vervang `StructuredDocumentTagType.PLAIN_TEXT` door `StructuredDocumentTagType.RICH_TEXT`. |
| **Opslaan naar een stream** | Gebruik `doc.save(OutputStream, SaveFormat.DOCX);` wanneer je het bestand via HTTP moet verzenden. |

## Pro‑tips

* **Reuse tag IDs** – Als je veel documenten genereert vanuit dezelfde sjabloon, houd de tag‑naam (`"MyTag"`) consistent zodat downstream verwerking (bijv. mail‑merge) deze betrouwbaar kan vinden.  
* **Performance** – Voor grote sjablonen, maak de `DocumentBuilder` één keer aan en hergebruik deze; het invoegen van veel SDT's in een lus is sneller dan de builder elke iteratie opnieuw te maken.  
* **Testing** – Na het genereren van de DOCX, controleer programmatisch of de placeholder bestaat met `doc.getRange().getStructuredDocumentTags().getCount()`.

## Conclusie

Je weet nu hoe je een **Word-document** kunt **maken** dat een **plain text content control** bevat met een aangepaste placeholder, waardoor je effectief een **docx met placeholder** produceert die klaar is voor gebruikersinvoer. Het voorbeeld toont de volledige cyclus van het initialiseren van het document, **how to insert sdt**, **add placeholder to tag**, reguliere inhoud toevoegen, en uiteindelijk het bestand opslaan.

### Volgende stappen

* Verken **how to insert sdt** binnen tabellen voor formulier‑achtige lay-outs.  
* Combineer deze techniek met **docx met placeholder**‑samenvoeging om geautomatiseerde rapportgeneratoren te bouwen.  
* Experimenteer met andere control‑types (`RICH_TEXT`, `CHECKBOX`) om rijkere Word‑formulieren te maken.

Voel je vrij om de code aan te passen voor je eigen sjabloon‑engine, en deel je resultaten in de reacties!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word‑document maken Java – Rechthoek‑vorm toevoegen met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hoe PDF‑documenten te maken met Aspose.Words voor Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}