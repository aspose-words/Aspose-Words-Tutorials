---
date: 2026-02-19
description: Naučte se, jak pomocí Aspose.Words pro Javu vytvořit dokument s vodoznakem
  a přidat obrázkový vodoznak v Javě pro profesionálně vypadající dokumenty.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Vytvořte dokument s vodoznakem pomocí Aspose.Words pro Java
url: /cs/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte dokument s vodoznakem pomocí Aspose.Words pro Java

V tomto tutoriálu **vytvoříte dokument s vodoznakem** pomocí API Aspose.Words pro Java. Vodoznaky – ať už textové nebo obrázkové – vám pomohou označit soubor jako důvěrný, koncept nebo schválený a lze je programově aplikovat na jakýkoli dokument Word. Provedeme vás nastavením knihovny, přidáním textových i obrázkových vodoznaků, úpravou jejich vzhledu a dokonce i jejich odebráním, když již nejsou potřeba.

## Rychlé odpovědi
- **Co vodoznak dělá?** Překrývá každou stránku textem nebo obrázkem, aby vyjádřil stav nebo značku.  
- **Která knihovna přidává vodoznaky v Javě?** Aspose.Words pro Java poskytuje vestavěnou podporu vodoznaků.  
- **Mohu přidat obrázkový vodoznak?** Ano – použijte třídu `Shape` a přístup **add image watermark java**.  
- **Je vodoznak poloprůhledný?** Průhlednost můžete řídit pomocí `setSemitransparent` u textových vodoznaků.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; pro produkční nasazení je vyžadována komerční licence.

## Co je vodoznak a proč jej používat?

Vodoznak je slabý překryv – textový nebo grafický – přidaný na každou stránku dokumentu. Často se používá k označení **důvěrnosti**, **stavu konceptu** nebo **značky** bez změny samotného obsahu. Programové přidání vodoznaků zajišťuje konzistenci napříč velkým množstvím souborů a šetří čas oproti ruční úpravě.

## Nastavení Aspose.Words pro Java

Než začneme přidávat vodoznaky, ujistěte se, že je knihovna připravena ve vašem projektu:

1. Stáhněte Aspose.Words pro Java z [here](https://releases.aspose.com/words/java/).  
2. Přidejte stažený JAR (nebo Maven/Gradle závislost) do classpath vašeho projektu.  
3. Naimportujte požadované třídy ve vašem Java souboru:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Nyní, když je knihovna nastavena, pojďme se podívat na samotný kód vodoznaku.

## Jak přidat textový vodoznak

Textové vodoznaky jsou ideální pro označení dokumentu jako „CONFIDENTIAL“ nebo „DRAFT“. Následující úryvek ukazuje čistý způsob, jak **vytvořit dokument s vodoznakem** pomocí `TextWatermarkOptions`.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### Přizpůsobení textového vodoznaku
- **Rodina a velikost písma** – změňte `setFontFamily` a `setFontSize`.  
- **Barva** – použijte libovolnou `java.awt.Color`.  
- **Rozvržení** – vyberte `HORIZONTAL`, `DIAGONAL` atd.  
- **Průhlednost** – zapněte `setSemitransparent(true)` pro světlejší vzhled.

## Jak přidat obrázkový vodoznak (add image watermark java)

Obrázkové vodoznaky jsou perfektní pro loga nebo vlastní grafiku. Níže je příklad **add image watermark java**, který vloží PNG do středu každé stránky.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### Tipy pro obrázkové vodoznaky
- **Změna velikosti** pomocí `setWidth` / `setHeight`, aby se vešly na stránku.  
- **Pozice** může být centrovaná nebo zarovnaná k libovolnému okraji pomocí `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Průhlednost** lze aplikovat úpravou alfa kanálu obrázku před načtením.

## Jak odebrat vodoznaky

Když dokument již vodoznak nepotřebuje, můžete jej programově smazat. Níže uvedený kód prochází všechny tvary a odstraňuje ty, které mají v názvu „Watermark“.

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Časté problémy a řešení

- **Chybějící vodoznak po uložení** – ujistěte se, že po nastavení vodoznaku voláte `doc.save()`.  
- **Obrázek se nezobrazuje** – ověřte, že cesta k obrázku je správná a že soubor je podporovaného formátu (PNG, JPEG, BMP).  
- **Průhlednost se neaplikovala** – `setSemitransparent(true)` funguje jen pro textové vodoznaky; u obrázků upravte alfa kanál PNG.  
- **Více sekcí** – pokud má dokument několik sekcí, přidejte vodoznak do těla každé sekce nebo použijte `doc.getWatermark().setText(...)`, který působí globálně.

## Často kladené otázky

**Q: Jak mohu změnit písmo textového vodoznaku?**  
A: Upravit vlastnost `setFontFamily` v `TextWatermarkOptions`, např. `options.setFontFamily("Times New Roman");`.

**Q: Mohu přidat více vodoznaků do jednoho dokumentu?**  
A: Ano. Vytvořte více objektů `Shape` (pro obrázky) nebo zavolejte `doc.getWatermark().setText(...)` s různými možnostmi pro každý vodoznak.

**Q: Lze vodoznak otočit?**  
A: U obrázkových vodoznaků nastavte rotaci na objektu `Shape` pomocí `watermark.setRotation(angle)`. U textových vodoznaků použijte vlastnost `setLayout` (např. `WatermarkLayout.DIAGONAL`).

**Q: Jak udělat vodoznak poloprůhledný?**  
A: Nastavte `options.setSemitransparent(true)` v `TextWatermarkOptions`. U obrázků upravte průhlednost obrázku před načtením.

**Q: Mohu přidat vodoznaky jen do konkrétních sekcí dokumentu?**  
A: Ano. Projděte `doc.getSections()` a přidejte vodoznak pouze do požadovaných sekcí.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Poslední aktualizace:** 2026-02-19  
**Testováno s:** Aspose.Words pro Java 24.12 (nejnovější)  
**Autor:** Aspose