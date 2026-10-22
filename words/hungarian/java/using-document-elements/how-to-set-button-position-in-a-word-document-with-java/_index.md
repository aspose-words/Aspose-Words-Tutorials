---
category: general
date: 2026-09-24
description: Állítsa be a gomb pozícióját egy Word dokumentumban Java és az Aspose.Words
  segítségével. Tanulja meg, hogyan szúrjon be gombot, adjon hozzá ActiveX vezérlőt,
  és hozza létre a Word dokumentumot Java stílusban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: hu
lastmod: 2026-09-24
og_description: Állítsa be a gomb pozícióját egy Word dokumentumban Java használatával.
  Ez az útmutató bemutatja, hogyan szúrjon be gombot, adjon hozzá ActiveX‑vezérlőt,
  és hogyan hozzon létre Word dokumentumot Java‑val az Aspose.Words segítségével.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Gomb helyének beállítása Word dokumentumban Java-val – teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Hogyan állítsuk be a gomb pozícióját egy Word-dokumentumban Java-val
url: /hu/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan állítsuk be a gomb pozícióját egy Word dokumentumban Java-val

Ha **gomb pozícióját** kell beállítania egy Word fájlban, ez az útmutató egy teljes, futtatható megoldást mutat be. Akár olyan sablont épít, amely felhasználói interakciót igényel, akár egy űrlapot automatizál, pontosan megtanulja, **hogyan szúrjon be gombot** az Aspose.Words for Java segítségével, és hogyan szabályozza annak elhelyezését.

Az útmutató mindent lefed, amire szüksége van **ActiveX vezérlő hozzáadásához** egy Word dokumentumhoz, bemutatja, hogyan **adjunk gombot a Word-hez**, és demonstrálja a teljes folyamatot a **Word dokumentum Java‑ban történő létrehozásához**. Külső hivatkozásokra nincs szükség – egyszerűen másolja, futtassa, és ellenőrizze az eredményt.

## Előfeltételek

* Java 17 (vagy bármely Java 8+ futtatókörnyezet) telepítve.
* Maven vagy Gradle a függőségek kezeléséhez.
* Aspose.Words for Java licenc (az ingyenes próba verzió értékelésre használható).
* Alapvető Java szintaxis ismeret.

> **Pro tipp:** Tartsa az Aspose.Words JAR fájlokat egy `libs/` mappában, és adja hozzá őket a projekt osztályútvonalához a verzióütközések elkerülése érdekében.

## 1. lépés: Maven projekt beállítása

Hozzon létre egy egyszerű Maven projektet (vagy használjon Gradlet), és adja hozzá az Aspose.Words függőséget:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

A `mvn clean compile` futtatása letölti a könyvtárat és előkészíti az építési útvonalat.

## 2. lépés: Új Word dokumentum létrehozása

Az első művelet a **Word dokumentum Java‑ban történő létrehozása**. Létrehozza a `Document` objektumot és egy `DocumentBuilder`‑t, amely lehetővé teszi a fájl szerkesztését.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A `Document` osztály a teljes .docx fájlt képviseli, míg a `DocumentBuilder` folyékony API‑t biztosít a tartalom beszúrásához.

## 3. lépés: Gomb beszúrása – ActiveX vezérlő hozzáadása

Az Aspose.Words a `Forms2OleControl` osztályt biztosítja régi ActiveX vezérlők, például CommandButton beszúrásához. Ez a lépés pontosan bemutatja, hogyan **szúrjon be gombot** a dokumentumba.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

Az `insertForms2OleControl` metódus egy `Forms2OleControl` példányt ad vissza, amelyet konfigurálhat. Ez a **ActiveX vezérlő hozzáadásának** központi része.

## 4. lépés: Gomb pozíciójának beállítása

Most ténylegesen **beállítjuk a gomb pozícióját**. A vezérlő `setLeft` és `setTop` metódusai pontban (pt) megadott értékeket fogadnak (1 pt = 1/72 in). A gombot a szokásos képernyőkoordinátákkal összehangolva átválthatja a pixeleket pontokra (1 px ≈ 0,75 pt). A példában a gombot 100 px-re a bal szélről és 150 px-re a felső szélről helyezzük el.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Mivel a **gomb pozíciójának beállítása** logika itt van kapszulázva, újra felhasználhatja ezeket a sorokat, amikor vezérlőt kell áthelyezni. Állítsa a számokat a saját elrendezési igényeihez.

