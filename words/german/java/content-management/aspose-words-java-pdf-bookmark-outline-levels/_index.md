---
date: '2026-04-02'
description: Erfahren Sie, wie Sie verschachtelte Lesezeichen erstellen, Lesezeichen‑Gliederungsebenen
  festlegen und Word‑Dokumente mit Aspose.Words für Java als PDFs speichern.
keywords:
- create nested bookmarks
- how to set bookmark
- save word pdf bookmarks
title: Erstellen von verschachtelten Lesezeichen und Festlegen von Gliederungsebenen
  in PDFs mit Aspose.Words für Java
url: /de/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen von verschachtelten Lesezeichen und Festlegen von Gliederungsebenen in PDFs mit Aspose.Words für Java

## Einführung
Haben Sie Schwierigkeiten, Lesezeichen beim Konvertieren von Word‑Dokumenten in PDFs zu verwalten? **Dieses Tutorial zeigt Ihnen, wie Sie verschachtelte Lesezeichen erstellen**, deren Gliederungsebenen konfigurieren und das Ergebnis als sauberes, navigierbares PDF mit Aspose.Words für Java speichern. Am Ende dieser Anleitung haben Sie ein professionell aussehendes PDF, in dem Leser direkt zu den benötigten Abschnitten springen können.

**Was Sie lernen werden**
- Aspose.Words für Java in Ihrem Projekt einrichten  
- **Verschachtelte Lesezeichen** in einem Word‑Dokument erstellen  
- **Wie man Lesezeichen‑Gliederungsebenen** für klare Hierarchie festlegt  
- **Word‑PDF‑Lesezeichen** mit der korrekten Struktur speichern  

### Schnelle Antworten
- **Was ist die primäre Klasse zum Erstellen von Dokumenten?** `DocumentBuilder`  
- **Welche Methode fügt eine Lesezeichen‑Gliederungsebene hinzu?** `BookmarksOutlineLevels.add()`  
- **Benötige ich eine Lizenz zum Exportieren von PDFs?** Eine Lizenz ist für die Produktion erforderlich; eine kostenlose Testversion funktioniert für die Evaluierung.  
- **Kann ich Lesezeichen beliebig tief verschachteln?** Ja, aber halten Sie die Hierarchie für Endbenutzer lesbar.  
- **Welche Version von Aspose.Words wird benötigt?** Version 25.3 oder neuer.  

## Was bedeutet „verschachtelte Lesezeichen erstellen“?
Verschachtelte Lesezeichen sind Lesezeichen, die innerhalb anderer Lesezeichen platziert werden und eine Eltern‑Kind‑Hierarchie bilden. In einem PDF erscheinen sie als ausklappbare Elemente im Lesezeichen‑Bereich, sodass Leser Abschnitte bei Bedarf ein- oder ausklappen können.

## Warum Gliederungsebenen für Lesezeichen festlegen?
Gliederungsebenen definieren die visuelle Verschachtelungsreihenfolge im Lesezeichen‑Bereich eines PDFs. Richtige Ebenen verbessern die Navigation, insbesondere in langen Rechtsverträgen, technischen Berichten oder E‑Books, in denen Benutzer Informationen schnell finden müssen.

## Voraussetzungen
- **Bibliotheken und Abhängigkeiten**: Aspose.Words für Java (Version 25.3 oder neuer).  
- **Umgebung**: JDK 8+ und eine IDE wie IntelliJ IDEA oder Eclipse.  
- **Kenntnisse**: Grundlegendes Java, Maven‑ oder Gradle‑Kenntnisse.  

### Einrichtung von Aspose.Words
Fügen Sie die Bibliothek Ihrem Projekt mit Maven oder Gradle hinzu.

**Maven**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Lizenzbeschaffung
Aspose.Words ist ein kommerzielles Produkt, aber Sie können mit einer kostenlosen Testversion beginnen.

