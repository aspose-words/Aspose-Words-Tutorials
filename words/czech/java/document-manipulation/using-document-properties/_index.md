---
"description": "Optimalizujte správu dokumentů s Aspose.Words pro Javu. V tomto komplexním tutoriálu se naučte pracovat s vlastnostmi dokumentu, přidávat vlastní metadata a další."
"linktitle": "Použití vlastností dokumentu"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Použití vlastností dokumentu v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Použití vlastností dokumentu v Aspose.Words pro Javu


## Úvod do vlastností dokumentu

Vlastnosti dokumentu jsou důležitou součástí každého dokumentu. Poskytují další informace o samotném dokumentu, jako je jeho název, autor, předmět, klíčová slova a další. V Aspose.Words pro Javu můžete manipulovat s vestavěnými i vlastními vlastnostmi dokumentu.

## Výčet vlastností dokumentu

### Vestavěné vlastnosti

Pro načtení a práci s vestavěnými vlastnostmi dokumentu můžete použít následující úryvek kódu:

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

Tento kód zobrazí název dokumentu a jeho vestavěné vlastnosti, včetně vlastností jako „Název“, „Autor“ a „Klíčová slova“.

### Vlastnosti uživatele

Pro práci s vlastními vlastnostmi dokumentu můžete použít následující úryvek kódu:

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

Tento úryvek kódu ukazuje, jak přidat vlastní vlastnosti dokumentu, včetně booleovské hodnoty, řetězce, data, čísla revize a číselné hodnoty.

## Odebrání vlastností dokumentu

Chcete-li odebrat určité vlastnosti dokumentu, můžete použít následující kód:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Tento kód odstraní z dokumentu vlastní vlastnost „Datum autorizace“.

## Konfigurace odkazu na obsah

V některých případech můžete chtít v dokumentu vytvořit odkazy. Zde je návod, jak to udělat:

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

    // Přidat vlastnost odkazovanou na obsah.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Tento úryvek kódu ukazuje, jak vytvořit záložku v dokumentu a přidat vlastní vlastnost dokumentu, která na tuto záložku odkazuje.

## Převod mezi měrnými jednotkami

V Aspose.Words pro Javu můžete snadno převádět měrné jednotky. Zde je příklad, jak to udělat:

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

Tento úryvek kódu nastavuje různé okraje a vzdálenosti v palcích jejich převodem na body.

## Používání řídicích znaků

Řídicí znaky mohou být užitečné při práci s textem. Zde je návod, jak nahradit řídicí znak v textu:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Nahraďte řídicí znak „\r“ znakem „\r\n“.
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

V tomto příkladu nahradíme znak konce vozíku (`\r`) s návratem vozíku následovaným posunem řádku (`\r\n`).

## Závěr

Vlastnosti dokumentů hrají v Aspose.Words pro Javu významnou roli v efektivní správě a organizaci dokumentů. Ať už jde o práci s vestavěnými vlastnostmi, vlastními vlastnostmi nebo používání řídicích znaků, máte k dispozici řadu nástrojů pro vylepšení možností správy dokumentů.

## Často kladené otázky

### Jak získám přístup k vestavěným vlastnostem dokumentu?

Pro přístup k vestavěným vlastnostem dokumentu v Aspose.Words pro Javu můžete použít `getBuiltInDocumentProperties` metoda na `Document` objekt. Tato metoda vrací kolekci vestavěných vlastností, kterými můžete iterovat.

### Mohu do dokumentu přidat vlastní vlastnosti dokumentu?

Ano, do dokumentu můžete přidat vlastní vlastnosti pomocí `CustomDocumentProperties` kolekce. Můžete definovat vlastní vlastnosti s různými datovými typy, včetně řetězců, booleovských hodnot, dat a číselných hodnot.

### Jak mohu odebrat konkrétní vlastní vlastnost dokumentu?

Chcete-li odebrat konkrétní vlastní vlastnost dokumentu, můžete použít `remove` metoda na `CustomDocumentProperties` kolekce, kde jako parametr předáte název vlastnosti, kterou chcete odebrat.

### Jaký je účel odkazování na obsah v dokumentu?

Propojení s obsahem v dokumentu umožňuje vytvářet dynamické odkazy na konkrétní části dokumentu. To může být užitečné pro vytváření interaktivních dokumentů nebo křížových odkazů mezi sekcemi.

### Jak mohu v Aspose.Words pro Javu převádět mezi různými měrnými jednotkami?

V Aspose.Words pro Javu můžete převádět mezi různými měrnými jednotkami pomocí `ConvertUtil` třída. Poskytuje metody pro převod jednotek, jako jsou palce na body, body na centimetry a další.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}