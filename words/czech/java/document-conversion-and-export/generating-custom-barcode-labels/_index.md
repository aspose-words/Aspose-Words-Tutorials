---
title: Generování vlastních štítků s čárovým kódem v Aspose.Words pro Java
linktitle: Generování vlastních štítků s čárovými kódy
second_title: Aspose.Words Java Document Processing API
description: Generujte vlastní štítky s čárovými kódy v Aspose.Words pro Java. V tomto podrobném průvodci se dozvíte, jak vytvářet personalizovaná řešení čárových kódů pomocí Aspose.Words for Java.
weight: 10
url: /cs/java/document-conversion-and-export/generating-custom-barcode-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generování vlastních štítků s čárovým kódem v Aspose.Words pro Java


## Úvod do generování vlastních štítků s čárovým kódem v Aspose.Words pro Javu

Čárové kódy jsou v moderních aplikacích nezbytné, ať už spravujete inventář, generujete vstupenky nebo vyrábíte identifikační karty. S Aspose.Words pro Java se vytváření vlastních štítků s čárovými kódy stává hračkou. Tento tutoriál vás krok za krokem provede generováním vlastních štítků s čárovým kódem pomocí rozhraní IBarcodeGenerator. Jste připraveni se ponořit? Jdeme na to!


## Předpoklady

Než začneme kódovat, ujistěte se, že máte následující:

- Java Development Kit (JDK): Verze 8 nebo vyšší.
-  Aspose.Words for Java Library:[Stahujte zde](https://releases.aspose.com/words/java/).
-  Aspose.BarCode for Java Library:[Stahujte zde](https://releases.aspose.com/).
- Integrované vývojové prostředí (IDE): IntelliJ IDEA, Eclipse nebo jakékoli IDE, které preferujete.
-  Dočasná licence: Získejte a[dočasná licence](https://purchase.aspose.com/temporary-license/) pro neomezený přístup.

## Importujte balíčky

Použijeme knihovny Aspose.Words a Aspose.BarCode. Importujte do svého projektu následující balíčky:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Tyto importy nám umožňují využívat funkce generování čárových kódů a integrovat je do dokumentů aplikace Word.

Rozdělme tento úkol na zvládnutelné kroky.

## Krok 1: Vytvořte třídu Utility pro operace s čárovými kódy

Pro zjednodušení operací souvisejících s čárovým kódem vytvoříme třídu obslužných programů s pomocnými metodami pro běžné úlohy, jako je převod barev a úprava velikosti.

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

- `twipsToPixels` Metoda: Převede twipy (používané v dokumentech aplikace Word) na pixely.
- `convertColor` Metoda: Převede hexadecimální barevné kódy do`Color` objektů.

## Krok 2: Implementujte Vlastní generátor čárových kódů

 Budeme implementovat`IBarcodeGenerator` rozhraní pro generování čárových kódů a jejich integraci s Aspose.Words.

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
  -  Vytvoří a`BarcodeGenerator` instance.
  - Nastaví barvu čárového kódu, barvu pozadí a vygeneruje obrázek.

## Krok 3: Vygenerujte čárový kód a přidejte jej do dokumentu aplikace Word

Nyní integrujeme náš generátor čárových kódů do dokumentu aplikace Word.

### Kód:

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Načtěte nebo vytvořte dokument aplikace Word
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Nastavte vlastní generátor čárových kódů
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Vygenerujte obrázek čárového kódu
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Vložte obrázek čárového kódu do dokumentu aplikace Word
        builder.insertImage(barcodeImage, 200, 200);

        // Uložte dokument
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

### Vysvětlení:

- Inicializace dokumentu: Vytvořte nebo načtěte dokument aplikace Word.
- Parametry čárového kódu: Definujte typ, hodnotu a barvy čárového kódu.
- Vložení obrázku: Přidejte vygenerovaný obrázek čárového kódu do dokumentu aplikace Word.
- Uložit dokument: Uložte soubor v požadovaném formátu.

## Závěr

Podle těchto kroků můžete bez problémů generovat a vkládat vlastní štítky s čárovými kódy do dokumentů aplikace Word pomocí Aspose.Words for Java. Tento přístup je flexibilní a lze jej přizpůsobit různým aplikacím. Šťastné kódování!


## Nejčastější dotazy

1. Mohu používat Aspose.Words for Java bez licence?
 Ano, ale bude mít určitá omezení. Získejte a[dočasná licence](https://purchase.aspose.com/temporary-license/) pro plnou funkčnost.

2. Jaké typy čárových kódů mohu generovat?
Aspose.BarCode podporuje QR, Code 128, EAN-13 a mnoho dalších typů. Zkontrolujte[dokumentace](https://reference.aspose.com/words/java/) pro úplný seznam.

3. Jak mohu změnit velikost čárového kódu?
 Upravte`XDimension` a`BarHeight` parametry v`BarcodeGenerator` nastavení.

4. Mohu použít vlastní písma pro čárové kódy?
 Ano, můžete si přizpůsobit textová písma čárových kódů prostřednictvím`CodeTextParameters` vlastnictví.

5. Kde mohu získat pomoc s Aspose.Words?
 Navštivte[fórum podpory](https://forum.aspose.com/c/words/8/) o pomoc.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
