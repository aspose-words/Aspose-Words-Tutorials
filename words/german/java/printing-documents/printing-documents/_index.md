---
title: Drucken von Dokumenten in Aspose.Words für Java
linktitle: Dokumente drucken
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words für Java Dokumente drucken. Schritt-für-Schritt-Anleitung für nahtloses Drucken in Ihren Java-Anwendungen.
weight: 10
url: /de/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Drucken von Dokumenten in Aspose.Words für Java


Wenn Sie Dokumente mit Aspose.Words für Java drucken möchten, sind Sie hier richtig. In dieser Schritt-für-Schritt-Anleitung führen wir Sie anhand des bereitgestellten Quellcodes durch den Vorgang des Druckens von Dokumenten mit Aspose.Words für Java.

## Einführung

Das Drucken von Dokumenten ist in vielen Anwendungen eine gängige Aufgabe. Aspose.Words für Java bietet eine leistungsstarke API zum Arbeiten mit Word-Dokumenten, einschließlich der Möglichkeit, diese zu drucken. In diesem Tutorial führen wir Sie Schritt für Schritt durch den Vorgang des Druckens eines Word-Dokuments.

## Einrichten Ihrer Umgebung

Bevor wir uns in den Code vertiefen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Java Development Kit (JDK) installiert
- Aspose.Words für Java-Bibliothek heruntergeladen und zu Ihrem Projekt hinzugefügt

## Einlegen des Dokuments

 Um zu beginnen, müssen Sie das Word-Dokument laden, das Sie drucken möchten. Ersetzen Sie`"Your Document Directory"` mit dem Pfad zu Ihrem Dokument und`"Your Output Directory"` mit dem gewünschten Ausgabeverzeichnis.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Erstellen eines Druckauftrags

Als nächstes erstellen wir einen Druckauftrag, um unser geladenes Dokument zu drucken. Der folgende Codeausschnitt initialisiert einen Druckauftrag und legt die gewünschten Druckereinstellungen fest.

```java
// Erstellen Sie einen Druckauftrag, mit dem unser Dokument gedruckt wird.
PrinterJob pj = PrinterJob.getPrinterJob();
// Initialisieren Sie einen Attributsatz mit der Anzahl der Seiten im Dokument.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Übergeben Sie die Druckereinstellungen zusammen mit den weiteren Parametern an das Druckdokument.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Drucken des Dokuments

Nachdem wir nun unseren Druckauftrag eingerichtet haben, ist es an der Zeit, das Dokument zu drucken. Der folgende Codeausschnitt verknüpft das Dokument mit dem Druckauftrag und leitet den Druckvorgang ein.

```java
// Übergeben Sie das auszudruckende Dokument mit dem Druckauftrag.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Vollständiger Quellcode
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Erstellen Sie einen Druckauftrag, mit dem unser Dokument gedruckt wird.
PrinterJob pj = PrinterJob.getPrinterJob();
// Initialisieren Sie einen Attributsatz mit der Anzahl der Seiten im Dokument.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Übergeben Sie die Druckereinstellungen zusammen mit den weiteren Parametern an das Druckdokument.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Übergeben Sie das auszudruckende Dokument mit dem Druckauftrag.
pj.setPrintable(awPrintDoc);
pj.print();
```
Quellcode von MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <Zusammenfassung>
    /// Der Konstruktor der benutzerdefinierten PrintDocument-Klasse.
    // / </summary>
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        //Die Seitenstart- und Seitenendindizes, wie im Attributsatz definiert.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Berechnen Sie den Seitenindex, der als nächstes gerendert werden soll.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Wenn der Seitenindex größer als der gesamte Seitenbereich ist, dann gibt es nichts
        // mehr zu rendern.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Berechnen Sie die Größe jedes Miniaturbildplatzhalters in Punkten.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Berechnen Sie die Nummer der ersten Seite, die auf dieses Blatt Papier gedruckt werden soll.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Wählen Sie die Nummer der letzten Seite aus, die auf dieses Blatt Papier gedruckt werden soll.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Durchlaufen Sie die ausgewählten Seiten von der gespeicherten aktuellen Seite bis zur berechneten
        // letzte Seite.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Berechnen Sie die Spalten- und Zeilenindizes.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Definieren Sie den Standort der Miniaturansicht in Weltkoordinaten (in diesem Fall Punkte).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Berechnen Sie die linken und oberen Startpositionen.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Rendern Sie die Dokumentseite mit berechneten Koordinaten in das Grafikobjekt.
                // und Größe des Platzhalters für Miniaturansichten.
                // Der nützliche Rückgabewert ist der Maßstab, in dem die Seite gerendert wurde.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //Zeichnen Sie die Seitenränder (das Seiten-Thumbnail könnte kleiner sein als das Thumbnail
                // Platzhaltergröße).
                if (mPrintPageBorders) {
                    // Holen Sie sich die tatsächliche 100 %-Größe der Seite in Punkten.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Zeichnen Sie mit dem bekannten Skalierungsfaktor den Rahmen um die skalierte Seite.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Zeichnen Sie den Rahmen um den Platzhalter für die Miniaturansicht.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Wenn beim Rendern Fehler auftreten, unternehmen Sie nichts.
                // Dadurch wird eine leere Seite gezeichnet, wenn beim Rendern Fehler auftreten.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Definieren Sie die Anzahl der Spalten und Zeilen auf dem Blatt für die
        // Querformatiges Papier.
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // Vertauschen Sie Breite und Höhe, wenn das Papier im Hochformat vorliegt.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich ein Word-Dokument mit Aspose.Words für Java gedruckt. Diese Schritt-für-Schritt-Anleitung soll Ihnen dabei helfen, den Dokumentendruck nahtlos in Ihre Java-Anwendungen zu integrieren.

## FAQs

### F1: Kann ich mit Aspose.Words für Java bestimmte Seiten eines Dokuments drucken?

 Ja, Sie können den Seitenbereich beim Drucken eines Dokuments angeben. Im Codebeispiel haben wir verwendet`attributes.add(new PageRanges(1, doc.getPageCount()))` um alle Seiten zu drucken. Sie können den Seitenbereich nach Bedarf anpassen.

### F2: Ist Aspose.Words für Java für den Stapeldruck geeignet?

Absolut! Aspose.Words für Java eignet sich gut für Stapeldruckaufgaben. Sie können eine Liste von Dokumenten durchlaufen und sie mit ähnlichem Code nacheinander ausdrucken.

### F3: Wie kann ich mit Druckfehlern oder Ausnahmen umgehen?

Sie sollten alle möglichen Ausnahmen behandeln, die während des Druckvorgangs auftreten können. Informationen zur Behandlung von Ausnahmen finden Sie in der Dokumentation zu Aspose.Words für Java.

### F4: Kann ich die Druckeinstellungen weiter anpassen?

Ja, Sie können die Druckeinstellungen an Ihre spezifischen Anforderungen anpassen. Weitere Informationen zu den verfügbaren Druckoptionen finden Sie in der Dokumentation zu Aspose.Words für Java.

### F5: Wo kann ich weitere Hilfe und Unterstützung für Aspose.Words für Java erhalten?

 Für weitere Unterstützung und Hilfe besuchen Sie bitte die[Aspose.Words für Java-Forum](https://forum.aspose.com/).

---

Nachdem Sie nun erfolgreich gelernt haben, wie Sie Dokumente mit Aspose.Words für Java drucken, können Sie mit der Implementierung dieser Funktionalität in Ihren Java-Anwendungen beginnen. Viel Spaß beim Programmieren!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
