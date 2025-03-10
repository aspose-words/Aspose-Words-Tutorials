---
title: Aufteilen von Dokumenten in HTML-Seiten in Aspose.Words für Java
linktitle: Aufteilen von Dokumenten in HTML-Seiten
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words für Java Dokumente in HTML-Seiten aufteilen. Folgen Sie unserer Schritt-für-Schritt-Anleitung zur nahtlosen Dokumentkonvertierung.
weight: 25
url: /de/java/document-manipulation/splitting-documents-into-html-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aufteilen von Dokumenten in HTML-Seiten in Aspose.Words für Java


## Einführung in das Aufteilen von Dokumenten in HTML-Seiten in Aspose.Words für Java

In dieser Schritt-für-Schritt-Anleitung erfahren Sie, wie Sie Dokumente mit Aspose.Words für Java in HTML-Seiten aufteilen. Aspose.Words ist eine leistungsstarke Java-API für die Arbeit mit Microsoft Word-Dokumenten und bietet umfangreiche Funktionen zur Dokumentbearbeitung, darunter die Möglichkeit, Dokumente in verschiedene Formate, einschließlich HTML, zu konvertieren.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Auf Ihrem System ist Java Development Kit (JDK) installiert.
-  Aspose.Words für Java-Bibliothek. Sie können es herunterladen von[Hier](https://releases.aspose.com/words/java/).

## Schritt 1: Erforderliche Pakete importieren

```java
import com.aspose.words.*;
import java.io.*;
import java.util.ArrayList;
```

## Schritt 2: Erstellen Sie eine Methode zur Konvertierung von Word in HTML

```java
class WordToHtmlConverter
{
    // Implementierungsdetails für die Konvertierung von Word in HTML.
    // ...
}
```

## Schritt 3: Überschriftenabsätze als Themenanfänge auswählen

```java
private ArrayList<Paragraph> selectTopicStarts()
{
    NodeCollection paras = mDoc.getChildNodes(NodeType.PARAGRAPH, true);
    ArrayList<Paragraph> topicStartParas = new ArrayList<Paragraph>();
    for (Paragraph para : (Iterable<Paragraph>) paras)
    {
        int style = para.getParagraphFormat().getStyleIdentifier();
        if (style == StyleIdentifier.HEADING_1)
            topicStartParas.add(para);
    }
    return topicStartParas;
}
```

## Schritt 4: Abschnittsumbrüche vor den Überschriften der Absätze einfügen

```java
private void insertSectionBreaks(ArrayList<Paragraph> topicStartParas)
{
    DocumentBuilder builder = new DocumentBuilder(mDoc);
    for (Paragraph para : topicStartParas)
    {
        Section section = para.getParentSection();
        if (para != section.getBody().getFirstParagraph())
        {
            builder.moveTo(para.getFirstChild());
            builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
            section.getBody().getLastParagraph().remove();
        }
    }
}
```

## Schritt 5: Teilen Sie das Dokument in Themen auf

```java
private ArrayList<Topic> saveHtmlTopics() throws Exception
{
    ArrayList<Topic> topics = new ArrayList<Topic>();
    for (int sectionIdx = 0; sectionIdx < mDoc.getSections().getCount(); sectionIdx++)
    {
        Section section = mDoc.getSections().get(sectionIdx);
        String paraText = section.getBody().getFirstParagraph().getText();
        String fileName = makeTopicFileName(paraText);
        if ("".equals(fileName))
            fileName = "UNTITLED SECTION " + sectionIdx;
        fileName = mDstDir + fileName + ".html";
        String title = makeTopicTitle(paraText);
        if ("".equals(title))
            title = "UNTITLED SECTION " + sectionIdx;
        Topic topic = new Topic(title, fileName);
        topics.add(topic);
        saveHtmlTopic(section, topic);
    }
    return topics;
}
```

## Schritt 6: Speichern Sie jedes Thema als HTML-Datei

```java
private void saveHtmlTopic(Section section, Topic topic) throws Exception
{
    Document dummyDoc = new Document();
    dummyDoc.removeAllChildren();
    dummyDoc.appendChild(dummyDoc.importNode(section, true, ImportFormatMode.KEEP_SOURCE_FORMATTING));
    dummyDoc.getBuiltInDocumentProperties().setTitle(topic.getTitle());
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    {
        saveOptions.setPrettyFormat(true);
        saveOptions.setAllowNegativeIndent(true);
        saveOptions.setExportHeadersFootersMode(ExportHeadersFootersMode.NONE);
    }
    dummyDoc.save(topic.getFileName(), saveOptions);
}
```

## Schritt 7: Erstellen Sie ein Inhaltsverzeichnis für die Themen

```java
private void saveTableOfContents(ArrayList<Topic> topics) throws Exception
{
    Document tocDoc = new Document(mTocTemplate);
    tocDoc.getMailMerge().setFieldMergingCallback(new HandleTocMergeField());
    tocDoc.getMailMerge().executeWithRegions(new TocMailMergeDataSource(topics));
    tocDoc.save(mDstDir + "contents.html");
}
```

Nachdem wir nun die Schritte skizziert haben, können Sie jeden Schritt in Ihrem Java-Projekt implementieren, um Dokumente mit Aspose.Words für Java in HTML-Seiten aufzuteilen. Mit diesem Prozess können Sie eine strukturierte HTML-Darstellung Ihrer Dokumente erstellen und sie so zugänglicher und benutzerfreundlicher machen.

## Abschluss

In diesem umfassenden Handbuch haben wir den Prozess des Aufteilens von Dokumenten in HTML-Seiten mit Aspose.Words für Java behandelt. Indem Sie die beschriebenen Schritte befolgen, können Sie Word-Dokumente effizient in das HTML-Format konvertieren und so Ihre Inhalte im Web besser zugänglich machen.

## Häufig gestellte Fragen

### Wie installiere ich Aspose.Words für Java?

 Um Aspose.Words für Java zu installieren, können Sie die Bibliothek von herunterladen[Hier](https://releases.aspose.com/words/java/) und befolgen Sie die Installationsanweisungen in der Dokumentation.

### Kann ich die HTML-Ausgabe anpassen?

 Ja, Sie können die HTML-Ausgabe anpassen, indem Sie die Speicheroptionen im`HtmlSaveOptions` Klasse. Dadurch können Sie die Formatierung und das Erscheinungsbild der generierten HTML-Dateien steuern.

### Welche Versionen von Microsoft Word werden von Aspose.Words für Java unterstützt?

Aspose.Words für Java unterstützt eine Vielzahl von Microsoft Word-Dokumentformaten, darunter DOC, DOCX, RTF und mehr. Es ist mit verschiedenen Versionen von Microsoft Word kompatibel.

### Wie kann ich mit Bildern im konvertierten HTML umgehen?

Aspose.Words für Java kann Bilder im konvertierten HTML verarbeiten, indem es sie als separate Dateien im selben Ordner wie die HTML-Datei speichert. Dadurch wird sichergestellt, dass Bilder in der HTML-Ausgabe korrekt angezeigt werden.

### Gibt es eine Testversion von Aspose.Words für Java?

Ja, Sie können von der Aspose-Website eine kostenlose Testversion von Aspose.Words für Java anfordern, um die Funktionen und Fähigkeiten zu testen, bevor Sie eine Lizenz erwerben.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
