---
"description": "Naučte se krok za krokem, jak používat záhlaví a zápatí v Aspose.Words pro Javu. Vytvářejte profesionální dokumenty bez námahy."
"linktitle": "Používání záhlaví a zápatí"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Používání záhlaví a zápatí v Aspose.Words pro Javu"
"url": "/cs/java/using-document-elements/using-headers-and-footers/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání záhlaví a zápatí v Aspose.Words pro Javu


V této komplexní příručce vás provedeme procesem práce se záhlavími a zápatími v Aspose.Words pro Javu. Záhlaví a zápatí jsou základními prvky formátování dokumentů a Aspose.Words poskytuje výkonné nástroje pro jejich vytváření a přizpůsobení vašim potřebám.

Nyní se pojďme podrobněji ponořit do každého z těchto kroků.

## 1. Úvod do Aspose.Words

Aspose.Words je výkonné Java API, které umožňuje programově vytvářet, manipulovat a vykreslovat dokumenty Wordu. Nabízí rozsáhlé funkce pro formátování dokumentů, včetně záhlaví a zápatí.

## 2. Nastavení prostředí Java

Než začnete používat Aspose.Words, ujistěte se, že máte správně nastavené vývojové prostředí Java. Potřebné pokyny k nastavení naleznete na stránce s dokumentací k Aspose.Words: [Dokumentace k Aspose.Words v Javě](https://reference.aspose.com/words/java/).

## 3. Vytvoření nového dokumentu

Pro práci se záhlavími a zápatími je třeba vytvořit nový dokument pomocí Aspose.Words. Následující kód ukazuje, jak to udělat:

```java
// Kód v Javě pro vytvoření nového dokumentu
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Pochopení nastavení stránky

Nastavení stránky je klíčové pro řízení rozvržení dokumentu. Můžete zadat různé vlastnosti související se záhlavími a zápatími pomocí `PageSetup` třída. Například:

```java
// Nastavení vlastností stránky
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Různé záhlaví/zápatí první stránky

Aspose.Words umožňuje mít pro první stránku dokumentu různá záhlaví a zápatí. Použijte `pageSetup.setDifferentFirstPageHeaderFooter(true);` pro povolení této funkce.

## 6. Práce se záhlavími

### 6.1. Přidávání textu do záhlaví

Do záhlaví můžete přidat text pomocí `DocumentBuilder`Zde je příklad:

```java
// Přidání textu do záhlaví první stránky
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Vkládání obrázků do záhlaví

Pro vložení obrázků do záhlaví můžete použít `insertImage` metoda. Zde je příklad:

```java
// Vložení obrázku do záhlaví
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Úprava stylů záhlaví

Styly záhlaví si můžete přizpůsobit nastavením různých vlastností, jako je písmo, zarovnání a další, jak je znázorněno ve výše uvedených příkladech.

## 7. Práce se zápatími

### 7.1. Přidávání textu do zápatí

Podobně jako u záhlaví můžete přidat text do zápatí pomocí `DocumentBuilder`Zde je příklad:

```java
// Přidání textu do primární patičky
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Vložte text a pole dle potřeby
```

### 7.2. Vkládání obrázků do zápatí

Chcete-li vložit obrázky do zápatí, použijte `insertImage` metoda, stejně jako v záhlavích.

### 7.3. Úprava stylů zápatí

Přizpůsobte si styly zápatí pomocí `DocumentBuilder`, podobně jako přizpůsobování záhlaví.

## 8. Číslování stránek

Čísla stránek můžete do záhlaví a zápatí zahrnout pomocí polí jako `PAGE` a `NUMPAGES`Tato pole se automaticky aktualizují při přidávání nebo odebírání stránek.

## 9. Informace o autorských právech v zápatí

Chcete-li do zápatí dokumentu přidat informace o autorských právech, můžete použít tabulku se dvěma buňkami, přičemž jednu zarovnejte doleva a druhou doprava, jak je znázorněno v úryvku kódu.

## 10. Práce s více sekcemi

Aspose.Words umožňuje pracovat s více sekcemi v dokumentu. Pro každou sekci můžete nastavit různá nastavení stránky a záhlaví/zápatí.

## 11. Orientace na šířku

V případě potřeby můžete změnit orientaci konkrétních sekcí na režim na šířku.

## 12. Kopírování záhlaví/zápatí z předchozích sekcí

Kopírování záhlaví a zápatí z předchozích sekcí může ušetřit čas při vytváření složitých dokumentů.

## 13. Uložení dokumentu

Po vytvoření a úpravě dokumentu jej nezapomeňte uložit pomocí `doc.save()` metoda.

## Kompletní zdrojový kód
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Určete, zda chceme, aby se záhlaví/zápatí první stránky lišily od ostatních stránek.
        // Můžete také použít vlastnost PageSetup.OddAndEvenPagesHeaderFooter k určení
        // různé záhlaví/zápatí pro liché a sudé stránky.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Vložte obrázek s umístěním do horního/levého rohu záhlaví.
        // Vzdálenost od horního/levého okraje stránky je nastavena na 10 bodů.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Pro vytvoření jedné části textu na řádku (s číslováním stránek) používáme tabulku se dvěma buňkami.
        // Zarovnat doleva a zbývající část textu (s autorskými právy) doprava.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Používá pole PAGE a NUMPAGES k automatickému výpočtu aktuálního čísla stránky a počtu stránek.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Zalomením stránky vytvořte druhou stránku, na které se zobrazí primární záhlaví/zápatí.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Tato sekce nepotřebuje samostatnou záhlaví/zápatí první stránky, v dokumentu potřebujeme pouze jednu titulní stránku.
        // a záhlaví/zápatí pro tuto stránku již bylo definováno v předchozí části.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Tato sekce zobrazuje záhlaví/zápatí z předchozí sekce
        // Ve výchozím nastavení volejte currentSection.HeadersFooters.LinkToPrevious(false) pro zrušení této šířky stránky.
        // se pro novou sekci liší, a proto musíme pro tabulku zápatí nastavit různé šířky buněk.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Pokud chceme pro tuto sekci použít již existující sadu záhlaví/zápatí.
        // Ale s drobnými úpravami může být vhodné kopírovat záhlaví/zápatí
        // z předchozí části a aplikovat potřebné úpravy tam, kde je chceme.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Zdrojový kód metody copyHeadersFootersFromPreviousSection
```java
    /// <souhrn>
    //Klonuje a kopíruje záhlaví/zápatí z předchozí sekce do zadané sekce.
    /// </summary>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Závěr

V tomto tutoriálu jsme se seznámili se základy práce se záhlavími a zápatími v Aspose.Words pro Javu. Naučili jste se, jak vytvářet, upravovat a upravovat styly záhlaví a zápatí a také další základní techniky formátování dokumentů.

Další podrobnosti a pokročilé funkce naleznete v [Dokumentace k Aspose.Words v Javě](https://reference.aspose.com/words/java/).

## Často kladené otázky

### 1. Jak mohu přidat čísla stránek do zápatí dokumentu?
Čísla stránek můžete přidat vložením `PAGE` pole do zápatí pomocí Aspose.Words.

### 2. Je Aspose.Words kompatibilní s vývojovými prostředími Java?
Ano, Aspose.Words poskytuje podporu pro vývoj v Javě. Ujistěte se, že máte potřebná nastavení.

### 3. Mohu si přizpůsobit písmo a styl záhlaví a zápatí?
Jistě, můžete si přizpůsobit písma, zarovnání a další styly, aby vaše záhlaví a zápatí byly vizuálně přitažlivé.

### 4. Je možné mít různé záhlaví pro liché a sudé stránky?
Ano, můžete použít `PageSetup.OddAndEvenPagesHeaderFooter` zadat různé záhlaví pro liché a sudé stránky.

### 5. Jak začít s Aspose.Words pro Javu?
Pro začátek navštivte [Dokumentace k Aspose.Words v Javě](https://reference.aspose.com/words/java/) pro komplexní pokyny k používání API.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}