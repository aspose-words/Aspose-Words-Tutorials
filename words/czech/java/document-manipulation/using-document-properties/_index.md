---
title: Použití vlastností dokumentu v Aspose.Words pro Javu
linktitle: Použití vlastností dokumentu
second_title: Aspose.Words Java Document Processing API
description: Optimalizujte správu dokumentů pomocí Aspose.Words pro Java. Naučte se pracovat s vlastnostmi dokumentu, přidávat vlastní metadata a další v tomto komplexním kurzu.
weight: 32
url: /cs/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití vlastností dokumentu v Aspose.Words pro Javu


## Úvod do vlastností dokumentu

Vlastnosti dokumentu jsou důležitou součástí každého dokumentu. Poskytují další informace o dokumentu samotném, jako je jeho název, autor, předmět, klíčová slova a další. V Aspose.Words for Java můžete manipulovat s vestavěnými i uživatelskými vlastnostmi dokumentu.

## Výčet vlastností dokumentu

### Vestavěné vlastnosti

Chcete-li načíst integrované vlastnosti dokumentu a pracovat s nimi, můžete použít následující fragment kódu:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

Tento kód zobrazí název dokumentu a vestavěné vlastnosti, včetně vlastností jako „Název“, „Autor“ a „Klíčová slova“.

### Uživatelské vlastnosti

Chcete-li pracovat s vlastními vlastnostmi dokumentu, můžete použít následující fragment kódu:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

Tento fragment kódu ukazuje, jak přidat vlastní vlastnosti dokumentu, včetně booleovské hodnoty, řetězce, data, čísla revize a číselné hodnoty.

## Odebrání vlastností dokumentu

Chcete-li odebrat konkrétní vlastnosti dokumentu, můžete použít následující kód:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Tento kód odebere z dokumentu uživatelskou vlastnost "Authorized Date".

## Konfigurace odkazu na obsah

V některých případech můžete chtít v dokumentu vytvořit odkazy. Můžete to udělat takto:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Přidat propojené s vlastností obsahu.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Tento fragment kódu ukazuje, jak vytvořit záložku v dokumentu a přidat vlastní vlastnost dokumentu, která odkazuje na tuto záložku.

## Převod mezi měrnými jednotkami

V Aspose.Words for Java můžete snadno převádět měrné jednotky. Zde je příklad, jak na to:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Nastavte okraje v palcích.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Tento fragment kódu nastavuje různé okraje a vzdálenosti v palcích jejich převodem na body.

## Použití řídicích znaků

Řídicí znaky mohou být užitečné při práci s textem. Zde je návod, jak nahradit řídicí znak v textu:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Nahraďte řídicí znak "\r" znakem "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

V tomto příkladu nahradíme návrat vozíku (`\r`) s návratem vozíku následovaným posunem řádku (`\r\n`).

## Závěr

Vlastnosti dokumentu hrají významnou roli při efektivní správě a organizaci vašich dokumentů v Aspose.Words for Java. Ať už se jedná o práci s vestavěnými vlastnostmi, uživatelskými vlastnostmi nebo používání řídicích znaků, máte k dispozici řadu nástrojů pro vylepšení možností správy dokumentů.

## FAQ

### Jak získám přístup k integrovaným vlastnostem dokumentu?

 Pro přístup k vestavěným vlastnostem dokumentu v Aspose.Words for Java můžete použít`getBuiltInDocumentProperties` metoda na`Document` objekt. Tato metoda vrací kolekci vestavěných vlastností, kterými můžete iterovat.

### Mohu do dokumentu přidat vlastní vlastnosti dokumentu?

 Ano, můžete do dokumentu přidat vlastní vlastnosti dokumentu pomocí`CustomDocumentProperties` sbírka. Uživatelské vlastnosti můžete definovat s různými datovými typy, včetně řetězců, booleovských hodnot, dat a číselných hodnot.

### Jak mohu odebrat konkrétní vlastnost vlastního dokumentu?

 Chcete-li odebrat konkrétní vlastnost vlastního dokumentu, můžete použít`remove` metoda na`CustomDocumentProperties`kolekce, předáním názvu vlastnosti, kterou chcete odstranit, jako parametru.

### Jaký je účel odkazování na obsah v dokumentu?

Propojení s obsahem v dokumentu umožňuje vytvářet dynamické odkazy na konkrétní části dokumentu. To může být užitečné pro vytváření interaktivních dokumentů nebo křížových odkazů mezi sekcemi.

### Jak mohu převádět mezi různými měrnými jednotkami v Aspose.Words pro Java?

 Můžete převádět mezi různými měrnými jednotkami v Aspose.Words pro Java pomocí`ConvertUtil` třída. Poskytuje metody pro převod jednotek, jako jsou palce na body, body na centimetry a další.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
