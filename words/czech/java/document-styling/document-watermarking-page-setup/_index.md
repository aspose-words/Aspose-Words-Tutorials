---
title: Vodoznak dokumentu a nastavení stránky
linktitle: Vodoznak dokumentu a nastavení stránky
second_title: Aspose.Words Java Document Processing API
description: Naučte se používat vodoznaky a nastavovat konfigurace stránek pomocí Aspose.Words for Java. Komplexní průvodce se zdrojovým kódem.
weight: 13
url: /cs/java/document-styling/document-watermarking-page-setup/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vodoznak dokumentu a nastavení stránky

## Zavedení

V oblasti manipulace s dokumenty je Aspose.Words for Java mocným nástrojem, který umožňuje vývojářům ovládat každý aspekt zpracování dokumentů. V tomto komplexním průvodci se ponoříme do složitosti vodoznaku dokumentu a nastavení stránky pomocí Aspose.Words for Java. Ať už jste ostřílený vývojář nebo teprve vstupujete do světa zpracování dokumentů Java, tento podrobný průvodce vás vybaví znalostmi a zdrojovým kódem, které potřebujete.

## Vodoznak dokumentu

### Přidávání vodoznaků

Přidání vodoznaků do dokumentů může být zásadní pro branding nebo zabezpečení vašeho obsahu. Aspose.Words pro Java tento úkol zjednodušuje. Zde je postup:

```java
// Vložte dokument
Document doc = new Document("document.docx");

// Vytvořte vodoznak
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// Umístěte vodoznak
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// Vložte vodoznak
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Uložte dokument
doc.save("document_with_watermark.docx");
```

### Přizpůsobení vodoznaků

Vodoznaky můžete dále přizpůsobit úpravou písma, velikosti, barvy a otočení. Tato flexibilita zajišťuje, že váš vodoznak hladce odpovídá stylu vašeho dokumentu.

## Nastavení stránky

### Velikost a orientace stránky

Nastavení stránky je při formátování dokumentu stěžejní. Aspose.Words for Java nabízí úplnou kontrolu nad velikostí a orientací stránky:

```java
// Vložte dokument
Document doc = new Document("document.docx");

// Nastavte velikost stránky na A4
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// Změňte orientaci stránky na šířku
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// Uložte upravený dokument
doc.save("formatted_document.docx");
```

### Okraje a číslování stránek

Přesná kontrola nad okraji a číslování stránek je pro profesionální dokumenty zásadní. Dosáhněte toho pomocí Aspose.Words pro Java:

```java
// Vložte dokument
Document doc = new Document("document.docx");

// Nastavte okraje
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// Povolit číslování stránek
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// Uložte naformátovaný dokument
doc.save("formatted_document.docx");
```

## Nejčastější dotazy

### Jak mohu odstranit vodoznak z dokumentu?

Chcete-li vodoznak z dokumentu odstranit, můžete procházet tvary dokumentu a odstranit ty, které představují vodoznaky. Zde je úryvek:

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### Mohu přidat více vodoznaků do jednoho dokumentu?

Ano, do dokumentu můžete přidat více vodoznaků vytvořením dalších objektů Shape a jejich umístěním podle potřeby.

### Jak změním velikost stránky na legal v orientaci na šířku?

Chcete-li nastavit velikost stránky na legal v orientaci na šířku, upravte šířku a výšku stránky následovně:

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### Jaké je výchozí písmo pro vodoznaky?

Výchozí písmo pro vodoznaky je Calibri s velikostí písma 36.

### Jak mohu přidat čísla stránek počínaje konkrétní stránkou?

Toho lze dosáhnout nastavením čísla počáteční stránky v dokumentu takto:

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### Jak zarovnám text v záhlaví nebo zápatí na střed?

Text v záhlaví nebo zápatí můžete zarovnat na střed pomocí metody setAlignment u objektu Odstavec v záhlaví nebo zápatí.

## Závěr

tomto rozsáhlém průvodci jsme prozkoumali umění vodoznaku dokumentu a nastavení stránky pomocí Aspose.Words for Java. Vyzbrojeni dodanými úryvky zdrojového kódu a přehledy nyní máte nástroje k jemné manipulaci a formátování dokumentů. Aspose.Words for Java vám umožňuje vytvářet profesionální, značkové dokumenty šité na míru vašim přesným specifikacím.

Zvládnutí manipulace s dokumenty je pro vývojáře cennou dovedností a Aspose.Words for Java je vaším důvěryhodným společníkem na této cestě. Začněte vytvářet úžasné dokumenty ještě dnes!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
