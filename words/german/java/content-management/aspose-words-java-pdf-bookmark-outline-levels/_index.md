---
date: '2025-11-27'
description: Erfahren Sie, wie Sie Lesezeichen erstellen, PDFs mit Lesezeichen erzeugen
  und Word in PDF in Java mit Aspose.Words konvertieren. Dieser Leitfaden behandelt
  verschachtelte Lesezeichen und Gliederungsebenen.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: de
title: Wie man Lesezeichen erstellt und Gliederungsebenen in PDFs mit Aspose.Words
  Java festlegt
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Lesezeichen erstellt und Gliederungsebenen in PDFs mit Aspose.Words Java festlegt

## Einführung
Wenn Sie jemals Schwierigkeiten hatten, **wie man Lesezeichen erstellt**, die beim Konvertieren eines Word‑Dokuments in PDF organisiert bleiben, sind Sie hier genau richtig. In diesem Tutorial führen wir Sie durch den gesamten Prozess, ein PDF mit Lesezeichen zu erzeugen, diese zu verschachteln und Gliederungsebenen zuzuweisen, sodass das fertige PDF leicht zu navigieren ist. Am Ende können Sie **Word PDF Java**‑artig mit einer sauberen Lesezeichen‑Hierarchie konvertieren, die in jedem PDF‑Betrachter funktioniert.

### Was Sie lernen werden
- Aspose.Words für Java in Ihrer Entwicklungsumgebung einrichten.  
- **Wie man Lesezeichen** programmgesteuert erstellt und verschachtelt.  
- Lesezeichen‑Gliederungsebenen konfigurieren, um PDFs mit Lesezeichen zu erzeugen, die die Dokumentstruktur widerspiegeln.  
- Die Word‑Datei als PDF speichern und dabei die Lesezeichen‑Hierarchie erhalten.

## Schnellantworten
- **Was ist die primäre Klasse zum Erstellen von Dokumenten?** `DocumentBuilder`.  
- **Welche Option steuert die Lesezeichen‑Hierarchie?** `BookmarksOutlineLevelCollection` innerhalb von `PdfSaveOptions`.  
- **Kann ich Maven oder Gradle verwenden?** Ja – beide werden unten gezeigt.  
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion reicht für Tests; für die Produktion ist eine permanente Lizenz erforderlich.  
- **Ist dieser Ansatz für große Dokumente geeignet?** Ja, aber berücksichtigen Sie Speicher‑Optimierungstechniken (z. B. das Entfernen ungenutzter Ressourcen).

### Voraussetzungen
Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- **Bibliotheken und Abhängigkeiten** – Aspose.Words für Java (25.3 oder neuer).  
- **Umgebung** – JDK 8 oder neuer und eine IDE wie IntelliJ IDEA oder Eclipse.  
- **Grundkenntnisse** – Java‑Programmiergrundlagen und Vertrautheit mit Maven oder Gradle.

## Aspose.Words einrichten
Fügen Sie zunächst die erforderlichen Abhängigkeiten zu Ihrem Projekt hinzu. So können Sie Aspose.Words mit Maven oder Gradle einbinden:

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
Aspose.Words ist eine kommerzielle Bibliothek, aber Sie können mit einer kostenlosen Testversion starten:

