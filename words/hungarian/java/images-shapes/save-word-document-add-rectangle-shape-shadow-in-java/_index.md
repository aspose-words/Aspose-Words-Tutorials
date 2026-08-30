---
category: general
date: 2026-06-20
description: Word dokumentum mentése Aspose.Words használatával Java-ban, miközben
  egy téglalap alakzatot adunk hozzá és árnyékot alkalmazunk. Tanulja meg, hogyan
  illessze be az alakzatot lépésről lépésre.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: hu
og_description: Word dokumentum mentése az Aspose.Words Java-val. Ez az útmutató bemutatja,
  hogyan adhatunk hozzá egy téglalap alakzatot, alkalmazhatunk árnyékot, és szúrhatjuk
  be egy bekezdésbe.
og_title: Word-dokumentum mentése – Téglalap alakzat és árnyék hozzáadása Java-ban
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Word-dokumentum mentése – Téglalap alakzat és árnyék hozzáadása Java-ban
url: /hu/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum mentése – Téglalap alakzat és árnyék hozzáadása Java-ban

Gondolkodtál már azon, hogyan **menthetsz egy Word dokumentumot** miután testreszabtad a megjelenését? Nem vagy egyedül – a legtöbb fejlesztő ebben ütközik, amikor programozottan szeretne gazdagítani egy DOCX fájlt. A jó hír, hogy az Aspose.Words for Java segítségével **menthetsz egy Word dokumentumot**, elhelyezhetsz egy téglalap alakzatot pontosan ott, ahol szeretnéd, és még egy finom árnyékot is adhatunk az alakzathoz.

Ebben a tutorialban végigvezetünk a teljes folyamaton: egy meglévő fájl betöltése, **téglalap alakzat hozzáadása**, az **árnyék** beállítása, az alakzat beszúrása az első bekezdésbe, és végül a **Word dokumentum mentése**. A végére egy futtatható Java programod lesz, amely egy kifinomult `shadow.docx` fájlt hoz létre – manuális beavatkozás nélkül.

> **Amire szükséged lesz**  
> * Java 17 (vagy bármely friss JDK)  
> * Aspose.Words for Java könyvtár (Maven/Gradle vagy a JAR)  
> * Egy bemeneti DOCX fájl (`input.docx`) egy ismert mappában  

Ha ezek megvannak, merüljünk el a részletekben.

---

## Word dokumentum mentése – Teljes Java példa

Az alábbi kódrészlet a teljes, azonnal futtatható forráskód. Másold be a kedvenc IDE-dbe, állítsd be az elérési útvonalakat, és nyomd meg a **Run** gombot.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**Várható eredmény:** A program futtatása után nyisd meg a `shadow.docx` fájlt. Látni fogod az eredeti tartalmat, valamint egy 100 × 50 pt fekete téglalapot egy lágy árnyékkal, közvetlenül az első bekezdés elején.

---

## Téglalap alakzat hozzáadása Word dokumentumhoz

Miért használjunk egyáltalán téglalap alakzatot? Gondolj rá úgy, mint egy vizuális horgonyra – tökéletes kiemelésekhez, helyőrzőkhöz vagy egyszerű grafikákhoz. Az Aspose.Words‑ben a `Shape` osztály képviseli az összes rajzoló objektumot, és a `ShapeType.RECTANGLE` egy tiszta dobozt ad extra felesleges beállítások nélkül.

**Fontos tudnivalók téglalap alakzat hozzáadásakor**

- **Az egységek pontok** (1 pt = 1/72 in). Állítsd be a `setWidth`/`setHeight` értékeket a kívánt elrendezéshez.  
- Az alakzat a dokumentum csomópontfájában él, így bárhol beszúrható, ahol `Paragraph` vagy `Run` megengedett.  
- A téglalapot (kitöltés, vonalszín stb.) stílusozhatod, mielőtt árnyékot alkalmaznál.

> **Pro tipp:** Ha átlátszó kitöltésre van szükséged, hívd a `rectangle.getFill().setTransparent(true);` metódust.

---

## Árnyék alkalmazása alakzatra

Az árnyékok mélységet adnak. A `Shape`‑hez csatolt `Shadow` objektum olyan tulajdonságokat kínál, amelyek közvetlenül a Word felhasználói felületének beállításaira vonatkoznak.

