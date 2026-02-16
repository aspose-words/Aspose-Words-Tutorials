---
date: 2026-02-16
description: Naučte se, jak vytvořit textové pole, přidat vodoznakové slovo, seskupit
  více tvarů, nastavit poměr stran tvaru a umístit tvar do buňky tabulky pomocí Aspose.Words
  pro Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Jak vytvořit textové pole a použít tvary dokumentu v Aspose.Words pro Javu
url: /cs/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání tvarů dokumentu v Aspose.Words pro Java

## Úvod do používání tvarů dokumentu v Aspose.Words pro Java

V tomto komplexním průvodci **se naučíte, jak vytvořit text box** objekty a další výkonné tvary s Aspose.Words pro Java. Tvary vám umožní obohatit Word dokumenty o callouty, tlačítka, vodoznaky, SmartArt a další — čímž je učiníte vizuálně přitažlivými a interaktivními. Provedeme vás reálnými příklady, od vložení jednoduchého text boxu po seskupení více tvarů, nastavení poměru stran a umístění tvarů uvnitř buněk tabulky.

## Rychlé odpovědi
- **Jaký je hlavní způsob, jak přidat text box?** Use `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Mohu seskupit tvary dohromady?** Yes – create a `GroupShape` and append child shapes.
- **Jak zamknout nebo odemknout poměr stran tvaru?** Call `shape.setAspectRatioLocked(true/false)`.
- **Je možné přidat vodoznak pomocí tvaru?** Absolutely – insert a `Shape` with `TEXT_PLAIN_TEXT` and set its fill/stroke.
- **Fungují diagramy SmartArt s Aspose.Words?** Yes – detect with `shape.hasSmartArt()` and update via `shape.updateSmartArtDrawing()`.

## Co je text box a proč vytvářet tvary text boxu?

Text box je kontejner, který může obsahovat formátovaný text, obrázky nebo jiné tvary. Použití **create text box** ve vaší automatizaci vám umožní umístit plovoucí obsah kdekoli na stránce, ideální pro anotace, callouty nebo dekorativní prvky, aniž byste měnili hlavní tok dokumentu.

## Jak přidat tvar

Než se ponoříme do kódu, ujistěte se, že Aspose.Words pro Java je ve vašem projektu zahrnut. Pokud jste jej ještě nepřidali, stáhněte knihovnu z oficiálního webu:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Přidávání tvarů do dokumentů

## Jak seskupit více tvarů

`GroupShape` vám umožní zacházet s několika jednotlivými tvary jako s jednou jednotkou — užitečné pro jejich společný přesun nebo otáčení.

### Vkládání GroupShape

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

## Jak vytvořit text box (create text box)

### Vkládání tvaru Text Box

Metoda `insertShape` usnadňuje přidání text boxu. Níže uvedený příklad ukazuje dva způsoby, jak umístit a otočit text box.

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

## Jak nastavit poměr stran tvaru

### Správa poměru stran

Někdy potřebujete, aby se tvar roztáhl bez zachování původních proporcí. Následující úryvek ukazuje odemknutí poměru stran obrázkového tvaru.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Jak umístit tvar do buňky tabulky

### Umístění tvaru uvnitř buňky tabulky

Níže je krok‑za‑krokem příklad, který vytvoří tabulku a poté vloží vodoznakový tvar, který je umístěn relativně k stránce, ale může být také umístěn uvnitř buňky.

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
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
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

## Práce se SmartArt tvary

### Detekce SmartArt tvarů

Můžete programově najít objekty SmartArt v dokumentu pomocí metody `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aktualizace SmartArt výkresů

Jakmile lokalizujete SmartArt tvary, můžete obnovit jejich vnitřní výkresová data pomocí `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Závěr

V tomto průvodci jsme pokryli, jak **create text box** objekty, seskupovat více tvarů, upravovat poměr stran, vkládat tvary do buněk tabulky, přidávat vodoznaky a pracovat s diagramy SmartArt pomocí Aspose.Words pro Java. Tyto techniky vám umožní programově vytvářet bohatě formátované, interaktivní Word dokumenty.

## Často kladené otázky

### Co je Aspose.Words pro Java?

Aspose.Words pro Java je Java knihovna, která vývojářům umožňuje programově vytvářet, upravovat a konvertovat Word dokumenty. Poskytuje širokou škálu funkcí a nástrojů pro práci s dokumenty v různých formátech.

### Jak mohu stáhnout Aspose.Words pro Java?

Můžete stáhnout Aspose.Words pro Java z webu Aspose pomocí tohoto odkazu: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Jaké jsou výhody používání tvarů dokumentu?

Tvary dokumentu přidávají vizuální prvky a interaktivitu vašim dokumentům, čímž je činí poutavějšími a informativnějšími. S tvary můžete vytvářet callouty, tlačítka, obrázky, vodoznaky a další, což zlepšuje celkový uživatelský zážitek.

### Mohu přizpůsobit vzhled tvarů?

Ano, můžete přizpůsobit vzhled tvarů úpravou jejich vlastností, jako jsou velikost, pozice, rotace a barva výplně. Aspose.Words pro Java poskytuje rozsáhlé možnosti pro přizpůsobení tvarů.

### Je Aspose.Words pro Java kompatibilní se SmartArt?

Ano, Aspose.Words pro Java podporuje SmartArt tvary, což vám umožní pracovat s komplexními diagramy a grafikou ve vašich dokumentech.

## Často kladené otázky

**Q: Mohu kombinovat text box s obrázkem uvnitř stejného tvaru?**  
A: Ano. Vložte obrázek do text boxu pomocí `builder.insertImage()` po vytvoření tvaru a poté upravte jeho rozložení podle potřeby.

**Q: Jak zajistím, aby se vodoznak zobrazoval za veškerým obsahem dokumentu?**  
A: Nastavte tvaru `WrapType` na `NONE` a upravte jeho `RelativeHorizontalPosition` a `RelativeVerticalPosition` na `PAGE`. Tím se vodoznak umístí za hlavní tok.

**Q: Je možné animovat seskupený tvar ve Wordu?**  
A: Přestože Aspose.Words může vytvářet a seskupovat tvary, animační funkce nejsou podporovány, protože závisí na UI možnostech Wordu.

**Q: Jaká verze Aspose.Words je vyžadována pro podporu SmartArt?**  
A: Detekce a aktualizace SmartArt jsou k dispozici od Aspose.Words 20.9 pro Java a novějších.

**Q: Zvládá knihovna efektivně velké dokumenty s mnoha tvary?**  
A: Ano. Použijte `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` nebo vyšší pro zlepšení výkonu u dokumentů s mnoha tvary.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}