1. **Kostenlose Testversion** – Laden Sie von der [Aspose‑Release‑Seite](https://releases.aspose.com/words/java/) herunter, um die vollen Funktionen zu testen.  
2. **Temporäre Lizenz** – Beantragen Sie sie auf der [temporären Lizenz‑Seite von Aspose](https://purchase.aspose.com/temporary-license/), wenn Sie einen kurzzeitigen Schlüssel benötigen.  
3. **Kauf** – Kaufen Sie eine permanente Lizenz über das [Kauf‑Portal von Aspose](https://purchase.aspose.com/buy).

Initialisieren Sie die Lizenzdatei in Ihrem Code, bevor Sie irgendeine Aspose‑API verwenden, um alle Funktionen freizuschalten.

## Implementierungs‑Leitfaden

### Wie man verschachtelte Lesezeichen in einem Word‑Dokument erstellt
Wir erstellen ein einfaches Dokument und fügen drei Lesezeichen hinzu, von denen eines ein weiteres Lesezeichen enthält.

#### Schritt 1: Dokument und Builder initialisieren
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### Schritt 2: Erstes (übergeordnetes) Lesezeichen einfügen
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Schritt 3: Ein zweites Lesezeichen innerhalb des ersten verschachteln
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Schritt 4: Das äußere Lesezeichen schließen
```java
builder.endBookmark("Bookmark 1");
```

#### Schritt 5: Ein unabhängiges drittes Lesezeichen hinzufügen
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Wie man Lesezeichen‑Gliederungsebenen für den PDF‑Export festlegt
Jetzt konfigurieren wir die Gliederungshierarchie, die im finalen PDF erscheinen wird.

#### Schritt 1: `PdfSaveOptions` vorbereiten
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Schritt 2: Gliederungsebenen jedem Lesezeichen zuweisen
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Schritt 3: Dokument als PDF mit den konfigurierten Lesezeichen speichern
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Häufige Probleme und Lösungen
- **Fehlende Lesezeichen** – Stellen Sie sicher, dass jedes `startBookmark` ein passendes `endBookmark` hat.  
- **Falsche Hierarchie** – Überprüfen Sie die zugewiesenen Ebenennummern; eine niedrigere Zahl bedeutet eine höhere (übergeordnete) Ebene.  
- **Lizenz nicht angewendet** – Wenn Lesezeichen verschwinden, stellen Sie sicher, dass die Lizenzdatei vor jeder Dokumentverarbeitung geladen wird.  

## Praktische Anwendungen
1. **Rechtsverträge** – Schnell zu Klauseln, Unterklauseln und Anhängen springen.  
2. **Technische Berichte** – Abschnitte, Tabellen und Abbildungen ohne Scrollen navigieren.  
3. **E‑Learning‑Material** – Studenten ermöglichen, Kapitel zu erweitern und Beispiele bei Bedarf zu reduzieren.  

## Leistungstipps
- Entfernen Sie ungenutzte Abschnitte oder Bilder vor dem Speichern, um die PDF‑Größe klein zu halten.  
- Bei sehr großen Dokumenten rufen Sie `doc.cleanup()` auf oder verarbeiten die Datei in Teilen, um den Speicherverbrauch zu reduzieren.  

## Häufig gestellte Fragen

**F: Wie installiere ich Aspose.Words für Java?**  
A: Fügen Sie die oben gezeigte Maven‑ oder Gradle‑Abhängigkeit hinzu, legen Sie dann Ihre Lizenzdatei im Projekt ab und initialisieren Sie sie im Code.  

**F: Kann ich Lesezeichen ohne Festlegen von Gliederungsebenen verwenden?**  
A: Ja, aber ohne Gliederungsebenen zeigt der Lesezeichen‑Bereich des PDFs eine flache Liste, was die Navigation erschwert.  

**F: Gibt es ein Limit, wie tief Lesezeichen verschachtelt werden können?**  
A: Technisch gibt es kein Limit, aber halten Sie die Hierarchie mit 3‑4 Ebenen für die Lesbarkeit der Benutzer angemessen.  

**F: Wie geht Aspose mit sehr großen Word‑Dateien um?**  
A: Die Bibliothek streamt Inhalte und bietet Methoden wie `Document.optimizeResources()`, um den Speicherverbrauch gering zu halten.  

**F: Kann ich die Lesezeichen nach der PDF‑Erstellung bearbeiten?**  
A: Ja, Sie können Aspose.PDF für Java verwenden, um Lesezeichentitel, Ziele oder die Hierarchie nach der Erstellung zu ändern.  

## Ressourcen
- [Aspose.Words Dokumentation](https://reference.aspose.com/words/java/)
- [Neueste Releases herunterladen](https://releases.aspose.com/words/java/)
- [Lizenz kaufen](https://purchase.aspose.com/buy)
- [Kostenlose Testversion](https://releases.aspose.com/words/java/)
- [Antrag auf temporäre Lizenz](https://purchase.aspose.com/temporary-license/)
- [Aspose Support‑Forum](https://forum.aspose.com/c/words/10)

---

**Zuletzt aktualisiert:** 2026-04-02  
**Getestet mit:** Aspose.Words 25.3 für Java  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}