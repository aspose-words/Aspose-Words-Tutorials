---
category: general
date: 2026-10-20
description: Nastavte kódování LoadOptions v Javě tak, aby správně načítal dokumenty,
  a změňte kódování dokumentu na UTF‑8 pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: cs
lastmod: 2026-10-20
og_description: Nastavte kódování LoadOptions v Javě, aby bylo zajištěno správné zacházení
  s znaky, a zjistěte, jak změnit kódování dokumentu na UTF‑8 pomocí Aspose.Words.
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: Konfigurace kódování LoadOptions v Javě – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: Jak nakonfigurovat kódování LoadOptions v Javě
url: /cs/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nakonfigurovat kódování LoadOptions v Javě

Pokud potřebujete **konfigurovat kódování LoadOptions** v Javě, tento průvodce vám ukáže, jak nastavit správnou znakovou sadu a poté **změnit kódování dokumentu na UTF-8** pomocí Aspose.Words. Správné kódování zabraňuje poškozenému textu při načítání souborů, které používají starší kódové stránky jako Big5, Shift_JIS nebo Windows‑1252.

Naučíte se, jak:

* vytvořit instanci `LoadOptions` s konkrétním kódováním,
* načíst zdrojový dokument, který používá toto kódování,
* uložit dokument v jiném kódování (UTF‑8) bez ztráty dat,
* ověřit, že konverze byla úspěšná.

Průvodce předpokládá, že máte základní vývojové prostředí pro Javu a platnou licenci Aspose.Words pro Java. Žádné externí nástroje nejsou vyžadovány.

## Požadavky

| Požadavek | Proč je důležité |
|-------------|----------------|
| Java 17 nebo novější | Poskytuje moderní jazykové funkce a dlouhodobou podporu. |
| Aspose.Words for Java (v23.9 nebo novější) | Třída `LoadOptions` se nachází v této knihovně. |
| Zdrojový dokument kódovaný starou kódovou stránkou (např. Big5) | Ukazuje potřebu vlastního kódování. |
| IDE nebo nástroj pro sestavení (Maven/Gradle) | Umožňuje jednoduchou kompilaci a spuštění příkladu. |

Přidejte závislost Aspose.Words do vašeho `pom.xml`, pokud používáte Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Nakonfigurujte kódování LoadOptions

Prvním krokem je říci Aspose.Words, jakou znakovou sadu má očekávat při čtení souboru. To se provádí nastavením objektu `LoadOptions`.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**Proč je to důležité:** Když je dokument uložen se starým kódováním, výchozí načítač předpokládá UTF‑8. Explicitním nastavením kódování se vyhnete mojibake (poškozeným znakům) a zachováte původní text.

### Tip
Pokud si nejste jisti, jaké kódování soubor používá, můžete zkontrolovat jeho značku pořadí bajtů (BOM) nebo se zeptat poskytovatele dokumentu. Běžná stará kódování zahrnují `Big5`, `Shift_JIS` a `Windows-1252`.

## Načtěte dokument s nakonfigurovanými možnostmi

Nyní, když je `LoadOptions` připraven, načtěte zdrojový soubor. Konstruktor, který přijímá cestu k souboru a instanci `LoadOptions`, zajišťuje, že se použije vlastní kódování.

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**Proč je to důležité:** Objekt `Document` nyní obsahuje text přesně tak, jak se objevuje v původním souboru, protože načítač respektoval kódovou stránku Big5, kterou jste zadali.

## Změňte kódování dokumentu na UTF-8

Aspose.Words ukládá text interně jako Unicode, takže při ukládání dokumentu se určuje externí kódování. Pro vytvoření souboru UTF‑8 stačí uložit bez specifikace dalšího kódování – UTF‑8 je výchozí pro moderní formáty Office Open XML. Přesto jej můžete explicitně vynutit pro přehlednost.

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

Pokud potřebujete vytvořit čistý textový výstup (např. `.txt`) s UTF‑8, předávejte objekt `SaveOptions`:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**Proč je to důležité:** Uložení jako UTF‑8 zaručuje, že jakýkoli následný systém – webové služby, databáze nebo moderní editory – může soubor přečíst bez dalších konverzních kroků.

## Ověřte konverzi

Rychlý způsob, jak potvrdit, že změna kódování byla úspěšná, je přečíst uložený soubor zpět pomocí UTF‑8 čtečky a vytisknout několik znaků.

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

Pokud výstup zobrazí čitelné znaky (žádné symboly �), konverze fungovala podle očekávání.

## Kompletní spustitelný příklad

Níže je samostatný program, který spojuje všechny kroky. Nahraďte cesty k souborům vlastními umístěními.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**Očekávaný výstup**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

Pokud se znaky zobrazí správně, úspěšně jste **nakonfigurovali kódování LoadOptions** a **změnili kódování dokumentu na UTF-8**.

## Časté úskalí a jak se jim vyhnout

| Příznak | Příčina | Oprava |
|---------|---------|--------|
| Poškozené znaky po načtení | `LoadOptions` není nastaven nebo je špatný název znakové sady | Ujistěte se, že `loadOptions.setEncoding(Charset.forName("Big5"))` odpovídá kódové stránce zdrojového souboru. |
| `UnsupportedEncodingException` | Chybný název znakové sady | Použijte přesný název uvedený v `Charset.availableCharsets()`. |
| Výstupní soubor stále ukazuje mojibake | Uloženo ve starém formátu (např. `.rtf`) bez možností UTF‑8 | Použijte `TxtSaveOptions` s `setEncoding("UTF-8")` nebo uložte jako `.docx`. |
| Zpomalení výkonu u velkých souborů | Znovu vytváření `LoadOptions` pro každý dokument | Znovu použijte jedinou instanci `LoadOptions` při zpracování mnoha souborů se stejným zdrojovým kódováním. |

## Závěr

Nyní víte, jak **konfigurovat kódování LoadOptions** v Javě pro čtení dokumentů se starým kódováním a jak **změnit kódování dokumentu na UTF-8** pro bezpečnou následnou spotřebu. Tento přístup funguje pro jakoukoli kódovou stránku podporovanou třídou `Charset` v Javě, což z něj činí flexibilní řešení pro vícejazyčné aplikace.

Dále můžete zkoumat:

* **Dávková konverze** – procházet složku dokumentů a použít stejnou logiku kódování.
* **Detekce kódování** – použít knihovny jako juniversalchardet pro automatickou detekci zdrojové znakové sady před konfigurací `LoadOptions`.
* **Zachování formátování** – experimentovat s ukládáním do PDF nebo HTML při zachování souladu s UTF‑8.

Klidně přizpůsobte kód architektuře vašeho projektu a nechte robustní Aspose.Words API provést těžkou práci s manipulací dokumentů.

![Code snippet showing configuration of LoadOptions encoding and document save](/images/encoding-demo.png){: .align-center alt="Ukázka kódu zobrazující konfiguraci kódování LoadOptions a uložení dokumentu"}

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s krok za krokem vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak nastavit LoadOptions v Aspose.Words pro Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Jak převést RTF text s kódováním UTF-8 v Javě pomocí Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Obnova poškozeného DOCX Word dokumentu pomocí Aspose.Words LoadOptions – průvodce pro Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}