---
category: general
date: 2026-05-30
description: Naučte se, jak vytvořit dokument splňující PDF/UA‑2 pomocí Aspose.Words
  pro Javu. Exportujte Word do přístupného PDF s podrobným kódem krok za krokem.
draft: false
keywords:
- create pdf/ua‑2 compliant document
- export word to accessible pdf
language: cs
og_description: Vytvořte dokument kompatibilní s PDF/UA‑2 pomocí Aspose.Words pro
  Java. Tento průvodce přesně ukazuje, jak exportovat Word do přístupného PDF.
og_title: Vytvořte dokument kompatibilní s PDF/UA-2 – Java tutoriál
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to create PDF/UA-2 compliant document using Aspose.Words
    for Java. Export Word to accessible PDF with step‑by‑step code.
  headline: Create PDF/UA-2 Compliant Document – Complete Java Guide
  type: TechArticle
- description: Learn how to create PDF/UA-2 compliant document using Aspose.Words
    for Java. Export Word to accessible PDF with step‑by‑step code.
  name: Create PDF/UA-2 Compliant Document – Complete Java Guide
  steps:
  - name: Prerequisites
    text: '- Java 17 (or any recent JDK) installed on your machine. - Maven or Gradle
      to manage dependencies (we’ll show the Maven snippet). - A Word document (`.docx`)
      you want to make accessible. - An active Aspose.Words for Java license (the
      free trial works for testing).'
  - name: Expected Output
    text: 'When you run the program, the console prints:'
  - name: 1. Missing Fonts
    text: 'If the source Word uses a font that isn’t installed on the server, Aspose.Words
      will substitute it, which can break accessibility. To pre‑empt this:'
  - name: 2. Custom Tags or Alt Text
    text: Images without `alt` text will be marked as decorative, which is fine for
      purely decorative graphics but not for informative ones. Ensure your Word document
      includes meaningful alt text before conversion.
  - name: 3. Large Documents
    text: For multi‑hundred‑page reports, you might hit memory limits. Use `Document.save(OutputStream,
      SaveOptions)` with a streaming approach, or split the document into sections
      before conversion.
  - name: 4. Document Permissions
    text: 'If you need to lock down editing after conversion, add:'
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF/UA-2
- Accessibility
title: Vytvořte dokument splňující PDF/UA-2 – kompletní Java průvodce
url: /cs/java/document-conversion-and-export/create-pdf-ua-2-compliant-document-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření dokumentu splňujícího PDF/UA-2 – Kompletní průvodce pro Javu

Už jste někdy potřebovali **vytvořit dokument splňující PDF/UA-2** z Word souboru, ale nebyli jste si jisti, které volání API udělá těžkou práci? Nejste v tom sami. Standardy přístupnosti jako PDF/UA‑2 mohou připomínat bludiště, zejména když v Java projektu manipulujete s konverzí dokumentů.

Aspose.Words for Java celý proces téměř eliminuje. V tomto tutoriálu projdeme vše, co potřebujete k **exportu Wordu do přístupného PDF**, od načtení zdrojového `.docx` až po doladění možností uložení pro plnou shodu s PDF/UA‑2. Na konci budete mít připravený úryvek kódu, který můžete vložit do libovolného Maven nebo Gradle projektu.

## Co se naučíte

- Proč je PDF/UA‑2 důležité pro přístupnost a právní soulad.  
- Které třídy Aspose.Words jsou součástí konverzního řetězce.  
- Jak nakonfigurovat `PdfSaveOptions` pro výstup PDF/UA‑2.  
- Běžné úskalí (chybějící písma, vlastní značky) a jak se jim vyhnout.  
- Kompletní, spustitelný Java program, který můžete okamžitě přizpůsobit.

### Předpoklady

- Java 17 (nebo jakýkoli aktuální JDK) nainstalovaný na vašem počítači.  
- Maven nebo Gradle pro správu závislostí (ukážeme Maven ukázku).  
- Word dokument (`.docx`), který chcete zpřístupnit.  
- Aktivní licence Aspose.Words pro Java (zdarma zkušební verze funguje pro testování).

> **Tip:** Pokud běžíte na CI serveru, nastavte licenci programově, abyste se vyhnuli varováním za běhu.

## Krok 1: Přidání závislosti Aspose.Words

Nejprve řekněte svému nástroji pro sestavení, aby stáhl knihovnu Aspose.Words. Pro Maven vložte následující do souboru `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Pokud dáváte přednost Gradlu, ekvivalent je:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Why this matters:** The library bundles the PDF renderer and the accessibility engine, so you don’t need any extra jars.

## Krok 2: Načtení zdrojového Word dokumentu

Nyní, když je knihovna na classpath, můžete načíst libovolný `.docx`. Třída `Document` je vstupním bodem; parsuje Word soubor do objektového modelu v paměti.

```java
import com.aspose.words.*;

public class PdfUaDemo {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your Word file
        String sourcePath = "C:/Docs/ReportWithHR.docx";
        Document doc = new Document(sourcePath);
        // Continue with PDF/UA‑2 settings...
    }
}
```

> **What’s happening:** Aspose.Words reads the Word Open XML package, resolves styles, images, and even custom XML parts. No need to manually handle fonts or layout.

## Krok 3: Konfigurace PDF Save Options pro PDF/UA‑2

Magie spočívá v `PdfSaveOptions`. Nastavením úrovně shody na `PdfCompliance.PDF_UA_2` exportér vloží požadované značky, strukturální elementy a metadata, na které se spoléhají asistivní technologie.

```java
// Step 3: Set PDF save options to enable PDF/UA‑2 compliance
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCompliance(PdfCompliance.PDF_UA_2);

