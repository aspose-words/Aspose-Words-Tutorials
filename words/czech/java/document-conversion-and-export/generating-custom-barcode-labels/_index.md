---
date: 2025-12-10
description: Naučte se, jak generovat vlastní štítky s čárovými kódy pomocí Aspose.Words
  pro Javu. Tento krok‑za‑krokem průvodce vám ukáže, jak vložit čárové kódy do dokumentů
  Word.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Vytvořte vlastní štítky s čárovým kódem v Aspose.Words pro Javu
url: /cs/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření vlastních štítků s čárovým kódem v Aspose.Words pro Java

## Úvod do generování vlastního čárového kódu v Aspose.Words pro Java

Čárové kódy jsou nezbytné v moderních aplikacích – ať už spravujete zásoby, tisknete vstupenky nebo vytváříte ID karty. V tomto tutoriálu **vytvoříte vlastní štítky s čárovým kódem** a vložíte je přímo do dokumentu Word pomocí rozhraní `IBarcodeGenerator`. Provedeme vás každým krokem, od nastavení prostředí po vložení obrázku čárového kódu, abyste mohli okamžitě začít používat čárové kódy ve svých Java projektech.

## Rychlé odpovědi
- **Co se v tomto tutoriálu učí?** Jak vytvořit vlastní štítky s čárovým kódem a vložit je do souboru Word pomocí Aspose.Words pro Java.  
- **Jaký typ čárového kódu je v příkladu použit?** QR kód (můžete jej nahradit libovolným podporovaným typem).  
- **Potřebuji licenci?** Pro neomezený přístup během vývoje je vyžadována dočasná licence.  
- **Jaká verze Javy je požadována?** JDK 8 nebo vyšší.  
- **Mohu změnit velikost nebo barvy čárového kódu?** Ano – upravte nastavení `BarcodeParameters` a `BarcodeGenerator`.

## Předpoklady

Než začneme programovat, ujistěte se, že máte následující:

- Java Development Kit (JDK): verze 8 nebo vyšší.  
- Knihovna Aspose.Words pro Java: [Download here](https://releases.aspose.com/words/java/).  
- Knihovna Aspose.BarCode pro Java: [Download here](https://releases.aspose.com/).  
- Integrované vývojové prostředí (IDE): IntelliJ IDEA, Eclipse nebo jakékoli jiné IDE dle vaší preference.  
- Dočasná licence: Získejte [temporary license](https://purchase.aspose.com/temporary-license/) pro neomezený přístup.

## Import balíčků

Budeme používat knihovny Aspose.Words a Aspose.BarCode. Importujte následující balíčky do svého projektu:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Tyto importy nám poskytují přístup k API pro generování čárových kódů a třídám pro práci s dokumenty Word, které budeme potřebovat.

## Krok 1: Vytvoření pomocné třídy pro operace s čárovým kódem

Aby byl hlavní kód přehledný, zabalíme běžné pomocné metody – jako **převod twips na pixely** a **konverzi hex‑barev** – do utility třídy.

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
- `convertColor` – Převádí hexadecimální řetězec (např. `"FF0000"` pro červenou) na objekt `java.awt.Color`, což vám umožní **how to insert barcode** s vlastními barvami popředí a pozadí.

## Krok 2: Implementace vlastního generátoru čárových kódů

Nyní implementujeme rozhraní `IBarcodeGenerator`. Tato třída bude zodpovědná za **generate qr code java**‑stylové obrázky, které Aspose.Words může vložit.

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

- `getBarcodeImage` vytvoří instanci `BarcodeGenerator`, použije barvy předané přes `BarcodeParameters` a nakonec vrátí `BufferedImage`.  
- Metoda také elegantně ošetřuje chyby tím, že vrátí zástupný obrázek, což zajišťuje, že tvorba dokumentu Word nikdy nezhavě selže.

## Krok 3: Vytvoření čárového kódu a **vložit čárový kód do Wordu**

S připraveným generátorem můžeme nyní vytvořit obrázek čárového kódu a **vložit jej do dokumentu Word**.

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
3. **Vložení obrázku** – `builder.insertImage` umístí vygenerovaný čárový kód na požadovanou velikost (200 × 200 pixelů). Toto je jádro **how to insert barcode** do souboru Word.  
4. **Uložení** – Výsledný dokument `CustomBarcodeLabels.docx` obsahuje vložený čárový kód připravený k tisku nebo distribuci.

## Proč generovat vlastní štítky s čárovým kódem pomocí Aspose.Words?

- **Plná kontrola** nad vzhledem čárového kódu (typ, velikost, barvy).  
- **Bezproblémová integrace** – není potřeba mezilehlých souborů obrázků; čárový kód se generuje v paměti a vkládá přímo.  
- **Cross‑platform** – funguje na jakémkoli OS, který podporuje Javu, což je ideální pro server‑side generování dokumentů.  
- **Škálovatelnost** – můžete v cyklu projít zdroj dat a vytvořit stovky personalizovaných štítků během jednoho spuštění.

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Oprava |
|---------|-----------------------|--------|
| Čárový kód je prázdný | Barvy v `BarcodeParameters` jsou stejné (např. černá na černé) | Ověřte hodnoty `foregroundColor` a `backgroundColor`. |
| Obrázek je deformovaný | Nesprávné rozměry pixelů předané do `insertImage` | Upravte argumenty šířky/výšky nebo použijte převod `twipsToPixels` pro přesné měření. |
| Chyba nepodporovaného typu čárového kódu | Použit typ, který `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` nezná | Ujistěte se, že řetězec typu čárového kódu odpovídá jedné z podporovaných hodnot `EncodeTypes` (např. `"QR"`, `"CODE128"`). |

## Často kladené otázky

**Q: Můžu používat Aspose.Words pro Java bez licence?**  
A: Ano, ale budou zde určité omezení. Pro plnou funkčnost získáte [temporary license](https://purchase.aspose.com/temporary-license/).

**Q: Jaké typy čárových kódů mohu generovat?**  
A: Aspose.BarCode podporuje QR, Code 128, EAN‑13 a mnoho dalších formátů. Kompletní seznam najdete v [dokumentaci](https://reference.aspose.com/words/java/).

**Q: Jak mohu změnit velikost čárového kódu?**  
A: Upravit argumenty šířky a výšky v `builder.insertImage`, nebo použít `twipsToPixels` pro převod jednotek Wordu na pixely.

**Q: Je možné použít vlastní písmo pro text čárového kódu?**  
A: Ano, můžete přizpůsobit písmo textu prostřednictvím vlastnosti `CodeTextParameters` třídy `BarcodeGenerator`.

**Q: Kde mohu získat pomoc, pokud narazím na problémy?**  
A: Navštivte [support forum](https://forum.aspose.com/c/words/8/) a požádejte o pomoc komunitu a inženýry Aspose.

## Závěr

Postupným následováním výše uvedených kroků nyní umíte **generovat vlastní obrázky čárových kódů** a **vkládat čárový kód do dokumentů Word** pomocí Aspose.Words pro Java. Tato technika je dostatečně flexibilní pro štítky zásob, vstupenky na akce nebo jakýkoli scénář, kde je čárový kód součástí generovaného dokumentu. Experimentujte s různými typy čárových kódů a možnostmi stylování, aby vyhovovaly vašim konkrétním obchodním potřebám.

---

**Poslední aktualizace:** 2025-12-10  
**Testováno s:** Aspose.Words pro Java 24.12, Aspose.BarCode pro Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}