---
date: 2025-12-27
description: Erfahren Sie, wie Sie die Richtung festlegen, txt‑Dateien laden, Leerzeichen
  entfernen und txt in docx mit Aspose.Words für Java konvertieren.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Wie man die Richtung festlegt und Textdateien mit Aspose.Words für Java lädt
url: /de/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man die Richtung festlegt und Textdateien mit Aspose.Words für Java lädt

## Einführung in das Laden von Textdateien mit Aspose.Words für Java

In diesem Leitfaden erfahren Sie **wie man die Richtung festlegt** beim Laden von Nur‑Text‑Dokumenten und sehen praktische Methoden zum **Laden von txt**, **Entfernen von Leerzeichen** und **Konvertieren von txt zu docx** mit Aspose.Words für Java. Egal, ob Sie einen Dokument‑Konvertierungsservice erstellen oder eine feinkörnige Kontrolle über die Listenerkennung benötigen, führt Sie dieses Tutorial durch jeden Schritt mit klaren Erklärungen und sofort ausführbarem Code.

## Schnelle Antworten
- **Wie lege ich die Text­richtung für eine geladene TXT‑Datei fest?** Verwenden Sie `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` oder geben Sie `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT` an.
- **Kann Aspose.Words nummerierte Listen im Nur‑Text erkennen?** Ja – aktivieren Sie `DetectNumberingWithWhitespaces` in `TxtLoadOptions`.
- **Wie kann ich führende und nachfolgende Leerzeichen entfernen?** Setzen Sie `TxtLeadingSpacesOptions.TRIM` und `TxtTrailingSpacesOptions.TRIM`.
- **Ist es möglich, eine TXT‑Datei in einem Schritt zu DOCX zu konvertieren?** Laden Sie die TXT‑Datei mit `TxtLoadOptions` und rufen Sie `Document.save("output.docx")` auf.
- **Welche Java‑Version wird benötigt?** Java 8+ ist ausreichend für Aspose.Words 24.x.

## Was bedeutet „wie man die Richtung festlegt“ in Aspose.Words?

Enthält eine Textdatei Rechts‑nach‑Links‑Schriften (z. B. Hebräisch oder Arabisch), muss die Bibliothek die Lesereihenfolge kennen. Das `DocumentDirection`‑Enum ermöglicht es Ihnen, die **Richtung** manuell festzulegen oder Aspose automatisch erkennen zu lassen, wodurch ein korrektes Layout und die Bidi‑Formatierung sichergestellt werden.

## Warum Aspose.Words zum Laden von TXT‑Dateien verwenden?

- **Genaue Listenerkennung** – verarbeitet nummerierte, Aufzählungs‑ und durch Leerzeichen getrennte Listen.
- **Feinkörnige Leerzeichen‑Verarbeitung** – führende/nachfolgende Leerzeichen entfernen oder beibehalten.
- **Automatische Erkennung der Text­richtung** – ideal für mehrsprachige Dokumente.
- **Ein‑Schritt‑Konvertierung** – laden Sie eine `.txt` und speichern Sie sie als `.docx`, `.pdf` oder ein anderes unterstütztes Format.

## Voraussetzungen
- Java 8 oder neuer.
- Aspose.Words für Java Bibliothek (fügen Sie die Maven/Gradle‑Abhängigkeit oder die JAR zu Ihrem Projekt hinzu).
- Grundkenntnisse von Java‑I/O‑Streams.

## Schritt‑für‑Schritt‑Anleitung

### Schritt 1: Erkennen von Listen (wie man txt lädt)

Um ein Textdokument zu laden und Listen automatisch zu erkennen, erstellen Sie eine Instanz von `TxtLoadOptions` und aktivieren die Listenerkennung. Der untenstehende Code zeigt verschiedene Listentypen und aktiviert die Leerzeichen‑bewusste Nummerierung.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Pro Tipp:** Wenn Sie nur die grundlegende Listenerkennung benötigen, können Sie die Leerzeichen‑Option überspringen – Aspose erkennt weiterhin die Standard‑Muster `1.` und `1)`.

### Schritt 2: Optionen für Leerzeichen (wie man Leerzeichen entfernt)

Führende und nachfolgende Leerzeichen verursachen häufig Formatierungsprobleme. Verwenden Sie `TxtLeadingSpacesOptions` und `TxtTrailingSpacesOptions`, um dieses Verhalten zu steuern.

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

> **Warum das wichtig ist:** Das Entfernen von Leerzeichen verhindert unerwünschte Einrückungen im resultierenden DOCX und sorgt dafür, dass das Dokument sauber aussieht, ohne manuelle Nachbearbeitung.

### Schritt 3: Steuerung der Text­richtung (wie man die Richtung festlegt)

Für Rechts‑nach‑Links‑Sprachen setzen Sie die Dokumenten­richtung vor dem Laden. Das nachstehende Beispiel lädt eine hebräische Textdatei und gibt das Bidi‑Flag aus, um die Richtung zu bestätigen.

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

> **Häufiger Fehler:** Wenn `DocumentDirection` nicht gesetzt wird, kann es zu verzerrtem Arabisch‑/Hebräisch‑Text kommen, bei dem die Zeichen in falscher Reihenfolge erscheinen.

