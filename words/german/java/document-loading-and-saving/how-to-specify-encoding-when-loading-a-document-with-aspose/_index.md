---
category: general
date: 2026-10-26
description: Erfahren Sie, wie Sie die Kodierung in Java mit LoadOptions angeben.
  Dieser Leitfaden behandelt Zeichenkodierung, die setEncoding‑Methode und Optionen
  zum Laden von Dokumenten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: de
lastmod: 2026-10-26
og_description: Wie man die Codierung in Java mit Aspose.Words angibt. Folgen Sie
  diesem vollständigen Tutorial, um Dokumente mit dem richtigen Zeichensatz zu laden.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Wie man die Kodierung in Java mit Aspose.Words festlegt – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Wie man die Zeichenkodierung beim Laden eines Dokuments mit Aspose.Words für
  Java festlegt
url: /de/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man die Kodierung beim Laden eines Dokuments mit Aspose.Words für Java angibt

Wenn Sie **wie man die Kodierung angibt** für eine Quelldatei in Java benötigen, zeigt Ihnen dieses Tutorial die genauen Schritte. Unabhängig davon, ob das Dokument Big5, UTF‑8 oder ein anderer Zeichensatz verwendet, können Sie den Lesevorgang mit `LoadOptions` steuern. Am Ende des Leitfadens verstehen Sie, warum Zeichencodierung wichtig ist, wie Sie die `setEncoding`‑Methode anwenden und wie Sie überprüfen, dass das Dokument korrekt geladen wird.

Das Laden eines Dokuments mit der richtigen Zeichencodierung verhindert unlesbaren Text und stellt sicher, dass mehrsprachiger Inhalt wie beabsichtigt dargestellt wird. Dieses Tutorial behandelt:

* Die Rolle der **Zeichencodierung in Java** beim Lesen von Dateien.
* Wie man **LoadOptions‑Kodierung** für Aspose.Words konfiguriert.
* Praktischen Code, den Sie in Ihr Projekt kopieren können.
* Häufige Stolperfallen wie nicht passende Kodierungen und wie man sie behebt.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java Development Kit (JDK) 8 oder höher.
* Maven oder Gradle zur Verwaltung von Abhängigkeiten.
* Aspose.Words für Java 23.10 oder neuer (die in diesem Leitfaden verwendete Version).
* Ein Beispiel‑Textdokument (`input.doc`), das mit der gewünschten Kodierung gespeichert wurde (z. B. Big5).

Sie benötigen keine zusätzlichen Bibliotheken; das Beispiel verwendet nur die Kern‑API von Aspose.Words.

## Schritt 1: Aspose.Words zu Ihrem Projekt hinzufügen

