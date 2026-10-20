---
date: '2026-02-06'
description: Erfahren Sie, wie Sie HTML‑VML mit Aspose.Words für Java laden, HTML‑Java‑Dateien
  verschlüsseln, die HTML‑Basis‑URI festlegen und HTML‑Steuerungsoptionen konfigurieren.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: HTML‑VMl mit Aspose.Words für Java laden – Komplettanleitung
url: /de/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Umfassende HTML-Funktionen mit Aspose.Words für Java: Ein Entwicklerhandbuch

## Einführung

Die Navigation durch die komplexe Welt der Dokumentenverarbeitung kann entmutigend sein, besonders beim Umgang mit verschiedenen HTML‑Funktionen. Egal, ob Sie Unterstützung für Vector Markup Language (VML), verschlüsselte Dokumente oder spezifische HTML‑Importverhalten benötigen, **Aspose.Words für Java** bietet eine robuste Lösung. In diesem Leitfaden lernen Sie **how to load html vml** effizient und sicher, während Sie auch verwandte Aufgaben wie **encrypt html java**, **set html base uri** und **configure html control** Optionen abdecken.

**Was Sie lernen werden:**
- Wie man HTML‑Dokumente mit VML‑Unterstützung lädt.
- Techniken zum Umgang mit Fixed‑Page‑HTML und Warnungen.
- Methoden zum Verschlüsseln und Laden passwortgeschützter HTML‑Dokumente.
- Verwendung von Base‑URIs in HTML‑Ladeoptionen.
- Importieren von HTML‑Input‑Elementen als Structured Document Tags oder Formularfelder.
- Ignorieren von `<noscript>`‑Elementen beim HTML‑Laden.
- Konfigurieren von Block‑Importmodi zur Steuerung der HTML‑Strukturerhaltung.
- Unterstützung von `@font-face`‑Regeln für benutzerdefinierte Schriften.

