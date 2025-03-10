---
title: Dokumente als Markdown in Aspose.Words für Java speichern
linktitle: Dokumente als Markdown speichern
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie Word-Dokumente mit Aspose.Words für Java in Markdown konvertieren. Diese Schritt-für-Schritt-Anleitung behandelt Tabellenausrichtung, Bildverarbeitung und mehr.
weight: 18
url: /de/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumente als Markdown in Aspose.Words für Java speichern


## Einführung in das Speichern von Dokumenten als Markdown in Aspose.Words für Java

In dieser Schritt-für-Schritt-Anleitung zeigen wir Ihnen, wie Sie Dokumente mit Aspose.Words für Java als Markdown speichern. Markdown ist eine leichtgewichtige Auszeichnungssprache, die häufig zum Formatieren von Textdokumenten verwendet wird. Mit Aspose.Words für Java können Sie Ihre Word-Dokumente ganz einfach in das Markdown-Format konvertieren. Wir behandeln verschiedene Aspekte des Speicherns von Markdown-Dateien, darunter die Ausrichtung von Tabelleninhalten und die Handhabung von Bildern.

## Voraussetzungen

Stellen Sie zunächst sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Auf Ihrem System ist Java Development Kit (JDK) installiert.
-  Aspose.Words für Java-Bibliothek. Sie können es herunterladen von[Hier](https://releases.aspose.com/words/java/).

## Schritt 1: Erstellen eines Word-Dokuments

Beginnen wir mit der Erstellung eines Word-Dokuments, das wir später in das Markdown-Format konvertieren. Sie können dieses Dokument nach Ihren Anforderungen anpassen.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen einer Tabelle mit zwei Zellen
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Speichern Sie das Dokument als Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 In diesem Beispiel erstellen wir eine einfache Tabelle mit zwei Zellen und legen die Ausrichtung der Absätze innerhalb dieser Zellen fest. Anschließend speichern wir das Dokument als Markdown mit dem`MarkdownSaveOptions`.

## Schritt 2: Ausrichtung des Tabelleninhalts anpassen

Mit Aspose.Words für Java können Sie die Ausrichtung des Tabelleninhalts beim Speichern als Markdown anpassen. Sie können den Tabelleninhalt links, rechts, zentriert ausrichten oder ihn automatisch basierend auf dem ersten Absatz in jeder Tabellenspalte bestimmen lassen.

So passen Sie die Ausrichtung des Tabelleninhalts an:

```java
// Stellen Sie die Ausrichtung des Tabelleninhalts auf links ein
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Stellen Sie die Ausrichtung des Tabelleninhalts auf rechts ein
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Zentrierung des Tabelleninhalts
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Stellen Sie die Ausrichtung des Tabelleninhalts auf „Automatisch“ (wird durch den ersten Absatz bestimmt).
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Durch Ändern der`TableContentAlignment` -Eigenschaft können Sie steuern, wie der Inhalt in Tabellen bei der Konvertierung in Markdown ausgerichtet wird.

## Schritt 3: Umgang mit Bildern

 Um Bilder in Ihr Markdown-Dokument einzubinden, müssen Sie den Ordner angeben, in dem sich die Bilder befinden. Mit Aspose.Words für Java können Sie den Bilderordner im`MarkdownSaveOptions`.

So legen Sie den Bilderordner fest und speichern das Dokument mit Bildern:

```java
// Laden Sie ein Dokument mit Bildern
Document doc = new Document("document_with_images.docx");

// Legen Sie den Bilderordnerpfad fest
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Speichern Sie das Dokument mit Bildern
doc.save("document_with_images.md", saveOptions);
```

 Ersetzen Sie unbedingt`"document_with_images.docx"` mit dem Pfad zu Ihrem Word-Dokument mit Bildern und`"images_folder/"` durch den tatsächlichen Pfad zum Ordner, in dem Ihre Bilder gespeichert sind.

## Vollständiger Quellcode zum Speichern von Dokumenten als Markdown in Aspose.Words für Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Sorgt dafür, dass alle Absätze innerhalb der Tabelle ausgerichtet werden.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Die Ausrichtung wird in diesem Fall dem ersten Absatz in der entsprechenden Tabellenspalte entnommen.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Abschluss

In diesem Handbuch haben wir untersucht, wie man Dokumente mit Aspose.Words für Java als Markdown speichert. Wir haben die Erstellung eines Word-Dokuments, die Anpassung der Ausrichtung von Tabelleninhalten und den Umgang mit Bildern in Markdown-Dateien behandelt. Sie können Ihre Word-Dokumente jetzt effizient in das Markdown-Format konvertieren, sodass sie für verschiedene Veröffentlichungsplattformen und Dokumentationsanforderungen geeignet sind.

## Häufig gestellte Fragen

### Wie installiere ich Aspose.Words für Java?

 Aspose.Words für Java kann installiert werden, indem Sie die Bibliothek in Ihr Java-Projekt einbinden. Sie können die Bibliothek herunterladen von[Hier](https://releases.aspose.com/words/java/) und befolgen Sie die Installationsanweisungen in der Dokumentation.

### Kann ich komplexe Word-Dokumente mit Tabellen und Bildern in Markdown konvertieren?

Ja, Aspose.Words für Java unterstützt die Konvertierung komplexer Word-Dokumente mit Tabellen, Bildern und verschiedenen Formatierungselementen in Markdown. Sie können die Markdown-Ausgabe entsprechend der Komplexität Ihres Dokuments anpassen.

### Wie kann ich Bilder in Markdown-Dateien verarbeiten?

 Um Bilder in Markdown-Dateien einzubinden, legen Sie den Bilderordnerpfad mit dem`setImagesFolder`Methode in`MarkdownSaveOptions`. Stellen Sie sicher, dass die Bilddateien im angegebenen Ordner gespeichert sind, und Aspose.Words für Java behandelt die Bildreferenzen entsprechend.

### Gibt es eine Testversion von Aspose.Words für Java?

Ja, Sie können eine Testversion von Aspose.Words für Java von der Aspose-Website herunterladen. Mit der Testversion können Sie die Funktionen der Bibliothek testen, bevor Sie eine Lizenz erwerben.

### Wo finde ich weitere Beispiele und Dokumentation?

 Weitere Beispiele, Dokumentationen und detaillierte Informationen zu Aspose.Words für Java finden Sie im[Dokumentation](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
