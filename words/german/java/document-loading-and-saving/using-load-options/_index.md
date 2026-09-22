---
date: 2025-12-27
description: Erfahren Sie, wie Sie LoadOptions in Aspose.Words für Java festlegen,
  einschließlich der Angabe des temporären Ordners, der Einstellung der Word-Version,
  der Konvertierung von Metadateien in PNG und der Umwandlung von Formen in mathematische
  Formeln für eine flexible Dokumentenverarbeitung.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Wie man LoadOptions in Aspose.Words für Java festlegt
url: /de/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man LoadOptions in Aspose.Words für Java festlegt

In diesem Tutorial gehen wir Schritt für Schritt durch **wie man LoadOptions** für verschiedene reale Szenarien beim Arbeiten mit Aspose.Words für Java einstellt. LoadOptions geben Ihnen eine feinkörnige Kontrolle darüber, wie ein Dokument geöffnet wird – ob Sie schmutzige Felder aktualisieren, mit verschlüsselten Dateien arbeiten, Formen in Office Math konvertieren oder der Bibliothek mitteilen müssen, wo temporäre Daten gespeichert werden sollen. Am Ende können Sie das Ladeverhalten exakt an die Anforderungen Ihrer Anwendung anpassen.

## Schnelle Antworten
- **Was ist LoadOptions?** Ein Konfigurationsobjekt, das beeinflusst, wie Aspose.Words ein Dokument lädt.  
- **Kann ich Felder beim Laden aktualisieren?** Ja – setzen Sie `setUpdateDirtyFields(true)`.  
- **Wie öffne ich eine passwortgeschützte Datei?** Übergeben Sie das Passwort dem `LoadOptions`‑Konstruktor.  
- **Ist es möglich, den temporären Ordner zu ändern?** Verwenden Sie `setTempFolder("Pfad")`.  
- **Welche Methode konvertiert Formen zu Office Math?** `setConvertShapeToOfficeMath(true)`.

## Warum LoadOptions verwenden?
LoadOptions ermöglichen es, Nachbearbeitungsschritte zu vermeiden, den Speicherverbrauch zu reduzieren und sicherzustellen, dass das Dokument genau so interpretiert wird, wie Sie es benötigen. Beispielsweise verhindert das Konvertieren von Metadateien zu PNG während des Ladens spätere Rasterisierungsprobleme, und das Festlegen der MS‑Word‑Version hilft, die Layout‑Treue bei Legacy‑Dateien zu wahren.

## Voraussetzungen
- Java 17 oder höher  
- Aspose.Words für Java (neueste Version)  
- Eine gültige Aspose‑Lizenz für den Produktionseinsatz  

## Schritt‑für‑Schritt‑Anleitung

### Schmutzige Felder aktualisieren

Wenn ein Dokument Felder enthält, die bearbeitet, aber nicht aktualisiert wurden, können Sie Aspose.Words anweisen, diese beim Laden automatisch zu aktualisieren.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*Der Aufruf `setUpdateDirtyFields(true)` stellt sicher, dass alle schmutzigen Felder sofort nach dem Öffnen des Dokuments neu berechnet werden.*

### Verschlüsseltes Dokument laden

Ist Ihre Quelldatei passwortgeschützt, geben Sie das Passwort beim Erzeugen der `LoadOptions`‑Instanz an. Sie können beim Speichern in ein anderes Format auch ein neues Passwort festlegen.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Form in Office Math konvertieren

Einige ältere Dokumente speichern Gleichungen als Zeichenformen. Durch Aktivieren dieser Option werden diese Formen in native Office‑Math‑Objekte umgewandelt, die später leichter zu bearbeiten sind.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### MS‑Word‑Version festlegen

Die Angabe der Ziel‑Word‑Version hilft der Bibliothek, die richtigen Render‑Regeln zu wählen, insbesondere beim Umgang mit älteren Dateiformaten.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Temporären Ordner verwenden