## Schnelle Antworten
- **Wie aktiviert man VML beim Laden von HTML?** Set `loadOptions.setSupportVml(true)`.
- **Kann ich passwortgeschützte HTML‑Dateien laden?** Ja, übergeben Sie das Passwort an `HtmlLoadOptions`.
- **Wie löse ich relative Bildpfade auf?** Verwenden Sie `loadOptions.setBaseUri("your/base/uri")`.
- **Ist es möglich, `<select>` als Formularfeld zu importieren?** Set `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **Welche Klasse erfasst Warnungen beim Laden?** Implementieren Sie `IWarningCallback` und weisen Sie sie `loadOptions.setWarningCallback(...)` zu.

## Voraussetzungen

Bevor wir mit der Implementierung verschiedener HTML‑Funktionen mit Aspose.Words für Java beginnen, stellen Sie sicher, dass Ihre Umgebung korrekt eingerichtet ist:

- **Erforderliche Bibliotheken:** Sie benötigen die Aspose.Words‑Bibliothek Version 25.3 oder höher.
- **Entwicklungsumgebung:** Dieser Leitfaden geht davon aus, dass Sie entweder Maven oder Gradle für das Abhängigkeitsmanagement verwenden.
- **Wissensbasis:** Ein grundlegendes Verständnis von Java und Vertrautheit mit HTML‑Dokumenten ist vorteilhaft.

## Einrichtung von Aspose.Words

Um mit Aspose.Words zu arbeiten, müssen Sie es zunächst in Ihr Projekt einbinden. Im Folgenden finden Sie die Schritte zur Einrichtung der Bibliothek mit Maven und Gradle:

### Maven

Fügen Sie die folgende Abhängigkeit zu Ihrer `pom.xml`‑Datei hinzu:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Fügen Sie dies in Ihre `build.gradle`‑Datei ein:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Lizenzbeschaffung

Aspose.Words benötigt eine Lizenz für die volle Funktionalität. Sie können eine kostenlose Testversion erhalten, eine temporäre Lizenz anfordern oder eine permanente Lizenz erwerben. Besuchen Sie die [Kaufseite](https://purchase.aspose.com/buy) für weitere Details.

Um Aspose.Words in Ihrem Java‑Projekt zu initialisieren, stellen Sie sicher, dass Sie die Lizenzierung korrekt eingerichtet haben:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## Implementierungsleitfaden

Wir werden die Implementierung in Abschnitte aufteilen, basierend auf den Funktionen, die wir implementieren möchten.

### Wie man html vml mit Aspose.Words lädt

**Übersicht:**  
Das Laden eines HTML‑Dokuments mit VML‑Unterstützung ermöglicht eine vielseitige Darstellung von Vektorgrafiken wie Diagrammen und Formen. Dies ist der zentrale Schritt für das Hauptkeyword **load html vml**.

#### Schritt‑für‑Schritt

1. **Ladeoptionen einrichten**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Dokument laden**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Bildtyp überprüfen**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Laden von Fixed‑Page‑HTML und Warnungen behandeln

**Übersicht:**  
Das Laden von Fixed‑Page‑HTML‑Dokumenten kann Warnungen erzeugen, die für eine genaue Verarbeitung verwaltet werden müssen.

#### Schritt‑für‑Schritt

1. **Warn‑Callback definieren**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **Ladeoptionen konfigurieren**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Dokument laden und Warnungen prüfen**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### HTML‑Dokumente verschlüsseln

**Übersicht:**  
Das Verschlüsseln eines HTML‑Dokuments mit einem Passwort gewährleistet einen sicheren Zugriff, was für vertrauliche Informationen unerlässlich ist – dies deckt das Szenario **encrypt html java** ab.

#### Schritt‑für‑Schritt

1. **Digitale Signatur‑Optionen vorbereiten**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **Dokument signieren und verschlüsseln**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Verschlüsseltes Dokument laden**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### Base‑URI für HTML‑Ladeoptionen

**Übersicht:**  
Die Angabe eines **set html base uri** hilft, relative URIs aufzulösen, insbesondere beim Umgang mit Bildern oder anderen verknüpften Ressourcen.

#### Schritt‑für‑Schritt

1. **Ladeoptionen mit Base‑URI konfigurieren**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Dokument laden und Bild prüfen**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### HTML‑Select als Structured Document Tag importieren

**Übersicht:**  
Um das Verhalten von **configure html control** zu steuern, können Sie `<select>`‑Elemente als Structured Document Tags importieren, was Ihnen eine feinere Kontrolle über Formularfelder in Word‑Dokumenten ermöglicht.

#### Schritt‑für‑Schritt

1. **Bevorzugten Steuertyp festlegen**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Dokument laden und Struktur prüfen**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## Häufige Probleme und Lösungen

| Problem | Ursache | Lösung |
|---------|---------|--------|
| VML‑Grafiken werden nicht angezeigt | `supportVml`‑Flag blieb auf dem Standardwert (`false`) | Stellen Sie sicher, dass `loadOptions.setSupportVml(true)` vor dem Laden gesetzt ist. |
| Bilder fehlen nach dem Laden | Relative Pfade können nicht aufgelöst werden | Verwenden Sie **set html base uri** (`loadOptions.setBaseUri(...)`), um auf den richtigen Ordner zu verweisen. |
| Passwortgeschütztes HTML wirft eine Ausnahme | Passwort nicht angegeben | Übergeben Sie das Passwort an `new HtmlLoadOptions("yourPassword")`. |
| Formularsteuerelemente erscheinen als Klartext | Falscher `HtmlControlType` | Setzen Sie `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` oder `FormField` nach Bedarf. |
| Unerwartete Warnungen | Nicht behandelte HTML‑Elemente | Implementieren Sie `IWarningCallback`, um Warnungen zu erfassen und zu prüfen. |

## Häufig gestellte Fragen

**F: Kann ich HTML‑Dateien laden, die sowohl VML‑ als auch moderne SVG‑Grafiken enthalten?**  
A: Ja. Aktivieren Sie VML mit `setSupportVml(true)`; SVG wird automatisch von Aspose.Words verarbeitet.

**F: Wie verschlüssele ich ein HTML‑Dokument, ohne ein digitales Zertifikat zu verwenden?**  
A: Verwenden Sie den `HtmlLoadOptions`‑Konstruktor, der ein Passwort akzeptiert, und speichern Sie das Dokument mit `Document.save(..., SaveFormat.HTML)`, nachdem Sie das Passwort gesetzt haben.

**F: Was passiert, wenn die Base‑URI auf einen nicht existierenden Ordner zeigt?**  
A: Aspose.Words wirft eine `FileNotFoundException` für fehlende Ressourcen. Überprüfen Sie den Pfad vor dem Laden.

**F: Ist es möglich, den Standard‑Steuertyp für alle HTML‑Formularelemente zu ändern?**  
A: Ja. Verwenden Sie `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`, um ihn global anzuwenden.

**F: Sind Warn‑Callbacks thread‑sicher?**  
A: Die Callback‑Implementierung sollte thread‑sicher sein, wenn Sie Dokumente gleichzeitig laden möchten. Verwenden Sie synchronisierte Sammlungen oder Thread‑Local‑Speicher.

---

**Zuletzt aktualisiert:** 2026-02-06  
**Getestet mit:** Aspose.Words für Java 25.3  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}