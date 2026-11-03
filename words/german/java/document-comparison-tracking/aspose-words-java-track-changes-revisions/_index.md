---
date: '2026-11-02'
description: Erfahren Sie, wie Sie Änderungen in Word-Dokumenten mit Aspose.Words
  für Java nachverfolgen, einschließlich document comparison, inline revision handling,
  licensing und performance tips.
keywords:
- how to track changes
- track formatting changes
- document comparison aspose
- aspose.words license java
lastmod: '2026-11-02'
og_description: Erfahren Sie, wie Sie Änderungen in Word-Dokumenten mit Aspose.Words
  für Java nachverfolgen, einschließlich document comparison, inline revision handling
  und licensing details.
og_image_alt: Guide showing how to track changes in Word documents with Aspose.Words
  Java
og_title: Wie man Änderungen in Word-Dokumenten mit Aspose.Words Java nachverfolgt
schemas:
- author: Aspose
  dateModified: '2026-11-02'
  description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  headline: How to track changes in Word docs with Aspose.Words Java
  type: TechArticle
- description: Learn how to track changes in Word docs using Aspose.Words for Java,
    covering document comparison, inline revision handling, licensing, and performance
    tips.
  name: How to track changes in Word docs with Aspose.Words Java
  steps:
  - name: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
    text: '**Free trial:** Download the library from [Aspose Downloads](https://releases.aspose.com/words/java/)
      and use it with evaluation limitations.'
  - name: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
    text: '**Temporary license:** Obtain a temporary license for extended usage without
      evaluation restrictions by visiting [Temporary License](https://purchase.aspose.com/temporary-license/).'
  - name: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
    text: '**Purchase license:** Consider purchasing if you need full access to Aspose.Words
      features by following the instructions on their purchase page.'
  - name: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
    text: '**Collaborative editing:** Teams can review and approve changes before
      publishing a final contract.'
  - name: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
    text: '**Legal document review:** Lawyers track amendments to clauses, ensuring
      every change is auditable.'
  - name: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
    text: '**Software documentation:** Technical writers manage updates to API references
      while preserving version history.'
  type: HowTo
- questions:
  - answer: An inline node represents a run of text or a character‑level element inside
      a paragraph, such as a `Run` or a `Field`.
    question: What is an inline node in Aspose.Words?
  - answer: Call `document.startTrackRevisions()` on your `Document` instance before
      making any edits.
    question: How do I start tracking revisions with Aspose.Words Java?
  - answer: Yes, use `document.acceptAllRevisions()` or `document.rejectAllRevisions()`
      to apply the changes programmatically.
    question: Can I automate accepting or rejecting revisions in a document?
  - answer: It supports DOCX, PDF, HTML, ODT, RTF, EPUB, and more than 35 formats
      for both import and export.
    question: What types of documents does Aspose.Words support?
  - answer: Process the file section by section, use low‑memory load options, and
      leverage batch revision methods to keep CPU and RAM usage optimal.
    question: How do I handle large documents efficiently with Aspose.Words?
  type: FAQPage
tags:
- track changes
- Aspose.Words Java
- document revisions
- inline revisions
- Java document processing
title: Wie man Änderungen in Word-Dokumenten mit Aspose.Words Java nachverfolgt
url: /de/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Änderungen in Word-Dokumenten mit Aspose.Words Java nachverfolgt

Die Zusammenarbeit an wichtigen Dokumenten bedeutet häufig, dass Sie **Änderungen in Word-Dokumenten nachverfolgen** müssen, damit jede Bearbeitung sichtbar und kontrollierbar ist. Aspose.Words für Java bietet Ihnen eine programmatische „Track Changes“-Engine, die ohne Microsoft Word funktioniert und es Ihnen ermöglicht, Revisionen direkt aus Ihrem Code zu starten, abzufragen, zu akzeptieren oder abzulehnen. In diesem Leitfaden richten Sie die Bibliothek ein, untersuchen die Behandlung von Inline-Revisionen und entdecken leistungseffiziente Techniken für große Dateien.

## Schnelle Antworten
- **Welche Bibliothek ermöglicht das Nachverfolgen von Änderungen in Word-Dokumenten?** Aspose.Words for Java  
- **Welcher Abhängigkeitsmanager wird empfohlen?** Maven oder Gradle (beide unterstützt)  
- **Benötige ich eine Lizenz für die Entwicklung?** Eine kostenlose Testversion funktioniert für die Evaluierung; für den Produktionseinsatz ist eine Lizenz erforderlich  
- **Kann ich große Dokumente effizient verarbeiten?** Ja – verwenden Sie die Verarbeitung Abschnitt für Abschnitt und Batch‑Operationen  
- **Gibt es eine Methode, um das Tracking programmgesteuert zu starten?** `document.startTrackRevisions()` startet die Tracking‑Sitzung  

## Was bedeutet „how to track changes“?
`how to track changes` bezieht sich auf den Vorgang, die integrierte Revisionsverfolgungsfunktion von Word programmgesteuert zu aktivieren. Wenn sie aktiv ist, wird jede Einfügung, Löschung, Formatierungsänderung oder Verschiebung als separates Revisionsobjekt aufgezeichnet. Diese Objekte können später aufgelistet, überprüft und entweder akzeptiert werden, um die Änderung dauerhaft zu machen, oder abgelehnt, um sie zu verwerfen, wodurch eine vollständige Nachvollziehbarkeit von Dokumentenänderungen gewährleistet wird.

## Warum Aspose.Words für die Änderungsverfolgung verwenden?
Aspose.Words unterstützt **über 35 Eingabe‑ und Ausgabeformate** — darunter DOCX, PDF, HTML und ODT — und kann **500‑seitige Dokumente in weniger als 3 Sekunden** auf Standard‑Serverhardware verarbeiten, ohne Microsoft Word zu benötigen. Die API funktioniert unter Windows, Linux und macOS und ist damit ideal für cloud‑basierte oder lokale Lösungen, die ein zuverlässiges Revisionsmanagement benötigen.

## Voraussetzungen

- **Java Development Kit (JDK):** Version 8 oder höher.  
- **IDE:** IntelliJ IDEA, Eclipse oder NetBeans.  
- **Build‑Tool:** Maven oder Gradle für das Abhängigkeitsmanagement.  
- Grundlegende Java‑Kenntnisse zum Verstehen der Code‑Snippets.

## Einrichtung von Aspose.Words

### Maven‑Einrichtung

Fügen Sie die folgende Abhängigkeit zu Ihrer `pom.xml`‑Datei hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

### Gradle‑Einrichtung

Fügen Sie diese Zeile in Ihre `build.gradle`‑Datei ein:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Lizenzbeschaffung

Aspose bietet eine kostenlose Testversion an, um seine Funktionen zu testen und zu prüfen, ob sie Ihren Anforderungen entsprechen. So starten Sie:

1. **Kostenlose Testversion:** Laden Sie die Bibliothek von [Aspose-Downloads](https://releases.aspose.com/words/java/) herunter und verwenden Sie sie mit Evaluationsbeschränkungen.  
2. **Temporäre Lizenz:** Erhalten Sie eine temporäre Lizenz für erweiterten Gebrauch ohne Evaluationsbeschränkungen, indem Sie die Seite [Temporäre Lizenz](https://purchase.aspose.com/temporary-license/) besuchen.  
3. **Lizenz erwerben:** Erwägen Sie den Kauf, wenn Sie vollen Zugriff auf die Funktionen von Aspose.Words benötigen, indem Sie den Anweisungen auf ihrer Kaufseite folgen.

#### Grundlegende Initialisierung

`Document` ist das primäre Objekt von Aspose.Words, das eine Word‑Datei im Speicher repräsentiert. Um zu initialisieren, erstellen Sie eine Instanz von `Document` und beginnen Sie damit zu arbeiten:

```java
import com.aspose.words.Document;

public class Main {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("input.docx");
        // Further processing here
    }
}
```

## Wie man Änderungen in Word-Dokumenten mit Aspose.Words Java nachverfolgt
`document.startTrackRevisions()` startet eine Revisions‑Tracking‑Sitzung für das Dokument. Laden Sie eine Word‑Datei, rufen Sie `startTrackRevisions()` auf, um die Tracking‑Sitzung zu beginnen, führen Sie die gewünschten Änderungen durch und speichern Sie das Dokument schließlich. Die API zeichnet jede Bearbeitung als Revisionsobjekt auf, das Sie später auflisten, akzeptieren oder ablehnen können. Dieses Zwei‑Schritt‑Muster – Tracking starten, Änderungen vornehmen – deckt Einfügungen, Löschungen, Formatierungsänderungen und Verschiebungen ab.

## Implementierungsleitfaden

In diesem Abschnitt untersuchen wir, wie man verschiedene Arten von Revisionen mit Aspose.Words Java verarbeitet.

### Umgang mit Inline‑Revisionen

#### Überblick

Beim Nachverfolgen von Änderungen erscheinen Inline‑Revisionen innerhalb eines Absatzes als Runs. Sie können Einfügungen, Löschungen, Formatierungsänderungen oder Verschiebe‑Operationen sein. Das Verständnis jedes Typs ermöglicht den Aufbau benutzerfreundlicher Review‑Tools.

#### Code‑Implementierung

Das folgende Snippet demonstriert, wie man den Revisionstyp eines Inline‑Knotens prüft:

```java
import com.aspose.words.Document;
import com.aspose.words.Paragraph;
import com.aspose.words.Run;
import com.aspose.words.Revision;
import org.testng.Assert;

public class RevisionHandler {
    public void handleRevisions() throws Exception {
        Document doc = new Document("Revision runs.docx");

        // Check the number of revisions
        Assert.assertEquals(6, doc.getRevisions().getCount());

        // Accessing a specific revision's parent node
        Run run = (Run) doc.getRevisions().get(0).getParentNode();

        Paragraph paragraph = run.getParentParagraph();
        com.aspose.words.RunCollection runs = paragraph.getRuns();

        Assert.assertEquals(runs.getCount(), 6);

        // Identifying different types of revisions
        Assert.assertTrue(runs.get(2).isInsertRevision());  // Insert revision
        Assert.assertTrue(runs.get(2).isFormatRevision());  // Format revision
        Assert.assertTrue(runs.get(4).isMoveFromRevision()); // Move from revision
        Assert.assertTrue(runs.get(1).isMoveToRevision());   // Move to revision
        Assert.assertTrue(runs.get(5).isDeleteRevision());   // Delete revision
    }
}
```

#### Erklärung
- **Einfüge‑Revision:** Text, der hinzugefügt wurde, während das Tracking aktiv ist.  
- **Format‑Revision:** Änderungen an Schriftart, Farbe oder Stil, die auf bestehenden Text angewendet werden.  
- **Verschiebe‑von / -zu Revisionen:** Stellen Text dar, der innerhalb des Dokuments verschoben wurde; sie erscheinen immer als Paar.  
- **Lösch‑Revision:** Text, der entfernt, aber bis zur Annahme oder Ablehnung beibehalten wird.

### Praktische Anwendungen

Praxisnahe Szenarien, in denen die Handhabung von Revisionen glänzt:

1. **Kollaboratives Bearbeiten:** Teams können Änderungen prüfen und genehmigen, bevor ein endgültiger Vertrag veröffentlicht wird.  
2. **Rechtliche Dokumentenprüfung:** Anwälte verfolgen Änderungen an Klauseln und stellen sicher, dass jede Änderung nachvollziehbar ist.  
3. **Software‑Dokumentation:** Technische Redakteure verwalten Aktualisierungen von API‑Referenzen und bewahren dabei die Versionshistorie.

### Leistungsüberlegungen

`LoadOptions` konfiguriert, wie ein Dokument geladen wird, einschließlich Einstellungen zur Speicherverwendung. Die Verarbeitung großer, revisionsintensiver Dokumente kann speicherintensiv sein. Befolgen Sie diese bewährten Methoden:

- **Abschnitt‑für‑Abschnitt Verarbeitung:** Laden und verarbeiten Sie jeweils einen Abschnitt, um die Speichernutzung gering zu halten.  
- **Batch‑Operationen:** Verwenden Sie `Document.acceptAllRevisions()` oder `Document.rejectAllRevisions()` für ganze Abschnitte, anstatt einzelne Knoten zu bearbeiten, wann immer möglich.  
- **Streaming‑API:** Für Dateien größer als 1 GB nutzen Sie den Streaming‑Modus von `LoadOptions`, um zu vermeiden, dass die gesamte Datei in den RAM geladen wird.

## Häufige Fallstricke und Fehlersuche

`document.startTrackRevisions()` startet das Verfolgen von Revisionen für die angegebene Document‑Instanz.

- **Fehlende Revisionen nach dem Bearbeiten:** Stellen Sie sicher, dass Sie `document.startTrackRevisions()` *vor* den Änderungen aufgerufen haben; ein Start des Trackings nach den Änderungen erfasst frühere Modifikationen nicht.  
- **Unerwartete Formatierungsänderungen:** Einige Stiländerungen werden als `RevisionType.Format` gemeldet. Wenn Sie nur an Textinhalt interessiert sind, filtern Sie Format‑Revisionen in Ihrer Auflistungslogik heraus.  
- **Verlangsamung bei großen Dokumenten:** Aktivieren Sie `LoadOptions.memoryUsage = LoadOptions.MemoryUsageMode.LowMemory`, um den Spitzen‑Speicherverbrauch zu reduzieren.

## Häufig gestellte Fragen

`Document.acceptAllRevisions()` wendet alle ausstehenden Revisionen an und macht alle Änderungen dauerhaft. `Document.rejectAllRevisions()` verwirft alle ausstehenden Revisionen und stellt das Dokument in seinen Originalzustand zurück.

**F: Was ist ein Inline‑Knoten in Aspose.Words?**  
A: Ein Inline‑Knoten stellt einen Textlauf oder ein Zeichen‑Element innerhalb eines Absatzes dar, z. B. ein `Run` oder ein `Field`.

**F: Wie starte ich das Tracking von Revisionen mit Aspose.Words Java?**  
A: Rufen Sie `document.startTrackRevisions()` auf Ihrer `Document`‑Instanz auf, bevor Sie Änderungen vornehmen.

**F: Kann ich das Akzeptieren oder Ablehnen von Revisionen in einem Dokument automatisieren?**  
A: Ja, verwenden Sie `document.acceptAllRevisions()` oder `document.rejectAllRevisions()`, um die Änderungen programmgesteuert anzuwenden.

**F: Welche Dokumenttypen unterstützt Aspose.Words?**  
A: Es unterstützt DOCX, PDF, HTML, ODT, RTF, EPUB und mehr als 35 Formate für Import und Export.

**F: Wie gehe ich effizient mit großen Dokumenten in Aspose.Words um?**  
A: Verarbeiten Sie die Datei Abschnitt für Abschnitt, verwenden Sie Low‑Memory‑Ladeoptionen und nutzen Sie Batch‑Revisionsmethoden, um CPU‑ und RAM‑Verbrauch zu optimieren.

## Ressourcen

- [Aspose.Words Java-Dokumentation](https://reference.aspose.com/words/java/)  
- [Aspose.Words für Java herunterladen](https://releases.aspose.com/words/java/)  
- [Lizenz erwerben](https://purchase.aspose.com/buy)  
- [Kostenlose Testversion](https://releases.aspose.com/words/java/)  
- [Temporäre Lizenz](https://purchase.aspose.com/temporary-license/)  
- [Aspose Support‑Forum](https://forum.aspose.com/c/words/10)

Starten Sie noch heute Ihre Reise mit Aspose.Words Java und nutzen Sie das volle Potenzial der Dokumentenverarbeitung in Ihren Anwendungen!

---

**Zuletzt aktualisiert:** 2026-11-02  
**Getestet mit:** Aspose.Words 25.3 für Java  
**Autor:** Aspose

## Verwandte Tutorials

- [Änderungsverfolgung in Aspose.Words für Java implementieren](/words/java/document-comparison-tracking/)
- [Word nach PDF konvertieren mit Aspose.Words für Java Dokumentkonvertierungs‑API](/words/java/document-converting/)
- [Aspose Words LoadOptions: Beschädigte Word‑Dokumente in Java wiederherstellen](/words/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}