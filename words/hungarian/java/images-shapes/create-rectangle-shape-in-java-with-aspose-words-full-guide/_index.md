---
category: general
date: 2026-07-06
description: Hozzon létre téglalap alakzatot Java-ban az Aspose.Words segítségével
  – tanulja meg, hogyan adhat árnyékot az alakzathoz, állíthatja be az alakzat átlátszóságát,
  és mentheti a dokumentumot PDF formátumban.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: hu
og_description: Hozzon létre téglalap alakzatot Java-ban az Aspose.Words segítségével.
  Ez az útmutató bemutatja, hogyan adhat árnyékot az alakzathoz, állíthatja be az
  alakzat átlátszóságát, és mentheti a dokumentumot PDF formátumban.
og_title: Téglalap alakzat létrehozása Java-ban – Aspose.Words oktatóanyag
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: Téglalap alakzat létrehozása Java-ban az Aspose.Words segítségével – Teljes
  útmutató
url: /hu/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Java-ban az Aspose.Words segítségével – Teljes útmutató

Gondolkodtál már azon, hogyan **hozhatsz létre téglalap alakzatot** Java-ban anélkül, hogy alacsony szintű rajzoló API-kkal küzdenél? Nem vagy egyedül. Sok fejlesztőnek gyors, megbízható módra van szüksége, hogy egy téglalapot helyezzen el egy Word dokumentumban, finom árnyékot adjon neki, állítsa be az átlátszóságát, majd a végeredményt PDF-ként exportálja.  

Ebben az útmutatóban pontosan ezt fogjuk végigjárni—lépésről lépésre, teljes, futtatható kóddal. A végére tudni fogod, **hogyan adhatsz árnyékot** egy alakzathoz, **hogyan állíthatod be az alakzat átlátszóságát**, és **hogyan mentheted a dokumentumot PDF‑ként** az Aspose.Words for Java használatával. Nincs felesleges részlet, csak gyakorlati útmutatás, amit ma be tudsz másolni a projektedbe.

## Mit fogsz megtanulni

- A minimális beállítás, amely szükséges az Aspose.Words Java projektben való használatához.  
- Hogyan **hozz létre téglalap alakzatot** programozottan.  
- A pontos hívások, amelyek szükségesek az **árnyék hozzáadásához az alakzathoz**, valamint a homály, eltolás és átlátszatlanság beállításához.  
- Módszerek a **alakzat átlátszóságának beállítására**, hogy a téglalap szépen beleolvadjon a környező tartalomba.  
- A legegyszerűbb módszer a **dokumentum PDF‑ként való mentésére** további konverziós lépések nélkül.  

Ha magabiztos vagy az alap Java használatában, és rendelkezel Maven vagy Gradle builddel, már készen állsz a kezdésre.

## Előfeltételek

- Java 8 vagy újabb.  
- Aspose.Words for Java 23.x (vagy a legújabb verzió a cikk olvasásakor).  
- IDE vagy parancssori build eszköz (IntelliJ, Eclipse, Maven, Gradle—válaszd, ami a legjobban megfelel).  

> **Pro tipp:** Az Aspose ingyenes, ideiglenes licencet kínál kiértékeléshez. Szerezd be a fiókportálodról, és helyezd a `license.xml` fájlt az osztályútvonalba; különben vízjelet látsz a PDF‑ben.

---

## 1. lépés: **Téglalap alakzat létrehozása** az Aspose.Words segítségével

Az első dolog, amire szükségünk van, egy üres `Document` és egy `DocumentBuilder`. A builder a munkaerő, amely lehetővé teszi, hogy alakzatokat közvetlenül a dokumentum áramlásába illesszünk.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**Miért fontos:** A `ShapeType.RECTANGLE` azt jelzi az Aspose‑nak, hogy egy tökéletes téglalapot szeretnénk. A szélesség és magasság pontokban van megadva (1 pt ≈ 1/72 hú), ami finomhangolt vezérlést biztosít a végméret felett.

---

## 2. lépés: **Árnyék hozzáadása az alakzathoz**

Miután megvan a téglalap, adjunk neki egy finom vetett árnyékot. A `ShadowFormat` objektum mindent elérhetővé tesz, amire szükségünk van — a homály sugár, X/Y eltolás, és még az átlátszóság is.

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**Miért fontos:** A homály nélküli árnyék kemény vonalnak tűnik, ami ritkán felel meg a tervezők elvárásainak. A `setBlur` hívás kisimítja a széleket, míg a `setTransparency` lehetővé teszi, hogy az árnyék elhalványuljon a háttérben. Állítsd be ezeket az értékeket a UI irányelveidnek megfelelően.

---

## 3. lépés: **Alakzat átlátszóságának beállítása**

Néha szükség van arra, hogy maga a téglalap félig átlátszó legyen — például logó vagy vízjel átfedéséhez. Az Aspose ezt egyetlen sorban megoldja.

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**Miért fontos:** Az átlátszóság életmentő lehet, amikor alakzatokat rétegezel. Vedd figyelembe, hogy az árnyék átlátszósága önálló, így lehet egy halvány alakzat sötétebb árnyékkal, ha ez illik a tervezésedhez.