## 5. lépés: Méret és felirat meghatározása

A címke nélküli gomb zavaró. Használja a `setWidth`, `setHeight` és `setCaption` metódusokat, hogy látható megjelenést adjon neki.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

A méret is pontban van megadva, ezért a konzisztencia érdekében pixelekből konvertálunk.

## 6. lépés: Dokumentum mentése – a Word dokumentum Java‑ban történő létrehozásának befejezése

Végül mentse a fájlt a lemezre. Az útvonal lehet abszolút vagy a projekt gyökérkönyvtárához relatív.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

A program futtatása létrehozza a `CommandButtonDemo.docx` fájlt az `output` mappában. A fájl megnyitása a Microsoft Wordben egy kattintható gombot mutat, amely pontosan a megadott helyen van.

### Várt kimenet

* Egy **CommandButtonDemo.docx** nevű `.docx` fájl.
* A dokumentumban egy **CommandButton** jelenik meg “Click Me” felirattal, amely 100 px-re van a bal margótól és 150 px-re a felső margótól.
* A gomb kattintásra reagál, amikor a dokumentumot Wordben nyitják meg (alapértelmezett ActiveX üzenetet jelenít meg, hacsak nem csatol egyedi VBA kódot).

## 7. lépés: Gyakori variációk és szélsőséges esetek

### Több gomb hozzáadása

Ha többször kell **gombot hozzáadni a Word-hez**, ismételje meg a 3‑5. lépéseket minden alkalommal egy új `Forms2OleControl` példánnyal. Ne felejtse el a `setTop` értéket úgy módosítani, hogy a gombok ne fedjék egymást.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Licenc nélküli használat

Az Aspose.Words licenc nélkül használva vízjelet ad a dokumentumhoz. Gyártási kód esetén vásároljon licencet, és alkalmazza a `main` elején:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Kompatibilitás régebbi Office verziókkal

Az ActiveX vezérlők támogatottak a `.doc` (Word 97‑2003) formátumban. Régi fájl létrehozásához módosítsa a mentési formátumot:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Teljes forráskód (futtatható)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Mentse a fájlt `src/main/java/CommandButtonDemo.java` néven, futtassa a `mvn exec:java -Dexec.mainClass=CommandButtonDemo` parancsot, és nyissa meg a generált dokumentumot az eredmény megtekintéséhez.

## Gyakran ismételt kérdések

**Q: Működik ez OpenJDK-val?**  
A: Igen. Az Aspose.Words tisztán Java, és bármely JDK 8+ implementáción fut, beleértve az OpenJDK-t.

**Q: Meg tudom változtatni a gomb betűtípusát vagy színét?**  
A: Az ActiveX gomb megjelenését a gazdaalkalmazás (Word) szabályozza. VBA kódot csatolhat a tulajdonságok futás közbeni módosításához, de a statikus megjelenés csak az alapértelmezett stílusra korlátozódik.

**Q: Mi a teendő, ha a gombot egy táblázat cellájába kell helyezni?**  
A: Helyezze a `DocumentBuilder` kurzort a cellába az `insertForms2OleControl` hívása előtt. A vezérlő örökli a cella elrendezését, és továbbra is használhatja a `setLeft`/`setTop` metódusokat a finomhangoláshoz.

## Következtetés

Most már tudja, hogyan **állítsa be a gomb pozícióját** egy Word dokumentumban Java-val, hogyan **szúrjon be gombot**, hogyan **adjon hozzá ActiveX vezérlőt**, és hogyan **adjon gombot a Word-hez**, miközben a **Word dokumentum Java‑ban történő létrehozásához** legjobb gyakorlatokat követi. A teljes példa bemutatja az egész munkafolyamatot – a projekt beállításától egy funkcionális CommandButton-t tartalmazó `.docx` fájl mentéséig.

### Következő lépések

* Fedezze fel a `Forms2OleControl.ControlType` egyéb értékeit (pl. `CHECKBOX`, `TEXTBOX`) a gazdagabb űrlapok építéséhez.
* Kombinálja a gombot VBA makrókkal egyedi kattintáskezeléshez.
* Használja az Aspose.Words levél-összefűzés funkcióját személyre szabott dokumentumok generálásához, amelyek már tartalmaznak interaktív vezérlőket.

Boldog kódolást, és élvezze a Word dokumentumok Java‑val történő automatizálását!

## Mit érdemes legközelebb megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}