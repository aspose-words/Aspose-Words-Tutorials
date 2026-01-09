---
date: 2026-01-09
description: Erfahren Sie, wie Sie DOCX-Dateien mit einem Passwort verschlüsseln und
  beim Speichern von Dokumenten im OOXML-Format die Komprimierungsstufe ändern, indem
  Sie Aspose.Words für Java verwenden.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: DOCX mit Passwort verschlüsseln – OOXML speichern mit Aspose.Words Java
url: /de/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# DOCX mit Passwort verschlüsseln – OOXML speichern mit Aspose.Words Java

## Einführung in das Speichern von Dokumenten im OOXML-Format mit Aspose.Words für Java

In diesem Leitfaden erfahren Sie, wie Sie **DOCX mit Passwort verschlüsseln** und Dokumente im OOXML-Format mit Aspose.Words für Java speichern. OOXML (Office Open XML) ist das moderne Dateiformat, das von Microsoft Word und vielen anderen Office-Anwendungen verwendet wird. Wir gehen die gebräuchlichsten Optionen durch – Passwortschutz, Konformitätsstufen, Aktualisierung von Eigenschaften, Behandlung von Legacy‑Steuerzeichen und **wie man die Komprimierungsstufe ändert** – damit Sie die Ausgabe exakt an Ihre Anforderungen anpassen können.

## Quick Answers
- **Wie kann ich eine Word‑Datei schützen?** Verwenden Sie `OoxmlSaveOptions.setPassword("yourPassword")` vor dem Speichern.  
- **Welche OOXML‑Konformitätsstufe sollte ich wählen?** ISO 29500 2008 Strict für maximale Kompatibilität mit modernen Office‑Versionen.  
- **Kann ich Legacy‑Steuerzeichen beibehalten?** Ja, aktivieren Sie `setKeepLegacyControlChars(true)`.  
- **Wie ändere ich die Komprimierungsstufe?** Setzen Sie `setCompressionLevel(CompressionLevel.SUPER_FAST)` oder `MAXIMUM` nach Bedarf.  
- **Beeinflussen diese Optionen die Dateigröße?** Die Komprimierungsstufe und die Behandlung von Legacy‑Steuerzeichen können die endgültige .docx‑Größe merklich verändern.

## Was bedeutet „DOCX mit Passwort verschlüsseln“?
Das Verschlüsseln einer DOCX‑Datei bedeutet, dass das Dokument mit AES‑256‑Verschlüsselung gespeichert wird und ein Passwort zum Öffnen in Word oder einem kompatiblen Viewer erforderlich ist. Dies ist unerlässlich, um vertrauliche Informationen zu schützen, wenn Dateien per E‑Mail, Cloud‑Speicher oder Intranet‑Portalen geteilt werden.

## Warum OOXML‑Speicheroptionen verwenden?
- **Sicherheit:** Passwortschutz verhindert unbefugten Zugriff.  
- **Kompatibilität:** Konformitätseinstellungen stellen sicher, dass die Datei in verschiedenen Word‑Versionen funktioniert.  
- **Leistung:** Das Anpassen der Kompression kann das Speichern beschleunigen oder die Dateigröße reduzieren.  
- **Erhaltung:** Das Beibehalten von Legacy‑Steuerzeichen bewahrt die Treue bei der Konvertierung älterer Dokumente.

## Voraussetzungen
- Aspose.Words für Java‑Bibliothek zu Ihrem Projekt hinzugefügt (Maven/Gradle oder manuelles JAR).  
- Java 8 oder höher.  
- Ein Quelldokument (`.docx` oder `.doc`), das Sie verarbeiten möchten.

## Speichern eines Dokuments mit Passwortverschlüsselung

Sie können Ihr Dokument beim Speichern im OOXML-Format mit einem Passwort verschlüsseln. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **Profi‑Tipp:** Wählen Sie ein starkes Passwort und bewahren Sie es sicher auf; das Passwort kann aus der verschlüsselten Datei nicht wiederhergestellt werden.