| Property | Mit csinál | Tipikus érték |
|----------|------------|---------------|
| `setVisible(true)` | Bekapcsolja az árnyékot | `true` |
| `setColor(Color.BLACK)` | Árnyék színe | `Color.BLACK` |
| `setBlurRadius(5.0)` | Az él lágyasága | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | Vízszintes/vertikális eltolás | `4.0` mindkettő |
| `setTransparency(0.3)` | Átlátszóság (0 = átlátszatlan, 1 = láthatatlan) | `0.3` |

Amikor a **„hogyan alkalmazzunk árnyékot alakzatra”** kérdésre keresünk választ, egyszerűen ezeket a hat tulajdonságot kell módosítani. Kísérletezhetsz – nagyobb eltolások „felemelt” hatást keltenek, míg a nagyobb blur radius egy szórtabb megjelenést eredményez.

> **Gyakori hiba:** A `setVisible(true)` elhagyása árnyék nélküli alakzatot eredményez, még ha a többi tulajdonságot be is állítottad.

---

## Alakzat beszúrása bekezdésbe

Alakzat beszúrása nem varázslat, csak csomópontmanipuláció. Az `appendChild` metódus a alakzatot a bekezdés gyermekcsomópontjainak végére helyezi. Ha a szöveg előtt szeretnéd elhelyezni, használd a `insertBefore` metódust.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

Ez a kis változtatás megválaszolja a **„hogyan szúrjunk be alakzatot”** kérdést – legyen szó bármely meglévő run előtt, egy címsor után, vagy akár egy táblázat cellájában (ekkor előbb szerezd be a megfelelő `Cell` csomópontot).

---

## A kód futtatása és a kimenet ellenőrzése

1. **Fordítás** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **Végrehajtás** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **Megnyitás** `shadow.docx` Microsoft Word vagy LibreOffice programban. Látnod kell a téglalapot egy lágy fekete árnyékkal, amely az első bekezdés elején van rögzítve.

Ha az alakzat nem jelenik meg, ellenőrizd a következőket:

- A bemeneti fájl elérési útja helyes.  
- Friss Aspose.Words verziót használsz (az API 20.12 előtt kissé változott).  
- A dokumentumnak legalább egy bekezdése van (különben a `getParagraphs().get(0)` IndexOutOfBoundsException‑t dob).

---

## Gyakran Ismételt Kérdések (GYIK)

**Q: Hozzáadhatom az alakzatot egy adott oldalhoz?**  
A: Igen. Szerezd meg a cél `Section` vagy `PageSetup` objektumot, és szúrd be az alakzatot egy azon az oldalon található bekezdésbe.

**Q: Működik ez .doc fájlokkal is?**  
A: Teljesen. Az Aspose.Words elrejti a formátum részleteit, így ugyanaz a kód **ment egy Word dokumentumot**, legyen az `.doc` vagy `.docx`.

**Q: Mi van, ha egy másik alakzatra, például ellipszisre van szükségem?**  
A: Cseréld le a `ShapeType.RECTANGLE`-t `ShapeType.ELLIPSE`-re. Az összes árnyék‑tulajdonság változatlan marad.

---

## Összegzés

Most már tudod, hogyan **ments egy Word dokumentumot** miközben **téglalap alakzatot adsz hozzá**, **árnyékot alkalmazol**, és **az alakzatot** az első bekezdésbe szúrod – mindezt néhány tiszta Java sorral. Ez a minta könnyen skálázható: cseréld le az alakzat típusát, finomítsd az árnyék beállításait, vagy helyezd el az alakzatot táblázatokban és fejlécekben. A lehetőségek annyira szélesek, mint a dokumentum‑automatizálási igényeid.

Készen állsz a következő kihívásra? Próbáld meg több alakzat rétegezését, szöveg hozzáadását a téglalap belsejébe, vagy egy teljes jelentés generálását diagramokkal és vízjelekkel. Mindez ugyanazokra az alapokra épül, amelyeket itt megtanultál – így már egy lépéssel előrébb vagy.

Boldog kódolást, és legyen a Word automatizálásod árnyék‑mentes!

## Mit érdemes legközelebb tanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy könnyedén elsajátíthasd a további API‑funkciókat, és alternatív megvalósítási módokat fedezhess fel saját projektjeidben.

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hogyan mentse a dokumentumot PDF‑ként az Aspose.Words for Java használatával](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Hogyan mentse a Word dokumentumot PCL formátumban az Aspose.Words for Java használatával](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}