Große Dokumente können temporäre Dateien erzeugen (z. B. beim Extrahieren von Bildern). Sie können diese Dateien in einen von Ihnen gewählten Ordner leiten, was in sandbox‑Umgebungen nützlich ist.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Warnungs‑Callback

Während des Ladens kann Aspose.Words Warnungen ausgeben (z. B. nicht unterstützte Features). Durch Implementieren eines Callbacks können Sie diese Ereignisse protokollieren oder darauf reagieren.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Metadateien in PNG konvertieren

Metadateien wie WMF können beim Laden in PNG gerastert werden, wodurch ein konsistentes Rendering über Plattformen hinweg gewährleistet wird.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Vollständiger Quellcode für die Arbeit mit LoadOptions in Aspose.Words für Java

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
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
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
		// Prints warnings and their details as they arise during document loading.
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

## Häufige Anwendungsfälle & Tipps

- **Batch‑Konvertierungs‑Pipelines** – Kombinieren Sie `setTempFolder` mit einem geplanten Job, um Hunderte von Dateien zu verarbeiten, ohne das System‑Temp‑Verzeichnis zu füllen.  
- **Migration von Legacy‑Dokumenten** – Verwenden Sie `setMswVersion` zusammen mit `setConvertShapeToOfficeMath`, um alte Konstruktionsdokumente in ein modernes Format zu überführen und dabei Gleichungen zu erhalten.  
- **Sichere Dokumentenverarbeitung** – Kombinieren Sie `loadEncryptedDocument` mit `OdtSaveOptions`, um Dateien mit einem neuen Passwort in einem anderen Format neu zu verschlüsseln.  

## Häufig gestellte Fragen

**F: Wie kann ich Warnungen während des Dokumentenladens behandeln?**  
A: Implementieren Sie ein benutzerdefiniertes `IWarningCallback` (wie im *Warnungs‑Callback*-Beispiel gezeigt) und registrieren Sie es über `loadOptions.setWarningCallback(...)`. So können Sie je nach Schweregrad protokollieren, ignorieren oder den Vorgang abbrechen.

**F: Kann ich Formen beim Laden eines Dokuments in Office‑Math‑Objekte konvertieren?**  
A: Ja – rufen Sie `loadOptions.setConvertShapeToOfficeMath(true)` auf, bevor Sie das `Document` konstruieren. Die Bibliothek ersetzt kompatible Formen automatisch durch native Office‑Math‑Objekte.

**F: Wie lege ich die MS‑Word‑Version für das Laden eines Dokuments fest?**  
A: Verwenden Sie `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (oder einen anderen Enum‑Wert), um Aspose.Words mitzuteilen, welche Word‑Version‑Renderregeln angewendet werden sollen.

**F: Welchen Zweck hat die Methode `setTempFolder` in LoadOptions?**  
A: Sie leitet alle während des Ladens erzeugten temporären Dateien (wie extrahierte Bilder) in einen von Ihnen kontrollierten Ordner, was in Umgebungen mit eingeschränkten System‑Temp‑Verzeichnissen entscheidend ist.

**F: Ist es möglich, Metadateien wie WMF beim Laden in PNG zu konvertieren?**  
A: Absolut – aktivieren Sie dies mit `loadOptions.setConvertMetafilesToPng(true)`. Dadurch werden Rasterbilder als PNG gespeichert, was die Kompatibilität mit modernen Betrachtern verbessert.

## Fazit

Wir haben die wesentlichen Techniken behandelt, **wie man LoadOptions** in Aspose.Words für Java festlegt – vom Aktualisieren schmutziger Felder über den Umgang mit verschlüsselten Dateien, das Konvertieren von Formen, das Festlegen der Word‑Version, das Lenken temporärer Speicherorte und mehr. Durch die Nutzung dieser Optionen können Sie robuste, leistungsstarke Dokumenten‑Verarbeitungspipelines bauen, die sich an ein breites Spektrum von Eingabeszenarien anpassen.

---

**Zuletzt aktualisiert:** 2025-12-27  
**Getestet mit:** Aspose.Words für Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}