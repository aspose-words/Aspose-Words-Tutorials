---
title: Použití tvarů dokumentu v Aspose.Words pro Java
linktitle: Použití tvarů dokumentu
second_title: Aspose.Words Java Document Processing API
description: Odemkněte sílu tvarů dokumentů v Aspose.Words pro Java. Naučte se vytvářet vizuálně poutavé dokumenty pomocí příkladů krok za krokem.
weight: 14
url: /cs/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití tvarů dokumentu v Aspose.Words pro Java


## Úvod do používání tvarů dokumentů v Aspose.Words pro Javu

tomto komplexním průvodci se ponoříme do světa tvarů dokumentů v Aspose.Words for Java. Tvary jsou základními prvky, pokud jde o vytváření vizuálně přitažlivých a interaktivních dokumentů. Ať už potřebujete přidat popisky, tlačítka, obrázky nebo vodoznaky, Aspose.Words pro Java poskytuje nástroje, jak to udělat efektivně. Pojďme prozkoumat, jak tyto tvary používat krok za krokem s příklady zdrojového kódu.

## Začínáme s tvary dokumentů

 Než se pustíme do kódu, nastavíme naše prostředí. Ujistěte se, že máte Aspose.Words for Java integrovanou do vašeho projektu. Pokud jste tak ještě neučinili, můžete si jej stáhnout z webu Aspose[Stáhněte si Aspose.Words pro Java](https://releases.aspose.com/words/java/)

## Přidávání tvarů do dokumentů

### Vložení GroupShape

 A`GroupShape` umožňuje seskupit více tvarů dohromady. Zde je návod, jak můžete vytvořit a vložit a`GroupShape`:

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

### Vložení tvaru textového pole

 Chcete-li vložit tvar textového pole, můžete použít`insertShape` metoda, jak je ukázáno v příkladu níže:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Manipulace s vlastnostmi tvaru

### Správa poměru stran

Můžete ovládat, zda je poměr stran tvaru uzamčen nebo ne. Zde je návod, jak odemknout poměr stran tvaru:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Umístění tvaru do buňky tabulky

Pokud potřebujete umístit tvar do buňky tabulky, můžete toho dosáhnout pomocí následujícího kódu:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Zobrazte tvar mimo buňku tabulky, pokud bude umístěn do buňky.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Práce s tvary SmartArt

### Detekce tvarů SmartArt

Obrazce SmartArt v dokumentu můžete rozpoznat pomocí následujícího kódu:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aktualizace kreseb SmartArt

Chcete-li aktualizovat výkresy SmartArt v dokumentu, použijte následující kód:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Závěr

V této příručce jsme prozkoumali svět tvarů dokumentů v Aspose.Words pro Java. Naučili jste se přidávat do dokumentů různé tvary, manipulovat s jejich vlastnostmi a pracovat s tvary SmartArt. S těmito znalostmi můžete snadno vytvářet vizuálně přitažlivé a interaktivní dokumenty.

## FAQ

### Co je Aspose.Words for Java?

Aspose.Words for Java je knihovna Java, která umožňuje vývojářům vytvářet, upravovat a převádět dokumenty aplikace Word programově. Poskytuje širokou škálu funkcí a nástrojů pro práci s dokumenty v různých formátech.

### Jak si mohu stáhnout Aspose.Words pro Java?

 Aspose.Words for Java si můžete stáhnout z webu Aspose kliknutím na tento odkaz:[Stáhněte si Aspose.Words pro Java](https://releases.aspose.com/words/java/)

### Jaké jsou výhody používání tvarů dokumentů?

Tvary dokumentů dodávají vašim dokumentům vizuální prvky a interaktivitu, díky čemuž jsou poutavější a informativnější. Pomocí tvarů můžete vytvářet popisky, tlačítka, obrázky, vodoznaky a další, čímž vylepšíte celkový uživatelský dojem.

### Mohu přizpůsobit vzhled tvarů?

Ano, vzhled tvarů můžete přizpůsobit úpravou jejich vlastností, jako je velikost, poloha, otočení a barva výplně. Aspose.Words for Java poskytuje rozsáhlé možnosti přizpůsobení tvaru.

### Je Aspose.Words for Java kompatibilní se SmartArt?

Ano, Aspose.Words for Java podporuje tvary SmartArt, což vám umožňuje pracovat se složitými diagramy a grafikou ve vašich dokumentech.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
