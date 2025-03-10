---
title: Dokumentendruck
linktitle: Dokumentendruck
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie in dieser ausführlichen Anleitung, wie Sie Dokumente mit Aspose.Words für Java drucken. Enthält Schritte zum Konfigurieren der Druckeinstellungen, Anzeigen der Druckvorschau und mehr.
weight: 10
url: /de/java/document-printing/automating-document-printing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentendruck


## Einführung

Das programmgesteuerte Drucken von Dokumenten ist eine leistungsstarke Funktion bei der Arbeit mit Java und Aspose.Words. Egal, ob Sie Berichte, Rechnungen oder andere Dokumenttypen erstellen, die Möglichkeit, direkt aus Ihrer Anwendung zu drucken, kann Zeit sparen und Ihre Arbeitsabläufe optimieren. Aspose.Words für Java bietet robuste Unterstützung für das Drucken von Dokumenten, sodass Sie die Druckfunktion nahtlos in Ihre Anwendungen integrieren können.

In diesem Handbuch erfahren Sie, wie Sie Dokumente mit Aspose.Words für Java drucken. Wir behandeln alles, vom Öffnen eines Dokuments über das Konfigurieren der Druckeinstellungen bis hin zum Anzeigen der Druckvorschau. Am Ende verfügen Sie über das Wissen, mit dem Sie Ihren Java-Anwendungen problemlos Druckfunktionen hinzufügen können.

## Voraussetzungen

Bevor Sie mit dem Druckvorgang beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

