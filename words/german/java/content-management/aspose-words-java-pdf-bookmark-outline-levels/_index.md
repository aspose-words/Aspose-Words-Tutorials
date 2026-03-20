---
date: '2026-03-20'
description: Erfahren Sie, wie Sie verschachtelte Lesezeichen erstellen und PDFs mit
  Lesezeichen mithilfe von Aspose.Words für Java generieren, um die Lesbarkeit und
  Navigation zu verbessern.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Verschachtelte Lesezeichen in PDFs mit Aspose.Words Java erstellen
url: /de/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen von verschachtelten Lesezeichen in PDFs mit Aspose.Words Java

## Einführung
Wenn Sie jemals Schwierigkeiten hatten, PDF‑Lesezeichen nach der Konvertierung eines Word‑Dokuments zu organisieren, sind Sie nicht allein. In diesem Tutorial **erstellen Sie verschachtelte Lesezeichen** und lernen, wie man **PDFs mit Lesezeichen** erzeugt, die sich leicht navigieren lassen. Wir führen Sie durch die Einrichtung von Aspose.Words, den Aufbau einer Lesezeichen‑Hierarchie, das Zuweisen von Gliederungsebenen und schließlich das Exportieren eines sauberen PDFs.

**Was Sie lernen werden**
- Wie man Aspose.Words für Java einrichtet
- Wie man **verschachtelte Lesezeichen** in einem Word‑Dokument erstellt
- Wie man die Gliederungsebenen von Lesezeichen für eine klare PDF‑Navigation konfiguriert
- Wie man **PDFs mit Lesezeichen** erzeugt, die die von Ihnen definierte Hierarchie widerspiegeln

### Schnelle Antworten
- **Was ist die primäre Klasse zum Erstellen von Dokumenten?** `DocumentBuilder`
- **Welche Methode fügt ein Lesezeichen hinzu?** `startBookmark(String name)`
- **Wie setzt man eine Gliederungsebene für ein Lesezeichen?** `outlineLevels.add(name, level)`
- **Benötige ich eine Lizenz für die Produktion?** Ja, eine gekaufte Lizenz schaltet alle Funktionen frei.
- **Kann ich das mit Maven oder Gradle verwenden?** Absolut – beide werden unterstützt.

### Voraussetzungen
Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes haben:
- **Aspose.Words for Java** (Version 25.3 oder höher).  
- Ein installiertes JDK und eine IDE wie IntelliJ IDEA oder Eclipse.  
- Grundlegende Java‑Kenntnisse und Vertrautheit mit Maven oder Gradle.

## Was bedeutet „verschachtelte Lesezeichen erstellen“?
Verschachtelte Lesezeichen zu erstellen bedeutet, ein Lesezeichen innerhalb eines anderen zu platzieren und so eine Eltern‑Kind‑Hierarchie zu bilden. Wenn das Dokument als PDF gespeichert wird, erscheinen diese Beziehungen als zusammenklappbare Einträge im Lesezeichen‑Bereich des PDFs, wodurch große Dokumente deutlich leichter zu durchsuchen sind.

## Warum Gliederungsebenen verwenden, wenn Sie PDFs mit Lesezeichen erzeugen?
Gliederungsebenen definieren die visuelle Hierarchie der Lesezeichen im PDF‑Viewer. Ein Lesezeichen der Ebene 1 erscheint als oberster Eintrag, Ebene 2 als Kind usw. Richtige Gliederungsebenen verwandeln eine flache Liste von Lesezeichen in ein strukturiertes Inhaltsverzeichnis, was besonders bei Rechtsverträgen, technischen Berichten und E‑Books wertvoll ist.

## Einrichtung von Aspose.Words
Fügen Sie die Bibliothek Ihrem Projekt über Maven oder Gradle hinzu.

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Lizenzbeschaffung
Aspose.Words ist ein kommerzielles Produkt, aber Sie können mit einer kostenlosen Testversion beginnen.

