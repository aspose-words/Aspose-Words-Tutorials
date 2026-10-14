---
category: general
date: 2026-10-13
description: Hozzon létre űrlapmező‑gombot a Wordben az Aspose.Words for Java használatával.
  Tanulja meg, hogyan szúrjon be parancsgombos Word‑űrlapmezőket, és állítsa be a
  parancsgomb feliratát néhány egyszerű lépésben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: hu
lastmod: 2026-10-13
og_description: Hozzon létre űrlapmező gombot a Wordben az Aspose.Words for Java segítségével.
  Ez az útmutató bemutatja, hogyan szúrjon be parancsgomb mezőket a Wordben, és hogyan
  állítsa be gyorsan a parancsgomb feliratát.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Űrlapmező gomb létrehozása Wordben – Aspose.Words Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Űrlapmező gomb létrehozása Wordben az Aspose.Words Java-val
url: /hu/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Űrlapmező gomb létrehozása Word-ben az Aspose.Words Java-val

Ha **create form field button**-t kell létrehoznia egy Word dokumentumban, ez az útmutató végigvezeti a teljes folyamaton az Aspose.Words for Java használatával. Akár kitöltendő űrlap sablont épít, akár interaktív vezérlőket ad hozzá egy jelentéshez, megtanulja, hogyan **insert command button word** űrlapmezőket szúrjon be, és hogyan **set command button caption**-t állítson be minimális kóddal.

Az útmutató mindent lefed a Maven beállítástól egy teljesen futtatható példáig, így egyszerűen másolhatja és beillesztheti a kódot, futtathatja, és megtekintheti a `.docx` fájlt, amely egy kattintható gombot tartalmaz, készen állva a további testreszabásra.

## Előfeltételek

- Java 17 (vagy újabb) telepítve és konfigurálva van a gépén.
- Maven 3.6+ a függőségkezeléshez.
- Az Ön által választott IDE vagy szövegszerkesztő (pl. IntelliJ IDEA, VS Code).
- Érvényes Aspose.Words for Java licenc (az ingyenes próba a kiértékeléshez megfelelő).

## 1. lépés: Aspose.Words hozzáadása a Maven projekthez

Hozzon létre egy `pom.xml` fájlt (vagy szerkessze a meglévőt), és adja hozzá az Aspose.Words függőséget:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Pro tip:** Tartsa naprakészen a verziószámot. Az új kiadások támogatják a legújabb Word funkciókat és javítják a teljesítményt.

## 2. lépés: Üres dokumentum és `DocumentBuilder` inicializálása

A `DocumentBuilder` osztály egy folyékony API-t biztosít a Word dokumentum szerkesztéséhez. Ebben a lépésben egy üres `Document`-et hozunk létre, és egy builder-t csatolunk hozzá.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A dokumentum létrehozása a **creating form field button** objektumok későbbi létrehozásának alapja az útmutatóban.

## 3. lépés: Parancsgomb űrlapmező beszúrása

Az Aspose.Words a `Forms2OleControl` osztályt biztosítja az OLE űrlapvezérlőkhöz. A **insert command button word** űrlapmezők beszúrásához hívja meg az `insertForms2OleControl` metódust a `COMMANDBUTTON` enum értékkel.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

A metódus egy `Forms2OleControl` példányt ad vissza, amelyet a mentés előtt konfigurálhatunk.

## 4. lépés: A gomb méretének és pozíciójának meghatározása

A parancsgombnak explicit méretekre és elhelyezésre van szüksége az oldalon. Állítsa be a szélességet, magasságot és a koordinátákat a kívánt elrendezésnek megfelelően.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Ezen értékek finomhangolása biztosítja, hogy a gomb pontosan a kívánt helyen jelenjen meg a végső dokumentumban.

## 5. lépés: **Set command button caption**

A gomb látható szövegét a `setCaption` metódus szabályozza. Itt **set command button caption**-t állítunk be, hogy a felhasználót irányítsuk.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

A `"Click Me"` szöveget bármilyen címkére cserélheti, amely megfelel az űrlap céljának, például `"Submit"` vagy `"Approve"`.

## 6. lépés: Dokumentum mentése

Végül írja a dokumentumot a lemezre. A keletkezett fájl tartalmazza az interaktív gombot, és megnyitható a Microsoft Word vagy a LibreOffice programokban.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

A program futtatása `CommandButtonDemo.docx` fájlt hoz létre. A Word-ben megnyitva egy **Click Me** felirattal ellátott gombot láthat, amely 50 pt távolságra van a bal szélétől és 100 pt távolságra a felső szélétől.

### Várt kimenet

- Egy `CommandButtonDemo.docx` nevű `.docx` fájl.
- A dokumentum egyetlen oldalt tartalmaz egy parancsgomb űrlapmezővel.
- A gomb a beállított feliratot jeleníti meg (pl. **Click Me**).

## Gyakori variációk és szélhelyzetek

| Szituáció | Hogyan alkalmazzuk |
|-----------|--------------------|
| **Több gomb** | Hívja meg többször az `insertForms2OleControl`-t, és minden új gombnál állítsa be a `setLeft`/`setTop` értékeket. |
| **Különböző felirat gombonként** | Használja a `setCaption`-t egy egyedi karakterlánccal minden beszúrás után. |
| **Gomb táblázatcellában** | A kurzort mozgassa a kívánt cellába a `builder.moveTo(cell.getFirstParagraph())` segítségével a vezérlő beszúrása előtt. |
| **Legacy Word formátumok (.doc)** | Mentse a `doc.save("Demo.doc", SaveFormat.DOC);` használatával – a parancsgomb megmarad. |
| **Csak olvasható űrlapok** | A beszúrás után állítsa be a `commandButton.setEnabled(false);` értéket a felhasználói interakció megakadályozásához. |

## Tippek a robusztus megvalósításhoz

- **Méretek ellenőrzése**: Rendkívül nagy szélességek a gombot a lap margóján túlra tolhatják.
- **Licenc érvényesítése**: Érvényes licenc nélkül az Aspose.Words vízjelet ad a generált dokumentumhoz. Alkalmazza a licencet korán a `License license = new License(); license.setLicense("Aspose.Words.lic");` kóddal.
- **Tesztelés**: Nyissa meg a generált fájlt Word-ben, és kapcsolja be a **Design Mode**-ot (Developer → Design Mode), hogy lássa a gomb tulajdonságait.

## Teljes forráskód összefoglaló

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Másolja a kódot egy `InsertCommandButtonDemo.java` nevű fájlba, fordítsa Maven-nel (`mvn compile`), és futtassa (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). A generált dokumentum a projekt gyökérkönyvtárában jelenik meg.

## Következtetés

Most már tudja, hogyan kell **create form field button**-t létrehozni Word-ben az Aspose.Words for Java használatával, hogyan kell **insert command button word** űrlapmezőket beszúrni, és hogyan kell **set command button caption**-t programozottan beállítani. Ez az vég‑végi példa szilárd alapot nyújt a gazdagabb, interaktív Word dokumentumok építéséhez – legyen szó egyetlen elküldés gombról vagy egy teljes űrlapvezérlő csomagról.

### Mi a következő lépés?

- [Hogyan hozzunk létre űrlapmezőket és adjunk hozzá tartalmat a DocumentBuilder használatával az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Combo Box űrlapmező hozzáadása Word dokumentumhoz az Aspose.Words for .NET használatával](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Check Box űrlapmező hozzáadása Word dokumentumhoz az Aspose.Words for .NET használatával](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}