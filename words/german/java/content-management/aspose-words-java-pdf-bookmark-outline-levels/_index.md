---
date: '2026-03-23'
description: Erfahren Sie, wie Sie beim Konvertieren von Word‑Dokumenten in PDFs mit
  Aspose.Words für Java Lesezeichen hinzufügen und Gliederungsebenen konfigurieren.
  Dieser Leitfaden behandelt das Konvertieren von Word‑PDF‑Lesezeichen und verbessert
  die Navigation.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Wie man Lesezeichen in PDFs mit Aspose.Words Java hinzufügt
url: /de/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# So fügen Sie Lesezeichen in PDFs mit Aspose.Words Java hinzu

## Einführung
Wenn Sie jemals Schwierigkeiten hatten, **Lesezeichen** hinzuzufügen, die ein PDF leicht navigierbar machen, sind Sie hier genau richtig. In diesem Tutorial führen wir Sie durch **das Hinzufügen von Lesezeichen** und das Festlegen von Gliederungsebenen beim Konvertieren von Word‑Dokumenten zu PDFs mit Aspose.Words für Java. Am Ende verstehen Sie den gesamten Arbeitsablauf – vom Erstellen verschachtelter Lesezeichen in einer Word‑Datei bis zum Exportieren eines sauberen, durchsuchbaren PDFs mit einer logischen Lesezeichen‑Hierarchie.

**Was Sie lernen werden**
- Aspose.Words für Java in Ihrem Projekt einrichten  
- Verschachtelte Lesezeichen in einem Word‑Dokument erstellen  
- Lesezeichen‑Gliederungsebenen konfigurieren für ein professionelles PDF‑Navigations‑Erlebnis  
- Das Dokument als PDF speichern und dabei die Lesezeichenstruktur beibehalten  

### Schnelle Antworten
- **Was ist der Hauptvorteil des Hinzufügens von Lesezeichen?** Es ermöglicht Lesern, direkt zu Abschnitten zu springen, was die Benutzerfreundlichkeit verbessert.  
- **Welche Bibliothek verarbeitet PDF‑Lesezeichen in Java?** Aspose.Words für Java (mit optionalem Aspose.PDF für die Nachbearbeitung).  
- **Benötige ich eine Lizenz für diese Funktion?** Eine Testversion funktioniert für die Entwicklung; für die Produktion ist eine kommerzielle Lizenz erforderlich.  
- **Kann ich die Hierarchie der Lesezeichen steuern?** Ja, indem man Gliederungsebenen über `PdfSaveOptions` festlegt.  
- **Ist dieser Ansatz für große Dokumente geeignet?** Absolut – Aspose.Words streamt Inhalte effizient.  

## Was bedeutet „Lesezeichen hinzufügen“ im Kontext der PDF‑Konvertierung?
Lesezeichen hinzuzufügen bedeutet, benannte Anker in einem Word‑Dokument einzufügen, die in das PDF übernommen werden. Wenn das PDF geöffnet wird, erscheinen diese Lesezeichen im Navigationsbereich und ermöglichen es den Benutzern, Kapitel, Abschnitte oder beliebige benutzerdefinierte Punkte sofort zu finden.

## Warum Aspose.Words für Java verwenden, um Word → PDF‑Lesezeichen zu konvertieren?
Aspose.Words bewahrt die genaue Lesezeichen‑Hierarchie, die Sie in Word definieren, im Gegensatz zu vielen kostenlosen Konvertern, die sie flachlegen oder entfernen. Es ermöglicht Ihnen außerdem, **Gliederungsebenen** zuzuweisen, wodurch Sie eine feinkörnige Kontrolle über die Anzeige des Inhaltsverzeichnisses im PDF erhalten.

