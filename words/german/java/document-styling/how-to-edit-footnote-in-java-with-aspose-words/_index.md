---
category: general
date: 2026-08-07
description: Wie man Fußnoten in Java mit Aspose.Words bearbeitet – benutzerdefinierten
  Strich hinzufügen, Fußnotenlinie ändern und Absatzausrichtung festlegen für polierte
  Dokumente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: de
lastmod: 2026-08-07
og_description: Wie man Fußnoten in Java mit Aspose.Words bearbeitet. Erfahren Sie,
  wie Sie ein benutzerdefiniertes Strichzeichen hinzufügen, die Fußnotenlinie ändern
  und die Absatzausrichtung in nur wenigen Schritten festlegen.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Wie man Fußnote in Java bearbeitet – Bindestrich hinzufügen, Zeile ändern,
  Ausrichtung festlegen
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Wie man Fußnoten in Java mit Aspose.Words bearbeitet
url: /de/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Fußnoten in Java mit Aspose.Words bearbeitet

Wenn Sie **wie man Fußnoten bearbeitet** in einem Word‑Dokument mit Java benötigen, zeigt diese Anleitung den kompletten Workflow. Sie lernen, wie man einen benutzerdefinierten Gedankenstrich hinzufügt, die Fußnotenlinie ändert und die Absatzausrichtung festlegt, sodass der Fußnoten‑Separator professionell aussieht.

Das Bearbeiten von Fußnoten ist ein häufiges Anliegen beim Erstellen von Rechtsverträgen, wissenschaftlichen Arbeiten oder Marketing‑Broschüren. Die nachfolgenden Schritte decken alles ab – vom Laden des Dokuments bis zum Speichern der finalen Datei – ohne zusätzliche Werkzeuge.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java 17 oder neuer installiert.
* Aspose.Words für Java (neueste Version) im Klassenpfad Ihres Projekts.
* Eine DOCX‑Datei (`input.docx`), die mindestens eine Fußnote enthält.

Diese Punkte garantieren, dass der Code ohne Laufzeitfehler ausgeführt wird.

## Wie man den Fußnoten‑Separator und die Linie bearbeitet

Der Fußnoten‑Separator ist der Absatz, der zwischen dem Haupttext und der Liste der Fußnoten erscheint. Das Ändern seines Aussehens verbessert die Lesbarkeit und entspricht dem Corporate Branding.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Warum jede Zeile wichtig ist

1. **Laden des Dokuments** – `new Document(...)` liest die DOCX‑Datei in den Speicher und gibt Ihnen Zugriff auf alle Knoten.
2. **Abrufen des Separators** – `getFootnoteSeparator()` liefert den speziellen Absatz, den Aspose.Words als Fußnoten‑Linie behandelt. Dieses Objekt ist der einzige Ort, an dem Sie den Separator sicher ändern können.
3. **Festlegen der Absatzausrichtung** – `setAlignment(ParagraphAlignment.CENTER)` ändert die Ausrichtung der Linie. Das Stichwort *set paragraph alignment* wird direkt auf den Separator angewendet und sorgt für einen zentrierten Gedankenstrich.
4. **Hinzufügen eines benutzerdefinierten Gedankenstrichs** – Durch das Leeren vorhandener Runs und das Hinzufügen eines neuen `Run` mit dem Em‑Dash‑Zeichen (`—`) erzielen Sie den Effekt *add custom dash* und gleichzeitig *change footnote line* nach Ihrem gewünschten Stil.
5. **Speichern des Dokuments** – `doc.save(...)` schreibt die Änderungen zurück auf die Festplatte und erzeugt eine Ausgabedatei, die alle Modifikationen enthält.

## Benutzerdefinierten Gedankenstrich zum Fußnoten‑Separator hinzufügen