1. **Kostenlose Testversion** – Download von der [Aspose release page](https://releases.aspose.com/words/java/).  
2. **Temporäre Lizenz** – Beantragen Sie sie auf der [temporary‑license page](https://purchase.aspose.com/temporary-license/), wenn Sie einen kurzfristigen Schlüssel benötigen.  
3. **Vollständige Lizenz** – Kauf über das [Aspose purchasing portal](https://purchase.aspose.com/buy) für den Produktionseinsatz.

Nach Erhalt der Lizenzdatei laden Sie sie beim Anwendungsstart, um alle Funktionen freizuschalten.

## Wie man Lesezeichen in PDFs mit Aspose.Words Java erstellt
Im Folgenden teilen wir die Implementierung in klare, nummerierte Schritte. Jeder Schritt enthält eine kurze Erklärung, gefolgt vom Original‑Codeblock (unverändert).

### Schritt 1: Ein Document und einen DocumentBuilder initialisieren
Wir beginnen mit einer frischen `Document`‑Instanz und einem `DocumentBuilder`, der das Einfügen von Inhalt und Lesezeichen ermöglicht.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Schritt 2: Das erste (übergeordnete) Lesezeichen einfügen
Erstellen Sie ein Lesezeichen der obersten Ebene, das später ein untergeordnetes Lesezeichen enthalten wird.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Schritt 3: Ein untergeordnetes Lesezeichen im übergeordneten einbetten
Jetzt fügen wir ein zweites Lesezeichen hinzu, das innerhalb des ersten liegt und die Verschachtelung demonstriert.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Schritt 4: Das übergeordnete Lesezeichen schließen
Beenden Sie das äußere Lesezeichen nach dem verschachtelten Inhalt.

```java
builder.endBookmark("Bookmark 1");
```

### Schritt 5: Ein unabhängiges drittes Lesezeichen hinzufügen
Sie können jederzeit weitere Lesezeichen hinzufügen, die nicht verschachtelt sind.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Konfiguration der Lesezeichen‑Gliederungsebenen
Nachdem die Lesezeichen gesetzt sind, teilen wir Aspose.Words mit, wie diese im PDF‑Outline (linke Navigationsleiste) erscheinen sollen.

### Schritt 6: PdfSaveOptions vorbereiten
`PdfSaveOptions` gibt Zugriff auf die Outline‑Einstellungen.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Schritt 7: Hierarchie‑Ebenen zuweisen
Jedes Lesezeichen erhält eine ganzzahlige Ebene; niedrigere Zahlen stehen höher in der Hierarchie.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Schritt 8: Das Dokument als PDF speichern
Exportieren Sie schließlich das Word‑Dokument nach PDF und erhalten dabei die Lesezeichen‑Outline.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Warum diesen Ansatz zur PDF‑Erstellung mit Lesezeichen verwenden?
- **Professionelle Navigation** – Leser können direkt zu Abschnitten springen, was die Bedienbarkeit großer Berichte oder Rechtsverträge verbessert.  
- **Volle Kontrolle** – Sie bestimmen die Hierarchie, nicht der PDF‑Betrachter.  
- **Plattformübergreifend** – Funktioniert auf Windows, Linux und macOS identisch, da es reines Java ist.  

## Häufige Probleme und Lösungen
| Symptom | Wahrscheinliche Ursache | Lösung |
|---|---|---|
| Lesezeichen fehlen im PDF | Ein `startBookmark` ohne passendes `endBookmark` | Stellen Sie sicher, dass jeder `startBookmark` ein entsprechendes `endBookmark` hat. |
| Falsche Hierarchie | Outline‑Ebenen wurden in falscher Reihenfolge zugewiesen | Achten Sie darauf, dass übergeordnete Lesezeichen niedrigere Ebenennummern haben als ihre Kinder. |
| Lizenz nicht angewendet | Lizenzdatei nicht geladen, bevor das Dokument erstellt wird | Laden Sie die Lizenz zu Beginn Ihrer Anwendung (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## Praktische Anwendungsfälle
1. **Rechtsdokumente** – Schnelles Navigieren zu Klauseln, Anlagen und Anhängen.  
2. **Finanzberichte** – Springen zwischen Bereichen wie Gewinn‑ und Verlustrechnung, Bilanz und Anmerkungen.  
3. **E‑Learning‑Materialien** – Bereitstellung eines Inhaltsverzeichnisses, das dem PDF‑Outline entspricht.

## Leistungsüberlegungen
- **Speichermanagement** – Bei sehr großen Word‑Dateien sollten Sie `doc.cleanup()` vor dem Speichern aufrufen.  
- **Ressourcen‑Optimierung** – Entfernen Sie ungenutzte Bilder oder Stile, um die PDF‑Größe klein zu halten.

## Häufig gestellte Fragen

**F: Wie installiere ich Aspose.Words für Java?**  
A: Fügen Sie die oben gezeigte Maven‑ oder Gradle‑Abhängigkeit hinzu, platzieren Sie Ihre Lizenzdatei im Klassenpfad und laden Sie sie zur Laufzeit.

**F: Kann ich Lesezeichen erstellen, ohne Outline‑Ebenen zu setzen?**  
A: Ja, aber der PDF‑Betrachter zeigt sie dann als flache Liste an, was bei komplexen Dokumenten die Navigation erschwert.

**F: Gibt es ein Limit, wie tief Lesezeichen verschachtelt werden können?**  
A: Technisch gibt es kein Limit, aber die meisten PDF‑Betrachter unterstützen komfortabel bis zu 9 Ebenen. Halten Sie die Hierarchie logisch für die Leser.

**F: Wie geht Aspose mit sehr großen Word‑Dateien um?**  
A: Die Bibliothek streamt Inhalte und bietet Methoden wie `Document.optimizeResources()`, um den Speicherverbrauch zu reduzieren.

**F: Kann ich die Lesezeichen nach der PDF‑Erstellung bearbeiten?**  
A: Absolut – Sie können Aspose.PDF für Java verwenden, um Lesezeichen in einer bestehenden PDF hinzuzufügen, zu entfernen oder umzubenennen.

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

**Zuletzt aktualisiert:** 2025-11-27  
**Getestet mit:** Aspose.Words 25.3 für Java  
**Autor:** Aspose