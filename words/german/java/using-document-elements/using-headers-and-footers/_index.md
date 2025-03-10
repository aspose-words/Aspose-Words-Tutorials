---
title: Verwenden von Kopf- und Fußzeilen in Aspose.Words für Java
linktitle: Kopf- und Fußzeilen verwenden
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie Schritt für Schritt, wie Sie Kopf- und Fußzeilen in Aspose.Words für Java verwenden. Erstellen Sie mühelos professionelle Dokumente.
weight: 16
url: /de/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Kopf- und Fußzeilen in Aspose.Words für Java


In dieser umfassenden Anleitung führen wir Sie durch den Prozess der Arbeit mit Kopf- und Fußzeilen in Aspose.Words für Java. Kopf- und Fußzeilen sind wesentliche Elemente der Dokumentformatierung und Aspose.Words bietet leistungsstarke Tools, um sie nach Ihren Anforderungen zu erstellen und anzupassen.

Lassen Sie uns nun jeden dieser Schritte im Detail durchgehen.

## 1. Einführung in Aspose.Words

Aspose.Words ist eine leistungsstarke Java-API, mit der Sie Word-Dokumente programmgesteuert erstellen, bearbeiten und rendern können. Es bietet umfangreiche Funktionen zur Dokumentformatierung, einschließlich Kopf- und Fußzeilen.

