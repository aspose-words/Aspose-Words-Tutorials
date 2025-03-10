---
title: Zusammenfügen und Anhängen von Dokumenten in Aspose.Words für Java
linktitle: Dokumente zusammenfügen und anhängen
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words für Java mühelos Dokumente zusammenfügen und anhängen. Behalten Sie die Formatierung bei, verwalten Sie Kopf- und Fußzeilen und mehr.
weight: 30
url: /de/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zusammenfügen und Anhängen von Dokumenten in Aspose.Words für Java


## Einführung in das Zusammenfügen und Anhängen von Dokumenten in Aspose.Words für Java

In diesem Tutorial erfahren Sie, wie Sie Dokumente mithilfe der Bibliothek Aspose.Words für Java zusammenfügen und anhängen. Sie lernen, wie Sie mehrere Dokumente nahtlos zusammenführen und dabei Formatierung und Struktur beibehalten.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Aspose.Words für die Java-API in Ihrem Java-Projekt eingerichtet haben.

## Optionen zum Zusammenführen von Dokumenten

### Einfaches Anhängen

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Anhängen mit Importformatoptionen

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### An leeres Dokument anhängen

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Anhängen mit Seitenzahlkonvertierung

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Konvertieren von NUMPAGES-Feldern
dstDoc.updatePageLayout(); // Aktualisieren Sie das Seitenlayout für die korrekte Nummerierung
```

## Umgang mit unterschiedlichen Seiteneinstellungen

Beim Anhängen von Dokumenten mit unterschiedlichem Seitenaufbau:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Stellen Sie sicher, dass die Seiteneinrichtungseinstellungen mit dem Zieldokument übereinstimmen
```

## Zusammenführen von Dokumenten mit unterschiedlichen Stilen

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Smart Style-Verhalten

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Einfügen von Dokumenten mit DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Beibehalten der Quellennummerierung

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Umgang mit Textfeldern

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Kopf- und Fußzeilen verwalten

### Verknüpfen von Kopf- und Fußzeilen

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Aufheben der Verknüpfung von Kopf- und Fußzeilen

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Abschluss

Aspose.Words für Java bietet flexible und leistungsstarke Tools zum Zusammenfügen und Anhängen von Dokumenten, egal ob Sie die Formatierung beibehalten, verschiedene Seiteneinstellungen handhaben oder Kopf- und Fußzeilen verwalten müssen. Experimentieren Sie mit diesen Techniken, um Ihre spezifischen Anforderungen an die Dokumentverarbeitung zu erfüllen.

## Häufig gestellte Fragen

### Wie kann ich Dokumente mit unterschiedlichen Stilen nahtlos zusammenführen?

 Um Dokumente mit unterschiedlichen Stilen zusammenzuführen, verwenden Sie`ImportFormatMode.USE_DESTINATION_STYLES` beim Anhängen.

### Kann ich beim Anhängen von Dokumenten die Seitennummerierung beibehalten?

 Ja, Sie können die Seitennummerierung beibehalten, indem Sie`convertNumPageFieldsToPageRef` Methode und Aktualisieren des Seitenlayouts.

### Was ist Smart Style Behavior?

 Smart Style Behavior hilft dabei, konsistente Stile beim Anhängen von Dokumenten beizubehalten. Verwenden Sie es mit`ImportFormatOptions` für bessere Ergebnisse.

### Wie kann ich beim Anhängen von Dokumenten mit Textfeldern umgehen?

Satz`importFormatOptions.setIgnoreTextBoxes(false)` um Textfelder beim Anhängen einzuschließen.

### Was passiert, wenn ich Kopf- und Fußzeilen zwischen Dokumenten verknüpfen/die Verknüpfung aufheben möchte?

 Sie können Kopf- und Fußzeilen verknüpfen mit`linkToPrevious(true)` oder trennen Sie sie mit`linkToPrevious(false)` nach Bedarf.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