### Vollständiger Quellcode zum Laden von Textdateien mit Aspose.Words für Java

Unten finden Sie den vollständigen, sofort ausführbaren Quellcode, der Listenerkennung, Leerzeichen‑Verarbeitung und Richtungssteuerung kombiniert. Sie können ihn in eine einzelne Klasse kopieren und die drei Testmethoden einzeln ausführen.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Häufige Probleme und Lösungen

| Problem | Ursache | Lösung |
|---------|---------|--------|
| Listen werden nicht erkannt | `DetectNumberingWithWhitespaces` blieb `false` für durch Leerzeichen getrennte Listen | Aktivieren Sie `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Zusätzliche Einrückung nach dem Laden | Führende Leerzeichen wurden beibehalten | Setzen Sie `TxtLeadingSpacesOptions.TRIM` |
| Hebräischer Text erscheint umgekehrt | Dokumenten­richtung nicht gesetzt oder auf `LEFT_TO_RIGHT` gesetzt | Verwenden Sie `DocumentDirection.AUTO` oder `RIGHT_TO_LEFT` |
| Ausgabedocx ist leer | Eingabestream wurde vor dem zweiten Laden nicht zurückgesetzt | Erstellen Sie `ByteArrayInputStream` für jeden Ladevorgang neu |

## Häufig gestellte Fragen

### F: Was ist Aspose.Words für Java?

A: Aspose.Words für Java ist eine leistungsstarke Dokumenten‑Verarbeitungsbibliothek, die Entwicklern ermöglicht, Word‑Dokumente programmgesteuert in Java‑Anwendungen zu erstellen, zu manipulieren und zu konvertieren. Sie unterstützt ein breites Spektrum an Funktionen, von einfachem Text‑Laden bis hin zu komplexer Formatierung und Konvertierung.

### F: Wie kann ich mit Aspose.Words für Java beginnen?

A: 1. Laden Sie die Aspose.Words für Java‑Bibliothek herunter und installieren Sie sie. 2. Lesen Sie die Dokumentation unter [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) für detaillierte Informationen und Beispiele. 3. Erkunden Sie den Beispielcode und die Tutorials, um zu lernen, wie Sie die Bibliothek effektiv einsetzen.

### F: Wie lade ich ein Textdokument mit Aspose.Words für Java?

A: Verwenden Sie die Klasse `TxtLoadOptions` zusammen mit dem `Document`‑Konstruktor. Geben Sie Optionen wie Listenerkennung, Leerzeichen‑Verarbeitung oder Text­richtung an, wie in den oben beschriebenen Schritt‑für‑Schritt‑Abschnitten gezeigt.

### F: Kann ich ein geladenes Textdokument in andere Formate konvertieren?

A: Ja. Nachdem Sie die TXT‑Datei in ein `Document`‑Objekt geladen haben, rufen Sie `doc.save("output.pdf")`, `doc.save("output.docx")` oder ein anderes unterstütztes Format auf.

### F: Wie gehe ich mit Leerzeichen in geladenen Textdokumenten um?

A: Steuern Sie führende und nachfolgende Leerzeichen mit `TxtLeadingSpacesOptions` und `TxtTrailingSpacesOptions`. Setzen Sie sie auf `TRIM`, um unerwünschte Leerzeichen zu entfernen, oder auf `PRESERVE`, wenn Sie die ursprüngliche Abstände beibehalten müssen.

### F: Welche Bedeutung hat die Text­richtung in Aspose.Words für Java?

A: Die Text­richtung sorgt für die korrekte Darstellung von Rechts‑nach‑Links‑Schriften (Hebräisch, Arabisch usw.). Durch das Setzen von `DocumentDirection` stellen Sie sicher, dass Bidi‑Text im resultierenden Dokument richtig angezeigt wird.

### F: Wo finde ich weitere Ressourcen und Support für Aspose.Words für Java?

A: Besuchen Sie die [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) für API‑Referenzen, Code‑Beispiele und detaillierte Anleitungen. Sie können auch die Aspose‑Community‑Foren beitreten oder den Aspose‑Support für spezifische Fragen kontaktieren.

### F: Ist Aspose.Words für Java für kommerzielle Projekte geeignet?

A: Ja. Es bietet Lizenzierungsoptionen für sowohl private als auch kommerzielle Nutzung. Prüfen Sie die Lizenzbedingungen auf der Aspose‑Website, um den passenden Plan für Ihr Projekt zu wählen.

## Fazit

Sie verfügen nun über ein vollständiges Toolkit, um **txt‑Dateien zu laden**, **Listen zu erkennen**, **Leerzeichen zu entfernen** und **die Richtung festzulegen**, wenn Sie Nur‑Text in reichhaltige Word‑Dokumente mit Aspose.Words für Java konvertieren. Nutzen Sie diese Muster, um Dokumenten‑Workflows zu automatisieren, die mehrsprachige Unterstützung zu verbessern und jedes Mal ein sauberes, professionelles Ergebnis zu gewährleisten.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}