---
date: '2026-04-27'
description: Erfahren Sie, wie Sie Lesezeichen setzen und PDFs mit Lesezeichen mithilfe
  von Aspose.Words für Java speichern. Verbessern Sie die Lesbarkeit und Navigation
  mit diesem umfassenden Leitfaden.
keywords:
- how to set bookmarks
- save pdf with bookmarks
- create nested bookmarks
- generate pdf with bookmarks
- convert word pdf bookmarks
title: Wie man Lesezeichen in PDFs mit Aspose.Words Java setzt
url: /de/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Lesezeichen in PDFs mit Aspose.Words Java setzt

## Einführung
Wenn Sie Schwierigkeiten haben, **wie man Lesezeichen setzt** beim Konvertieren von Word‑Dokumenten in PDFs, sind Sie hier genau richtig. In diesem Tutorial führen wir Sie durch den gesamten Prozess mit Aspose.Words für Java, von der Erstellung verschachtelter Lesezeichen bis zur Konfiguration ihrer Outline‑Level, sodass das endgültige PDF sauber, professionell und leicht zu navigieren ist.

**Was Sie lernen werden**
- Aspose.Words für Java in Ihrem Projekt einrichten  
- **Verschachtelte Lesezeichen** in einem Word‑Dokument erstellen  
- **Outline‑Level für Lesezeichen** konfigurieren, um eine strukturierte PDF‑Gliederung zu erhalten  
- **PDF mit Lesezeichen** speichern, das die von Ihnen definierte Hierarchie widerspiegelt  

### Schnellantworten
- **Welche Hauptklasse wird zum Erstellen von Dokumenten verwendet?** `DocumentBuilder`  
- **Welche Option steuert die Lesezeichen‑Hierarchie?** `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()`  
- **Kann ich Maven oder Gradle verwenden?** Ja, beide werden unterstützt (siehe Code‑Snippets)  
- **Benötige ich eine Lizenz?** Eine Testversion funktioniert für die Evaluierung; eine permanente Lizenz ist für die Produktion erforderlich  
- **Behält das PDF verschachtelte Lesezeichen bei?** Absolut, wenn die Outline‑Level korrekt gesetzt sind  

## Was bedeutet „wie man Lesezeichen setzt“ in einem PDF?
Lesezeichen zu setzen bedeutet, anklickbare Einträge im Navigationsbereich eines PDFs zu definieren, die zu bestimmten Abschnitten des Dokuments springen. Wenn Lesezeichen verschachtelt und Outline‑Level zugewiesen werden, erscheinen sie als zusammenklappbarer Baum, was die Navigation in großen Dokumenten erheblich erleichtert.

## Warum Aspose.Words für Lesezeichen‑Outline‑Level verwenden?
Aspose.Words gibt Ihnen die vollständige programmgesteuerte Kontrolle über die Word‑zu‑PDF‑Konvertierung, einschließlich der Möglichkeit, **PDFs mit Lesezeichen** zu erzeugen, die die Struktur Ihres Dokuments widerspiegeln. Das eliminiert manuellen Nachbearbeitungsaufwand und sorgt für ein konsistentes Benutzererlebnis in allen erzeugten PDFs.

## Voraussetzungen
- **Bibliotheken und Abhängigkeiten**: Aspose.Words für Java (Version 25.3 oder höher).  
- **Umgebung**: JDK 8 oder neuer, IDE wie IntelliJ IDEA oder Eclipse.  
- **Kenntnisse**: Grundlegendes Java, Erfahrung mit Maven oder Gradle.

## Aspose.Words einrichten
Fügen Sie die benötigte Bibliothek zu Ihrem Build‑System hinzu.

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
Aspose.Words ist ein kommerzielles Produkt, aber Sie können mit einer kostenlosen Testversion starten.