1. Java Development Kit (JDK): Stellen Sie sicher, dass auf Ihrem System JDK 8 oder höher installiert ist. Aspose.Words für Java ist für die ordnungsgemäße Funktion auf ein kompatibles JDK angewiesen.
2. Integrierte Entwicklungsumgebung (IDE): Verwenden Sie eine IDE wie IntelliJ IDEA oder Eclipse zum Verwalten Ihrer Java-Projekte und -Bibliotheken.
3.  Aspose.Words für Java-Bibliothek: Laden Sie die Aspose.Words für Java-Bibliothek herunter und integrieren Sie sie in Ihr Projekt. Sie können die neueste Version erhalten[Hier](https://releases.aspose.com/words/java/).
4.  Grundlegendes Verständnis des Java-Druckens: Machen Sie sich mit der Druck-API von Java und Konzepten wie`PrinterJob` Und`PrintPreviewDialog`.

## Pakete importieren

Um mit Aspose.Words für Java arbeiten zu können, müssen Sie die erforderlichen Pakete importieren. Dadurch erhalten Sie Zugriff auf die Klassen und Methoden, die zum Drucken von Dokumenten erforderlich sind.

```java
import com.aspose.words.*;
import java.awt.print.PrinterJob;
import javax.print.attribute.PrintRequestAttributeSet;
import javax.print.attribute.standard.PageRanges;
import javax.print.attribute.HashPrintRequestAttributeSet;
import javax.swing.PrintPreviewDialog;
```

Diese Importe bilden die Grundlage für die Arbeit mit Aspose.Words und der Druck-API von Java.

## Schritt 1: Öffnen Sie das Dokument

Bevor Sie ein Dokument drucken können, müssen Sie es mit Aspose.Words für Java öffnen. Dies ist der erste Schritt bei der Vorbereitung Ihres Dokuments für den Druck.

```java
Document doc = new Document("TestFile.doc");
```

Erläuterung: 
- `Document doc = new Document("TestFile.doc");` initialisiert eine neue`Document` Objekt aus der angegebenen Datei. Stellen Sie sicher, dass der Pfad zum Dokument korrekt ist und auf die Datei zugegriffen werden kann.

## Schritt 2: Initialisieren des Druckauftrags

Als Nächstes richten Sie den Druckauftrag ein. Dazu gehört das Konfigurieren der Druckattribute und das Anzeigen des Druckdialogs für den Benutzer.

```java
PrinterJob pj = PrinterJob.getPrinterJob();
```

Erläuterung: 
- `PrinterJob.getPrinterJob();` erhält eine`PrinterJob` -Instanz, die zur Abwicklung des Druckauftrags verwendet wird. Dieses Objekt verwaltet den Druckvorgang, einschließlich des Sendens von Dokumenten an den Drucker.

## Schritt 3: Druckattribute konfigurieren

Richten Sie die Druckattribute, beispielsweise Seitenbereiche, ein und zeigen Sie dem Benutzer den Druckdialog an.

```java
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));

if (!pj.printDialog(attributes)) {
    return;
}
```

Erläuterung:
- `PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();` erstellt einen neuen Satz Druckattribute.
- `attributes.add(new PageRanges(1, doc.getPageCount()));` Gibt den zu druckenden Seitenbereich an. In diesem Fall wird von Seite 1 bis zur letzten Seite des Dokuments gedruckt.
- `if (!pj.printDialog(attributes)) { return; }` zeigt dem Benutzer den Druckdialog an. Wenn der Benutzer den Druckdialog abbricht, wird die Methode vorzeitig beendet.

## Schritt 4: Erstellen und Konfigurieren von AsposeWordsPrintDocument

 Dieser Schritt umfasst die Erstellung eines`AsposeWordsPrintDocument` -Objekt, um das Dokument für den Druck darzustellen.

```java
AsposeWordsPrintDocument awPrintDoc = new AsposeWordsPrintDocument(doc);
pj.setPageable(awPrintDoc);
```

Erläuterung:
- `AsposeWordsPrintDocument awPrintDoc = new AsposeWordsPrintDocument(doc);` initialisiert den`AsposeWordsPrintDocument` mit dem auszudruckenden Dokument.
- `pj.setPageable(awPrintDoc);` legt den`AsposeWordsPrintDocument` als Pageable für die`PrinterJob`was bedeutet, dass das Dokument gerendert und an den Drucker gesendet wird.

## Schritt 5: Druckvorschau anzeigen

Vor dem Drucken möchten Sie dem Benutzer möglicherweise eine Druckvorschau anzeigen. Dieser Schritt ist optional, kann jedoch nützlich sein, um zu überprüfen, wie das Dokument gedruckt aussehen wird.

```java
PrintPreviewDialog previewDlg = new PrintPreviewDialog(awPrintDoc);
previewDlg.setPrinterAttributes(attributes);

if (previewDlg.display()) {
    pj.print(attributes);
}
```

Erläuterung:
- `PrintPreviewDialog previewDlg = new PrintPreviewDialog(awPrintDoc);` erstellt einen Druckvorschaudialog mit dem`AsposeWordsPrintDocument`.
- `previewDlg.setPrinterAttributes(attributes);` legt die Druckattribute für die Vorschau fest.
- `if (previewDlg.display()) { pj.print(attributes); }` zeigt den Vorschaudialog an. Akzeptiert der Benutzer die Vorschau, wird das Dokument mit den angegebenen Attributen gedruckt.

## Abschluss

Das programmgesteuerte Drucken von Dokumenten mit Aspose.Words für Java kann die Fähigkeiten Ihrer Anwendung erheblich verbessern. Mit der Möglichkeit, Dokumente zu öffnen, Druckeinstellungen zu konfigurieren und Druckvorschauen anzuzeigen, können Sie Ihren Benutzern ein nahtloses Druckerlebnis bieten. Ganz gleich, ob Sie die Berichterstellung automatisieren oder Dokument-Workflows verwalten, diese Funktionen können Ihnen Zeit sparen und die Effizienz steigern.

Wenn Sie dieser Anleitung folgen, sollten Sie nun ein solides Verständnis dafür haben, wie Sie den Dokumentendruck mithilfe von Aspose.Words in Ihre Java-Anwendungen integrieren. Experimentieren Sie mit verschiedenen Konfigurationen und Einstellungen, um den Druckvorgang an Ihre Bedürfnisse anzupassen.

## FAQs

### 1. Kann ich bestimmte Seiten aus einem Dokument ausdrucken?

 Ja, Sie können Seitenbereiche angeben mit dem`PageRanges` Klasse. Passen Sie die Seitenzahlen in der`PrintRequestAttributeSet` um nur die Seiten zu drucken, die Sie benötigen.

### 2. Wie kann ich den Ausdruck mehrerer Dokumente einrichten?

 Sie können den Druck für mehrere Dokumente einrichten, indem Sie die Schritte für jedes Dokument wiederholen. Erstellen Sie separate`Document` Objekte und`AsposeWordsPrintDocument` Instanzen für jeden einzelnen.

### 3. Ist es möglich, den Druckvorschaudialog anzupassen?

 Während die`PrintPreviewDialog` bietet grundlegende Vorschaufunktionen, Sie können es jedoch anpassen, indem Sie das Verhalten des Dialogs durch zusätzliche Java Swing-Komponenten oder -Bibliotheken erweitern oder ändern.

### 4. Kann ich Druckeinstellungen für die zukünftige Verwendung speichern?

 Sie können Druckeinstellungen speichern, indem Sie die`PrintRequestAttributeSet`Attribute in einer Konfigurationsdatei oder Datenbank. Laden Sie diese Einstellungen, wenn Sie einen neuen Druckauftrag einrichten.

### 5. Wo finde ich weitere Informationen zu Aspose.Words für Java?

 Ausführliche Informationen und weitere Beispiele finden Sie im[Aspose.Words-Dokumentation](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
