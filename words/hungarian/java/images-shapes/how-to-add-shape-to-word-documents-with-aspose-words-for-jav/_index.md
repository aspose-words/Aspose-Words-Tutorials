---
category: general
date: 2026-11-22
description: Ismerje meg, hogyan adhat hozzá alakzatot a Word-hez az Aspose.Words
  for Java segítségével – szúrjon be egy téglalapot, és programozottan rejtse el.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: hu
lastmod: 2026-11-22
og_description: Adj hozzá alakzatot a Word-hez az Aspose.Words for Java segítségével.
  Ez az útmutató bemutatja, hogyan lehet beszúrni egy téglalapot, elrejteni az alakzatot,
  és menteni a dokumentumot.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Alakzat hozzáadása a Word-hez az Aspose.Words segítségével – Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Hogyan adhatunk hozzá alakzatot Word dokumentumokhoz az Aspose.Words for Java
  használatával
url: /hu/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adjon hozzá alakzatot Word dokumentumokhoz az Aspose.Words for Java segítségével

Ha programozott módon **alakzatot kell hozzáadnia Word** dokumentumokhoz, az Aspose.Words for Java egyszerűvé teszi ezt. Ebben az útmutatóban megtanulja, **hogyan szúrjon be alakzatot**, hogyan szabályozza annak láthatóságát, és **hogyan rejtsen el egy alakzatot**, hogy a végső fájl pontosan úgy nézzen ki, ahogy elvárja.

Egy teljes, futtatható példán keresztül vezetünk, amely betölt egy meglévő `.docx` fájlt, beszúr egy téglalapot, elrejti azt, és elmenti az eredményt. Nem szükséges külső szkript vagy manuális lépés, és az útmutató lefedi a gyakori változatokat, például egy új dokumentum létrehozását a semmiből vagy egy alakzat elrejtését csak nyomtatáskor.

## Előfeltételek

* Java 17 (vagy újabb) telepítve – a korábbi verziók is működnek, de a legújabb LTS jobb teljesítményt nyújt.  
* Maven 3.8+ a függőségkezeléshez.  
* Érvényes Aspose.Words for Java licenc (az ingyenes értékelő verzió tanuláshoz megfelelő).  
* A választott IDE vagy szövegszerkesztő (pl. IntelliJ IDEA, VS Code).

## 1. lépés: Aspose.Words hozzáadása Maven projektjéhez

Adja hozzá a következő függőséget a `pom.xml` fájlhoz. Ez letölti a legújabb stabil verziót (2026. november állapotában).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro tipp:** Használjon `<scope>provided</scope>` elemet, ha saját licencelési logikával szeretné szállítani a JAR-t.

## Alakzat hozzáadása Word-hez – a dokumentum inicializálása

Az első funkcionális lépés egy `Document` objektum beszerzése. Betölthet egy meglévő fájlt, vagy létrehozhat egy újat.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Miért fontos*: A `Document` osztály a belépési pont minden Word-manipulációhoz. Egy meglévő fájl betöltése megőrzi a stílusokat, fejléceket és lábléceket, míg egy új dokumentum tiszta lappal indul.

## Hogyan szúrjunk be alakzatot Word dokumentumba

Ezután hozzon létre egy `DocumentBuilder`‑t a dokumentum tartalmának módosításához. A builder módszereket biztosít szöveg, táblázat és **alakzatok** beszúrásához.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

Az `insertShape` hívás egy `Shape` objektumot ad vissza, amelyet tovább konfigurálhat (szín, keret, szöveg stb.). A méretek pontban vannak megadva (1 pt = 1/72 in).

*Miért használhat téglalapot*: A téglalapok a leggyakoribb tárolók megjegyzésekhez, vízjelekhez vagy helyőrzőkhöz. A `ShapeType.RECTANGLE` helyett használhatja a `ShapeType.ELLIPSE`, `ShapeType.LINE` stb. értékeket, hogy különböző vizuális igényeket elégítsen ki.

## Hogyan rejtsünk el alakzatot Word-ben

Néha szükség van arra, hogy egy alakzat létezzen a elrendezés számításaihoz, de ne jelenjen meg a végső megjelenítésben. Az Aspose.Words biztosítja a `setHidden(true)` metódust ennek eléréséhez.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

A rejtett jelző úgy működik, mint a **Hidden** formázási opció a Microsoft Wordben: az alakzat kimarad a vizuális elrendezésből, de továbbra is részt vesz a dokumentum objektummodelljében. Ez hasznos a következőkre:

