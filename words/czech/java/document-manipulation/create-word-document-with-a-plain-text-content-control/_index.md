---
category: general
date: 2026-10-04
description: Vytvořte dokument Word pomocí Javy, který obsahuje prostý textový ovládací
  prvek a zástupný text. Naučte se, jak přidat zástupný text do značky a jak vložit
  sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: cs
lastmod: 2026-10-04
og_description: Vytvořte dokument Word s ovládacím prvkem prostého textu a zástupným
  textem. Tento tutoriál ukazuje, jak přidat zástupný text k značce a jak vložit sdt
  pomocí Aspose.Words pro Javu.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Vytvořte dokument Word s ovládacím prvkem – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: Vytvořit dokument Word s ovládacím prvkem prostého textu
url: /cs/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte Word dokument s ovládacím prvkem prostého textu

Pokud potřebujete **vytvořit Word dokument**, který obsahuje uživatelem editovatelnou oblast, nejspolehlivějším přístupem je ovládací prvek prostého textu. Tento tutoriál ukazuje přesně, jak vložit Structured Document Tag (SDT), nastavit placeholder a uložit výsledek jako **docx s placeholderem**. Uvidíte kompletní, spustitelný Java příklad, který funguje s Aspose.Words for Java 23.8.

Průvodce pokrývá všechny předpoklady, vysvětluje, proč je každé volání API důležité, a poskytuje tipy pro řešení okrajových případů, jako jsou vícejazyčné placeholdery nebo vnořené značky. Na konci budete schopni vygenerovat Word soubor, který uživatele vyzve k zadání „Enter text…“ přímo v dokumentu.

## Požadavky

* Java 17 (nebo novější) nainstalovaný a nastavený v PATH.  
* Maven 3.8+ pro správu závislostí.  
* Licence Aspose.Words for Java (vyzkoušení funguje pro testování).  
* Vývojové IDE (IntelliJ IDEA, Eclipse nebo VS Code).

Přidejte Aspose.Words do svého `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Vytvořte Word dokument s ovládacím prvkem prostého textu

Základní pracovní postup se skládá ze čtyř logických kroků. Každý krok je zabalen do jasně pojmenované metody, takže můžete logiku znovu použít ve větších projektech.

### Krok 1: Inicializace dokumentu a builderu

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**Proč je to důležité:** `Document` představuje Word soubor v paměti. `DocumentBuilder` je fluent API, které vám umožňuje vkládat odstavce, tabulky a SDT. Začátek s prázdným dokumentem zajišťuje, že se placeholder objeví na samém začátku, což je užitečné pro šablony.

### Krok 2: Vložení Structured Document Tag (SDT) s prostým textem

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Proč je to důležité:** `StructuredDocumentTagType.PLAIN_TEXT` vytváří ovládací prvek, který přijímá pouze prosté znaky, čímž zabraňuje nechtěnému formátování. Volání `setPlaceholderName` vyplní šedý nápovědný text, který uživatelé vidí před psaním — toto je operace **add placeholder to tag**, která způsobí, že se dokument chová jako formulář.

### Krok 3: Přidání běžného obsahu po SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Proč je to důležité:** Přidání obsahu po ovládacím prvku ověřuje, že SDT neabsorbuje celý tok dokumentu. Také ukazuje, jak kombinovat strukturované značky s běžnými odstavci, což je častý požadavek při tvorbě šablon.

### Krok 4: Uložení výsledného souboru

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Proč je to důležité:** Metoda `save` zapíše model v paměti do fyzického souboru **docx s placeholderem**. Vygenerovaný soubor lze otevřít v Microsoft Word, LibreOffice nebo v jakékoli knihovně, která podporuje formát OpenXML.

## Kompletní zdrojový kód

Sestavením všech částí získáte samostatný program, který můžete zkompilovat a spustit:

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Očekávaný výstup

Spuštěním programu se vytvoří `SdtDemo.docx`. Otevřením souboru ve Wordu se zobrazí:

* Šedý placeholder „Enter text…“ uvnitř ovládacího prvku prostého textu označeného **MyTag**.  
* Řádek **After SDT** ihned pod ovládacím prvkem.

Placeholder zmizí, jakmile uživatel začne psát, a zachová původní formátování.

## Běžné varianty a okrajové případy

| Scénář | Doporučená změna |
|----------|--------------------|
| **Multilingual placeholder** | Použijte Unicode znaky v `setPlaceholderName`, např. `sdt.setPlaceholderName("Введите текст…");`. |
| **Nested content controls** | Vložte druhý SDT uvnitř prvního voláním `builder.moveTo(sdt.getParagraph());` před druhým `insertStructuredDocumentTag`. |
| **Read‑only control** | Zavolejte `sdt.setLockContentControl(true);` aby uživatelé nemohli značku smazat. |
| **Rich‑text instead of plain text** | Nahraďte `StructuredDocumentTagType.PLAIN_TEXT` za `StructuredDocumentTagType.RICH_TEXT`. |
| **Saving to a stream** | Použijte `doc.save(OutputStream, SaveFormat.DOCX);` když potřebujete soubor poslat přes HTTP. |

## Profesionální tipy

* **Reuse tag IDs** – Pokud generujete mnoho dokumentů ze stejné šablony, udržujte název značky (`"MyTag"`) konzistentní, aby následné zpracování (např. mail‑merge) mohlo spolehlivě najít.  
* **Performance** – Pro velké šablony vytvořte `DocumentBuilder` jednou a znovu jej použijte; vkládání mnoha SDT v cyklu je rychlejší než opakované vytváření builderu v každé iteraci.  
* **Testing** – Po vygenerování DOCX programově ověřte, že placeholder existuje pomocí `doc.getRange().getStructuredDocumentTags().getCount()`.

## Závěr

Nyní víte, jak **vytvořit Word dokument**, který obsahuje **ovládací prvek prostého textu** s vlastním placeholderem, čímž efektivně vytvoříte **docx s placeholderem** připravený pro vstup uživatele. Příklad ukazuje celý cyklus od inicializace dokumentu, **jak vložit sdt**, **add placeholder to tag**, přidání běžného obsahu a nakonec uložení souboru.

### Další kroky

* Prozkoumejte **how to insert sdt** uvnitř tabulek pro rozvržení podobné formulářům.  
* Kombinujte tuto techniku s **docx s placeholderem** slučováním pro tvorbu automatizovaných generátorů reportů.  
* Experimentujte s dalšími typy ovládacích prvků (`RICH_TEXT`, `CHECKBOX`) pro vytvoření bohatějších Word formulářů.

Neváhejte upravit kód pro svůj vlastní šablonový engine a sdílet své výsledky v komentářích!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Vytvořit Word dokument v Javě – Přidat obdélníkový tvar se stínovým efektem](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Jak vytvořit PDF dokumenty s Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}