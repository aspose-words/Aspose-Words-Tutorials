---
date: 2025-12-22
description: Erfahren Sie, wie Sie Markdown exportieren, indem Sie Word-Dokumente
  mit Aspose.Words für Java in Markdown konvertieren. Dieser Schritt-für-Schritt-Leitfaden
  behandelt Tabellenausrichtung, Bildverarbeitung und mehr.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Wie man Markdown mit Aspose.Words für Java exportiert
url: /de/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# So exportieren Sie Markdown mit Aspose.Words für Java

## Einführung in das Exportieren von Markdown mit Aspose.Words für Java

In diesem Schritt‑für‑Schritt‑Tutorial **lernen Sie, wie Sie Markdown** aus Word‑Dokumenten mit Aspose.Words für Java exportieren. Markdown ist eine leichtgewichtige Auszeichnungssprache, die sich perfekt für Dokumentation, statische Site‑Generatoren und viele Veröffentlichungsplattformen eignet. Am Ende dieses Leitfadens können Sie **Word in Markdown konvertieren**, die Tabellenausrichtung anpassen und **Bilder in Markdown** mühelos **verarbeiten**.

## Schnelle Antworten
- **Was ist die primäre Klasse zum Speichern als Markdown?** `MarkdownSaveOptions`
- **Können Bilder automatisch eingebettet werden?** Ja – legen Sie den Bildordner über `setImagesFolder` fest.
- **Wie kann ich die Tabellenausrichtung steuern?** Verwenden Sie `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Was sind die Mindestanforderungen?** JDK 8+ und die Aspose.Words für Java‑Bibliothek.
- **Ist eine Testversion verfügbar?** Ja, laden Sie sie von der Aspose‑Website herunter.

## Was bedeutet „Markdown exportieren“?
Das Exportieren von Markdown bedeutet, ein Rich‑Text‑Word‑Dokument (`.docx`) zu nehmen und eine Nur‑Text‑`.md`‑Datei zu erzeugen, die Überschriften, Tabellen und Bilder in Markdown‑Syntax bewahrt.

## Warum Aspose.Words für Java zum Konvertieren von DOCX mit Bildern verwenden?
Aspose.Words verarbeitet komplexe Layouts, eingebettete Bilder und Tabellenstrukturen, ohne an Genauigkeit zu verlieren. Es bietet Ihnen zudem eine feinkörnige Kontrolle über die Markdown‑Ausgabe, wie Tabellenausrichtung und Bildordnerverwaltung.

## Voraussetzungen

- Java Development Kit (JDK) auf Ihrem System installiert.
- Aspose.Words für Java‑Bibliothek. Sie können sie von [hier](https://releases.aspose.com/words/java/) herunterladen.

## Schritt 1: Erstellen Sie ein einfaches Word‑Dokument

Zuerst erstellen wir ein kleines Dokument, das eine Tabelle enthält. Damit können wir später **die Tabellenausrichtung anpassen** demonstrieren.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Im obigen Snippet haben wir:

1. Ein neues `Document` erstellen.  
2. `DocumentBuilder` verwenden, um eine zweizellige Tabelle einzufügen.  
3. **Rechte** und **zentrierte** Absatzausrichtung in jeder Zelle anwenden.  
4. Die Datei mit `MarkdownSaveOptions` als Markdown speichern.

## Schritt 2: Tabellinhalt‑Ausrichtung anpassen

Aspose.Words ermöglicht es Ihnen zu bestimmen, wie Tabellenzellen im finalen Markdown gerendert werden. Sie können links, rechts oder zentriert ausrichten oder die Bibliothek automatisch basierend auf dem ersten Absatz jeder Spalte entscheiden lassen.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Durch Ändern der Eigenschaft `TableContentAlignment` steuern Sie die **Anpassung der Tabellenausrichtung** für die Markdown‑Ausgabe.

## Schritt 3: Bilder beim Exportieren nach Markdown verarbeiten

Wenn ein Dokument Bilder enthält, sollen diese Bilder korrekt in der erzeugten `.md`‑Datei erscheinen. Legen Sie den Ordner fest, in den Aspose.Words die extrahierten Bilder ablegen soll.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Ersetzen Sie `"document_with_images.docx"` durch den Pfad zu Ihrer Quelldatei und `"images_folder/"` durch den Ort, an dem die Bilder gespeichert werden sollen. Das resultierende Markdown enthält Bildlinks, die auf diesen Ordner verweisen, sodass Sie **Bilder in Markdown** nahtlos **verarbeiten** können.

## Vollständiger Quellcode zum Speichern von Dokumenten als Markdown in Aspose.Words für Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Häufige Probleme und Lösungen

| Problem | Lösung |
|-------|----------|
| Bilder erscheinen nicht in der `.md`‑Datei | Stellen Sie sicher, dass `setImagesFolder` auf ein beschreibbares Verzeichnis zeigt und dass der Ordner in dem erzeugten Markdown korrekt referenziert wird. |
| Tabellenausrichtung sieht falsch aus | Verwenden Sie `TableContentAlignment.AUTO`, damit Aspose.Words die beste Ausrichtung basierend auf dem ersten Absatz jeder Spalte ermittelt. |
| Ausgabedatei ist leer | Vergewissern Sie sich, dass das `Document`‑Objekt tatsächlich Inhalt enthält, bevor Sie `save` aufrufen. |

## Häufig gestellte Fragen

**Q: Wie installiere ich Aspose.Words für Java?**  
A: Aspose.Words für Java kann installiert werden, indem Sie die Bibliothek in Ihr Java‑Projekt einbinden. Sie können die Bibliothek von [hier](https://releases.aspose.com/words/java/) herunterladen und den Installationsanweisungen in der Dokumentation folgen.

**Q: Kann ich komplexe Word‑Dokumente mit Tabellen und Bildern nach Markdown konvertieren?**  
A: Ja, Aspose.Words für Java unterstützt die Konvertierung komplexer Word‑Dokumente mit Tabellen, Bildern und verschiedenen Formatierungselementen nach Markdown. Sie können die Markdown‑Ausgabe an die Komplexität Ihres Dokuments anpassen.

**Q: Wie kann ich Bilder in Markdown‑Dateien verarbeiten?**  
A: Legen Sie den Bildordnerpfad mit der Methode `setImagesFolder` in `MarkdownSaveOptions` fest. Stellen Sie sicher, dass die Bilddateien im angegebenen Ordner gespeichert werden; Aspose.Words erzeugt die entsprechenden Markdown‑Bildlinks.

**Q: Gibt es eine Testversion von Aspose.Words für Java?**  
A: Ja, Sie können eine Testversion von Aspose.Words für Java von der Aspose‑Website erhalten. Die Testversion ermöglicht es Ihnen, die Fähigkeiten der Bibliothek zu evaluieren, bevor Sie eine Lizenz erwerben.

**Q: Wo finde ich weitere Beispiele und Dokumentation?**  
A: Für weitere Beispiele, Dokumentation und detaillierte Informationen zu Aspose.Words für Java besuchen Sie bitte die [Dokumentation](https://reference.aspose.com/words/java/).

---

**Zuletzt aktualisiert:** 2025-12-22  
**Getestet mit:** Aspose.Words für Java 24.12 (zum Zeitpunkt des Schreibens aktuell)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}