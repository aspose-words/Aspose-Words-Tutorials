---
date: 2025-12-24
description: Erfahren Sie, wie Sie mit Aspose.Words für Java eine Nur‑Text‑Datei aus
  Word‑Dokumenten erstellen. Dieser Leitfaden zeigt, wie Sie Word in TXT konvertieren,
  Tab‑Einrückungen verwenden und Word als TXT speichern.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Wie man eine Textdatei mit Aspose.Words für Java erstellt
url: /de/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man eine Textdatei mit Aspose.Words für Java erstellt

## Einführung in das Speichern von Dokumenten als Textdateien in Aspose.Words für Java

In diesem Tutorial lernen Sie **wie man eine reine Textdatei** aus einem Word-Dokument mit der Aspose.Words für Java-Bibliothek erstellt. Egal, ob Sie **Word in TXT konvertieren**, die Berichtserstellung automatisieren oder einfach Rohtext für weitere Verarbeitung extrahieren müssen, führt Sie diese Anleitung durch den gesamten Arbeitsablauf – von der Dokumenterstellung bis zur Feinabstimmung der Speicheroptionen wie **Tab‑Einrückung verwenden** oder Bidi‑Markierungen hinzufügen. Lassen Sie uns beginnen!

## Schnelle Antworten
- **Was ist die primäre Klasse zum Erstellen eines Dokuments?** `Document` von Aspose.Words.
- **Welche Option fügt Bidi‑Markierungen für Rechts‑nach‑Links‑Sprachen hinzu?** `TxtSaveOptions.setAddBidiMarks(true)`.
- **Wie kann ich Listenelemente mit Tabs einrücken?** Setzen Sie `ListIndentation.Character` auf `'\t'`.
- **Benötige ich eine Lizenz für die Entwicklung?** Eine kostenlose Testversion funktioniert für Tests; für die Produktion ist eine Lizenz erforderlich.
- **Kann ich die Datei mit einem benutzerdefinierten Namen und Pfad speichern?** Ja – übergeben Sie den vollständigen Pfad an `doc.save()`.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllt haben:

- Java Development Kit (JDK) auf Ihrem System installiert.  
- Aspose.Words für Java-Bibliothek in Ihr Projekt integriert. Sie können sie von [hier](https://releases.aspose.com/words/java/) herunterladen.  
- Grundkenntnisse in Java-Programmierung.

## Schritt 1: Dokument erstellen

Um **Word als TXT zu speichern**, benötigen wir zunächst eine `Document`-Instanz. Unten finden Sie ein einfaches Java‑Snippet, das ein Dokument erstellt und ein paar Zeilen mehrsprachigen Textes schreibt:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

In diesem Code erstellen wir ein neues Dokument, fügen englischen, hebräischen und arabischen Text hinzu und aktivieren die Rechts‑nach‑Links‑Formatierung für den hebräischen Absatz.

## Schritt 2: Text‑Speicheroptionen definieren

Als Nächstes konfigurieren wir, wie das Dokument als reine Textdatei gespeichert wird. Aspose.Words stellt die Klasse `TxtSaveOptions` bereit, mit der Sie alles von Bidi‑Markierungen bis zur Listeneinrückung steuern können.

### Beispiel 1: Bidi‑Markierungen hinzufügen (wie man TXT mit korrekter RTL‑Unterstützung speichert)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Das Setzen von `AddBidiMarks` auf `true` stellt sicher, dass Rechts‑nach‑Links‑Zeichen im resultierenden **reinen Textdatei** korrekt dargestellt werden.

### Beispiel 2: Tab‑Zeichen für Listeneinrückung verwenden (Tab‑Einrückung verwenden)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Hier weisen wir Aspose.Words an, vor jeder Listenschicht ein Tab‑Zeichen (`'\t'`) vorzusetzen, wodurch die Textausgabe leichter lesbar wird.

## Schritt 3: Dokument als Text speichern

Jetzt, da die Speicheroptionen bereit sind, können Sie das Dokument als **reine Textdatei** speichern:

```java
doc.save("output.txt", saveOptions);
```

Ersetzen Sie `"output.txt"` durch den vollständigen Pfad, an dem Sie die Datei speichern möchten.

## Vollständiger Quellcode zum Speichern von Dokumenten als Textdateien in Aspose.Words für Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Häufige Probleme und Lösungen

| Problem | Lösung |
|-------|----------|
| **Bidi‑Zeichen erscheinen als unlesbarer Text** | Stellen Sie sicher, dass `setAddBidiMarks(true)` aktiviert ist und die Ausgabedatei mit UTF‑8‑Kodierung geöffnet wird. |
| **Listeneinrückung sieht falsch aus** | Überprüfen Sie, ob `ListIndentation.Count` und `Character` auf die gewünschten Werte (Tab `'\t'` oder Leerzeichen `' '` ) gesetzt sind. |
| **Datei wurde nicht erstellt** | Prüfen Sie, ob der Verzeichnispfad existiert und die Anwendung Schreibrechte hat. |

## Häufig gestellte Fragen

### Wie füge ich Bidi‑Markierungen zur Textausgabe hinzu?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Kann ich das Listeneinrückungszeichen anpassen?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Ist Aspose.Words für Java geeignet für die Verarbeitung mehrsprachigen Textes?

Ja, Aspose.Words für Java unterstützt eine breite Palette von Sprachen und Zeichenkodierungen, was es ideal macht, mehrsprachige Inhalte als reine Textdatei zu extrahieren und zu speichern.

### Wie kann ich weitere Dokumentation und Ressourcen für Aspose.Words für Java erhalten?

Sie finden umfassende Dokumentation und Ressourcen auf der Aspose.Words für Java Dokumentationsseite: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Wo kann ich Aspose.Words für Java herunterladen?

Sie können die Bibliothek von der offiziellen Seite herunterladen: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Was ist, wenn ich **Word in TXT** in einem Batch‑Prozess konvertieren muss?

Umwickeln Sie den oben gezeigten Code in einer Schleife, die jede `.docx`‑Datei lädt, dieselben `TxtSaveOptions` anwendet und jede als `.txt` speichert. Stellen Sie sicher, dass Sie Ressourcen verwalten, indem Sie `Document`‑Objekte nach jeder Iteration freigeben.

### Unterstützt die API das direkte Speichern in einen Stream anstatt in eine Datei?

Ja, Sie können einen `OutputStream` an `doc.save(outputStream, saveOptions)` übergeben, um in‑Speicher‑Verarbeitung oder die Integration mit Web‑Services zu ermöglichen.

---

**Zuletzt aktualisiert:** 2025-12-24  
**Getestet mit:** Aspose.Words für Java 24.12 (neueste)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}