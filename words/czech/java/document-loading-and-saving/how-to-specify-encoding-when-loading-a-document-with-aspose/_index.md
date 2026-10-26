---
category: general
date: 2026-10-26
description: Naučte se, jak v Javě pomocí LoadOptions specifikovat kódování. Tento
  průvodce se zabývá znakovým kódováním, metodou setEncoding a možnostmi načítání
  dokumentu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: cs
lastmod: 2026-10-26
og_description: Jak specifikovat kódování v Javě pomocí Aspose.Words. Sledujte tento
  kompletní návod, jak načíst dokumenty se správnou znakovou sadou.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Jak specifikovat kódování v Javě s Aspose.Words – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Jak specifikovat kódování při načítání dokumentu pomocí Aspose.Words pro Javu
url: /cs/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak specifikovat kódování při načítání dokumentu pomocí Aspose.Words pro Java

Pokud potřebujete **jak specifikovat kódování** pro zdrojový soubor v Javě, tento tutoriál vám ukáže přesné kroky. Ať už dokument používá Big5, UTF‑8 nebo jinou znakovou sadu, můžete řídit proces čtení pomocí `LoadOptions`. Na konci průvodce pochopíte, proč je kódování znaků důležité, jak použít metodu `setEncoding` a jak ověřit, že se dokument načte správně.

Načtení dokumentu se správným kódováním znaků zabraňuje poškozenému textu a zajišťuje, že vícejazyčný obsah se zobrazí tak, jak má. Tento tutoriál pokrývá:

* Úlohu **kódování znaků v Javě** při čtení souborů.
* Jak nastavit **kódování LoadOptions** pro Aspose.Words.
* Praktický kód, který můžete zkopírovat do svého projektu.
* Běžné úskalí, jako jsou nesprávná kódování, a jak je řešit.

## Požadavky

Před začátkem se ujistěte, že máte:

* Java Development Kit (JDK) 8 nebo vyšší.
* Maven nebo Gradle pro správu závislostí.
* Aspose.Words pro Java 23.10 nebo novější (verze použitá v tomto průvodci).
* Ukázkový textový dokument (`input.doc`) uložený s požadovaným kódováním (např. Big5).

Nemusíte instalovat žádné další knihovny; příklad používá pouze základní API Aspose.Words.

## Krok 1: Přidejte Aspose.Words do svého projektu

Pokud používáte Maven, přidejte následující závislost do souboru `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Pro Gradle umístěte tento řádek do souboru `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Zahrnutím knihovny získáte třídy `LoadOptions`, `Document` a `Encoding`.

## Krok 2: Vytvořte instanci `LoadOptions`

`LoadOptions` vám umožňuje přizpůsobit, jak Aspose.Words otevírá soubor. Vytvoření objektu je první částí **jak specifikovat kódování**.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

Objekt `LoadOptions` začíná s výchozími nastaveními. V dalším kroku upravíte jeho vlastnosti.

## Krok 3: Nastavte požadované kódování znaků

Metoda `setEncoding` určuje **kódování znaků v Javě**, které má načítač použít. V tomto příkladu volíme kódovou stránku Big5, která je běžná pro tradiční čínské textové soubory.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Proč je to důležité*: Pokud jsou bajty souboru interpretovány se špatnou kódovou stránkou, znaky se zobrazí jako otazníky nebo nesmysly. Výslovným voláním `setEncoding` řeknete Aspose.Words, aby dekódoval bajtový proud pomocí mapovací tabulky Big5.

Můžete nahradit `"Big5"` libovolným názvem znakové sady rozpoznávaným Javou, například `"UTF-8"`, `"ISO-8859-1"` nebo `"Windows-1252"`. Metoda vyhodí `UnsupportedEncodingException`, pokud je název neplatný, takže v produkčním kódu můžete tuto výjimku zachytit.

## Krok 4: Načtěte dokument s nakonfigurovanými možnostmi

Nyní, když je **kódování LoadOptions** nastaveno, předáte možnosti konstruktoru `Document`. Tento krok dokončuje hlavní workflow **jak specifikovat kódování**.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

Nahraďte `YOUR_DIRECTORY` absolutní nebo relativní cestou k vašemu souboru. Instance `Document` nyní obsahuje plně analyzovaný obsah, respektující zadané kódování.

## Krok 5: Ověřte, že se text načte správně