1. **Kostenlose Testversion** – Laden Sie von der [Aspose‑Release‑Seite](https://releases.aspose.com/words/java/) herunter, um die vollen Funktionen zu testen.  
2. **Temporäre Lizenz** – Beantragen Sie auf der [temporären Lizenzseite von Aspose](https://purchase.aspose.com/temporary-license/) für eine kurzfristige Evaluierung.  
3. **Kauf** – Erhalten Sie eine permanente Lizenz über das [Kaufportal von Aspose](https://purchase.aspose.com/buy).

Nachdem Sie die `.lic`‑Datei erhalten haben, laden Sie sie in Ihrem Code, um alle Funktionen freizuschalten.

## Implementierungsleitfaden
Im Folgenden finden Sie eine Schritt‑für‑Schritt‑Anleitung zum Erstellen eines Dokuments, Hinzufügen verschachtelter Lesezeichen, Zuweisen von Gliederungsebenen und Speichern des Ergebnisses als PDF.

### Schritt 1: Dokument und Builder initialisieren
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Dies erstellt ein leeres Word‑Dokument und ein Builder‑Objekt, das Sie zum Einfügen von Text und Lesezeichen verwenden.

### Schritt 2: Das erste (Eltern‑)Lesezeichen erstellen
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
Der Aufruf `startBookmark` öffnet ein neues Lesezeichen mit dem Namen **Bookmark 1**. Alles, was Sie nach diesem Aufruf schreiben, gehört zu diesem Lesezeichen, bis Sie es schließen.

### Schritt 3: Ein zweites Lesezeichen innerhalb des ersten verschachteln
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Da dieses Lesezeichen **nach** dem ersten gestartet und **vor** dem ersten geschlossen wird, wird es zum Kind von **Bookmark 1**.

### Schritt 4: Das Eltern‑Lesezeichen schließen
```java
builder.endBookmark("Bookmark 1");
```
Jetzt sieht die Hierarchie folgendermaßen aus:

- Bookmark 1 (Ebene 1)  
  - Bookmark 2 (Ebene 2)

### Schritt 5: Ein unabhängiges drittes Lesezeichen hinzufügen
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```
Dieses Lesezeichen befindet sich auf der obersten Ebene, getrennt von den ersten beiden.

### Schritt 6: Gliederungsebenen für den PDF‑Export konfigurieren
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Das `PdfSaveOptions`‑Objekt ermöglicht Ihnen die Kontrolle darüber, wie Lesezeichen im endgültigen PDF erscheinen.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 1);
```
Hier weisen wir Ebene 1 den Lesezeichen der obersten Ebene und Ebene 2 dem verschachtelten Lesezeichen zu.

### Schritt 7: Das Dokument als PDF speichern
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Das resultierende PDF zeigt einen sauberen, zusammenklappbaren Lesezeichen‑Bereich, der die von Ihnen definierte Hierarchie widerspiegelt.

## Häufige Probleme und Lösungen
- **Fehlende Lesezeichen** – Jeder `startBookmark` muss ein passendes `endBookmark` haben. Wird eines vergessen, wird das Lesezeichen im PDF ignoriert.  
- **Falsche Gliederungsebenen** – Überprüfen Sie die Namen, die Sie an `outlineLevels.add` übergeben, doppelt. Ein Tippfehler bedeutet, dass die Ebene nicht angewendet wird.  
- **Große Dokumente** – Bei sehr großen Dateien rufen Sie `doc.removeMacros()` auf oder löschen Sie ungenutzte Stile, bevor Sie speichern, um die PDF‑Größe angemessen zu halten.

## Praktische Anwendungen
1. **Rechtsverträge** – Schnell zwischen Klauseln und Unterklauseln springen.  
2. **Technische Berichte** – Durch Abschnitte, Tabellen und Abbildungen navigieren, ohne zu scrollen.  
3. **E‑Learning‑Material** – Bieten Sie ein anklickbares Inhaltsverzeichnis für Lernende.

## Leistungstipps
- Entfernen Sie ungenutzte Ressourcen (Bilder, Stile) vor dem Speichern.  
- Verwenden Sie Streaming‑APIs, wenn Sie PDFs größer als 100 MB verarbeiten, um den Speicherverbrauch gering zu halten.

## Fazit
Sie wissen jetzt, wie man **verschachtelte Lesezeichen** erstellt, Gliederungsebenen zuweist und **PDFs mit Lesezeichen** erzeugt, die sowohl funktional als auch benutzerfreundlich sind. Experimentieren Sie mit tieferen Hierarchien oder integrieren Sie diese Logik in Ihre Dokument‑Generierungspipeline für noch mehr Automatisierung.

## Häufig gestellte Fragen

**F: Wie installiere ich Aspose.Words für Java?**  
A: Fügen Sie die oben gezeigte Maven‑ oder Gradle‑Abhängigkeit hinzu und laden Sie Ihre Lizenzdatei zur Laufzeit.

**F: Kann ich Lesezeichen ohne Gliederungsebenen verwenden?**  
A: Ja, aber das PDF zeigt eine flache Liste, die bei komplexen Dokumenten schwer zu navigieren sein kann.

**F: Gibt es ein Limit, wie tief die Lesezeichen‑Verschachtelung gehen kann?**  
A: Technisch gibt es kein Limit, aber halten Sie die Hierarchie vernünftig (3‑4 Ebenen), um die Lesbarkeit zu wahren.

**F: Wie geht Aspose mit sehr großen Dokumenten um?**  
A: Es streamt Inhalte und bietet Speicher‑Management‑Hilfsmittel; dennoch sollten Sie ungenutzte Elemente entfernen.

**F: Kann ich die Lesezeichen nach der PDF‑Erstellung bearbeiten?**  
A: Absolut – verwenden Sie Aspose.PDF für Java, um Lesezeichentitel, Ziele oder Gliederungsebenen nachträglich zu ändern.

## Ressourcen
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Zuletzt aktualisiert:** 2026-03-20  
**Getestet mit:** Aspose.Words for Java 25.3  
**Autor:** Aspose