Wenn Sie Maven verwenden, fügen Sie die folgende Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Für Gradle platzieren Sie diese Zeile in Ihrer `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Durch das Einbinden der Bibliothek stehen Ihnen die Klassen `LoadOptions`, `Document` und `Encoding` zur Verfügung.

## Schritt 2: Eine `LoadOptions`‑Instanz erstellen

`LoadOptions` ermöglicht es Ihnen, anzupassen, wie Aspose.Words eine Datei öffnet. Das Erzeugen des Objekts ist der erste Teil von **wie man die Kodierung angibt**.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

Das `LoadOptions`‑Objekt startet mit den Standardeinstellungen. Sie werden seine Eigenschaften im nächsten Schritt anpassen.

## Schritt 3: Die gewünschte Zeichencodierung festlegen

Die Methode `setEncoding` definiert die **Zeichencodierung in Java**, die der Loader verwenden soll. In diesem Beispiel wählen wir die Big5‑Codepage, die häufig für traditionelle chinesische Textdateien verwendet wird.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Warum das wichtig ist*: Wenn die Bytes der Datei mit der falschen Codepage interpretiert werden, erscheinen Zeichen als Fragezeichen oder Kauderwelsch. Durch das explizite Aufrufen von `setEncoding` teilen Sie Aspose.Words mit, den Byte‑Strom mithilfe der Big5‑Zuordnungstabelle zu dekodieren.

Sie können `"Big5"` durch jeden von Java anerkannten Zeichensatznamen ersetzen, z. B. `"UTF-8"`, `"ISO-8859-1"` oder `"Windows-1252"`. Die Methode wirft `UnsupportedEncodingException`, wenn der Name ungültig ist; daher sollten Sie diese Ausnahme in Produktionscode abfangen.

## Schritt 4: Das Dokument mit den konfigurierten Optionen laden

Jetzt, wo **LoadOptions‑Kodierung** gesetzt ist, übergeben Sie die Optionen dem `Document`‑Konstruktor. Dieser Schritt schließt den Kern‑Workflow von **wie man die Kodierung angibt** ab.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

Ersetzen Sie `YOUR_DIRECTORY` durch den absoluten oder relativen Pfad zu Ihrer Datei. Die `Document`‑Instanz enthält nun den vollständig geparsten Inhalt, wobei die von Ihnen angegebene Kodierung berücksichtigt wird.

## Schritt 5: Überprüfen, dass der Text korrekt geladen wird

Eine schnelle Überprüfung hilft Ihnen sicherzustellen, dass die Kodierung wie erwartet angewendet wurde. Sie können den Text des Dokuments extrahieren und in der Konsole ausgeben:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

Wenn die Konsole lesbare chinesische Zeichen (oder die von Ihnen erwartete Sprache) anzeigt, war die Kodierung erfolgreich. Wenn weiterhin Kauderwelsch erscheint, überprüfen Sie die ursprüngliche Kodierung der Datei und stellen Sie sicher, dass der Zeichensatzname exakt übereinstimmt.

## Umgang mit häufigen Sonderfällen

### 5.1 Laden aus einem `InputStream`

Manchmal erhalten Sie ein Dokument als Stream (z. B. von einem Web‑Service). Sie können die Kodierung weiterhin steuern, indem Sie den Stream zusammen mit `LoadOptions` übergeben:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

Die gleichen **Dokument‑Ladeoptionen** gelten, und der Aufruf von `setEncoding` bleibt unverändert.

### 5.2 Rückgriff, wenn die Kodierung unbekannt ist

Wenn Sie den Zeichensatz der Quelldatei nicht bestimmen können, können Sie vor dem Setzen der Kodierung eine Erkennungsbibliothek (wie ICU4J) einsetzen. Sobald Sie eine Vermutung haben, rufen Sie `setEncoding` mit diesem Wert auf. Dieser Ansatz reduziert das Risiko von falsch dekodiertem Text.

### 5.3 Umgang mit nicht unterstützten Kodierungen

Java unterstützt eine breite Palette von Codepages, aber einige veraltete Kodierungen können fehlen. In diesem Fall sollten Sie die Datei extern nach UTF‑8 konvertieren (z. B. mit `iconv`), bevor Sie sie mit Aspose.Words laden. Nach der Konvertierung können Sie den Aufruf von `setEncoding` weglassen, da UTF‑8 der Standard für die meisten modernen APIs ist.

## Profi‑Tipp: `LoadOptions` für Batch‑Verarbeitung wiederverwenden

Wenn Sie viele Dokumente laden müssen, die denselben Zeichensatz verwenden, erstellen Sie eine einzige `LoadOptions`‑Instanz und verwenden Sie sie wieder:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

Das Wiederverwenden des Objekts reduziert den Overhead bei der Objekterstellung und garantiert eine konsistente Kodierung über den gesamten Batch hinweg.

## Vollständiges ausführbares Beispiel

Unten finden Sie das komplette Programm, das alle Schritte integriert, die erforderlichen Importe enthält und potenzielle Ausnahmen behandelt.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**Erwartete Ausgabe** (unter der Annahme, dass die Quelldatei chinesischen Text in Big5 enthält):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

Wenn die Ausgabe unlesbare Symbole zeigt, überprüfen Sie den Zeichensatznamen erneut oder verifizieren Sie die ursprüngliche Kodierung der Datei.

## Häufig gestellte Fragen

**Funktioniert das mit anderen Dokumentformaten (DOCX, RTF, HTML)?**  
Ja. Das gleiche `LoadOptions`‑Objekt gilt für jedes von Aspose.Words unterstützte Format. Die einzige Voraussetzung ist, dass die zugrunde liegende Datei tatsächlich den angegebenen Zeichensatz verwendet.

**Was, wenn ich die Kodierung nach dem Laden des Dokuments ändern muss?**  
Die Kodierung wirkt sich nur auf die Lesephase aus. Sobald das `Document`‑Objekt existiert, ist seine interne Unicode‑Darstellung unabhängig vom ursprünglichen Zeichensatz. Um die Ausgabe­kodierung zu ändern, passen Sie die `SaveOptions` beim Schreiben der Datei an.

**Kann ich diesen Ansatz mit anderen Bibliotheken (z. B. Apache POI) verwenden?**  
Apache POI führt seine eigene Zeichensatz‑Erkennung für ältere Binärformate durch, aber das Konzept, einem Loader einen Zeichensatz zu übergeben, ist ähnlich. Für Aspose.Words ist `LoadOptions` der offizielle Weg, um **wie man die Kodierung angibt** zu steuern.

## Fazit

Sie wissen jetzt, **wie man die Kodierung angibt** beim Laden eines Dokuments mit Aspose.Words für Java. Indem Sie ein `LoadOptions`‑Objekt erstellen, die `setEncoding`‑Methode aufrufen und die Optionen dem `Document`‑Konstruktor übergeben, stellen Sie sicher, dass die Bytes der Datei korrekt interpretiert werden. Diese Praxis eliminiert unlesbaren Text, unterstützt mehrsprachigen Inhalt und lässt sich nahtlos in Batch‑Verarbeitung oder Stream‑basierte Workflows integrieren.

Erkunden Sie verwandte Themen wie **Dokument‑Ladeoptionen**, **Speichern mit spezifischen Kodierungen** und **Umgang mit Unicode in Java**, um Ihre Textverarbeitungs‑Kompetenz zu vertiefen. Experimentieren Sie mit verschiedenen Zeichensatznamen, kombinieren Sie den Ansatz mit PDF‑Konvertierung oder integrieren Sie ihn in einen Web‑Service, der Uploads in verschiedenen Kodierungen akzeptiert.

Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man RTF-Text mit UTF-8-Kodierung in Java mit Aspose.Words konvertiert](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Wie man Optionen in Aspose.Words für Java festlegt – vollständige Anleitung](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Beschädigtes DOCX-Word-Dokument mit Aspose.Words LoadOptions wiederherstellen – Java‑Leitfaden](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}