---

## 4. lépés: **Dokumentum mentése PDF‑ként**

Minden vizuális munka elkészült; az utolsó lépés a dokumentum mentése. Az Aspose.Words közvetlenül PDF‑be tud írni, így nincs szükség külön konverziós könyvtárra.

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Miért fontos:** A `SaveFormat.PDF` megadásával a könyvtár a háttérben kezeli a betűtípus beágyazását, a képek tömörítését és a PDF/A megfelelőséget. Az eredményül kapott fájl készen áll a terjesztésre, nyomtatásra vagy archiválásra.

---

## Teljes működő példa

Mindent összevonva, itt a teljes, azonnal futtatható osztály. Másold be, állítsd be a kimeneti mappát, és kapsz egy PDF‑et egy olyan téglalappal, amely valósághű árnyékot vet.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Várható kimenet:** Amikor megnyitod a `RectangleWithShadow.pdf` fájlt, egy világosszürke téglalapot látsz az első oldal közepén, amelyet egy puha, félig átlátszó árnyék emel fel a lapról. Az alakzat maga 20 % átlátszó, így az alatta lévő szöveg (ha van) átlátszik.

---

## Gyakori kérdések és szélhelyzetek

### 1️⃣ Mi van, ha nagyobb téglalapra van szükségem?

Csak módosítsd a `insertShape` szélesség és magasság paramétereit. Ne feledd, hogy 72 pt = 1 hú, így a `400.0, 200.0` egy 5,5 × 2,8 hú (inch) téglalapot eredményez.

### 2️⃣ Használhatok más színt az árnyékhoz?

Természetesen. A `ShadowFormat` osztály szintén elérhetővé teszi a `setColor(java.awt.Color)` metódust. Egy finom szürke árnyékhoz próbáld ki a `shadow.setColor(java.awt.Color.DARK_GRAY);` kódot.

### 3️⃣ Működik a `save document as pdf` minden platformon?

Igen. Az Aspose.Words for Java platform‑független; ugyanaz a kód fut Windows, macOS és Linux rendszereken, amennyiben kompatibilis JRE‑t használsz.

### 4️⃣ Hogyan távolíthatom el később az árnyékot?

Hívd meg a `rect.getShadowFormat().clear();` metódust, vagy állítsd a `Visible` tulajdonságot `false`‑ra (`shadow.setVisible(false);`).

### 5️⃣ Mi a helyzet a DPI‑val és a képminőséggel?

PDF‑ként mentéskor az Aspose automatikusan 300 DPI‑t használ a vektoros grafikákhoz, például az alakzatokhoz, így a nagyítási szinttől függetlenül éles eredményt kapsz.

---

## Pro tippek és legjobb gyakorlatok

- **Kötegelt feldolgozás:** Ha tucatnyi PDF‑et kell generálni, használd újra egyetlen `Document` példányt, és csak a szekciókat töröld az iterációk között a GC terhelés csökkentése érdekében.  
- **Licencelés:** Helyezd a `License license = new License(); license.setLicense("license.xml");` kódot a `main` elejére, hogy elkerüld az értékelő vízjelet.  
- **Teljesítmény:** Az árnyék renderelése egyszerű alakzatoknál olcsó, de a komplex útvonalak lelassíthatják a PDF generálást. Profilozd a folyamatot, ha nagy kötegeket dolgozol fel.  
- **Tesztelés:** Először használd az Aspose `Document.save(..., SaveFormat.DOCX)` metódusát, hogy ellenőrizd, az alakzat helyesen jelenik meg Wordben, mielőtt PDF‑re konvertálnád.

---

## Összegzés

Most már tudod, hogyan **hozhatsz létre téglalap alakzatot** Java-ban az Aspose.Words segítségével, **adhatsz árnyékot az alakzathoz**, **állíthatod be az alakzat átlátszóságát**, és végül **mentheted a dokumentumot PDF‑ként**. A kód önálló, a legújabb Aspose könyvtárral működik, és bemutatja a legfontosabb API hívásokat, amelyekre a legtöbb dokumentum‑automatizálási helyzetben szükséged lesz.

Készen állsz a következő kihívásra? Próbáld ki a téglalap helyett egy ellipszist, kísérletezz színátmenetes kitöltésekkel, vagy fedezd fel, hogyan **adhatsz árnyékot** szövegkeretekhez. Ugyanazok az elvek érvényesek, és az Aspose API úgy működik, mintha egy szelet süti lenne.

Boldog kódolást, és nyugodtan hagyj megjegyzést, ha elakadsz!

## Mit érdemes legközelebb megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hogyan mentheted a dokumentumot PDF‑ként az Aspose.Words for Java‑val](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Hogyan hozhatsz létre űrlapmezőket és adhatsz tartalmat a DocumentBuilder segítségével az Aspose.Words for Java‑ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}