1. **Kostenlose Testversion**: Laden Sie sie von der [Aspose‑Release‑Seite](https://releases.aspose.com/words/java/) herunter, um die vollen Funktionen zu testen.  
2. **Temporäre Lizenz**: Beantragen Sie eine temporäre Lizenz auf der [temporären Lizenz‑Seite von Aspose](https://purchase.aspose.com/temporary-license/), falls nötig.  
3. **Kauf**: Für den dauerhaften Einsatz erwerben Sie eine Lizenz über das [Kauf‑Portal von Aspose](https://purchase.aspose.com/buy).

Initialisieren Sie die Lizenzdatei in Ihrem Code, um alle Funktionen freizuschalten.

## Implementierungs‑Leitfaden
Im Folgenden finden Sie eine Schritt‑für‑Schritt‑Durchführung, die **verschachtelte Lesezeichen erstellen**, deren Outline‑Level setzen und schließlich **PDF mit Lesezeichen speichern** abdeckt.

### Verschachtelte Lesezeichen erstellen
**Übersicht**: Erstellen Sie ein Word‑Dokument und betten Sie Lesezeichen ein, die eine Hierarchie widerspiegeln.

#### Schritt 1: Dokument und Builder initialisieren
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Damit wird ein frisches Dokument erstellt, das bereit für das Einfügen von Inhalten ist.

#### Schritt 2: Verschachtelte Lesezeichen einfügen
Beginnen Sie mit einem primären Lesezeichen und verschachteln Sie ein zweites darin.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

```java
builder.endBookmark("Bookmark 1");
```

#### Schritt 3: Weitere Lesezeichen hinzufügen
Sie können nach Bedarf weitere unabhängige Lesezeichen hinzufügen.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Outline‑Level für Lesezeichen konfigurieren
**Übersicht**: Weisen Sie Outline‑Level zu, sodass der Lesezeichen‑Bereich des PDFs die gewünschte Hierarchie widerspiegelt.

#### Schritt 1: PdfSaveOptions einrichten
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Diese Optionen werden beim Speichern des Dokuments als PDF verwendet.

#### Schritt 2: Outline‑Level hinzufügen
Ordnen Sie jedem Lesezeichennamen ein Outline‑Level zu (1 = Oberste Ebene, 2 = Unterebene usw.).

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Schritt 3: Dokument speichern
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Das resultierende PDF enthält nun einen strukturierten Lesezeichen‑Baum.

## Häufige Probleme und Lösungen
- **Fehlende Lesezeichen** – Stellen Sie sicher, dass jedes `startBookmark` ein entsprechendes `endBookmark` hat.  
- **Falsche Hierarchie** – Prüfen Sie die Outline‑Level‑Zahlen; ein Kind muss eine höhere Nummer als sein Elternteil haben.  
- **Große Dokumente** – Rufen Sie `doc.removeUnusedResources()` vor dem Speichern auf, um die Dateigröße zu reduzieren.

## Praktische Anwendungsfälle
1. **Rechtsverträge** – Schnell zu Klauseln und Unterklauseln springen.  
2. **Jahresberichte** – Abschnitte, Tabellen und Diagramme mühelos navigieren.  
3. **E‑Learning‑Material** – Ein klickbares Inhaltsverzeichnis für Lernende bereitstellen.

## Leistungsüberlegungen
- Entfernen Sie unnötige Knoten vor der Konvertierung, um das PDF leichtgewichtig zu halten.  
- Bei sehr großen Dateien sollten Sie das Dokument streamen, um den Speicherverbrauch zu minimieren.

## Fazit
Sie wissen jetzt **wie man Lesezeichen setzt**, deren Outline‑Level konfiguriert und **PDF mit Lesezeichen** mithilfe von Aspose.Words für Java speichert. Diese Technik verbessert die PDF‑Navigation erheblich und verleiht Ihren Dokumenten ein professionelles Finish.

**Nächste Schritte**: Versuchen Sie, benutzerdefinierte Symbole zu Lesezeichen hinzuzufügen oder diesen Workflow in einen Batch‑Verarbeitungs‑Service zu integrieren.

## Häufig gestellte Fragen

**F: Wie installiere ich Aspose.Words für Java?**  
A: Fügen Sie die oben gezeigte Maven‑ oder Gradle‑Abhängigkeit hinzu und platzieren Sie Ihre Lizenzdatei im Ressourcen‑Ordner des Projekts.

**F: Kann ich Lesezeichen ohne Outline‑Level erstellen?**  
A: Ja, aber ohne Outline‑Level wird der Navigationsbereich des PDFs alle Lesezeichen auf derselben Ebene auflisten, was die Durchsuchung großer Dokumente erschwert.

**F: Gibt es ein Limit, wie tief Lesezeichen verschachtelt werden können?**  
A: Technisch gibt es kein Limit, aber halten Sie die Hierarchie für Endbenutzer lesbar – in der Regel reichen 3‑4 Ebenen aus.

**F: Wie geht Aspose mit sehr großen Word‑Dateien um?**  
A: Es streamt den Inhalt und bietet Methoden wie `Document.optimizeResources()`, um den Speicherverbrauch gering zu halten.

**F: Kann ich die Lesezeichen nach der PDF‑Erstellung bearbeiten?**  
A: Ja, Sie können Aspose.PDF für Java verwenden, um Lesezeichentitel, Ziele oder die Hierarchie nach der Konvertierung zu ändern.

---

**Zuletzt aktualisiert:** 2026-04-27  
**Getestet mit:** Aspose.Words 25.3 für Java  
**Autor:** Aspose  

## Ressourcen
- [Aspose.Words Dokumentation](https://reference.aspose.com/words/java/)
- [Neueste Releases herunterladen](https://releases.aspose.com/words/java/)
- [Lizenz erwerben](https://purchase.aspose.com/buy)
- [Kostenlose Testversion](https://releases.aspose.com/words/java/)
- [Antrag für temporäre Lizenz](https://purchase.aspose.com/temporary-license/)
- [Aspose Support‑Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}