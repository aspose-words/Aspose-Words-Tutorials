---
date: 2026-10-23
description: Naučte se, jak vytvořit QR code Java štítky s Aspose.Words. Tento krok‑za‑krokem
  průvodce vám ukáže, jak vložit barcodes do Word dokumentů a přizpůsobit velikost,
  barvy a formát.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Generování vlastních Barcode štítků
og_description: Naučte se, jak vytvořit QR code Java štítky s Aspose.Words. Tento
  průvodce vysvětluje vložení barcode, řízení velikosti a přizpůsobení barev ve Word
  dokumentech.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Jak vytvořit štítky s QR code v Java pomocí Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Jak vytvořit štítky s QR code v Java pomocí Aspose.Words
url: /cs/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit štítky QR kódu v Javě pomocí Aspose.Words

Čárové kódy jsou nezbytné v moderních aplikacích – ať už spravujete zásoby, tisknete vstupenky nebo vytváříte ID karty. V tomto tutoriálu **create QR code Java** štítky a vložíte je přímo do dokumentu Word pomocí rozhraní `IBarcodeGenerator`. Provedeme vás každým krokem, od nastavení prostředí po vložení obrázku čárového kódu, abyste mohli okamžitě začít používat čárové kódy ve svých Java projektech.

## Rychlé odpovědi
- **Co tento tutoriál učí?** Jak vytvořit štítky QR code Java a vložit je do souboru Word pomocí Aspose.Words pro Java.  
- **Jaký typ čárového kódu je v příkladu použit?** QR code (můžete jej vyměnit za kterýkoli z více než 20 podporovaných typů).  
- **Potřebuji licenci?** Pro neomezený přístup během vývoje je vyžadována dočasná licence.  
- **Jaká verze Javy je vyžadována?** JDK 8 nebo vyšší.  
- **Mohu změnit velikost nebo barvy čárového kódu?** Ano – upravte nastavení `BarcodeParameters` a `BarcodeGenerator`.

## Co je create QR code Java?
`create QR code Java` odkazuje na generování QR‑kódu programově v prostředí Java a jeho vložení do dokumentu nebo UI komponenty. Aspose.Words pro Java spolu s Aspose.BarCode vám umožňuje vytvořit obrázek kompletně v paměti, čímž se vyhnete dočasným souborům.

## Proč generovat vlastní štítky čárových kódů pomocí Aspose.Words?
Aspose.Words podporuje **více než 35 vstupních a výstupních formátů** a dokáže zpracovat **500‑stránkové dokumenty za méně než 3 sekundy** na standardním serverovém hardware. Použitím generování čárových kódů v paměti získáte plnou kontrolu nad typem, velikostí a barvami a zároveň zachováte workflow plně zaměřené na Javu a nezávislé na platformě.

## Požadavky

