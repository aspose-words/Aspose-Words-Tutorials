---
date: '2026-02-06'
description: Lär dig hur du laddar HTML VML med Aspose.Words för Java, krypterar HTML
  Java‑filer, ställer in HTML‑bas‑URI och konfigurerar HTML‑kontrollalternativ.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Ladda HTML VML med Aspose.Words för Java – komplett guide
url: /sv/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Omfattande HTML‑funktioner med Aspose.Words för Java: En utvecklarguide

## Introduction

Att navigera i den komplexa världen av dokumentbehandling kan vara överväldigande, särskilt när man hanterar olika HTML‑funktioner. Oavsett om du arbetar med stöd för Vector Markup Language (VML), krypterade dokument eller specifika HTML‑importbeteenden, erbjuder **Aspose.Words för Java** en robust lösning. I den här guiden kommer du att lära dig **hur du laddar html vml** på ett effektivt och säkert sätt, samtidigt som du täcker relaterade uppgifter som **encrypt html java**, **set html base uri** och **configure html control**‑alternativ.

**What You'll Learn:**
- Hur du laddar HTML‑dokument med VML‑stöd.
- Tekniker för att hantera fast‑sidig HTML och varningar.
- Metoder för att kryptera och ladda lösenordsskyddade HTML‑dokument.
- Användning av bas‑URI:er i HTML Load Options.
- Import av HTML‑input‑element som Structured Document Tags eller formulärfält.
- Ignorera `<noscript>`‑element under HTML‑laddning.
- Konfigurera block‑importlägen för att styra bevarande av HTML‑struktur.
- Stöd för `@font-face`‑regler för anpassade teckensnitt.

## Quick Answers
- **What is the primary way to enable VML when loading HTML?** Set `loadOptions.setSupportVml(true)`.
- **Can I load password‑protected HTML files?** Yes, pass the password to `HtmlLoadOptions`.
- **How do I resolve relative image paths?** Use `loadOptions.setBaseUri("your/base/uri")`.
- **Is it possible to import `<select>` as a form field?** Set `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **What class captures warnings during load?** Implement `IWarningCallback` and assign it to `loadOptions.setWarningCallback(...)`.

## Prerequisites

Innan vi börjar implementera olika HTML‑funktioner med Aspose.Words för Java, se till att din miljö är korrekt konfigurerad:

- **Required Libraries:** Du behöver Aspose.Words‑biblioteket version 25.3 eller senare.
- **Development Environment:** Denna guide förutsätter att du använder antingen Maven eller Gradle för beroendehantering.
- **Knowledge Base:** En grundläggande förståelse för Java och bekantskap med HTML‑dokument är fördelaktigt.

## Setting Up Aspose.Words

För att börja arbeta med Aspose.Words måste du först inkludera det i ditt projekt. Nedan följer stegen för att sätta upp biblioteket med Maven och Gradle:

### Maven

Lägg till följande beroende i din `pom.xml`‑fil:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Inkludera detta i din `build.gradle`‑fil:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### License Acquisition

Aspose.Words kräver en licens för full funktionalitet. Du kan skaffa en gratis provversion, begära en tillfällig licens eller köpa en permanent licens. Besök [purchase page](https://purchase.aspose.com/buy) för mer information.

För att initiera Aspose.Words i ditt Java‑projekt, se till att du har konfigurerat licensen korrekt:

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

## Implementation Guide

Vi delar upp implementeringen i sektioner baserat på de funktioner vi vill implementera.

### How to load html vml with Aspose.Words

**Overview:**  
Att ladda ett HTML‑dokument med VML‑stöd möjliggör flexibel rendering av vektorgrafik såsom diagram och former. Detta är huvudsteget för nyckelordet **load html vml**.

#### Step‑by‑step

1. **Set Up Load Options**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Load the Document**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Verify Image Type**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Load HTML Fixed and Handle Warnings

**Overview:**  
Att ladda fast‑sidig HTML kan generera varningar som måste hanteras för korrekt bearbetning.

#### Step‑by‑step

1. **Define Warning Callback**

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

2. **Configure Load Options**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Load Document and Check Warnings**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### Encrypt HTML Documents

**Overview:**  
Att kryptera ett HTML‑dokument med ett lösenord säkerställer skyddad åtkomst, vilket är viktigt för känslig information – detta adresserar scenariot **encrypt html java**.

#### Step‑by‑step

1. **Prepare Digital Signature Options**

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

2. **Sign and Encrypt Document**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Load Encrypted Document**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### Base URI for HTML Load Options

**Overview:**  
Att specificera en **set html base uri** hjälper till att lösa relativa URI:er, särskilt när du arbetar med bilder eller andra länkade resurser.

#### Step‑by‑step

1. **Configure Load Options with Base URI**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Load Document and Verify Image**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### Import HTML Select as Structured Document Tag

**Overview:**  
För att **configure html control**‑beteende kan du importera `<select>`‑element som Structured Document Tags, vilket ger dig finare kontroll över formulärfält i Word‑dokument.

#### Step‑by‑step

1. **Set Preferred Control Type**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Load Document and Verify Structure**

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

## Common Issues and Solutions

| Issue | Reason | Fix |
|-------|--------|-----|
| VML graphics not appearing | `supportVml` flag left as default (`false`) | Ensure `loadOptions.setSupportVml(true)` before loading. |
| Images missing after load | Relative paths cannot be resolved | Use **set html base uri** (`loadOptions.setBaseUri(...)`) to point to the correct folder. |
| Password‑protected HTML throws exception | Password not supplied | Pass the password to `new HtmlLoadOptions("yourPassword")`. |
| Form controls appear as plain text | Wrong `HtmlControlType` | Set `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` or `FormField` as needed. |
| Unexpected warnings | Unhandled HTML elements | Implement `IWarningCallback` to capture and review warnings. |

## Frequently Asked Questions

**Q: Can I load HTML files that contain both VML and modern SVG graphics?**  
A: Yes. Enable VML with `setSupportVml(true)`; SVG is handled automatically by Aspose.Words.

**Q: How do I encrypt an HTML document without using a digital certificate?**  
A: Use the `HtmlLoadOptions` constructor that accepts a password and save the document with `Document.save(..., SaveFormat.HTML)` after setting the password.

**Q: What happens if the base URI points to a non‑existent folder?**  
A: Aspose.Words will throw a `FileNotFoundException` for missing resources. Verify the path before loading.

**Q: Is it possible to change the default control type for all HTML form elements?**  
A: Yes. Use `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` to apply it globally.

**Q: Are warning callbacks thread‑safe?**  
A: The callback implementation should be thread‑safe if you plan to load documents concurrently. Use synchronized collections or thread‑local storage.

---

**Last Updated:** 2026-02-06  
**Tested With:** Aspose.Words for Java 25.3  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}