## 2. Einrichten Ihrer Java-Umgebung

 Bevor Sie Aspose.Words verwenden, stellen Sie sicher, dass Ihre Java-Entwicklungsumgebung richtig eingerichtet ist. Die erforderlichen Einrichtungsanweisungen finden Sie auf der Aspose.Words-Dokumentationsseite:[Aspose.Words Java-Dokumentation](https://reference.aspose.com/words/java/).

## 3. Neues Dokument erstellen

Um mit Kopf- und Fußzeilen zu arbeiten, müssen Sie mit Aspose.Words ein neues Dokument erstellen. Der folgende Code zeigt, wie das geht:

```java
// Java-Code zum Erstellen eines neuen Dokuments
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Seiteneinrichtung verstehen

 Die Seiteneinrichtung ist entscheidend für die Steuerung des Layouts Ihres Dokuments. Sie können verschiedene Eigenschaften für Kopf- und Fußzeilen mithilfe der`PageSetup` Klasse. Beispiel:

```java
// Einrichten von Seiteneigenschaften
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Unterschiedliche Kopf-/Fußzeile auf der ersten Seite

Aspose.Words ermöglicht es Ihnen, verschiedene Kopf- und Fußzeilen für die erste Seite Ihres Dokuments zu verwenden. Verwenden Sie`pageSetup.setDifferentFirstPageHeaderFooter(true);` um diese Funktion zu aktivieren.

## 6. Arbeiten mit Headern

### 6.1. Text zu Überschriften hinzufügen

 Sie können Text zu Überschriften hinzufügen mit dem`DocumentBuilder`. Hier ist ein Beispiel:

```java
// Text zur Kopfzeile der ersten Seite hinzufügen
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Einfügen von Bildern in Kopfzeilen

 Um Bilder in Kopfzeilen einzufügen, können Sie das`insertImage` Methode. Hier ist ein Beispiel:

```java
// Einfügen eines Bildes in die Kopfzeile
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Anpassen von Header-Stilen

Sie können Kopfzeilenstile anpassen, indem Sie verschiedene Eigenschaften wie Schriftart, Ausrichtung und mehr festlegen, wie in den obigen Beispielen gezeigt.

## 7. Arbeiten mit Fußzeilen

### 7.1. Text zu Fußzeilen hinzufügen

 Ähnlich wie bei Kopfzeilen können Sie auch Fußzeilen Text hinzufügen, indem Sie`DocumentBuilder`. Hier ist ein Beispiel:

```java
// Hinzufügen von Text zur primären Fußzeile
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Fügen Sie nach Bedarf Text und Felder ein
```

### 7.2. Einfügen von Bildern in Fußzeilen

 Um Bilder in Fußzeilen einzufügen, verwenden Sie die`insertImage` Methode, genau wie in Headern.

### 7.3. Fußzeilenstile anpassen

 Passen Sie die Fußzeilenstile an mit dem`DocumentBuilder`ähnlich wie das Anpassen von Kopfzeilen.

## 8. Seitennummerierung

 Sie können Seitenzahlen in Ihre Kopf- und Fußzeilen einfügen, indem Sie Felder wie`PAGE` Und`NUMPAGES`. Diese Felder werden automatisch aktualisiert, wenn Sie Seiten hinzufügen oder entfernen.

## 9. Copyright-Informationen in Fußzeilen

Um der Fußzeile Ihres Dokuments Copyright-Informationen hinzuzufügen, können Sie eine Tabelle mit zwei Zellen verwenden, von denen eine links und die andere rechts ausgerichtet ist, wie im Codeausschnitt gezeigt.

## 10. Arbeiten mit mehreren Abschnitten

Aspose.Words ermöglicht Ihnen das Arbeiten mit mehreren Abschnitten innerhalb eines Dokuments. Sie können für jeden Abschnitt unterschiedliche Seitenlayouts und Kopf-/Fußzeilen festlegen.

## 11. Querformat

Sie können die Ausrichtung bestimmter Abschnitte bei Bedarf auf Querformat ändern.

## 12. Kopf-/Fußzeilen aus vorherigen Abschnitten kopieren

Das Kopieren von Kopf- und Fußzeilen aus vorherigen Abschnitten kann beim Erstellen komplexer Dokumente Zeit sparen.

## 13. Speichern Ihres Dokuments

Vergessen Sie nicht, Ihr Dokument nach der Erstellung und Anpassung mit dem`doc.save()` Verfahren.

## Vollständiger Quellcode
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Geben Sie an, ob sich die Kopf-/Fußzeilen der ersten Seite von denen der anderen Seiten unterscheiden sollen.
        // Sie können auch die Eigenschaft PageSetup.OddAndEvenPagesHeaderFooter verwenden, um anzugeben
        // unterschiedliche Kopf-/Fußzeilen für ungerade und gerade Seiten.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Fügen Sie in die obere/linke Ecke der Kopfzeile ein positioniertes Bild ein.
        // Der Abstand vom oberen/linken Seitenrand ist auf 10 Punkte eingestellt.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Wir verwenden eine Tabelle mit zwei Zellen, um einen Textteil in der Zeile darzustellen (mit Seitennummerierung).
        // Soll linksbündig ausgerichtet sein, der restliche Textteil (mit Copyright) rechtsbündig.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Es verwendet die Felder PAGE und NUMPAGES, um die aktuelle Seitenzahl und viele Seiten automatisch zu berechnen.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Machen Sie einen Seitenumbruch, um eine zweite Seite zu erstellen, auf der die primären Kopf-/Fußzeilen angezeigt werden.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Dieser Abschnitt benötigt keine andere Kopf-/Fußzeile auf der ersten Seite, wir brauchen nur eine Titelseite im Dokument,
        //und die Kopf-/Fußzeile für diese Seite wurde bereits im vorherigen Abschnitt definiert.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Dieser Abschnitt zeigt Kopf- und Fußzeilen aus dem vorherigen Abschnitt an.
        // Rufen Sie standardmäßig currentSection.HeadersFooters.LinkToPrevious(false) auf, um diese Seitenbreite aufzuheben
        // ist für den neuen Abschnitt anders und daher müssen wir für eine Fußzeilentabelle unterschiedliche Zellenbreiten festlegen.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Wenn wir für diesen Abschnitt den bereits vorhandenen Kopf-/Fußzeilensatz verwenden möchten.
        // Aber mit einigen geringfügigen Änderungen kann es dann sinnvoll sein, Kopf-/Fußzeilen zu kopieren
        // aus dem vorherigen Abschnitt und wenden Sie die erforderlichen Änderungen dort an, wo Sie sie wünschen.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Quellcode der Methode copyHeadersFootersFromPreviousSection
```java
    /// <Zusammenfassung>
    /// Klont und kopiert Kopf-/Fußzeilen vom vorherigen Abschnitt in den angegebenen Abschnitt.
    /// </summary>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Abschluss

In diesem Tutorial haben wir die Grundlagen der Arbeit mit Kopf- und Fußzeilen in Aspose.Words für Java behandelt. Sie haben gelernt, wie Sie Kopf- und Fußzeilen erstellen, anpassen und formatieren sowie andere wichtige Techniken zur Dokumentformatierung anwenden.

 Weitere Einzelheiten und erweiterte Funktionen finden Sie im[Aspose.Words Java-Dokumentation](https://reference.aspose.com/words/java/).

## FAQs

### 1. Wie kann ich der Fußzeile meines Dokuments Seitenzahlen hinzufügen?
 Sie können Seitenzahlen hinzufügen, indem Sie die`PAGE` Feld mit Aspose.Words in die Fußzeile.

### 2. Ist Aspose.Words mit Java-Entwicklungsumgebungen kompatibel?
Ja, Aspose.Words bietet Unterstützung für die Java-Entwicklung. Stellen Sie sicher, dass Sie über die erforderlichen Einstellungen verfügen.

### 3. Kann ich die Schriftart und den Stil von Kopf- und Fußzeilen anpassen?
Natürlich können Sie Schriftarten, Ausrichtung und andere Stile anpassen, um Ihre Kopf- und Fußzeilen optisch ansprechend zu gestalten.

### 4. Ist es möglich, unterschiedliche Kopfzeilen für ungerade und gerade Seiten zu haben?
 Ja, Sie können`PageSetup.OddAndEvenPagesHeaderFooter` um unterschiedliche Kopfzeilen für ungerade und gerade Seiten festzulegen.

### 5. Wie beginne ich mit Aspose.Words für Java?
 Besuchen Sie zunächst die[Aspose.Words Java-Dokumentation](https://reference.aspose.com/words/java/) für umfassende Anleitungen zur Verwendung der API.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
