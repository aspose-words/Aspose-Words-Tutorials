---
category: general
date: 2026-10-04
description: Erstelle ein Word-Dokument mit Java, das ein Plain‑Text‑Inhaltssteuerelement
  und einen Platzhalter enthält. Erfahre, wie man einen Platzhalter zum Tag hinzufügt
  und wie man ein SDT einfügt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: de
lastmod: 2026-10-04
og_description: Erstellen Sie ein Word‑Dokument mit einem einfachen Text‑Inhaltssteuerelement
  und einem Platzhalter. Dieses Tutorial zeigt, wie man einen Platzhalter zum Tag
  hinzufügt und wie man ein SDT mit Aspose.Words für Java einfügt.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Word‑Dokument mit Inhaltssteuerelement erstellen – Schritt‑für‑Schritt‑Anleitung
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
title: Word-Dokument mit einem einfachen Text‑Inhaltssteuerelement erstellen
url: /de/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument mit einem einfachen Text‑Inhaltssteuerelement erstellen

Wenn Sie ein **Word-Dokument** erstellen müssen, das einen vom Benutzer editierbaren Bereich enthält, ist ein einfaches Text‑Inhaltssteuerelement der zuverlässigste Ansatz. Dieses Tutorial zeigt genau, wie man ein Structured Document Tag (SDT) einfügt, einen Platzhalter festlegt und das Ergebnis als **docx with placeholder** speichert. Sie sehen ein vollständiges, ausführbares Java‑Beispiel, das mit Aspose.Words for Java 23.8 funktioniert.

Der Leitfaden behandelt alle Voraussetzungen, erklärt, warum jeder API‑Aufruf wichtig ist, und gibt Tipps zum Umgang mit Sonderfällen wie mehrsprachigen Platzhaltern oder verschachtelten Tags. Am Ende können Sie eine Word‑Datei erzeugen, die Benutzer direkt im Dokument mit „Enter text…“ auffordert.

## Voraussetzungen

* Java 17 (oder neuer) installiert und in Ihrem PATH konfiguriert.  
* Maven 3.8+ zur Verwaltung von Abhängigkeiten.  
* Eine Aspose.Words for Java Lizenz (Evaluierung funktioniert zum Testen).  
* Eine Entwicklungs‑IDE (IntelliJ IDEA, Eclipse oder VS Code).

Fügen Sie Aspose.Words zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Word-Dokument mit einem einfachen Text‑Inhaltssteuerelement erstellen

Der Kern‑Workflow besteht aus vier logischen Schritten. Jeder Schritt ist in einer klar benannten Methode gekapselt, sodass Sie die Logik in größeren Projekten wiederverwenden können.

### Schritt 1: Dokument und Builder initialisieren

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

**Warum das wichtig ist:** `Document` repräsentiert die im Speicher befindliche Word‑Datei. `DocumentBuilder` ist die Fluent‑API, mit der Sie Absätze, Tabellen und SDTs einfügen können. Wenn Sie mit einem leeren Dokument beginnen, erscheint der Platzhalter ganz am Anfang, was für Vorlagen nützlich ist.

### Schritt 2: Ein einfaches Text‑Structured Document Tag (SDT) einfügen

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Warum das wichtig ist:** `StructuredDocumentTagType.PLAIN_TEXT` erstellt ein Inhaltssteuerelement, das nur reine Zeichen akzeptiert und versehentliche Formatierungen verhindert. Der Aufruf `setPlaceholderName` füllt den grauen Hinweistext aus, den Benutzer sehen, bevor sie tippen – das ist die **add placeholder to tag**‑Operation, die das Dokument wie ein Formular wirken lässt.

### Schritt 3: Regulären Inhalt nach dem SDT hinzufügen

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Warum das wichtig ist:** Das Hinzufügen von Inhalt nach dem Steuerelement bestätigt, dass das SDT nicht den gesamten Dokumentenfluss beansprucht. Es zeigt zudem, wie strukturierte Tags mit normalen Absätzen gemischt werden können, was beim Erstellen von Vorlagen häufig erforderlich ist.

