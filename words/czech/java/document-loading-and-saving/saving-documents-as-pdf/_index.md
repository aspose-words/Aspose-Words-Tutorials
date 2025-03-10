---
title: Ukládání dokumentů jako PDF v Aspose.Words pro Java
linktitle: Ukládání dokumentů jako PDF
second_title: Aspose.Words Java Document Processing API
description: Naučte se ukládat dokumenty aplikace Word jako PDF pomocí Aspose.Words for Java. Přizpůsobte písma, vlastnosti a kvalitu obrazu. Komplexní průvodce převodem do PDF.
weight: 22
url: /cs/java/document-loading-and-saving/saving-documents-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů jako PDF v Aspose.Words pro Java


## Úvod do ukládání dokumentů jako PDF v Aspose.Words pro Java

V tomto podrobném průvodci prozkoumáme, jak ukládat dokumenty jako PDF pomocí Aspose.Words for Java. Probereme různé aspekty převodu PDF a poskytneme příklady kódu, které proces usnadní.

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

- Java Development Kit (JDK) nainstalovaný ve vašem systému.
-  Aspose.Words pro knihovnu Java. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/java/).

## Převod dokumentu do PDF

Chcete-li převést dokument aplikace Word do formátu PDF, můžete použít následující fragment kódu:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Nahradit`"input.docx"` s cestou k dokumentu aplikace Word a`"output.pdf"` s požadovanou cestou výstupního souboru PDF.

## Ovládání možností ukládání PDF

 Různé možnosti uložení PDF můžete ovládat pomocí`PdfSaveOptions` třída. Můžete například nastavit zobrazovaný titul pro dokument PDF takto:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Vkládání písem do PDF

Pro vložení písem do vygenerovaného PDF použijte následující kód:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Přizpůsobení vlastností dokumentu

Vlastnosti dokumentu ve vygenerovaném PDF můžete přizpůsobit. Například:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Export struktury dokumentu

 Chcete-li exportovat strukturu dokumentu, nastavte`exportDocumentStructure` možnost`true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Komprese obrazu

Kompresi obrazu můžete ovládat pomocí následujícího kódu:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Aktualizace naposledy vytištěné vlastnosti

Chcete-li aktualizovat vlastnost "Naposledy vytištěno" v PDF, použijte:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## Vykreslování DML 3D efektů

Pro pokročilé vykreslování DML 3D efektů nastavte režim vykreslování:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Interpolace obrázků

Pro zlepšení kvality obrazu můžete povolit interpolaci obrazu:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Závěr

Aspose.Words for Java poskytuje komplexní možnosti pro převod dokumentů aplikace Word do formátu PDF s flexibilitou a možnostmi přizpůsobení. Můžete ovládat různé aspekty výstupu PDF, včetně písem, vlastností dokumentu, komprese obrazu a dalších.

## FAQ

### Jak převedu dokument aplikace Word do formátu PDF pomocí Aspose.Words for Java?

Chcete-li převést dokument aplikace Word do formátu PDF, použijte následující kód:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Nahradit`"input.docx"` s cestou k dokumentu aplikace Word a`"output.pdf"` s požadovanou cestou výstupního souboru PDF.

### Mohu do PDF generovaného Aspose.Words for Java vložit písma?

 Ano, do PDF můžete vkládat písma nastavením`setEmbedFullFonts` možnost`true` v`PdfSaveOptions`. Zde je příklad:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Jak mohu upravit vlastnosti dokumentu ve vygenerovaném PDF?

 Vlastnosti dokumentu v PDF můžete upravit pomocí`setCustomPropertiesExport` možnost v`PdfSaveOptions`. Například:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Jaký je účel komprese obrázků v Aspose.Words for Java?

 Komprese obrázků umožňuje řídit kvalitu a velikost obrázků ve vygenerovaném PDF. Režim komprese obrazu můžete nastavit pomocí`setImageCompression` v`PdfSaveOptions`.

### Jak aktualizuji vlastnost "Naposledy vytištěno" v PDF?

 Vlastnost "Naposledy vytištěno" v PDF můžete aktualizovat nastavením`setUpdateLastPrintedProperty` na`true` v`PdfSaveOptions`. To bude odrážet poslední vytištěné datum v metadatech PDF.

### Jak mohu zlepšit kvalitu obrazu při převodu do PDF?

 Chcete-li zlepšit kvalitu obrazu, povolte nastavením interpolaci obrazu`setInterpolateImages` na`true` v`PdfSaveOptions`. Výsledkem budou hladší a kvalitnější obrázky v PDF.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
