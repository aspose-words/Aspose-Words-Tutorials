---
title: Použití záhlaví a zápatí v Aspose.Words pro Java
linktitle: Použití záhlaví a zápatí
second_title: Aspose.Words Java Document Processing API
description: Naučte se krok za krokem používat záhlaví a zápatí v Aspose.Words pro Java. Vytvářejte profesionální dokumenty bez námahy.
weight: 16
url: /cs/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití záhlaví a zápatí v Aspose.Words pro Java


V tomto komplexním průvodci vás provedeme procesem práce se záhlavími a zápatími v Aspose.Words pro Java. Záhlaví a zápatí jsou základními prvky formátování dokumentů a Aspose.Words poskytuje výkonné nástroje pro jejich vytváření a přizpůsobení podle vašich potřeb.

Nyní se pojďme ponořit do každého z těchto kroků podrobně.

## 1. Úvod do Aspose.Words

Aspose.Words je výkonné Java API, které vám umožňuje programově vytvářet, manipulovat a vykreslovat dokumenty Wordu. Poskytuje rozsáhlé funkce pro formátování dokumentů, včetně záhlaví a zápatí.

## 2. Nastavení prostředí Java

 Než začnete Aspose.Words používat, ujistěte se, že máte správně nastavené vývojové prostředí Java. Potřebné pokyny k nastavení naleznete na stránce dokumentace Aspose.Words:[Aspose.Words Java dokumentace](https://reference.aspose.com/words/java/).

## 3. Vytvoření nového dokumentu

Chcete-li pracovat se záhlavím a zápatím, musíte vytvořit nový dokument pomocí Aspose.Words. Následující kód ukazuje, jak to udělat:

```java
// Java kód pro vytvoření nového dokumentu
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Vysvětlení nastavení stránky

 Nastavení stránky je zásadní pro ovládání rozvržení dokumentu. Můžete zadat různé vlastnosti týkající se záhlaví a zápatí pomocí`PageSetup` třída. Například:

```java
// Nastavení vlastností stránky
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Různé záhlaví/zápatí první stránky

Aspose.Words vám umožňuje mít různá záhlaví a zápatí pro první stránku dokumentu. Použití`pageSetup.setDifferentFirstPageHeaderFooter(true);` pro aktivaci této funkce.

## 6. Práce s hlavičkami

### 6.1. Přidání textu do záhlaví

 Text do záhlaví můžete přidat pomocí`DocumentBuilder`. Zde je příklad:

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

 Chcete-li vložit obrázky do záhlaví, můžete použít`insertImage` metoda. Zde je příklad:

```java
// Vložení obrázku do záhlaví
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Přizpůsobení stylů záhlaví

Styly záhlaví můžete přizpůsobit nastavením různých vlastností, jako je písmo, zarovnání a další, jak je znázorněno na příkladech výše.

## 7. Práce se zápatím

### 7.1. Přidání textu do zápatí

 Podobně jako u záhlaví můžete přidat text do zápatí pomocí`DocumentBuilder`. Zde je příklad:

```java
// Přidání textu do primárního zápatí
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Vložte text a pole podle potřeby
```

### 7.2. Vkládání obrázků do zápatí

 Chcete-li vložit obrázky do zápatí, použijte`insertImage` stejně jako v hlavičkách.

### 7.3. Přizpůsobení stylů zápatí

 Přizpůsobte styly zápatí pomocí`DocumentBuilder`podobně jako přizpůsobení záhlaví.

## 8. Číslování stránek

 Čísla stránek můžete zahrnout do záhlaví a zápatí pomocí polí jako`PAGE` a`NUMPAGES`. Tato pole se automaticky aktualizují, když přidáváte nebo odebíráte stránky.

## 9. Informace o autorských právech v zápatí

Chcete-li do zápatí dokumentu přidat informace o autorských právech, můžete použít tabulku se dvěma buňkami, přičemž jednu zarovnáte doleva a druhou doprava, jak je znázorněno na úryvku kódu.

## 10. Práce s více sekcemi

Aspose.Words umožňuje pracovat s více sekcemi v rámci dokumentu. Pro každou sekci můžete nastavit různá nastavení stránky a záhlaví/zápatí.

## 11. Orientace v krajině

V případě potřeby můžete změnit orientaci určitých částí na režim na šířku.

## 12. Kopírování záhlaví/zápatí z předchozích sekcí

Kopírování záhlaví a zápatí z předchozích sekcí může ušetřit čas při vytváření složitých dokumentů.

## 13. Uložení dokumentu

Po vytvoření a přizpůsobení dokumentu jej nezapomeňte uložit pomocí`doc.save()` metoda.

## Kompletní zdrojový kód
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Určete, zda chceme, aby se záhlaví/zápatí první stránky lišilo od ostatních stránek.
        // K určení můžete také použít vlastnost PageSetup.OddAndEvenPagesHeaderFooter
        // různá záhlaví/zápatí pro liché a sudé stránky.
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
        // Vložte umístěný obrázek do horního/levého rohu záhlaví.
        // Vzdálenost od horního/levého okraje stránky je nastavena na 10 bodů.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Tabulkou se dvěma buňkami uděláme jednu část textu na řádku (s číslováním stránek).
        // Zarovnat doleva a druhou část textu (s autorským právem) zarovnat doprava.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // K automatickému výpočtu aktuálního čísla stránky a mnoha stránek používá pole PAGE a NUMPAGES.
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
        // Zalomením stránky vytvoříte druhou stránku, na které budou vidět primární záhlaví/zápatí.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Tato sekce nepotřebuje jiné záhlaví/zápatí na první stránce, potřebujeme pouze jednu titulní stránku v dokumentu,
        // záhlaví/zápatí pro tuto stránku již bylo definováno v předchozí části.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Tato sekce zobrazuje záhlaví/zápatí z předchozí sekce
        // ve výchozím nastavení zavolejte currentSection.HeadersFooters.LinkToPrevious(false) pro zrušení této šířky stránky
        // je pro novou sekci odlišná, a proto musíme pro tabulku zápatí nastavit různé šířky buněk.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Pokud chceme pro tuto sekci použít již existující sadu záhlaví/zápatí.
        // Ale s některými drobnými úpravami může být účelné zkopírovat záhlaví/zápatí
        // z předchozí části a aplikujte potřebné úpravy tam, kde je chceme.
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
    /// Klonuje a zkopíruje záhlaví/zápatí z předchozí sekce do zadané sekce.
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

tomto tutoriálu jsme probrali základy práce se záhlavím a zápatím v Aspose.Words pro Javu. Naučili jste se vytvářet, upravovat a upravovat záhlaví a zápatí a také další základní techniky formátování dokumentů.

 Další podrobnosti a pokročilé funkce naleznete v části[Aspose.Words Java dokumentace](https://reference.aspose.com/words/java/).

## Nejčastější dotazy

### 1. Jak mohu přidat čísla stránek do zápatí mého dokumentu?
 Čísla stránek můžete přidat vložením`PAGE` pole do zápatí pomocí Aspose.Words.

### 2. Je Aspose.Words kompatibilní s vývojovými prostředími Java?
Ano, Aspose.Words poskytuje podporu pro vývoj Java. Ujistěte se, že máte na místě potřebné nastavení.

### 3. Mohu přizpůsobit písmo a styl záhlaví a zápatí?
Rozhodně si můžete přizpůsobit písma, zarovnání a další styly, aby vaše záhlaví a zápatí byly vizuálně přitažlivé.

### 4. Je možné mít různá záhlaví pro liché a sudé stránky?
 Ano, můžete použít`PageSetup.OddAndEvenPagesHeaderFooter` k určení různých záhlaví pro liché a sudé stránky.

### 5. Jak mohu začít s Aspose.Words for Java?
 Chcete-li začít, navštivte[Aspose.Words Java dokumentace](https://reference.aspose.com/words/java/) pro komplexní návod k používání API.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
