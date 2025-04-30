---
"description": "Naučte se, jak snadno spojovat a přidávat dokumenty pomocí Aspose.Words pro Javu. Zachovávejte formátování, spravujte záhlaví, zápatí a další."
"linktitle": "Spojování a připojování dokumentů"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Spojování a přidávání dokumentů v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Spojování a přidávání dokumentů v Aspose.Words pro Javu


## Úvod do spojování a přidávání dokumentů v Aspose.Words pro Javu

V tomto tutoriálu se podíváme na spojování a přidávání dokumentů pomocí knihovny Aspose.Words pro Javu. Naučíte se, jak bezproblémově sloučit více dokumentů a zároveň zachovat formátování a strukturu.

## Předpoklady

Než začneme, ujistěte se, že máte ve svém projektu Java nastavené rozhraní Aspose.Words pro Java API.

## Možnosti spojování dokumentů

### Jednoduché připojení

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Přidat s možnostmi formátu importu

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Přidat k prázdnému dokumentu

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Přidat s převodem čísel stránek

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Převést pole NUMPAGES
dstDoc.updatePageLayout(); // Aktualizujte rozvržení stránky pro správné číslování
```

## Práce s různými nastaveními stránky

Při připojování dokumentů s různým nastavením stránky:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ujistěte se, že nastavení stránky odpovídá cílovému dokumentu.
```

## Spojování dokumentů s různými styly

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Chování v chytrém stylu

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Vkládání dokumentů pomocí nástroje DocumentBuilder

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

## Práce s textovými poli

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

Aspose.Words pro Javu poskytuje flexibilní a výkonné nástroje pro spojování a přidávání dokumentů, ať už potřebujete zachovat formátování, spravovat různá nastavení stránek nebo spravovat záhlaví a zápatí. Experimentujte s těmito technikami, abyste splnili své specifické potřeby v oblasti zpracování dokumentů.

## Často kladené otázky

### Jak mohu bez problémů spojit dokumenty s různými styly?

Chcete-li spojit dokumenty s různými styly, použijte `ImportFormatMode.USE_DESTINATION_STYLES` při připojování.

### Mohu při připojování dokumentů zachovat číslování stránek?

Ano, číslování stránek můžete zachovat pomocí `convertNumPageFieldsToPageRef` metodu a aktualizaci rozvržení stránky.

### Co je to chytré stylové chování?

Chování inteligentního stylu pomáhá udržovat konzistentní styly při připojování dokumentů. Používejte ho s `ImportFormatOptions` pro lepší výsledky.

### Jak mohu pracovat s textovými poli při přidávání dokumentů?

Soubor `importFormatOptions.setIgnoreTextBoxes(false)` zahrnout textová pole během přidávání.

### Co když chci propojit/odpojit záhlaví a zápatí mezi dokumenty?

Záhlaví a zápatí můžete propojit s `linkToPrevious(true)` nebo je odpojit od `linkToPrevious(false)` podle potřeby.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}