---
date: 2026-02-09
description: Vytvářejte vlastní štítky s čárovými kódy pomocí Aspose Barcode Java
  v Aspose.Words pro Java. Naučte se, jak vložit čárový kód do dokumentů Word a generovat
  příklady QR kódu v Javě.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Generování vlastních štítků s čárovým kódem pomocí Aspose Barcode Java
url: /cs/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generování vlastních štítků s čárovými kódy pomocí Aspose Barcode Java

## Úvod do generování vlastních štítků s čárovými kódy v Aspose.Words pro Java

Čárové kódy jsou nezbytné v moderních aplikacích a **Aspose Barcode Java** usnadňuje jejich tvorbu přímo v dokumentech Word. Ať už potřebujete **vložit čárový kód do Wordu**, vygenerovat QR kód pro URL nebo převést měrné jednotky, tento tutoriál vás provede vším, co potřebujete. Připravení ponořit se? Pojďme na to!

## Rychlé odpovědi
- **Jaká knihovna vytváří čárové kódy v Javě?** Aspose Barcode Java ve spojení s Aspose.Words pro Java.  
- **Jaký typ čárového kódu je demonstrován?** QR kód (generate qr code java).  
- **Jak převést twips na pixely?** Použijte poskytnutou pomocnou metodu `twipsToPixels`.  
- **Mohu přidat čárový kód do existujícího souboru Word?** Ano – stačí použít metodu `DocumentBuilder.insertImage`.  
- **Potřebuji licenci?** Dočasná licence odstraňuje omezení hodnocení.

## Co je Aspose Barcode Java?
Aspose Barcode Java je výkonné API, které umožňuje vývojářům programově generovat širokou škálu 1D a 2D čárových kódů (včetně QR kódů). V kombinaci s Aspose.Words pro Java můžete **vložit čárový kód do Wordu** do dokumentů, aniž byste opustili své Java prostředí.

## Proč používat Aspose Barcode Java s Aspose.Words?
- **Plná kontrola** nad vzhledem čárového kódu (barvy, velikost, formát).  
- **Bezproblémová integrace** – obrázek čárového kódu může být vložen přímo do dokumentu Word.  
- **Cross‑platform** – funguje na jakékoli platformě kompatibilní s Javou.  
- **Rozšiřitelný** – můžete vytvořit pomocné třídy pro opětovné použití logiky čárových kódů napříč projekty.

## Předpoklady

Než začneme kódovat, ujistěte se, že máte následující:

- Java Development Kit (JDK): verze 8 nebo vyšší.  
- Knihovna Aspose.Words pro Java: [Stáhnout zde](https://releases.aspose.com/words/java/).  
- Knihovna Aspose.BarCode pro Java: [Stáhnout zde](https://releases.aspose.com/).  
- Integrované vývojové prostředí (IDE): IntelliJ IDEA, Eclipse nebo jakékoli IDE, které preferujete.  
- Dočasná licence: Získejte [dočasnou licenci](https://purchase.aspose.com/temporary-license/) pro neomezený přístup.

## Import balíčků

Budeme používat knihovny Aspose.Words a Aspose.BarCode. Do svého projektu importujte následující balíčky:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Tyto importy nám umožňují využívat funkce generování čárových kódů a integrovat je do dokumentů Word.

Rozdělme tento úkol na zvládnutelné kroky.

## Krok 1: Vytvořte pomocnou třídu pro operace s čárovými kódy

Abychom zjednodušili operace související s čárovými kódy, vytvoříme pomocnou třídu s metodami pro běžné úkoly, jako je převod barev a **convert twips to pixels**.

### Code:

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

- `twipsToPixels` převádí měrnou jednotku používanou ve Wordu (twips) na pixely obrazovky – užitečná pomůcka, když potřebujete přesné rozměry.  
- `convertColor` převádí řetězec hexadecimální barvy (např. “FF0000”) na Java objekt `Color`, což vám umožní přizpůsobit popředí a pozadí čárového kódu.

## Krok 2: Implementujte vlastní generátor čárových kódů

Implementujeme rozhraní `IBarcodeGenerator`, aby Aspose.Words mohl požádat o obrázek čárového kódu, kdykoli narazí na pole čárového kódu.

### Code:

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

- `getBarcodeImage` vytvoří `BarcodeGenerator` pomocí typu **generate qr code java**, který specifikujete (QR v našem příkladu).  
- Aplikuje barvy popředí a pozadí pomocí pomocných metod a poté vrátí vykreslený obrázek.  
- Záložní obrázek zajišťuje, že program pokračuje i v případě selhání vytvoření čárového kódu.

## Krok 3: Vygenerujte čárový kód a přidejte jej do dokumentu Word

Nyní spojíme vše dohromady: vytvoříme dokument, vygenerujeme čárový kód a **how to add barcode** do souboru Word.

### Code:

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

1. **Inicializace dokumentu** – vytvoří nový `Document` (nebo můžete načíst existující .docx).  
2. **Parametry čárového kódu** – definují typ (`QR`), hodnotu a barvy, což demonstruje použití **generate qr code java**.  
3. **Vložení obrázku** – `builder.insertImage` umístí čárový kód tam, kde jej potřebujete, efektivně ukazující **how to add barcode** do souboru Word.  
4. **Ukládání** – finální dokument (`CustomBarcodeLabels.docx`) obsahuje vložený čárový kód připravený k tisku nebo distribuci.

## Časté problémy a řešení

| Problém | Příčina | Řešení |
|-------|-------|-----|
| Čárový kód se zobrazuje prázdně | Neplatný řetězec barvy nebo nepodporovaný typ čárového kódu | Ověřte formát hexadecimální barvy a použijte podporovaný typ (např. QR, Code128). |
| Velikost obrázku je špatná | Nesprávný převod pixelů | Použijte `twipsToPixels` k výpočtu přesných rozměrů podle rozvržení Wordu. |
| Výjimka licence | Žádná platná licence Aspose | Aplikujte dočasnou nebo zakoupenou licenci před spuštěním kódu. |

## Často kladené otázky

**Q: Mohu používat Aspose.Words pro Java bez licence?**  
A: Ano, ale narazíte na omezení hodnocení. Získejte [dočasnou licenci](https://purchase.aspose.com/temporary-license/) pro plnou funkčnost.

**Q: Jaké typy čárových kódů mohu generovat?**  
A: Aspose.BarCode podporuje QR, Code 128, EAN‑13 a mnoho dalších. Kompletní seznam najdete v oficiální [dokumentaci](https://reference.aspose.com/words/java/).

**Q: Jak mohu změnit velikost čárového kódu?**  
A: Upravit parametry šířky/výšky v `builder.insertImage` nebo změnit vlastnosti `XDimension` a `BarHeight` objektu `BarcodeGenerator`.

**Q: Mohu použít vlastní písma pro lidsky čitelnou část čárového kódu?**  
A: Rozhodně. Použijte vlastnost `CodeTextParameters` k nastavení rodiny písma, velikosti a stylu.

**Q: Kde mohu získat pomoc s Aspose.Words?**  
A: Navštivte [fórum podpory](https://forum.aspose.com/c/words/8/) pro komunitní pomoc a oficiální podporu.

---

**Last Updated:** 2026-02-09  
**Tested With:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}