## Festlegen der OOXML‑Konformität

Sie können die OOXML‑Konformitätsstufe beim Speichern des Dokuments festlegen. Zum Beispiel können Sie sie auf ISO 29500:2008 (Strict) setzen. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Aktualisieren der Eigenschaft „Last Saved Time“

Sie können beim Speichern des Dokuments die Eigenschaft „Last Saved Time“ (Letzte Speicherzeit) aktualisieren. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Beibehalten von Legacy‑Steuerzeichen

Falls Ihr Dokument Legacy‑Steuerzeichen enthält, können Sie diese beim Speichern beibehalten. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Ändern der Komprimierungsstufe beim Speichern von OOXML

Sie können die Komprimierungsstufe beim Speichern des Dokuments anpassen. Zum Beispiel können Sie `SUPER_FAST` für minimale Kompression oder `MAXIMUM` für die kleinste Dateigröße setzen. So geht's:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Dies sind einige der wichtigsten Optionen und Einstellungen, die Sie beim Speichern von Dokumenten im OOXML-Format mit Aspose.Words für Java verwenden können. Erkunden Sie gern weitere Optionen und passen Sie den Dokument‑Speicherungsprozess nach Bedarf an.

## Vollständiger Quellcode zum Speichern von Dokumenten im OOXML-Format mit Aspose.Words für Java

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

## Fazit

In diesem umfassenden Leitfaden haben wir untersucht, wie man **DOCX mit Passwort verschlüsselt** und Dokumente im OOXML-Format mit Aspose.Words für Java speichert. Egal, ob Sie Ihre Dateien schützen, strenge OOXML‑Konformität sicherstellen, Dokumenteneigenschaften aktualisieren, Legacy‑Steuerzeichen erhalten oder **die Komprimierungsstufe ändern** möchten – Aspose.Words bietet ein vielseitiges Set an Werkzeugen, um Ihre Anforderungen zu erfüllen.

## Häufig gestellte Fragen

**F: Wie entferne ich den Passwortschutz von einem passwortgeschützten Dokument?**  
A: Öffnen Sie das Dokument mit dem korrekten Passwort und speichern Sie es anschließend ohne Angabe eines Passworts in `OoxmlSaveOptions`. Dadurch entsteht eine ungeschützte Kopie.

**F: Kann ich beim Speichern eines Dokuments im OOXML-Format benutzerdefinierte Eigenschaften festlegen?**  
A: Ja. Verwenden Sie `BuiltInDocumentProperties` und `CustomDocumentProperties` am `Document`‑Objekt, bevor Sie `save()` aufrufen.

**F: Was ist die Standard‑Komprimierungsstufe beim Speichern eines Dokuments im OOXML-Format?**  
A: Der Standard ist `CompressionLevel.NORMAL`. Sie können zu `SUPER_FAST` für Geschwindigkeit oder `MAXIMUM` für die kleinste Dateigröße wechseln.

**F: Beeinflusst das Aktivieren von `keepLegacyControlChars` die Kompatibilität mit modernen Word‑Versionen?**  
A: Moderne Word‑Versionen können Dateien mit Legacy‑Steuerzeichen öffnen, jedoch können einige ältere Funktionen anders dargestellt werden. Verwenden Sie diese Option nur, wenn Sie den genauen Originalinhalt erhalten müssen.

**F: Ist es möglich, mehrere Speicheroptionen (z. B. Passwort + Kompression) in einem einzigen Aufruf zu kombinieren?**  
A: Absolut. Konfigurieren Sie alle gewünschten Eigenschaften in einer einzigen `OoxmlSaveOptions`‑Instanz, bevor Sie sie an `doc.save()` übergeben.

---

**Zuletzt aktualisiert:** 2026-01-09  
**Getestet mit:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}