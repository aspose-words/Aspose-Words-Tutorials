---
title: Použití vodoznaků k dokumentům v Aspose.Words pro Java
linktitle: Použití vodoznaků na dokumenty
second_title: Aspose.Words Java Document Processing API
description: Naučte se přidávat vodoznaky do dokumentů v Aspose.Words for Java. Přizpůsobte textové a obrazové vodoznaky pro profesionálně vypadající dokumenty.
weight: 15
url: /cs/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití vodoznaků k dokumentům v Aspose.Words pro Java


## Úvod do přidávání vodoznaků do dokumentů v Aspose.Words pro Javu

tomto tutoriálu prozkoumáme, jak přidat vodoznaky do dokumentů pomocí Aspose.Words for Java API. Vodoznaky jsou užitečným způsobem, jak označit dokumenty textem nebo grafikou, která označí jejich stav, důvěrnost nebo jiné relevantní informace. V této příručce se budeme zabývat textovými i obrázkovými vodoznaky.

## Nastavení Aspose.Words pro Java

Než začneme přidávat vodoznaky do dokumentů, musíme nastavit Aspose.Words pro Javu. Chcete-li začít, postupujte takto:

1.  Stáhněte si Aspose.Words pro Java z[zde](https://releases.aspose.com/words/java/).
2. Přidejte knihovnu Aspose.Words for Java do svého projektu Java.
3. Importujte potřebné třídy do kódu Java.

Nyní, když máme knihovnu nastavenou, přistoupíme k přidání vodoznaků.

## Přidání textových vodoznaků

Textové vodoznaky jsou běžnou volbou, když chcete do dokumentů přidat textové informace. Zde je návod, jak můžete přidat textový vodoznak pomocí Aspose.Words pro Java:

```java
// Vytvořte instanci dokumentu
Document doc = new Document("Document.docx");

// Definujte možnosti TextWatermark
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//Nastavte text a možnosti vodoznaku
doc.getWatermark().setText("Test", options);

// Uložte dokument s vodoznakem
doc.save("DocumentWithWatermark.docx");
```

## Přidání vodoznaků obrázku

Kromě textových vodoznaků můžete do dokumentů přidat také obrázkové vodoznaky. Zde je návod, jak přidat vodoznak obrázku:

```java
// Vytvořte instanci dokumentu
Document doc = new Document("Document.docx");

// Načtěte obrázek pro vodoznak
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Nastavte velikost a polohu vodoznaku
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Přidejte vodoznak do dokumentu
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Uložte dokument s vodoznakem
doc.save("DocumentWithImageWatermark.docx");
```

## Přizpůsobení vodoznaků

Vodoznaky můžete přizpůsobit úpravou jejich vzhledu a polohy. U textových vodoznaků můžete změnit písmo, velikost, barvu a rozvržení. U obrazových vodoznaků můžete upravit jejich velikost a polohu, jak je ukázáno v předchozích příkladech.

## Odstranění vodoznaků

Chcete-li odstranit vodoznak z dokumentu, můžete použít následující kód:

```java
// Vytvořte instanci dokumentu
Document doc = new Document("DocumentWithWatermark.docx");

// Odstraňte vodoznak
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Uložte dokument bez vodoznaku
doc.save("DocumentWithoutWatermark.docx");
```


## Závěr

tomto tutoriálu jsme se naučili přidávat vodoznaky do dokumentů pomocí Aspose.Words for Java. Ať už potřebujete přidat textové nebo obrázkové vodoznaky, Aspose.Words poskytuje nástroje pro jejich efektivní přizpůsobení a správu. Vodoznaky můžete také odstranit, když už je nepotřebujete, čímž zajistíte, že vaše dokumenty budou čisté a profesionální.

## FAQ

### Jak mohu změnit písmo textového vodoznaku?

 Chcete-li změnit písmo textového vodoznaku, upravte`setFontFamily` nemovitost v`TextWatermarkOptions`. Například:

```java
options.setFontFamily("Times New Roman");
```

### Mohu přidat více vodoznaků do jednoho dokumentu?

 Ano, do dokumentu můžete přidat více vodoznaků vytvořením více`Shape` objekty s různým nastavením a jejich přidání do dokumentu.

### Je možné vodoznak otočit?

 Ano, vodoznak můžete otočit nastavením`setRotation` nemovitost v`Shape` objekt. Kladné hodnoty otáčejí vodoznak po směru hodinových ručiček a záporné hodnoty proti směru hodinových ručiček.

### Jak mohu udělat vodoznak poloprůhledný?

 Chcete-li, aby byl vodoznak poloprůhledný, nastavte`setSemitransparent`majetek do`true` v`TextWatermarkOptions`.

### Mohu přidat vodoznaky do určitých částí dokumentu?

Ano, vodoznaky můžete přidat do určitých částí dokumentu procházením částí a přidáním vodoznaku do požadovaných částí.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
