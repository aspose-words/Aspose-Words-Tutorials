---
title: Inhaltsverzeichnisgenerierung
linktitle: Inhaltsverzeichnisgenerierung
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words für Java dynamische Inhaltsverzeichnisse erstellen. Meistern Sie die Inhaltsverzeichnisgenerierung mit Schritt-für-Schritt-Anleitung und Quellcodebeispielen.
weight: 14
url: /de/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inhaltsverzeichnisgenerierung

## Einführung

Hatten Sie schon einmal Probleme damit, ein dynamisches und professionell aussehendes Inhaltsverzeichnis (TOC) in Ihren Word-Dokumenten zu erstellen? Dann sind Sie hier richtig! Mit Aspose.Words für Java können Sie den gesamten Prozess automatisieren, Zeit sparen und Genauigkeit gewährleisten. Egal, ob Sie einen umfassenden Bericht oder eine wissenschaftliche Arbeit erstellen, dieses Tutorial führt Sie durch die programmgesteuerte Generierung eines Inhaltsverzeichnisses mit Java. Bereit, loszulegen? Dann legen wir los!

## Voraussetzungen

Bevor wir mit der Codierung beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Java Development Kit (JDK): Auf Ihrem System installiert. Sie können es herunterladen von[Website von Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Aspose.Words für Java-Bibliothek: Laden Sie die neueste Version von der[Veröffentlichungsseite](https://releases.aspose.com/words/java/).
3. Integrierte Entwicklungsumgebung (IDE): Wie IntelliJ IDEA, Eclipse oder NetBeans.
4.  Aspose Temporäre Lizenz: Um Evaluierungsbeschränkungen zu vermeiden, erhalten Sie eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).

## Pakete importieren

Um Aspose.Words für Java effektiv zu nutzen, stellen Sie sicher, dass Sie die erforderlichen Klassen importieren. Hier sind die Importe:

```java
import com.aspose.words.*;
```

Befolgen Sie diese Schritte, um ein dynamisches Inhaltsverzeichnis in Ihrem Word-Dokument zu generieren.

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

 Der erste Schritt besteht darin, ein neues Dokument zu erstellen und die`DocumentBuilder` Klasse, um es zu manipulieren.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Stellt das Word-Dokument dar.
- `DocumentBuilder`: Eine Hilfsklasse, die eine einfache Bearbeitung des Dokuments ermöglicht.

## Schritt 2: Inhaltsverzeichnis einfügen

Fügen wir nun das Inhaltsverzeichnis am Anfang des Dokuments ein.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Fügt ein Inhaltsverzeichnisfeld ein. Die Parameter geben an:
  - `\o "1-3"`: Überschriften der Ebenen 1 bis 3 einschließen.
  - `\h`: Einträge mit Hyperlinks versehen.
  - `\z`: Seitenzahlen für Webdokumente unterdrücken.
  - `\u`: Stile für Hyperlinks beibehalten.
- `insertBreak`: Fügt nach dem Inhaltsverzeichnis einen Seitenumbruch hinzu.

## Schritt 3: Überschriften zum Ausfüllen des Inhaltsverzeichnisses hinzufügen

Um das Inhaltsverzeichnis zu füllen, müssen Sie Absätze mit Überschriftenstilen hinzufügen.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : Legt den Absatzstil für eine bestimmte Überschriftenebene fest (z. B.`HEADING_1`, `HEADING_2`).
- `writeln`: Fügt dem Dokument Text im angegebenen Stil hinzu.

## Schritt 4: Verschachtelte Überschriften hinzufügen

Um Inhaltsverzeichnisebenen anzuzeigen, schließen Sie verschachtelte Überschriften ein.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Fügen Sie Überschriften tieferer Ebenen hinzu, um die Hierarchie im Inhaltsverzeichnis anzuzeigen.

## Schritt 5: Inhaltsverzeichnisfelder aktualisieren

Das Inhaltsverzeichnisfeld muss aktualisiert werden, um die neuesten Überschriften anzuzeigen.


```java
doc.updateFields();
```

- `updateFields`: Aktualisiert alle Felder im Dokument und stellt sicher, dass das Inhaltsverzeichnis die hinzugefügten Überschriften widerspiegelt.

## Schritt 6: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im gewünschten Format.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Exportiert das Dokument in eine`.docx` Datei. Sie können andere Formate angeben, wie`.pdf` oder`.txt` falls erforderlich.

## Abschluss

Herzlichen Glückwunsch! Sie haben mit Aspose.Words für Java erfolgreich ein dynamisches Inhaltsverzeichnis in einem Word-Dokument erstellt. Mit nur wenigen Codezeilen haben Sie eine Aufgabe automatisiert, die sonst Stunden dauern könnte. Und was kommt als Nächstes? Experimentieren Sie mit verschiedenen Überschriftenstilen und -formaten, um Ihr Inhaltsverzeichnis an Ihre spezifischen Anforderungen anzupassen.

## Häufig gestellte Fragen

### Kann ich das Inhaltsverzeichnisformat weiter anpassen?
Auf jeden Fall! Sie können Inhaltsverzeichnisparameter anpassen, z. B. Seitenzahlen einfügen, Text ausrichten oder benutzerdefinierte Überschriftenstile verwenden.

### Ist für Aspose.Words für Java eine Lizenz obligatorisch?
 Ja, für die volle Funktionalität ist eine Lizenz erforderlich. Sie können mit einer[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).

### Kann ich ein Inhaltsverzeichnis für ein vorhandenes Dokument generieren?
 Ja! Laden Sie das Dokument in ein`Document` -Objekt und befolgen Sie dieselben Schritte zum Einfügen und Aktualisieren des Inhaltsverzeichnisses.

### Funktioniert dies für PDF-Exporte?
 Ja, das Inhaltsverzeichnis erscheint im PDF, wenn Sie das Dokument speichern in`.pdf` Format.

### Wo finde ich weitere Dokumentation?
 Schauen Sie sich die[Aspose.Words für Java-Dokumentation](https://reference.aspose.com/words/java/) für weitere Beispiele und Einzelheiten.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
