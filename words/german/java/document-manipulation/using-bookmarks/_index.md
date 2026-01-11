---
date: 2026-01-11
description: Erfahren Sie, wie Sie Lesezeichen ein- und ausblenden und Lesezeichen
  in Java mit Aspose.Words für Java erstellen, um eine effiziente Dokumentennavigation
  und -manipulation zu ermöglichen.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Lesezeichen anzeigen/ausblenden mit Aspose.Words für Java
url: /de/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lesezeichen ein‑ und ausblenden mit Aspose.Words für Java

## Einführung in die Verwendung von Lesezeichen in Aspose.Words für Java

Lesezeichen sind ein leistungsstarkes Feature in Aspose.Words für Java, das es Ihnen ermöglicht, **create bookmark java**, zu bestimmten Inhalten zu navigieren und sogar **show hide bookmarks**, wenn Sie verschiedene Dokumentversionen erzeugen müssen. In diesem Schritt‑für‑Schritt‑Leitfaden gehen wir auf das Erstellen, Zugreifen, Aktualisieren, Kopieren und Umschalten der Sichtbarkeit von Lesezeichen ein und geben Ihnen volle Kontrolle über die Dokumentmanipulation.

## Schnelle Antworten
- **What is the primary purpose of bookmarks?** Um bestimmte Teile eines Dokuments zu markieren und später abzurufen.  
- **Can I hide bookmark markers in the final output?** Ja—verwenden Sie die show/hide API, um deren Sichtbarkeit umzuschalten.  
- **How do I create a bookmark inside a table cell?** Starten und beenden Sie das Lesezeichen mit `DocumentBuilder`, während sich der Cursor innerhalb der Zelle befindet.  
- **Is it possible to copy bookmarked text to another document?** Absolut—verwenden Sie `NodeImporter`, um die Formatierung beizubehalten.  
- **What version of Aspose.Words is required?** Jede aktuelle Version; der Code funktioniert mit dem neuesten Build von 2026.

## Was ist „show hide bookmarks“?

Das **show hide bookmarks**-Feature ermöglicht es Ihnen, Lesezeichen‑Begrenzer im gespeicherten Dokument programmgesteuert anzuzeigen oder zu verbergen. Dies ist nützlich, wenn Sie saubere Ausgaben für Endbenutzer erzeugen möchten, während Sie gleichzeitig Lesezeichendaten für die interne Verarbeitung behalten.

## Warum Lesezeichen in der Java‑Dokumentenautomatisierung verwenden?

- **Effiziente Navigation** – Springen Sie direkt zu Abschnitten, ohne die gesamte Datei zu durchsuchen.  
- **Dynamische Inhaltserstellung** – Fügen Sie Text ein, ersetzen oder entfernen Sie Text, der an ein Lesezeichen gebunden ist.  
- **Bedingte Sichtbarkeit** – Zeigen oder verbergen Sie Lesezeichen‑Marker basierend auf Benutzereinstellungen oder dem Ausgabeformat.  
- **Wiederverwendbarkeit** – Kopieren Sie markierte Fragmente zwischen Dokumenten, während Sie die Stile beibehalten.

## Voraussetzungen
- Java Development Kit (JDK) 8 oder höher.  
- Aspose.Words for Java-Bibliothek zu Ihrem Projekt hinzugefügt (Maven/Gradle oder JAR).  
- Grundlegende Kenntnisse der Klassen `Document` und `DocumentBuilder`.

## Schritt‑für‑Schritt‑Anleitung

### Schritt 1: Lesezeichen erstellen (create bookmark java)

Um ein Lesezeichen hinzuzufügen, starten Sie es, schreiben den Inhalt und beenden es anschließend. Dieses Beispiel erstellt ein einfaches Lesezeichen mit dem Namen **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Schritt 2: Lesezeichen zugreifen (access bookmarks java)

Lesezeichen können entweder über ihren nullbasierten Index oder über den Namen abgerufen werden. Der untenstehende Code demonstriert beide Ansätze.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Schritt 3: Lesezeichendaten aktualisieren (update bookmark text)

Sie können ein Lesezeichen umbenennen oder dessen Textinhalt ersetzen. Das ist praktisch, wenn das zugrunde liegende Dokument geändert wird.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Schritt 4: Mit markiertem Text arbeiten (copy bookmarked text)

Das Kopieren eines markierten Fragmentes in ein anderes Dokument bei gleichzeitiger Beibehaltung der ursprünglichen Formatierung ist mit `NodeImporter` unkompliziert.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Schritt 5: Lesezeichen ein‑ und ausblenden (show hide bookmarks)

Das folgende Snippet zeigt, wie Sie die Marker eines Lesezeichens in der gespeicherten Datei ausblenden können. Übergeben Sie `false`, um zu verbergen, `true`, um anzuzeigen.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Schritt 6: Zeilen‑Lesezeichen entwirren (bookmark table cell)

Wenn Lesezeichen über Tabellenzeilen hinweg reichen, können sie verknotet werden. Die untenstehenden Hilfsmethoden entwirren sie und ermöglichen das Löschen einer bestimmten Zeile anhand ihres Lesezeichens.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Häufige Probleme und Lösungen

| Problem | Lösung |
|---------|--------|
| **Lesezeichen nicht gefunden** | Stellen Sie sicher, dass der Lesezeichenname exakt (Groß‑/Kleinschreibung beachtend) übereinstimmt und dass das Dokument nach der Erstellung gespeichert wurde. |
| **Kopierter Text verliert die Formatierung** | Verwenden Sie `ImportFormatMode.KEEP_SOURCE_FORMATTING` mit `NodeImporter`, wie in Schritt 4 gezeigt. |
| **Ein‑/Ausblenden wirkt sich nicht auf die Ausgabe aus** | Stellen Sie sicher, dass Sie `showHideBookmarkedContent` **vor** dem Speichern des Dokuments aufrufen. |
| **Lesezeichen in einer Tabellenzelle wird ignoriert** | Setzen Sie die Start‑/End‑Aufrufe, während sich der Builder‑Cursor innerhalb der Zielzelle befindet. |

## Häufig gestellte Fragen

**Q: Wie erstelle ich ein Lesezeichen in einer Tabellenzelle?**  
A: Verwenden Sie `DocumentBuilder`, um den Cursor in die gewünschte Zelle zu bewegen, und rufen Sie dann `startBookmark` und `endBookmark` um den Zelleninhalt herum auf.

**Q: Kann ich ein Lesezeichen in ein anderes Dokument kopieren?**  
A: Ja—verwenden Sie die Klasse `NodeImporter` (siehe Schritt 4), um den markierten Knoten zu importieren und dabei die ursprüngliche Formatierung beizubehalten.

**Q: Wie kann ich eine Zeile anhand ihres Lesezeichens löschen?**  
A: Zuerst finden Sie die Zeile, die das Lesezeichen enthält, und rufen dann `remove` am Zeilen‑Knoten auf (wie in Schritt 6 demonstriert).

**Q: Was sind einige gängige Anwendungsfälle für Lesezeichen?**  
A: Erstellung eines Inhaltsverzeichnisses, Extrahieren spezifischer Abschnitte für Berichte und automatisierte Dokumentenzusammenstellung basierend auf Benutzerauswahlen.

**Q: Wo finde ich weitere Informationen zu Aspose.Words für Java?**  
A: Für detaillierte Dokumentation und Downloads besuchen Sie [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Zuletzt aktualisiert:** 2026-01-11  
**Getestet mit:** Aspose.Words for Java 24.11 (2026)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}