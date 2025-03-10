---
title: Spojení a připojení dokumentů v Aspose.Words pro Java
linktitle: Spojení a připojení dokumentů
second_title: Aspose.Words Java Document Processing API
description: Naučte se, jak snadno připojit a připojit dokumenty pomocí Aspose.Words for Java. Zachovejte formátování, spravujte záhlaví, zápatí a další.
weight: 30
url: /cs/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spojení a připojení dokumentů v Aspose.Words pro Java


## Úvod do spojování a připojování dokumentů v Aspose.Words pro Javu

V tomto tutoriálu prozkoumáme, jak připojit a připojit dokumenty pomocí knihovny Aspose.Words for Java. Dozvíte se, jak plynule sloučit více dokumentů při zachování formátování a struktury.

## Předpoklady

Než začneme, ujistěte se, že máte ve svém projektu Java nastaveno rozhraní Aspose.Words for Java API.

## Možnosti spojení dokumentů

### Jednoduchá příloha

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Připojit pomocí možností formátu importu

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Připojit k prázdnému dokumentu

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Připojit s převodem čísla stránky

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Převést NUMPAGES polí
dstDoc.updatePageLayout(); // Aktualizujte rozvržení stránky pro správné číslování
```

## Manipulace s různými nastaveními stránky

Při přidávání dokumentů s různým nastavením stránky:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ujistěte se, že nastavení nastavení stránky odpovídá cílovému dokumentu
```

## Spojení dokumentů s různými styly

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Chytré stylové chování

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Vkládání dokumentů pomocí DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Zachování číslování zdrojů

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Manipulace s textovými poli

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Správa záhlaví a zápatí

### Propojení záhlaví a zápatí

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Odpojení záhlaví a zápatí

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Závěr

Aspose.Words for Java poskytuje flexibilní a výkonné nástroje pro spojování a připojování dokumentů, ať už potřebujete udržovat formátování, zpracovávat různá nastavení stránek nebo spravovat záhlaví a zápatí. Experimentujte s těmito technikami, abyste splnili své specifické potřeby zpracování dokumentů.

## FAQ

### Jak mohu hladce spojit dokumenty s různými styly?

 Chcete-li spojit dokumenty s různými styly, použijte`ImportFormatMode.USE_DESTINATION_STYLES` při připojování.

### Mohu při přidávání dokumentů zachovat číslování stránek?

 Ano, číslování stránek můžete zachovat pomocí`convertNumPageFieldsToPageRef` metodu a aktualizaci rozvržení stránky.

### Co je chování v chytrém stylu?

 Chování inteligentního stylu pomáhá udržovat konzistentní styly při připojování dokumentů. Použijte jej s`ImportFormatOptions` pro lepší výsledky.

### Jak mohu zacházet s textovými poli při přidávání dokumentů?

Soubor`importFormatOptions.setIgnoreTextBoxes(false)` pro zahrnutí textových polí během přidávání.

### Co když chci propojit/zrušit propojení záhlaví a zápatí mezi dokumenty?

 Můžete propojit záhlaví a zápatí s`linkToPrevious(true)` nebo je odpojit`linkToPrevious(false)` podle potřeby.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