// Optional: embed all fonts to avoid substitution issues
saveOptions.setEmbedFullFonts(true);

// Optional: add a custom PDF/UA tag for the document title
saveOptions.setDocumentTitle("Annual HR Report – Accessible Version");
```

> **Why you should embed fonts:** Missing fonts can break the logical reading order, causing screen readers to stumble. `setEmbedFullFonts(true)` guarantees a faithful visual and structural copy.

## Krok 4: Uložení dokumentu jako přístupného PDF

Nakonec zavolejte `doc.save()` s cestou k výstupu a nakonfigurovanými možnostmi. Knihovna vytvoří PDF, které projde validačními nástroji PDF/UA‑2 (např. PDFTron nebo veraPDF).

```java
// Step 4: Save the document as a PDF/UA‑2 compliant file
String outputPath = "C:/Docs/Report_UA.pdf";
doc.save(outputPath, saveOptions);

System.out.println("Successfully created PDF/UA-2 compliant document at: " + outputPath);
```

To je vše—čtyři stručné kroky k **exportu Wordu do přístupného PDF**. Spusťte program, otevřete vzniklé PDF v Adobe Acrobat a zkontrolujte *File → Properties → Description → PDF/A and PDF/UA*; mělo by se zobrazit „PDF/UA‑2“ v sekci shody.

## Kompletní funkční příklad

Níže je kompletní, samostatná Java třída. Zkopírujte, vložte a spusťte; vytvoří PDF/UA‑2 dokument ze souboru `ReportWithHR.docx` umístěného v `C:/Docs`.

```java
import com.aspose.words.*;

public class PdfUaDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source Word document
        String sourcePath = "C:/Docs/ReportWithHR.docx";
        Document doc = new Document(sourcePath);

        // 2️⃣ Configure PDF/UA‑2 compliance
        PdfSaveOptions saveOptions = new PdfSaveOptions();
        saveOptions.setCompliance(PdfCompliance.PDF_UA_2);
        saveOptions.setEmbedFullFonts(true);
        saveOptions.setDocumentTitle("Annual HR Report – Accessible Version");

        // 3️⃣ Save as an accessible PDF
        String outputPath = "C:/Docs/Report_UA.pdf";
        doc.save(outputPath, saveOptions);

        System.out.println("✅ PDF/UA‑2 file created: " + outputPath);
    }
}
```

### Očekávaný výstup

Po spuštění programu se v konzoli vypíše:

```
✅ PDF/UA-2 file created: C:/Docs/Report_UA.pdf
```

Otevřete `Report_UA.pdf` v libovolném PDF prohlížeči a všimnete si:

- Všechen text je výběrný a prohledávatelný.  
- Hierarchie dokumentu (nadpisy, tabulky, seznamy) je zakódována jako strukturální značky.  
- Soubor prochází validací PDF/UA‑2 (můžete ověřit pomocí bezplatných nástrojů jako veraPDF).

## Řešení běžných okrajových případů

### 1. Chybějící písma

Pokud zdrojový Word používá písmo, které není nainstalováno na serveru, Aspose.Words jej nahradí, což může narušit přístupnost. Pro předcházení:

```java
saveOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL);
```

### 2. Vlastní značky nebo alternativní text

Obrázky bez `alt` textu budou označeny jako dekorativní, což je v pořádku pro čistě dekorativní grafiku, ale ne pro informativní. Ujistěte se, že váš Word dokument obsahuje smysluplný alternativní text před konverzí.

### 3. Velké dokumenty

U vícesetstránkových zpráv můžete narazit na limity paměti. Použijte `Document.save(OutputStream, SaveOptions)` s přístupem streamování, nebo rozdělte dokument na sekce před konverzí.

### 4. Oprávnění dokumentu

Pokud potřebujete po konverzi omezit úpravy, přidejte:

```java
saveOptions.setEncryptDocument(true);
saveOptions.setOwnerPassword("ownerSecret");
saveOptions.setUserPassword("userSecret");
```

## Ověření souladu s PDF/UA‑2

Po vygenerování PDF je rozumné spustit validátor:

1. Stáhněte **veraPDF** (open‑source validátor).  
2. Spusťte: `verapdf --format text Report_UA.pdf`.  
3. Hledejte „PDF/UA‑2“ v sekci souladu a ujistěte se, že nejsou žádné chyby.

Pokud narazíte na chyby, validátor ukáže chybějící značky nebo neembedovaná písma — stačí upravit `PdfSaveOptions` podle potřeby.

## Další kroky a související témata

- **Přidání PDF/UA‑2 značek ručně**: Prozkoumejte `PdfStructureElement` pro detailní kontrolu.  
- **Dávková konverze**: Procházejte adresář s `.docx` soubory a vytvořte zip přístupných PDF.  
- **Kombinace s OCR**: Pokud máte ve Word dokumentu naskenované obrázky, použijte Aspose.OCR k přidání prohledávatelného textu před konverzí.  
- **Integrace se Spring Boot**: Zveřejněte endpoint, který přijímá nahrání Word souboru a vrací PDF/UA‑2 stream.

Všechny tyto postupy staví na základním vzoru, který jsme právě probrali: načíst → nakonfigurovat → uložit.

*Připravení učinit každý PDF, který odesíláte, přístupným? Vezměte si kód, spusťte ho a nechte své uživatele se zdravotním postižením užívat stejný obsah jako vy. Pokud narazíte na problém, zanechte komentář — šťastné kódování!*

## Co byste se měli naučit dál?

- [Vytvořit přístupný PDF z Wordu – Převod na PDF/UA](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-word-convert-to-pdf-ua/)
- [Jak uložit dokument jako pdf s Aspose.Words pro Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Jak převést Word do PDF pomocí Aspose.Words pro Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}