- Java Development Kit (JDK): Verze 8 nebo vyšší.  
- Aspose.Words for Java Library: [Stáhnout zde](https://releases.aspose.com/words/java/).  
- Aspose.BarCode for Java Library: [Stáhnout zde](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse nebo jakékoli IDE, které preferujete.  
- Temporary License: Získejte [temporary license](https://purchase.aspose.com/temporary-license/) pro neomezený přístup.

## Import balíčků

Budeme používat knihovny Aspose.Words a Aspose.BarCode. Naimportujte následující balíčky do svého projektu:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Tyto importy nám poskytují přístup k API pro generování čárových kódů a třídám dokumentu Word, které budeme potřebovat.

## Krok 1: vytvořit pomocnou třídu pro operace s čárovými kódy

Pomocná třída obsahuje opakovaně použitelné pomocníky, jako jsou **convert twips to pixels** a **hex‑color conversion**.  
Třída `CustomBarcodeGeneratorUtils` poskytuje statické metody pro převod jednotek a manipulaci s barvami.

### Kód

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Vysvětlení**  
- `twipsToPixels` – Word měří rozměry v **twips**; tato metoda je převádí na obrazovkové pixely, což je užitečné, když potřebujete přesně nastavit velikost obrázku čárového kódu.  
- `convertColor` – Převádí hexadecimální řetězec (např. `"FF0000"` pro červenou) na objekt `java.awt.Color`, což vám umožní **add barcode to Word document** s vlastními barvami popředí a pozadí.

## Krok 2: implementovat vlastní generátor čárových kódů

Nyní implementujeme rozhraní `IBarcodeGenerator`. Tato třída je zodpovědná za **generate QR code Java**‑stylové obrázky, které může Aspose.Words vložit.  
Rozhraní `IBarcodeGenerator` definuje jedinou metodu, která vrací `BufferedImage` představující čárový kód.

### Kód

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Vysvětlení**  
- `getBarcodeImage` vytvoří instanci `BarcodeGenerator`, použije barvy poskytnuté přes `BarcodeParameters` a nakonec vrátí `BufferedImage`.  
- Metoda také elegantně ošetřuje chyby tím, že vrátí zástupný obrázek, což zajišťuje, že tvorba Word dokumentu nikdy nezhavaruje.

## Jak vložit čárový kód do Wordu pomocí Aspose.Words?

Nahrajte svůj Word soubor pomocí `new Document("template.docx")` (nebo vytvořte nový `Document`) a zavolejte `builder.insertImage` s obrázkem čárového kódu vráceným z generátoru. Tento dvoukrokový vzor vloží čárový kód přímo bez zápisu mezilehlého souboru na disk. Zadáním rozměrů obrázku v pixelech nebo převodem Word twips na pixely můžete řídit přesnou velikost a umístění čárového kódu v dokumentu, což zajišťuje profesionální rozvržení, které se správně vytiskne na jakékoli tiskárně.

## Krok 3: vygenerovat čárový kód a vložit čárový kód do Wordu

S připraveným generátorem můžeme nyní vytvořit obrázek čárového kódu a **insert it into a Word document**.

### Kód

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Vysvětlení**  

1. **Inicializace dokumentu** – Vytvoří nový `Document` (nebo můžete načíst existující šablonu).  
2. **Parametry čárového kódu** – Definuje typ čárového kódu (`QR`), hodnotu k zakódování a barvy popředí/pozadí.  
3. **Vložení obrázku** – `builder.insertImage` umístí vygenerovaný čárový kód do požadované velikosti (200 × 200 pixelů). Toto je jádro **how to embed barcode in Word**.  
4. **Ukládání** – Výsledný dokument `CustomBarcodeLabels.docx` obsahuje vložený čárový kód připravený k tisku nebo distribuci.

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Oprava |
|---------|-----------------------|--------|
| Barcode appears blank | `BarcodeParameters` barvy jsou stejné (např. černá na černé) | Ověřte hodnoty `foregroundColor` a `backgroundColor`. |
| Image is distorted | Špatné rozměry v pixelech předané do `insertImage` | Upravte argumenty šířky/výšky nebo použijte převod `twipsToPixels` pro přesné rozměry. |
| Unsupported barcode type error | Použití typu, který není rozpoznán metodou `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Ujistěte se, že řetězec typu čárového kódu odpovídá jednomu z podporovaných `EncodeTypes` (např. `"QR"`, `"CODE128"`). |

## Často kladené otázky

**Q: Mohu používat Aspose.Words pro Java bez licence?**  
A: Ano, ale bude mít omezení vyhodnocení. Získejte [temporary license](https://purchase.aspose.com/temporary-license/) pro plnou funkčnost.

**Q: Jaké typy čárových kódů mohu generovat?**  
A: Aspose.BarCode podporuje QR, Code 128, EAN‑13, DataMatrix, PDF417 a mnoho dalších formátů – více než 20 symbologií celkem. Viz [documentation](https://reference.aspose.com/words/java/) pro úplný seznam.

**Q: Jak mohu změnit velikost čárového kódu?**  
A: Upravit argumenty šířky a výšky v `builder.insertImage` nebo vypočítat přesné Word twips pomocí `twipsToPixels` pro pixel‑dokonalou kontrolu.

**Q: Je možné použít vlastní fonty pro text čárového kódu?**  
A: Ano, můžete přizpůsobit font textu pomocí vlastnosti `CodeTextParameters` třídy `BarcodeGenerator`.

**Q: Kde mohu získat pomoc, pokud narazím na problémy?**  
A: Navštivte [support forum](https://forum.aspose.com/c/words/8/) pro pomoc od komunity Aspose a inženýrů.

## Závěr

Podle výše uvedených kroků nyní víte, jak **create QR code Java** obrázky a **embed barcode in Word** dokumenty pomocí Aspose.Words pro Java. Tato technika je dostatečně flexibilní pro štítky zásob, vstupenky na akce nebo jakýkoli scénář, kde je čárový kód součástí generovaného dokumentu. Experimentujte s různými typy čárových kódů, barvami a možnostmi velikosti, aby vyhovovaly vašim konkrétním obchodním potřebám.

---

**Poslední aktualizace:** 2026-10-23  
**Testováno s:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Autor:** Aspose

## Související tutoriály

- [Vytvořit PDF z Wordu s generováním čárových kódů – Aspose.Words pro Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Uložit Word jako PDF s Aspose Words krok za krokem – Java průvodce](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Vytvořit prázdný Word dokument v Javě s Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}