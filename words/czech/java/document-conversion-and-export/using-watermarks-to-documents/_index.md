---
"description": "Naučte se, jak přidávat vodoznaky do dokumentů v Aspose.Words pro Javu. Přizpůsobte si textové a obrazové vodoznaky pro profesionálně vypadající dokumenty."
"linktitle": "Použití vodoznaků v dokumentech"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Použití vodoznaků v dokumentech v Aspose.Words pro Javu"
"url": "/cs/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Použití vodoznaků v dokumentech v Aspose.Words pro Javu


## Úvod do přidávání vodoznaků do dokumentů v Aspose.Words pro Javu

V tomto tutoriálu se podíváme na to, jak přidávat vodoznaky do dokumentů pomocí rozhraní Aspose.Words pro Java API. Vodoznaky jsou užitečným způsobem, jak označit dokumenty textem nebo grafikou, a tím uvést jejich stav, důvěrnost nebo jiné relevantní informace. V této příručce se budeme zabývat textovými i obrazovými vodoznaky.

## Nastavení Aspose.Words pro Javu

Než začneme s přidáváním vodoznaků do dokumentů, musíme si nastavit Aspose.Words pro Javu. Začněte takto:

1. Stáhněte si Aspose.Words pro Javu z [zde](https://releases.aspose.com/words/java/).
2. Přidejte do svého projektu v Javě knihovnu Aspose.Words for Java.
3. Importujte potřebné třídy do kódu Java.

Nyní, když máme knihovnu nastavenou, pojďme přidat vodoznaky.

## Přidávání textových vodoznaků

Textové vodoznaky jsou běžnou volbou, když chcete do dokumentů přidat textové informace. Zde je návod, jak přidat textový vodoznak pomocí Aspose.Words pro Javu:

```java
// Vytvoření instance dokumentu
Document doc = new Document("Document.docx");

// Definovat možnosti textového vodoznaku
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Nastavení textu a možností vodoznaku
doc.getWatermark().setText("Test", options);

// Uložte dokument s vodoznakem
doc.save("DocumentWithWatermark.docx");
```

## Přidávání vodoznaků do obrázků

Kromě textových vodoznaků můžete do dokumentů přidat také obrazové vodoznaky. Zde je návod, jak přidat obrazový vodoznak:

```java
// Vytvoření instance dokumentu
Document doc = new Document("Document.docx");

// Načtěte obrázek pro vodoznak
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Nastavení velikosti a umístění vodoznaku
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Přidání vodoznaku do dokumentu
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Uložte dokument s vodoznakem
doc.save("DocumentWithImageWatermark.docx");
```

## Přizpůsobení vodoznaků

Vodoznaky si můžete přizpůsobit úpravou jejich vzhledu a umístění. U textových vodoznaků můžete změnit písmo, velikost, barvu a rozvržení. U obrazových vodoznaků můžete upravit jejich velikost a umístění, jak je znázorněno v předchozích příkladech.

## Odstranění vodoznaků

Chcete-li z dokumentu odstranit vodoznaky, můžete použít následující kód:

```java
// Vytvoření instance dokumentu
Document doc = new Document("DocumentWithWatermark.docx");

// Odstranění vodoznaku
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Uložit dokument bez vodoznaku
doc.save("DocumentWithoutWatermark.docx");
```


## Závěr

V tomto tutoriálu jsme se naučili, jak přidávat vodoznaky do dokumentů pomocí Aspose.Words pro Javu. Ať už potřebujete přidat textové nebo obrazové vodoznaky, Aspose.Words poskytuje nástroje pro jejich efektivní přizpůsobení a správu. Vodoznaky můžete také odstranit, když již nejsou potřeba, a zajistit tak, aby vaše dokumenty byly čisté a profesionální.

## Často kladené otázky

### Jak mohu změnit písmo textového vodoznaku?

Chcete-li změnit písmo textového vodoznaku, upravte `setFontFamily` nemovitost v `TextWatermarkOptions`Například:

```java
options.setFontFamily("Times New Roman");
```

### Mohu do jednoho dokumentu přidat více vodoznaků?

Ano, do dokumentu můžete přidat více vodoznaků vytvořením několika `Shape` objekty s různým nastavením a jejich přidání do dokumentu.

### Je možné otočit vodoznak?

Ano, vodoznak můžete otočit nastavením `setRotation` nemovitost v `Shape` objektu. Kladné hodnoty otáčejí vodoznak ve směru hodinových ručiček a záporné hodnoty proti směru hodinových ručiček.

### Jak mohu vodoznak udělat poloprůhledným?

Chcete-li vodoznak nastavit jako poloprůhledný, nastavte `setSemitransparent` majetek `true` v `TextWatermarkOptions`.

### Mohu přidat vodoznaky do konkrétních částí dokumentu?

Ano, vodoznaky můžete přidat do konkrétních částí dokumentu tak, že je budete procházet a vodoznak přidáte do požadovaných částí.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}