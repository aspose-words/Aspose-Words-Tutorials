---
"description": "Naučte se, jak ukládat dokumenty Wordu jako PDF pomocí Aspose.Words pro Javu. Upravte si písma, vlastnosti a kvalitu obrazu. Komplexní průvodce převodem PDF."
"linktitle": "Ukládání dokumentů ve formátu PDF"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Ukládání dokumentů jako PDF v Aspose.Words pro Javu"
"url": "/cs/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů jako PDF v Aspose.Words pro Javu


## Úvod do ukládání dokumentů ve formátu PDF v Aspose.Words pro Javu

V tomto podrobném návodu se podíváme na to, jak ukládat dokumenty ve formátu PDF pomocí Aspose.Words pro Javu. Probereme různé aspekty převodu PDF a uvedeme příklady kódu, které celý proces usnadní.

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

- Na vašem systému nainstalovaná sada pro vývoj Java (JDK).
- Knihovna Aspose.Words pro Javu. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/java/).

## Převod dokumentu do PDF

Chcete-li převést dokument Word do PDF, můžete použít následující úryvek kódu:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Nahradit `"input.docx"` s cestou k vašemu dokumentu Word a `"output.pdf"` s požadovanou cestou k výstupnímu PDF souboru.

## Ovládání možností ukládání PDF

Různé možnosti ukládání PDF můžete ovládat pomocí `PdfSaveOptions` třída. Zobrazovaný název dokumentu PDF můžete například nastavit takto:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Vkládání písem do PDF

Chcete-li vložit písma do vygenerovaného PDF souboru, použijte následující kód:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Přizpůsobení vlastností dokumentu

Vlastnosti dokumentu v generovaném PDF souboru můžete upravit. Například:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Export struktury dokumentu

Chcete-li exportovat strukturu dokumentu, nastavte `exportDocumentStructure` možnost `true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Komprese obrazu

Kompresi obrázků můžete ovládat pomocí následujícího kódu:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Aktualizace poslední vytištěné vlastnosti

Chcete-li aktualizovat vlastnost „Naposledy vytištěno“ v PDF, použijte:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## Renderování 3D efektů DML

Pro pokročilé vykreslování 3D efektů DML nastavte režim vykreslování:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Interpolace obrázků

Interpolaci obrazu můžete povolit pro zlepšení kvality obrazu:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Závěr

Aspose.Words pro Javu nabízí komplexní funkce pro převod dokumentů Word do formátu PDF s flexibilitou a možnostmi přizpůsobení. Můžete ovládat různé aspekty výstupu PDF, včetně písem, vlastností dokumentu, komprese obrázků a dalších.

## Často kladené otázky

### Jak převedu dokument Wordu do PDF pomocí Aspose.Words pro Javu?

Chcete-li převést dokument Word do PDF, použijte následující kód:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Nahradit `"input.docx"` s cestou k vašemu dokumentu Word a `"output.pdf"` s požadovanou cestou k výstupnímu PDF souboru.

### Mohu vložit písma do PDF vygenerovaného programem Aspose.Words pro Javu?

Ano, písma můžete do PDF vložit nastavením `setEmbedFullFonts` možnost `true` v `PdfSaveOptions`Zde je příklad:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Jak mohu přizpůsobit vlastnosti dokumentu ve vygenerovaném PDF?

Vlastnosti dokumentu v PDF můžete přizpůsobit pomocí `setCustomPropertiesExport` možnost v `PdfSaveOptions`Například:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Jaký je účel komprese obrázků v Aspose.Words pro Javu?

Komprese obrázků umožňuje ovládat kvalitu a velikost obrázků ve vygenerovaném PDF. Režim komprese obrázků můžete nastavit pomocí `setImageCompression` v `PdfSaveOptions`.

### Jak aktualizuji vlastnost „Naposledy vytištěno“ v PDF?

Vlastnost „Naposledy vytištěno“ v PDF můžete aktualizovat nastavením `setUpdateLastPrintedProperty` na `true` v `PdfSaveOptions`Toto se projeví v metadatech PDF a zobrazí se datum posledního tisku.

### Jak mohu zlepšit kvalitu obrazu při převodu do PDF?

Chcete-li zlepšit kvalitu obrazu, povolte interpolaci obrazu nastavením `setInterpolateImages` na `true` v `PdfSaveOptions`Díky tomu budou obrázky v PDF plynulejší a kvalitnější.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}