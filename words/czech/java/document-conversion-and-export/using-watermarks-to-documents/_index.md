---
date: 2025-12-18
description: Naučte se, jak přidat vodoznak do dokumentů pomocí Aspose.Words pro Javu,
  včetně příkladu vodoznaku s obrázkem, změny barvy vodoznaku, nastavení průhlednosti
  vodoznaku a odstranění vodoznaku z dokumentu.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Jak přidat vodoznak do dokumentů pomocí Aspose.Words pro Javu
url: /cs/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat vodoznak do dokumentů pomocí Aspose.Words pro Java

## Úvod do přidávání vodoznaků do dokumentů v Aspose.Words pro Java

V tomto tutoriálu se naučíte **jak přidat vodoznak** do dokumentů Word pomocí Aspose.Words pro Java. Vodoznaky jsou rychlý způsob, jak označit soubor jako důvěrný, koncept nebo schválený, a mohou být textové i obrázkové. Provedeme vás nastavením knihovny, vytvořením textových a obrázkových vodoznaků, úpravou jejich vzhledu (včetně změny barvy vodoznaku a nastavení průhlednosti) a dokonce i odstraněním vodoznaku z dokumentu, když již není potřeba.

## Rychlé odpovědi
- **Co je vodoznak?** Poloprůhledná vrstva (text nebo obrázek), která se zobrazuje za hlavním obsahem dokumentu.  
- **Mohu přidat více vodoznaků?** Ano – vytvořte několik objektů `Shape` a přidejte je do požadovaných sekcí.  
- **Jak změním barvu vodoznaku?** Upravením vlastnosti `Color` v `TextWatermarkOptions`.  
- **Existuje příklad obrázkového vodoznaku?** Viz sekce „Přidání obrázkových vodoznaků“ níže.  
- **Potřebuji licenci k odstranění vodoznaku?** Pro produkční použití je vyžadována platná licence Aspose.Words.

## Nastavení Aspose.Words pro Java

Než začneme přidávat vodoznaky do dokumentů, musíme nastavit Aspose.Words pro Java. Postupujte podle následujících kroků:

1. Stáhněte si Aspose.Words pro Java z [zde](https://releases.aspose.com/words/java/).  
2. Přidejte knihovnu Aspose.Words pro Java do svého Java projektu.  
3. Naimportujte potřebné třídy ve svém Java kódu.

Nyní, když máme knihovnu nastavenou, pojďme se ponořit do samotného vytváření vodoznaku.

## Přidání textových vodoznaků

Textové vodoznaky jsou běžnou volbou, když chcete do dokumentu přidat textovou informaci. Zde je návod, jak přidat textový vodoznak pomocí Aspose.Words pro Java:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Proč je to důležité:** Úpravou `setFontFamily`, `setFontSize` a `setColor` můžete **změnit barvu vodoznaku** tak, aby odpovídala vaší značce, a `setSemitransparent(true)` vám umožní **nastavit průhlednost vodoznaku** pro jemný efekt.

## Přidání obrázkových vodoznaků

Kromě textových vodoznaků můžete do svých dokumentů také přidat obrázkové vodoznaky. Níže je **příklad obrázkového vodoznaku**, který ukazuje, jak vložit PNG logo nebo razítko:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Tento blok můžete opakovat s různými obrázky nebo pozicemi a **přidat tak více vodoznaků** do jednoho souboru.

## Přizpůsobení vodoznaků

Vodoznaky můžete přizpůsobit úpravou jejich vzhledu a umístění. U textových vodoznaků můžete měnit písmo, velikost, barvu a rozvržení. U obrázkových vodoznaků můžete měnit velikost, rotaci a zarovnání, jak bylo ukázáno v předchozích příkladech.

## Odstranění vodoznaků

Pokud potřebujete **odstranit vodoznak** z dokumentu, následující kód prochází všechny tvary a maže ty, které jsou identifikovány jako vodoznaky:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Běžné scénáře použití a tipy

- **Důvěrné koncepty:** Použijte poloprůhledný textový vodoznak jako „CONFIDENTIAL“.  
- **Branding:** Použijte obrázkový vodoznak obsahující logo vaší společnosti.  
- **Vodoznaky specifické pro sekce:** Procházejte `doc.getSections()` a přidejte vodoznak jen do vybraných sekcí.  
- **Tip pro výkon:** Při aplikaci stejného vodoznaku na mnoho dokumentů znovu použijte stejnou instanci `TextWatermarkOptions`.

## Často kladené otázky

### Jak mohu změnit písmo textového vodoznaku?

Pro změnu písma textového vodoznaku upravte vlastnost `setFontFamily` v `TextWatermarkOptions`. Například:

```java
options.setFontFamily("Times New Roman");
```

### Mohu přidat více vodoznaků do jednoho dokumentu?

Ano, můžete přidat více vodoznaků do dokumentu vytvořením několika objektů `Shape` s různými nastaveními a jejich přidáním do dokumentu.

### Je možné vodoznak otočit?

Ano, vodoznak můžete otočit nastavením vlastnosti `setRotation` v objektu `Shape`. Kladné hodnoty otáčejí vodoznak po směru hodinových ručiček, záporné hodnoty proti směru hodinových ručiček.

### Jak mohu udělat vodoznak poloprůhledný?

Pro nastavení poloprůhlednosti vodoznaku nastavte vlastnost `setSemitransparent` na `true` v `TextWatermarkOptions`.

### Mohu přidat vodoznaky do konkrétních sekcí dokumentu?

Ano, můžete přidat vodoznaky do konkrétních sekcí dokumentu tím, že projdete sekce a vodoznak přidáte do požadovaných sekcí.

---

**Poslední aktualizace:** 2025-12-18  
**Testováno s:** Aspose.Words pro Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}