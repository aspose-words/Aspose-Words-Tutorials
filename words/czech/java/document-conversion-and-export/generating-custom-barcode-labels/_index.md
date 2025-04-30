---
"description": "Generování vlastních štítků s čárovými kódy v Aspose.Words pro Javu. V tomto podrobném návodu se naučte, jak vytvářet personalizovaná řešení s čárovými kódy pomocí Aspose.Words pro Javu."
"linktitle": "Generování vlastních štítků s čárovými kódy"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Generování vlastních štítků s čárovými kódy v Aspose.Words pro Javu"
"url": "/cs/java/document-conversion-and-export/generating-custom-barcode-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generování vlastních štítků s čárovými kódy v Aspose.Words pro Javu


## Úvod do generování vlastních štítků s čárovými kódy v Aspose.Words pro Javu

Čárové kódy jsou v moderních aplikacích nezbytné, ať už spravujete zásoby, generujete lístky nebo vytváříte identifikační karty. S Aspose.Words pro Javu se vytváření vlastních štítků s čárovými kódy stává hračkou. Tento podrobný návod vás provede generováním vlastních štítků s čárovými kódy pomocí rozhraní IBarcodeGenerator. Jste připraveni se do toho pustit? Pojďme na to!


## Předpoklady

Než začneme s kódováním, ujistěte se, že máte následující:

- Vývojová sada pro Javu (JDK): verze 8 nebo vyšší.
- Aspose.Words pro knihovnu Java: [Stáhnout zde](https://releases.aspose.com/words/java/).
- Aspose.BarCode pro knihovnu Java: [Stáhnout zde](https://releases.aspose.com/).
- Integrované vývojové prostředí (IDE): IntelliJ IDEA, Eclipse nebo jakékoli jiné IDE, které preferujete.
- Dočasná licence: Získejte [dočasná licence](https://purchase.aspose.com/temporary-license/) pro neomezený přístup.

## Importovat balíčky

Použijeme knihovny Aspose.Words a Aspose.BarCode. Importujte do svého projektu následující balíčky:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Díky těmto importům můžeme využít funkce generování čárových kódů a integrovat je do dokumentů Wordu.

Rozdělme si tento úkol na zvládnutelné kroky.

## Krok 1: Vytvořte pomocnou třídu pro operace s čárovými kódy

Pro zjednodušení operací souvisejících s čárovými kódy vytvoříme utilitu s pomocnými metodami pro běžné úkoly, jako je převod barev a úprava velikosti.

### Kód:

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Za předpokladu, že výchozí DPI je 96
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

### Vysvětlení:

- `twipsToPixels` Metoda: Převede twipy (používané v dokumentech Wordu) na pixely.
- `convertColor` Metoda: Převádí hexadecimální barevné kódy na `Color` objekty.

## Krok 2: Implementace vlastního generátoru čárových kódů

Implementujeme `IBarcodeGenerator` rozhraní pro generování čárových kódů a jejich integraci s Aspose.Words.

### Kód:

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

### Vysvětlení:

- `getBarcodeImage` Metoda:
  - Vytvoří `BarcodeGenerator` instance.
  - Nastaví barvu čárového kódu, barvu pozadí a vygeneruje obrázek.

## Krok 3: Vygenerujte čárový kód a přidejte ho do dokumentu Word

Nyní integrujeme náš generátor čárových kódů do dokumentu Word.

### Kód:

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Načtení nebo vytvoření dokumentu Wordu
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Nastavení vlastního generátoru čárových kódů
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generovat obrázek čárového kódu
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Vložení obrázku čárového kódu do dokumentu Word
        builder.insertImage(barcodeImage, 200, 200);

        // Uložit dokument
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

### Vysvětlení:

- Inicializace dokumentu: Vytvoření nebo načtení dokumentu aplikace Word.
- Parametry čárového kódu: Definujte typ, hodnotu a barvy čárového kódu.
- Vložení obrázku: Přidejte vygenerovaný obrázek čárového kódu do dokumentu Word.
- Uložit dokument: Uložte soubor v požadovaném formátu.

## Závěr

Pomocí těchto kroků můžete bez problémů generovat a vkládat vlastní štítky s čárovými kódy do dokumentů Word pomocí Aspose.Words pro Javu. Tento přístup je flexibilní a lze jej přizpůsobit různým aplikacím. Hodně štěstí s programováním!


## Často kladené otázky

1. Mohu používat Aspose.Words pro Javu bez licence?
Ano, ale bude to mít určitá omezení. Získejte [dočasná licence](https://purchase.aspose.com/temporary-license/) pro plnou funkčnost.

2. Jaké typy čárových kódů mohu generovat?
Aspose.BarCode podporuje QR, Code 128, EAN-13 a mnoho dalších typů. Zkontrolujte [dokumentace](https://reference.aspose.com/words/java/) pro kompletní seznam.

3. Jak mohu změnit velikost čárového kódu?
Upravte `XDimension` a `BarHeight` parametry v `BarcodeGenerator` nastavení.

4. Mohu pro čárové kódy použít vlastní fonty?
Ano, písma textu čárových kódů si můžete přizpůsobit pomocí `CodeTextParameters` vlastnictví.

5. Kde mohu získat pomoc s Aspose.Words?
Navštivte [fórum podpory](https://forum.aspose.com/c/words/8/) o pomoc.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}