### Schritt 4: Ergebnisdatei speichern

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Warum das wichtig ist:** Die Methode `save` schreibt das im Speicher befindliche Modell in eine physische **docx with placeholder**‑Datei. Die erzeugte Datei kann in Microsoft Word, LibreOffice oder jeder Bibliothek, die das OpenXML‑Format unterstützt, geöffnet werden.

## Vollständiger Quellcode

Wenn Sie die Teile zusammenfügen, erhalten Sie ein eigenständiges Programm, das Sie kompilieren und ausführen können:

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

### Erwartete Ausgabe

Das Ausführen des Programms erzeugt `SdtDemo.docx`. Beim Öffnen der Datei in Word wird angezeigt:

* Ein grauer Platzhalter „Enter text…“ innerhalb eines einfachen Text‑Inhaltssteuerelements mit der Bezeichnung **MyTag**.  
* Die Zeile **After SDT** unmittelbar unter dem Steuerelement.

Der Platzhalter verschwindet, sobald der Benutzer tippt, und bewahrt die ursprüngliche Formatierung.

## Häufige Variationen und Sonderfälle

| Szenario | Empfohlene Änderung |
|----------|---------------------|
| **Multilingual placeholder** | Verwenden Sie Unicode‑Zeichen in `setPlaceholderName`, z. B. `sdt.setPlaceholderName("Введите текст…");`. |
| **Nested content controls** | Fügen Sie ein zweites SDT innerhalb des ersten ein, indem Sie `builder.moveTo(sdt.getParagraph());` vor dem zweiten `insertStructuredDocumentTag` aufrufen. |
| **Read‑only control** | Rufen Sie `sdt.setLockContentControl(true);` auf, um zu verhindern, dass Benutzer das Tag löschen. |
| **Rich‑text instead of plain text** | Ersetzen Sie `StructuredDocumentTagType.PLAIN_TEXT` durch `StructuredDocumentTagType.RICH_TEXT`. |
| **Saving to a stream** | Verwenden Sie `doc.save(OutputStream, SaveFormat.DOCX);`, wenn Sie die Datei über HTTP senden müssen. |

## Pro‑Tipps

* **Tag‑IDs wiederverwenden** – Wenn Sie viele Dokumente aus derselben Vorlage erzeugen, halten Sie den Tag‑Namen (`"MyTag"`) konsistent, damit nachgelagerte Prozesse (z. B. Seriendruck) ihn zuverlässig finden können.  
* **Performance** – Bei großen Vorlagen erstellen Sie den `DocumentBuilder` einmal und verwenden ihn erneut; das Einfügen vieler SDTs in einer Schleife ist schneller, als den Builder in jeder Iteration neu zu erzeugen.  
* **Testing** – Nach der Erzeugung des DOCX überprüfen Sie programmgesteuert, ob der Platzhalter existiert, mit `doc.getRange().getStructuredDocumentTags().getCount()`.

## Fazit

Sie wissen jetzt, wie Sie ein **Word-Dokument** erstellen, das ein **einfaches Text‑Inhaltssteuerelement** mit einem benutzerdefinierten Platzhalter enthält und damit ein **docx with placeholder** erzeugt, das für Benutzereingaben bereit ist. Das Beispiel demonstriert den gesamten Zyklus vom Initialisieren des Dokuments, **how to insert sdt**, **add placeholder to tag**, dem Hinzufügen regulären Inhalts und schließlich dem Speichern der Datei.

### Nächste Schritte

* Erkunden Sie **how to insert sdt** innerhalb von Tabellen für formularähnliche Layouts.  
* Kombinieren Sie diese Technik mit dem Zusammenführen von **docx with placeholder**, um automatisierte Berichtsgeneratoren zu erstellen.  
* Experimentieren Sie mit anderen Steuerelementtypen (`RICH_TEXT`, `CHECKBOX`), um umfangreichere Word‑Formulare zu erstellen.

Passen Sie den Code gerne an Ihre eigene Template‑Engine an und teilen Sie Ihre Ergebnisse in den Kommentaren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word-Dokument in Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Wie man PDF-Dokumente mit Aspose.Words für Java erstellt | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}