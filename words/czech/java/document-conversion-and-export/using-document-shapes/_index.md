---
date: 2025-12-14
description: Naučte se, jak **vložit obrázkový tvar** pomocí Aspose.Words pro Javu.
  Tento průvodce vám ukáže, jak přidávat tvary, vytvářet tvary textových polí, umisťovat
  tvary do tabulek, nastavit poměr stran tvaru a přidávat bublinové tvary.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Používání tvarů dokumentu v Aspose.Words pro Javu
url: /cs/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak **vložit tvar obrázku** s Aspose.Words for Java

V tomto komplexním tutoriálu se dozvíte, jak **vložit tvar obrázku** do dokumentů Word pomocí Aspose.Words for Java. Ať už vytváříte zprávy, marketingové materiály nebo interaktivní formuláře, tvary vám umožní přidat popisky, tlačítka, textová pole, vodoznaky a dokonce i SmartArt. Provedeme vás každým krokem, vysvětlíme, proč použít konkrétní tvar, a poskytneme připravené ukázky kódu.

## Rychlé odpovědi
- **Jaký je hlavní způsob přidání tvaru?** Použijte `DocumentBuilder.insertShape` nebo vytvořte instanci `Shape` a přidejte ji do stromu dokumentu.  
- **Mohu vložit obrázek jako tvar?** Ano – zavolejte `builder.insertImage` a poté zacházejte s vráceným `Shape` jako s jakýmkoli jiným.  
- **Jak zachovat poměr stran tvaru?** Nastavte `shape.setAspectRatioLocked(true)` nebo `false` podle vašich potřeb.  
- **Je možné seskupit tvary?** Rozhodně – zabalte je do `GroupShape` a vložte skupinu jako jediný uzel.  
- **Fungují diagramy SmartArt s Aspose.Words?** Ano, můžete programově detekovat a aktualizovat SmartArt tvary.

## Co je **vložit tvar obrázku**?
*Obrázkový tvar* je vizuální prvek, který obsahuje rastrovou nebo vektorovou grafiku uvnitř dokumentu Word. V Aspose.Words je obrázek reprezentován objektem `Shape`, který vám poskytuje plnou kontrolu nad velikostí, umístěním, rotací a obtékáním.

## Proč používat tvary ve vašich dokumentech?
- **Viz​uální dopad:** Tvary přitahují pozornost k důležitým informacím.  
- **Interaktivita:** Tlačítka a popisky mohou být propojeny s URL nebo záložkami.  
- **Flexibilita rozvržení:** Umístěte grafiku přesně pomocí absolutních nebo relativních souřadnic.  
- **Automatizace:** Generujte složité rozvržení bez ruční úpravy.

## Předpoklady
- Java Development Kit (JDK 8 nebo vyšší)  
- Knihovna Aspose.Words for Java (stáhněte z oficiálního webu)  
- Základní znalost Javy a objektově orientovaného programování  

Knihovnu můžete stáhnout zde: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Jak **přidat tvar** – Vkládání GroupShape
`GroupShape` vám umožní zacházet s několika tvary jako s jednou jednotkou. To je užitečné pro přesouvání nebo formátování více prvků najednou.

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

## Vytvořit **tvar textového pole**
Textové pole je kontejner, který může obsahovat formátovaný text. Můžete jej také otočit pro dynamický vzhled.

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

## Nastavit **poměr stran tvaru**
Někdy potřebujete, aby se tvar volně roztahoval, jindy chcete zachovat jeho původní proporce. Ovládání poměru stran je jednoduché.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Umístit **tvar do tabulky**
Vložení tvaru do buňky tabulky může být užitečné pro rozvržení zpráv. Níže uvedený příklad vytvoří tabulku a poté vloží tvar ve stylu vodoznaku, který přesahuje celou stránku.

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

## Přidat **popiskový tvar**
Popiskový tvar je ideální pro zvýraznění poznámek nebo varování. Zatímco výše uvedený kód již ukazuje `ACCENT_BORDER_CALLOUT_1`, můžete vyměnit `ShapeType` za libovolnou variantu popisku, která vyhovuje vašemu designu.

## Práce se SmartArt tvary

### Detekce SmartArt tvarů
Diagramy SmartArt lze programově identifikovat, což vám umožní je zpracovat nebo nahradit podle potřeby.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aktualizace SmartArt výkresů
Po detekci můžete obnovit grafiku SmartArt tak, aby odrážela jakékoli změny dat.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Časté problémy a tipy
- **Tvar se nezobrazuje:** Ujistěte se, že je tvar vložen po cílovém uzlu pomocí `builder.insertNode`.  
- **Neočekávaná rotace:** Pamatujte, že rotace se aplikuje kolem středu tvaru; v případě potřeby upravte `setLeft`/`setTop`.  
- **Poměr stran uzamčen:** Ve výchozím nastavení mnoho tvarů uzamkne svůj poměr stran; zavolejte `setAspectRatioLocked(false)`, abyste je mohli volně roztáhnout.  
- **Detekce SmartArt selže:** Ověřte, že používáte verzi Aspose.Words, která podporuje SmartArt (v24+).

## Často kladené otázky

**Q: Co je Aspose.Words for Java?**  
A: Aspose.Words for Java je Java knihovna, která vývojářům umožňuje programově vytvářet, upravovat a konvertovat Word dokumenty. Poskytuje širokou škálu funkcí a nástrojů pro práci s dokumenty v různých formátech.

**Q: Jak mohu stáhnout Aspose.Words for Java?**  
A: Aspose.Words for Java můžete stáhnout z webu Aspose pomocí tohoto odkazu: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: Jaké jsou výhody používání tvarů v dokumentech?**  
A: Tvary v dokumentech přidávají vizuální prvky a interaktivitu, což je činí poutavějšími a informativnějšími. Pomocí tvarů můžete vytvářet popisky, tlačítka, obrázky, vodoznaky a další, čímž zlepšujete celkový uživatelský zážitek.

**Q: Mohu přizpůsobit vzhled tvarů?**  
A: Ano, vzhled tvarů můžete přizpůsobit úpravou jejich vlastností, jako jsou velikost, umístění, rotace a barva výplně. Aspose.Words for Java poskytuje rozsáhlé možnosti pro přizpůsobení tvarů.

**Q: Je Aspose.Words for Java kompatibilní se SmartArt?**  
A: Ano, Aspose.Words for Java podporuje SmartArt tvary, což vám umožní pracovat s komplexními diagramy a grafikou ve vašich dokumentech.

---

**Poslední aktualizace:** 2025-12-14  
**Testováno s:** Aspose.Words for Java 24.12 (nejnovější)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}