Rychlé ověření vám pomůže zajistit, že bylo kódování použito podle očekávání. Můžete extrahovat text dokumentu a vytisknout jej do konzole:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

Pokud konzole zobrazí čitelný čínský text (nebo jazyk, který očekáváte), kódování bylo úspěšné. Pokud stále vidíte poškozený výstup, dvakrát zkontrolujte kódování původního souboru a ověřte, že název znakové sady přesně odpovídá.

## Řešení běžných okrajových případů

### 5.1 Načítání z `InputStream`

Někdy získáte dokument jako proud (např. z webové služby). Stále můžete řídit kódování předáním proudu spolu s `LoadOptions`:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

Stejné **možnosti načítání dokumentu** se použijí a volání `setEncoding` zůstane beze změny.

### 5.2 Náhradní řešení, když je kódování neznámé

Pokud nemůžete určit znakovou sadu zdrojového souboru, můžete před nastavením kódování zkusit detekční knihovnu (např. ICU4J). Jakmile máte odhad, zavolejte `setEncoding` s touto hodnotou. Tento přístup snižuje riziko špatně dekódovaného textu.

### 5.3 Práce s nepodporovanými kódováními

Java podporuje širokou škálu kódových stránek, ale některá starší kódování mohou chybět. V takovém případě zvažte externí konverzi souboru na UTF‑8 (např. pomocí `iconv`) před načtením pomocí Aspose.Words. Po konverzi můžete volání `setEncoding` vynechat, protože UTF‑8 je výchozí pro většinu moderních API.

## Profesionální tip: Znovupoužití `LoadOptions` pro dávkové zpracování

Pokud potřebujete načíst mnoho dokumentů, které sdílejí stejnou znakovou sadu, vytvořte jedinou instanci `LoadOptions` a znovu ji použijte:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

Znovupoužití objektu snižuje režii při vytváření objektů a zajišťuje konzistentní kódování napříč dávkou.

## Kompletní spustitelný příklad

Níže je kompletní program, který zahrnuje všechny kroky, potřebné importy a ošetřuje možné výjimky.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**Očekávaný výstup** (předpokládáme, že zdrojový soubor obsahuje čínský text kódovaný v Big5):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

Pokud výstup zobrazuje nečitelné symboly, zkontrolujte název znakové sady nebo ověřte původní kódování souboru.

## Často kladené otázky

**Funguje to i s jinými formáty dokumentů (DOCX, RTF, HTML)?**  
Ano. Stejný objekt `LoadOptions` platí pro jakýkoli formát podporovaný Aspose.Words. Jedinou podmínkou je, že podkladový soubor skutečně používá zadanou znakovou sadu.

**Co když potřebuji změnit kódování po načtení dokumentu?**  
Kódování ovlivňuje pouze fázi čtení. Jakmile existuje objekt `Document`, jeho vnitřní Unicode reprezentace je nezávislá na původní znakové sadě. Pro změnu výstupního kódování upravte `SaveOptions` při zápisu souboru.

**Mohu tento přístup použít s jinými knihovnami (např. Apache POI)?**  
Apache POI provádí vlastní detekci znakové sady pro starší binární formáty, ale koncept předání znakové sady načítači je podobný. Pro Aspose.Words je `LoadOptions` oficiální způsob, jak řídit **jak specifikovat kódování**.

## Závěr

Nyní víte **jak specifikovat kódování** při načítání dokumentu pomocí Aspose.Words pro Java. Vytvořením objektu `LoadOptions`, zavoláním metody `setEncoding` a předáním možností konstruktoru `Document` zajistíte, že bajty souboru jsou interpretovány správně. Tento postup eliminuje poškozený text, podporuje vícejazyčný obsah a hladce se integruje s dávkovým zpracováním nebo workflow založeným na streamech.

Prozkoumejte související témata, jako jsou **možnosti načítání dokumentu**, **ukládání s konkrétním kódováním** a **pracování Unicode v Javě**, abyste prohloubili své znalosti zpracování textu. Experimentujte s různými názvy znakových sad, kombinujte tento přístup s konverzí do PDF nebo jej integrujte do webové služby, která přijímá nahrávky v různých kódováních.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak převést RTF text s kódováním UTF-8 v Javě pomocí Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Jak nastavit možnosti v Aspose.Words pro Java – kompletní průvodce](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Obnovení poškozeného DOCX dokumentu Word pomocí Aspose.Words LoadOptions – průvodce pro Javu](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}