Der Code in **Schritt 4** demonstriert die *add custom dash*‑Technik. Sie können den Em‑Dash durch jede beliebige Zeichenkette ersetzen, z. B. `"***"` oder `"---"`, um die visuelle Sprache Ihres Dokuments anzupassen.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Die Verwendung eines benutzerdefinierten Gedankenstrichs ist besonders hilfreich, wenn die Standard‑Dünnlinie nicht den Branding‑Richtlinien entspricht.

## Fußnoten‑Linienstil ändern

Wenn Sie statt eines Gedankenstrichs lieber eine durchgezogene Linie möchten, können Sie ein Unicode‑Box‑Drawing‑Zeichen oder einen wiederholten Unterstrich einfügen.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

Der *change footnote line*‑Schritt funktioniert unabhängig vom gewählten Zeichen gleich, da der Separator‑Absatz lediglich den enthaltenen Text rendert.

## Absatzausrichtung für den Fußnoten‑Separator festlegen

Die *set paragraph alignment*‑Operation ist nicht auf zentrierte Ausrichtung beschränkt. Sie können links, rechts oder im Blocksatz ausrichten, je nach Layout‑Bedarf.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Die Ausrichtung des Separators nach rechts kann nützlich sein für Dokumente, die rechtsbündige Fußnoten verwenden, etwa bei zweisprachigen Publikationen.

## Vollständiges, ausführbares Beispiel

Nachfolgend das komplette Programm, das alle Konzepte integriert – Dokument laden, Fußnoten‑Separator bearbeiten, benutzerdefinierten Gedankenstrich hinzufügen, den Linienstil ändern und die Ausrichtung setzen.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Erwartete Ausgabe:** Die Datei `output.docx` enthält einen zentrierten Em‑Dash dort, wo zuvor die dünne Linie war. Alle Fußnoten bleiben erhalten und das Layout des Dokuments spiegelt den neuen Separator‑Stil wider.

## Häufige Stolperfallen und wie man sie vermeidet

| Problem | Grund | Lösung |
|-------|--------|-----|
| Separator nicht gefunden | Dokument enthält keine Fußnoten oder verwendet einen benutzerdefinierten Fußnoten‑Stil | Stellen Sie sicher, dass das Quell‑DOCX mindestens eine Fußnote enthält, bevor Sie `getFootnoteSeparator()` aufrufen |
| Benutzerdefinierter Gedankenstrich nicht sichtbar | Schriftart unterstützt das gewählte Zeichen nicht | Verwenden Sie ein Unicode‑Zeichen, das von der Standardschrift des Dokuments unterstützt wird, oder betten Sie eine kompatible Schriftart ein |
| Ausrichtung bleibt unverändert | Absatzformat wird später im Code überschrieben | Wenden Sie die Ausrichtung **nach** allen anderen Formatierungsaufrufen an, die sie zurücksetzen könnten |

Das Beachten dieser Punkte verhindert Laufzeitfehler und stellt sicher, dass der *how to edit footnote*‑Prozess zuverlässig funktioniert.

## Nächste Schritte

Jetzt, wo Sie **wie man Fußnoten bearbeitet** kennen, können Sie verwandte Aufgaben erkunden:

* **Benutzerdefinierten Fußnoten‑Referenzstil hinzufügen** – `FootnoteReference`‑Knoten modifizieren, um Nummerierung oder Symbole zu ändern.
* **Programmgesteuert neue Fußnoten einfügen** – `DocumentBuilder.insertFootnote()` für dynamischen Inhalt verwenden.
* **Bedingte Formatierung anwenden** – Fußnoten‑Aussehen basierend auf Absatzstil oder Inhaltslänge ändern.

Jede dieser Erweiterungen baut auf derselben API‑Oberfläche auf, die Sie zum *add custom dash*, *change footnote line* und *set paragraph alignment* verwendet haben.

---

*Viel Spaß beim Coden! Wenn Ihnen das Tutorial geholfen hat, die Fußnoten‑Bearbeitung zu meistern, teilen Sie es gern mit Ihrem Team oder senden Sie einen Pull‑Request, um das Beispiel weiter zu verbessern.*

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}