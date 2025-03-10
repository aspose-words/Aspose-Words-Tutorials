---
title: Speichern von Dokumenten im OOXML-Format in Aspose.Words für Java
linktitle: Dokumente im OOXML-Format speichern
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words für Java Dokumente im OOXML-Format speichern. Sichern, optimieren und passen Sie Ihre Dateien mühelos an.
weight: 20
url: /de/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Speichern von Dokumenten im OOXML-Format in Aspose.Words für Java


## Einführung in das Speichern von Dokumenten im OOXML-Format in Aspose.Words für Java

In dieser Anleitung erfahren Sie, wie Sie Dokumente mit Aspose.Words für Java im OOXML-Format speichern. OOXML (Office Open XML) ist ein Dateiformat, das von Microsoft Word und anderen Office-Anwendungen verwendet wird. Wir behandeln verschiedene Optionen und Einstellungen zum Speichern von Dokumenten im OOXML-Format.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie die Aspose.Words-Bibliothek für Java in Ihrem Projekt eingerichtet haben.

## Speichern eines Dokuments mit Kennwortverschlüsselung

Sie können Ihr Dokument beim Speichern im OOXML-Format mit einem Kennwort verschlüsseln. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Laden Sie das Dokument
Document doc = new Document("Document.docx");

// OoxmlSaveOptions erstellen und Passwort festlegen
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Speichern Sie das Dokument verschlüsselt
doc.save("EncryptedDoc.docx", saveOptions);
```

## Festlegen der OOXML-Konformität

Sie können die OOXML-Konformitätsstufe beim Speichern des Dokuments angeben. Sie können sie beispielsweise auf ISO 29500:2008 (streng) festlegen. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Laden Sie das Dokument
Document doc = new Document("Document.docx");

// Optimieren für Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// OoxmlSaveOptions erstellen und Compliance-Level festlegen
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Speichern Sie das Dokument mit der Compliance-Einstellung
doc.save("ComplianceDoc.docx", saveOptions);
```

## Aktualisieren der Eigenschaft „Zuletzt gespeicherter Zeitpunkt“

Sie können die Eigenschaft „Zuletzt gespeichert“ des Dokuments beim Speichern aktualisieren. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Laden Sie das Dokument
Document doc = new Document("Document.docx");

// Erstellen Sie OoxmlSaveOptions und aktivieren Sie die Aktualisierung der Eigenschaft „Letzte Speicherungszeit“
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Speichern Sie das Dokument mit der aktualisierten Eigenschaft
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Beibehalten von Legacy-Steuerzeichen

Wenn Ihr Dokument veraltete Steuerzeichen enthält, können Sie diese beim Speichern beibehalten. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//Laden eines Dokuments mit älteren Steuerzeichen
Document doc = new Document("LegacyControlChars.doc");

// Erstellen Sie OoxmlSaveOptions mit dem FLAT_OPC-Format und aktivieren Sie die Beibehaltung von Legacy-Steuerzeichen
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Speichern des Dokuments mit alten Steuerzeichen
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Einstellen der Komprimierungsstufe

Sie können die Komprimierungsstufe beim Speichern des Dokuments anpassen. Sie können sie beispielsweise auf SUPER_FAST für minimale Komprimierung einstellen. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Laden Sie das Dokument
Document doc = new Document("Document.docx");

// Erstellen Sie OoxmlSaveOptions und legen Sie die Komprimierungsstufe fest
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Speichern Sie das Dokument mit der angegebenen Komprimierungsstufe
doc.save("FastCompressionDoc.docx", saveOptions);
```

Dies sind einige der wichtigsten Optionen und Einstellungen, die Sie beim Speichern von Dokumenten im OOXML-Format mit Aspose.Words für Java verwenden können. Sie können gerne weitere Optionen erkunden und Ihren Dokumentspeicherprozess nach Bedarf anpassen.

## Vollständiger Quellcode zum Speichern von Dokumenten im OOXML-Format in Aspose.Words für Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Abschluss

In diesem umfassenden Handbuch haben wir untersucht, wie Sie Dokumente mit Aspose.Words für Java im OOXML-Format speichern. Ob Sie Ihre Dokumente mit Passwörtern verschlüsseln, die Einhaltung bestimmter OOXML-Standards sicherstellen, Dokumenteigenschaften aktualisieren, alte Steuerzeichen beibehalten oder Komprimierungsstufen anpassen müssen – Aspose.Words bietet einen vielseitigen Satz von Tools, die Ihren Anforderungen gerecht werden.

## Häufig gestellte Fragen

### Wie entferne ich den Kennwortschutz von einem kennwortgeschützten Dokument?

Um den Kennwortschutz eines kennwortgeschützten Dokuments aufzuheben, können Sie das Dokument mit dem richtigen Kennwort öffnen und anschließend speichern, ohne in den Speicheroptionen ein Kennwort anzugeben. Dadurch wird das Dokument ohne Kennwortschutz gespeichert.

### Kann ich beim Speichern eines Dokuments im OOXML-Format benutzerdefinierte Eigenschaften festlegen?

 Ja, Sie können benutzerdefinierte Eigenschaften für ein Dokument festlegen, bevor Sie es im OOXML-Format speichern. Verwenden Sie die`BuiltInDocumentProperties` Und`CustomDocumentProperties` Klassen zum Festlegen verschiedener Eigenschaften wie Autor, Titel, Schlüsselwörter und benutzerdefinierte Eigenschaften.

### Was ist die Standardkomprimierungsstufe beim Speichern eines Dokuments im OOXML-Format?

 Die Standardkomprimierungsstufe beim Speichern eines Dokuments im OOXML-Format mit Aspose.Words für Java ist`NORMAL` Sie können die Komprimierungsstufe ändern auf`SUPER_FAST` oder`MAXIMUM` nach Bedarf.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
