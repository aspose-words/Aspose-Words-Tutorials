---
category: general
date: 2026-10-04
description: Skapa ett Word‑dokument med Java som innehåller en vanlig textinnehållskontroll
  och en platshållare. Lär dig hur du lägger till en platshållare i taggen och hur
  du infogar en sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: sv
lastmod: 2026-10-04
og_description: Skapa ett Word‑dokument med en enkeltextinnehållskontroll och en platshållare.
  Denna handledning visar hur man lägger till en platshållare i taggen och hur man
  infogar sdt med Aspose.Words för Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Skapa Word-dokument med innehållskontroll – steg‑för‑steg‑guide
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
title: Skapa Word-dokument med en vanlig textinnehållskontroll
url: /sv/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word‑dokument med en vanlig textinnehållskontroll

Om du behöver **skapa Word‑dokument** som innehåller ett användar‑redigerbart område är en vanlig textinnehållskontroll det mest pålitliga tillvägagångssättet. Denna handledning visar exakt hur du infogar en Structured Document Tag (SDT), sätter ett platshållar‑text och sparar resultatet som en **docx med platshållare**. Du får ett komplett, körbart Java‑exempel som fungerar med Aspose.Words for Java 23.8.

Guiden täcker alla förutsättningar, förklarar varför varje API‑anrop är viktigt och ger tips för att hantera kantfall som flerspråkiga platshållare eller nästlade taggar. I slutet kan du generera en Word‑fil som uppmanar användare att “Enter text…” direkt i dokumentet.

## Förutsättningar

Innan du börjar, se till att du har:

* Java 17 (eller senare) installerat och konfigurerat i din PATH.  
* Maven 3.8+ för att hantera beroenden.  
* En Aspose.Words for Java‑licens (utvärderingslicens fungerar för testning).  
* En utvecklings‑IDE (IntelliJ IDEA, Eclipse eller VS Code).

Lägg till Aspose.Words i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Skapa Word‑dokument med en vanlig textinnehållskontroll

Det centrala arbetsflödet består av fyra logiska steg. Varje steg är inneslutet i en tydligt namngiven metod så att du kan återanvända logiken i större projekt.

### Steg 1: Initiera dokumentet och buildern

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

**Varför detta är viktigt:** `Document` representerar Word‑filen i minnet. `DocumentBuilder` är det flödande API‑et som låter dig infoga stycken, tabeller och SDT‑er. Att börja med ett tomt dokument säkerställer att platshållaren visas i början, vilket är praktiskt för mallar.

### Steg 2: Infoga en vanlig‑text Structured Document Tag (SDT)

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Varför detta är viktigt:** `StructuredDocumentTagType.PLAIN_TEXT` skapar en innehållskontroll som bara accepterar rena tecken, vilket förhindrar oavsiktlig formatering. Anropet `setPlaceholderName` fyller i den grå hint‑texten som användarna ser innan de skriver – detta är **add placeholder to tag**‑operationen som får dokumentet att kännas som ett formulär.

### Steg 3: Lägg till vanlig text efter SDT:n

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Varför detta är viktigt:** Att lägga till innehåll efter kontrollen verifierar att SDT:n inte konsumerar hela dokumentflödet. Det demonstrerar också hur man blandar strukturerade taggar med vanliga stycken, ett vanligt krav när man bygger mallar.

### Steg 4: Spara den resulterande filen

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Varför detta är viktigt:** `save`‑metoden skriver den minnesbaserade modellen till en fysisk **docx med platshållare**‑fil. Den genererade filen kan öppnas i Microsoft Word, LibreOffice eller vilket bibliotek som helst som stödjer OpenXML‑formatet.

## Fullständig källkod

När du sätter ihop delarna får du ett självständigt program som du kan kompilera och köra:

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

### Förväntad utdata

När programmet körs skapas `SdtDemo.docx`. När du öppnar filen i Word visas:

* En grå platshållare “Enter text…” inuti en vanlig‑text innehållskontroll med etiketten **MyTag**.  
* Raden **After SDT** omedelbart under kontrollen.

Platshållaren försvinner så snart användaren börjar skriva, samtidigt som den ursprungliga formateringen bevaras.

## Vanliga variationer och kantfall

| Scenario | Rekommenderad ändring |
|----------|----------------------|
| **Flerspråkig platshållare** | Använd Unicode‑tecken i `setPlaceholderName`, t.ex. `sdt.setPlaceholderName("Введите текст…");`. |
| **Nästlade innehållskontroller** | Infoga en andra SDT inuti den första genom att anropa `builder.moveTo(sdt.getParagraph());` innan den andra `insertStructuredDocumentTag`. |
| **Skrivskyddad kontroll** | Anropa `sdt.setLockContentControl(true);` för att förhindra att användare tar bort taggen. |
| **Rich‑text istället för vanlig text** | Byt ut `StructuredDocumentTagType.PLAIN_TEXT` mot `StructuredDocumentTagType.RICH_TEXT`. |
| **Spara till en ström** | Använd `doc.save(OutputStream, SaveFormat.DOCX);` när du behöver skicka filen via HTTP. |

## Pro‑tips

* **Återanvänd tagg‑ID:n** – Om du genererar många dokument från samma mall, håll taggnamnet (`"MyTag"`) konsekvent så att efterföljande bearbetning (t.ex. mail‑merge) kan hitta det på ett pålitligt sätt.  
* **Prestanda** – För stora mallar, skapa `DocumentBuilder` en gång och återanvänd den; att infoga många SDT‑er i en loop är snabbare än att återskapa buildern för varje iteration.  
* **Testning** – Efter att DOCX‑filen har genererats, verifiera programatiskt att platshållaren finns med `doc.getRange().getStructuredDocumentTags().getCount()`.

## Slutsats

Du vet nu hur du **skapar Word‑dokument** som innehåller en **vanlig textinnehållskontroll** med en anpassad platshållare, vilket effektivt producerar en **docx med platshållare** redo för användarinmatning. Exemplet demonstrerar hela cykeln från att initiera dokumentet, **hur man infogar sdt**, **lägger till platshållare till tagg**, lägger till vanlig text och slutligen sparar filen.

### Nästa steg

* Utforska **hur man infogar sdt** i tabeller för formulär‑liknande layouter.  
* Kombinera denna teknik med **docx med platshållare**‑sammanfogning för att bygga automatiska rapportgeneratorer.  
* Experimentera med andra kontrolltyper (`RICH_TEXT`, `CHECKBOX`) för att skapa rikare Word‑formulär.

Anpassa gärna koden för din egen mallmotor och dela dina resultat i kommentarerna!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}