* Metaadatok vagy jelölők tárolása, amelyeket az alkalmazása később olvas.  
* Helyőrzők létrehozása, amelyeket a közzététel előtt eltávolít.  
* Láthatóság szabályozása különböző kimeneti formátumoknál (pl. elrejtés HTML-ben, de megtartás PDF-ben).

> **Megjegyzés:** A rejtett alakzatok alapértelmezés szerint továbbra is exportálódnak PDF-be. Ha a PDF-ből is el szeretné őket távolítani, állítsa be a `rectangle.getWrapType( ) = WrapType.NONE` értéket, és ennek megfelelően módosítsa a `Hidden` tulajdonságot.

## 4. lépés: A módosított dokumentum mentése

Végül mentse el a változtatásokat egy új fájlba.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Amikor megnyitja a `output.docx` fájlt a Microsoft Wordben, a téglalap nem lesz látható, de a dokumentumfában továbbra is része marad. Programozottan ellenőrizheti a jelenlétét a fájl újratöltésével és a `Shape.isHidden()` ellenőrzésével.

### Várt kimenet

* A `output.docx` fájl látható alakzatok nélkül nyílik meg.  
* Ha az Aspose.Words segítségével vizsgálja a dokumentumot (pl. `doc.getChildNodes(NodeType.SHAPE, true).size()`), az alakzatszám **1** lesz, ami megerősíti, hogy az alakzat létezik, de rejtett.

## Haladó változatok és szélhelyzetek

### 1. Alakzat létrehozása egy új dokumentumban

Ha a semmiből kezdi, cserélje le a betöltő sort a következőre:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Az alakzat pontos elhelyezése

Alapértelmezés szerint az `insertShape` a jelenlegi kurzorpozícióba helyezi az alakzatot. Absólút elhelyezéshez:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Láthatóság szabályozása kimeneti formátumonként

Ha a alakzatnak láthatónak kell lennie a Word felhasználói felületén, de rejtettnek PDF exportáláskor, használja a `Shape.setWrapType(WrapType.NONE)`‑t a `Hidden` beállítással együtt:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Szöveg hozzáadása az alakzatba

Egy téglalap tartalmazhat szövegdobozt:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Ezután a szövegdobozt ugyanazzal a `setHidden(true)` hívással rejtheti el.

## Gyakori buktatók és elkerülésük módja

| Tünet | Ok | Megoldás |
|-------|----|----------|
| Alakzat megjelenik még a `setHidden(true)` után | A dokumentumot a rejtett jelző beállítása előtt mentették. | Győződjön meg róla, hogy a `setHidden(true)` **a** `doc.save()` **előtt** van meghívva. |
| Az alakzat mérete torzul | Pont és pixel keverése magas DPI-s képernyőkön. | Használjon pontot (72 pt = 1 in) a méretezés egységességéhez különböző platformokon. |
| A rejtett alakzat még nyomtat | Egyes nyomtatók figyelmen kívül hagyják a rejtett jelzőt. | Állítsa be a `Shape.setWrapType(WrapType.NONE)`‑t, és tisztítsa meg a `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)` beállítást is. |

## Következtetés

Most már tudja, hogyan **adjunk hozzá alakzatot Word** dokumentumokhoz az Aspose.Words for Java használatával, **hogyan szúrjunk be alakzatot**, és **hogyan rejtsünk el alakzatot**, hogy az felhasználók számára láthatatlan maradjon, de a dokumentumszerkezet része legyen. A fenti teljes példa betölt egy fájlt, beszúr egy téglalapot, elrejti, és elmenti az eredményt, lefedve a tipikus felhasználási eseteket és több szélhelyzetet is.

Innen tovább felfedezheti a kapcsolódó témákat, például a **alakzat beszúrását** egyedi kitöltőszínekkel, a **alakzat elrejtését Word-ben** feltételes nyomtatáshoz, vagy a tömeges dokumentumfeldolgozás automatizálását az Aspose.Words segítségével. Kísérletezzen különböző `ShapeType` értékekkel, elhelyezési lehetőségekkel és láthatósági jelzőkkel, hogy a saját munkafolyamatához illeszkedjen.

Boldog kódolást, és élvezze a programozott Word-manipuláció nyújtotta rugalmasságot Java alkalmazásaiban!

## Mit érdemes legközelebb megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API-funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Word dokumentum programozott létrehozása, alakzat hozzáadása és elrejtése Java-ban az Aspose.Words használatával](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Hogyan rejtsünk el alakzatot Word dokumentumban Java használatával](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Üres .docx Word dokumentum létrehozása és rejtett téglalap alakzat hozzáadása az Aspose.Words segítségével](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}