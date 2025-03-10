---
title: Verwenden von Ladeoptionen in Aspose.Words für Java
linktitle: Verwenden von Ladeoptionen
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Ladeoptionen in Aspose.Words für Java meistern. Passen Sie das Laden von Dokumenten an, handhaben Sie die Verschlüsselung, konvertieren Sie Formen, legen Sie Word-Versionen fest und mehr für eine effiziente Java-Dokumentenverarbeitung.
weight: 11
url: /de/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Ladeoptionen in Aspose.Words für Java


## Einführung in die Arbeit mit Ladeoptionen in Aspose.Words für Java

In diesem Tutorial erfahren Sie, wie Sie mit Ladeoptionen in Aspose.Words für Java arbeiten. Mit Ladeoptionen können Sie anpassen, wie Dokumente geladen und verarbeitet werden. Wir behandeln verschiedene Szenarien, darunter das Aktualisieren von schmutzigen Feldern, das Laden verschlüsselter Dokumente, das Konvertieren von Formen in Office Math, das Festlegen der MS Word-Version, das Angeben eines temporären Ordners, das Behandeln von Warnungen und das Konvertieren von Metadateien in PNG. Lassen Sie uns Schritt für Schritt eintauchen.

## Aktualisieren von nicht überprüften Feldern

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 Dieser Codeausschnitt zeigt, wie man schmutzige Felder in einem Dokument aktualisiert.`setUpdateDirtyFields(true)` Die Methode wird verwendet, um sicherzustellen, dass beim Laden des Dokuments fehlerhafte Felder aktualisiert werden.

## Verschlüsseltes Dokument laden

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 Hier laden wir ein verschlüsseltes Dokument mit einem Passwort.`LoadOptions` Der Konstruktor akzeptiert das Dokumentkennwort, und Sie können beim Speichern des Dokuments auch ein neues Kennwort angeben mit`OdtSaveOptions`.

## Shape in Office Math konvertieren

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 Dieser Code zeigt, wie Sie beim Laden von Dokumenten Formen in Office Math-Objekte konvertieren.`setConvertShapeToOfficeMath(true)`Methode ermöglicht diese Konvertierung.

## MS Word-Version festlegen

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 Sie können die MS Word-Version für das Laden von Dokumenten angeben. In diesem Beispiel setzen wir die Version auf Microsoft Word 2010 mit`setMswVersion`.

## Temporären Ordner verwenden

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 Durch Festlegen des temporären Ordners mit`setTempFolder`können Sie steuern, wo während der Dokumentverarbeitung temporäre Dateien gespeichert werden.

## Warnhinweis-Rückruf

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Behandeln Sie Warnungen, wenn diese beim Laden des Dokuments auftreten.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Dieser Code zeigt, wie Sie einen Warn-Callback einrichten, um Warnungen während des Ladens von Dokumenten zu behandeln. Sie können das Verhalten Ihrer Anwendung bei auftretenden Warnungen anpassen.

## Metadateien in PNG konvertieren

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 Um Metadateien (z. B. WMF) während des Ladens von Dokumenten in PNG-Bilder umzuwandeln, können Sie den`setConvertMetafilesToPng(true)` Verfahren.

## Vollständiger Quellcode zum Arbeiten mit Ladeoptionen in Aspose.Words für Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Erstellen Sie ein neues LoadOptions-Objekt, das standardmäßig Dokumente gemäß der MS Word 2019-Spezifikation lädt
	// und ändern Sie die Ladeversion auf Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		//Druckt Warnungen und deren Details, sobald sie beim Laden des Dokuments auftreten.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Abschluss

In diesem Tutorial haben wir uns mit verschiedenen Aspekten der Arbeit mit Ladeoptionen in Aspose.Words für Java befasst. Ladeoptionen spielen eine entscheidende Rolle bei der Anpassung der Art und Weise, wie Dokumente geladen und verarbeitet werden, sodass Sie Ihre Dokumentverarbeitung an Ihre spezifischen Anforderungen anpassen können. Lassen Sie uns die wichtigsten Punkte dieses Handbuchs noch einmal zusammenfassen:

## Häufig gestellte Fragen

### Wie kann ich mit Warnungen beim Laden von Dokumenten umgehen?

 Sie können einen Warn-Callback einrichten, wie in der`warningCallback()` Methode oben. Passen Sie die`DocumentLoadingWarningCallback` Klasse, um Warnungen entsprechend den Anforderungen Ihrer Anwendung zu behandeln.

### Kann ich beim Laden eines Dokuments Formen in Office Math-Objekte konvertieren?

 Ja, Sie können Formen in Office Math-Objekte umwandeln, indem Sie`loadOptions.setConvertShapeToOfficeMath(true)`.

### Wie gebe ich die MS Word-Version zum Laden von Dokumenten an?

 Verwenden`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` um die MS Word-Version zum Laden des Dokuments anzugeben.

###  Was ist der Zweck der`setTempFolder` method in Load Options?

 Der`setTempFolder`Mit dieser Methode können Sie den Ordner angeben, in dem während der Dokumentverarbeitung temporäre Dateien gespeichert werden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