## Voraussetzungen
- **Bibliotheken**: Aspose.Words für Java (25.3 oder neuer).  
- **Entwicklungsumgebung**: JDK 8 oder neuer, IDE wie IntelliJ IDEA oder Eclipse.  
- **Build‑Tool**: Maven oder Gradle (je nach Vorliebe).  
- **Grundlegende Java‑Kenntnisse** und Vertrautheit mit Maven/Gradle.  

### Aspose.Words einrichten
Fügen Sie die Bibliothek Ihrem Projekt mit einem der nachstehenden Snippets hinzu.

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
Aspose.Words ist kommerziell, aber Sie können mit einer kostenlosen Testversion beginnen:

1. **Kostenlose Testversion** – Download von der [Aspose‑Release‑Seite](https://releases.aspose.com/words/java/) zum Testen aller Funktionen.  
2. **Temporäre Lizenz** – Antrag stellen auf der [Aspose‑temporären Lizenzseite](https://purchase.aspose.com/temporary-license/) für Kurzzeitprojekte.  
3. **Kauf** – Erhalten Sie eine permanente Lizenz über das [Aspose‑Kaufportal](https://purchase.aspose.com/buy).

Nach dem Erhalt der `.lic`‑Datei laden Sie sie beim Anwendungsstart, um alle Funktionen freizuschalten.

## Schritt‑für‑Schritt‑Anleitung

### Verschachtelte Lesezeichen erstellen
**Übersicht:** Wir erstellen ein einfaches Word‑Dokument mit drei Lesezeichen, wobei ein Lesezeichen in einem anderen verschachtelt ist.

#### Schritt 1: Dokument und Builder initialisieren
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Dies erstellt ein leeres Word‑Dokument und ein Builder‑Objekt, mit dem wir Text und Lesezeichen einfügen können.

#### Schritt 2: Das erste (übergeordnete) Lesezeichen einfügen
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Schritt 3: Ein zweites Lesezeichen innerhalb des ersten verschachteln
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Schritt 4: Das übergeordnete Lesezeichen schließen
```java
builder.endBookmark("Bookmark 1");
```

#### Schritt 5: Ein unabhängiges drittes Lesezeichen hinzufügen
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

Zu diesem Zeitpunkt enthält das Word‑Dokument eine klare Hierarchie, die wir später in PDF‑Gliederungsebenen übersetzen können.

### Konfigurieren von Lesezeichen‑Gliederungsebenen
**Übersicht:** Gliederungsebenen teilen dem PDF‑Betrachter mit, wie tief jedes Lesezeichen im Navigationsbereich liegt.

#### Schritt 1: `PdfSaveOptions` vorbereiten
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Schritt 2: Ebenen jedem Lesezeichen zuweisen
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
Level 1 erscheint auf der obersten Ebene, Level 2 als Kind usw.

#### Schritt 3: Das Dokument als PDF speichern
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Das resultierende PDF zeigt ein strukturiertes Lesezeichen‑Fenster, das die von uns definierte Hierarchie widerspiegelt.

## Häufige Probleme und Lösungen

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| Lesezeichen verschwinden im PDF | `PdfSaveOptions` nicht konfiguriert | Stellen Sie sicher, dass `outlineLevels` vor dem Speichern hinzugefügt werden. |
| Verschachteltes Lesezeichen wird auf oberster Ebene angezeigt | Falsche Ebenennummer | Überprüfen Sie, dass untergeordnete Lesezeichen eine höhere numerische Ebene erhalten. |
| Fehlender Aufruf von `endBookmark` | Unausgeglichene start/end‑Aufrufe | Überprüfen Sie, dass jeder `startBookmark` einen passenden `endBookmark` hat. |

## Praktische Anwendungen
- **Rechtsverträge** – Schnell zu Klauseln und Unterklauseln springen.  
- **Technische Berichte** – Große Abschnitte wie Methodik, Ergebnisse und Anhänge navigieren.  
- **E‑Learning‑PDFs** – Ein klickbares Inhaltsverzeichnis für jedes Kapitel bereitstellen.  

## Leistungstipps
- Entfernen Sie ungenutzte Abschnitte vor dem Speichern, um das PDF leichtgewichtig zu halten.  
- Verwenden Sie Streaming (`doc.save(OutputStream)`) für sehr große Dateien, um den Speicherverbrauch zu reduzieren.

## Fazit
Sie wissen jetzt, **wie man Lesezeichen hinzufügt** und deren Gliederungsebenen beim Konvertieren von Word‑Dokumenten zu PDFs mit Aspose.Words für Java festlegt. Diese Technik verbessert die PDF‑Navigation erheblich und macht Ihre Dokumente professioneller und benutzerfreundlicher.

**Nächste Schritte:** Versuchen Sie, benutzerdefinierte Symbole zu Lesezeichen über `PdfBookmark`‑Objekte hinzuzufügen, oder integrieren Sie diesen Workflow in einen Batch‑Verarbeitungs‑Dienst, der mehrere Word‑Dateien automatisch konvertiert.

## FAQ‑Abschnitt
1. **Wie installiere ich Aspose.Words für Java?**  
   Fügen Sie es als Abhängigkeit über Maven oder Gradle hinzu und richten Sie dann Ihre Lizenzdatei ein.  
2. **Kann ich Lesezeichen ohne Gliederungsebenen verwenden?**  
   Ja, aber Gliederungsebenen bieten eine klarere Hierarchie im PDF‑Betrachter.  
3. **Was sind die Grenzen für das Verschachteln von Lesezeichen?**  
   Es gibt keine strikte Begrenzung, aber halten Sie die Struktur für Endbenutzer lesbar.  
4. **Wie geht Aspose mit großen Dokumenten um?**  
   Es streamt Inhalte effizient; dennoch sollten Sie Ressourcen für sehr große Dateien optimieren.  
5. **Kann ich Lesezeichen nach dem Speichern des PDFs ändern?**  
   Ja – verwenden Sie Aspose.PDF für Java, um Lesezeichen nach der Konvertierung zu bearbeiten.  

## Häufig gestellte Fragen

**F: Funktioniert diese Methode mit der neuesten Aspose.Words‑Version?**  
A: Absolut. Die API für Lesezeichen‑Gliederungsebenen ist seit Version 20 stabil.

**F: Wird eine separate Aspose.PDF‑Bibliothek benötigt, um Lesezeichen anzuzeigen?**  
A: Nein. Die Lesezeichen sind im PDF eingebettet und in jedem gängigen PDF‑Betrachter sichtbar.

**F: Kann ich Lesezeichentitel programmgesteuert ändern, nachdem das PDF erstellt wurde?**  
A: Ja, indem Sie das PDF mit Aspose.PDF laden und die `PdfBookmark`‑Sammlung aktualisieren.

**F: Funktioniert dieser Ansatz auf Nicht‑Windows‑Plattformen?**  
A: Aspose.Words für Java ist plattformunabhängig; es läuft auf jedem Betriebssystem mit einem unterstützten JDK.

**F: Wie kann ich die Lesezeichen‑Hierarchie testen, ohne das PDF zu öffnen?**  
A: Verwenden Sie `PdfBookmarkCollection` aus Aspose.PDF, um die Ebenen programmgesteuert aufzulisten und zu überprüfen.

---

**Zuletzt aktualisiert:** 2026-03-23  
**Getestet mit:** Aspose.Words 25.3 für Java  
**Autor:** Aspose  

**Ressourcen**  
- [Aspose.Words Dokumentation](https://reference.aspose.com/words/java/)  
- [Neueste Releases herunterladen](https://releases.aspose.com/words/java/)  
- [Lizenz kaufen](https://purchase.aspose.com/buy)  
- [Kostenlose Testversion](https://releases.aspose.com/words/java/)  
- [Antrag für temporäre Lizenz](https://purchase.aspose.com/temporary-license/)  
- [Aspose Support‑Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}