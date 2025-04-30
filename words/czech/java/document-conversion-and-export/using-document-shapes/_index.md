---
"description": "Odemkněte sílu tvarů dokumentů v Aspose.Words pro Javu. Naučte se vytvářet vizuálně poutavé dokumenty s podrobnými příklady."
"linktitle": "Používání tvarů dokumentu"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Použití tvarů dokumentů v Aspose.Words pro Javu"
"url": "/cs/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Použití tvarů dokumentů v Aspose.Words pro Javu


## Úvod do používání tvarů dokumentů v Aspose.Words pro Javu

této komplexní příručce se ponoříme do světa tvarů dokumentů v Aspose.Words pro Javu. Tvary jsou základními prvky, pokud jde o vytváření vizuálně přitažlivých a interaktivních dokumentů. Ať už potřebujete přidat popisky, tlačítka, obrázky nebo vodoznaky, Aspose.Words pro Javu poskytuje nástroje, které to udělají efektivně. Pojďme se krok za krokem podívat na to, jak tyto tvary používat, s příklady zdrojového kódu.

## Začínáme s tvary dokumentů

Než se pustíme do kódu, nastavme si naše prostředí. Ujistěte se, že máte ve svém projektu integrovaný Aspose.Words pro Javu. Pokud tak ještě neučiníte, můžete si ho stáhnout z webových stránek Aspose. [Stáhněte si Aspose.Words pro Javu](https://releases.aspose.com/words/java/)

## Přidávání tvarů do dokumentů

### Vložení skupinového tvaru

A `GroupShape` umožňuje seskupit více tvarů dohromady. Zde je návod, jak vytvořit a vložit `GroupShape`:

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

Chcete-li vložit tvar textového pole, můžete použít `insertShape` metodu, jak je znázorněno v níže uvedeném příkladu:

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

Můžete ovládat, zda je poměr stran tvaru uzamčen, či nikoli. Zde je návod, jak poměr stran tvaru odemknout:

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
watermark.isLayoutInCell(true); // Pokud bude tvar umístěn do buňky, zobrazí se mimo buňku tabulky.
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

Tvary SmartArt v dokumentu můžete detekovat pomocí následujícího kódu:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aktualizace kreseb SmartArt

Chcete-li aktualizovat kresby SmartArt v dokumentu, použijte následující kód:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Závěr

V této příručce jsme prozkoumali svět tvarů dokumentů v Aspose.Words pro Javu. Naučili jste se, jak do dokumentů přidávat různé tvary, manipulovat s jejich vlastnostmi a pracovat s tvary SmartArt. S těmito znalostmi můžete snadno vytvářet vizuálně přitažlivé a interaktivní dokumenty.

## Často kladené otázky

### Co je Aspose.Words pro Javu?

Aspose.Words pro Javu je knihovna v Javě, která umožňuje vývojářům programově vytvářet, upravovat a převádět dokumenty Wordu. Poskytuje širokou škálu funkcí a nástrojů pro práci s dokumenty v různých formátech.

### Jak si mohu stáhnout Aspose.Words pro Javu?

Aspose.Words pro Javu si můžete stáhnout z webových stránek Aspose pomocí tohoto odkazu: [Stáhněte si Aspose.Words pro Javu](https://releases.aspose.com/words/java/)

### Jaké jsou výhody používání tvarů dokumentů?

Tvary dokumentů přidávají do dokumentů vizuální prvky a interaktivitu, díky čemuž jsou poutavější a informativnější. Pomocí tvarů můžete vytvářet popisky, tlačítka, obrázky, vodoznaky a další prvky, což vylepšuje celkový uživatelský zážitek.

### Mohu si přizpůsobit vzhled tvarů?

Ano, vzhled tvarů si můžete přizpůsobit úpravou jejich vlastností, jako je velikost, poloha, otočení a barva výplně. Aspose.Words pro Javu nabízí rozsáhlé možnosti pro přizpůsobení tvarů.

### Je Aspose.Words pro Javu kompatibilní se SmartArt?

Ano, Aspose.Words pro Javu podporuje tvary SmartArt, což vám umožňuje pracovat se složitými diagramy a grafikou v dokumentech.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}