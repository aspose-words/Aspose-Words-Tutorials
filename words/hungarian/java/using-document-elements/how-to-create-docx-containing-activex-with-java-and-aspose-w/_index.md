---
category: general
date: 2026-09-27
description: Készítsen docx fájlt ActiveX-szel Java-ban az Aspose.Words használatával.
  Tanulja meg lépésről lépésre, hogyan szúrjon be egy ActiveX parancsgombot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: hu
lastmod: 2026-09-27
og_description: Hozzon létre docx fájlt ActiveX-szel Java-ban az Aspose.Words segítségével.
  Kövesse ezt az útmutatót egy ActiveX parancsgomb beszúrásához és a dokumentum mentéséhez.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Docx létrehozása, amely ActiveX-et tartalmaz Java-ban – teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Hogyan lehet Java és Aspose.Words segítségével ActiveX-et tartalmazó docx fájlt
  létrehozni
url: /hu/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre ActiveX-et tartalmazó docx fájlt Java-val és az Aspose.Words-szal

Ha **ActiveX-et tartalmazó docx fájlt kell létrehoznod**, ez az útmutató egy komplett megoldást mutat be. Megtanulod, hogyan **helyezz be ActiveX parancsgombot** egy Word fájlba az Aspose.Words for Java segítségével, majd hogyan mentsd el az eredményt .docx formátumban, amely megnyitható a Microsoft Wordben.

A Word dokumentum programozott előállítása megkímél a kézi szerkesztéstől, és biztosítja a konzisztenciát a jelentések, szerződések vagy űrlapsablonok között. Az alábbi lépések mindent lefednek a projekt beállításától a gyakori hibák kezeléséig, így a technikát bármely Java‑alkalmazásba beillesztheted.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következők telepítve vannak:

* Java Development Kit (JDK) 8 vagy újabb.
* Maven 3.6+ (vagy egy másik általad preferált build eszköz).
* Aspose.Words for Java licencfájl (az ingyenes értékelő verzió teszteléshez elegendő).
* Microsoft Word telepítve a célgépen, ha vizuálisan szeretnéd ellenőrizni az ActiveX vezérlőt.

Ezekre szükség van, mert az Aspose.Words biztosítja azt az API‑t, amely a dokumentumot létrehozza, míg a Word a ActiveX vezérlő megjelenítéséhez szükséges.

## 1. lépés: Maven projekt beállítása

Hozz létre egy új Maven projektet, vagy add hozzá az Aspose.Words függőséget egy meglévő `pom.xml`‑hez:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Tartsd az Aspose.Words verziót szinkronban a hivatalos kiadási jegyzékekkel, hogy élvezhesd a hibajavításokat és az új ActiveX funkciókat.

## 2. lépés: Írd meg a Java kódot, amely létrehozza a dokumentumot

Hozz létre egy `ActiveXDocxCreator` nevű osztályt. Az alábbi kód tartalmazza az összes szükséges importot, egy `main` metódust, és részletes megjegyzéseket, amelyek minden műveletet elmagyaráznak.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Miért fontos minden egyes sor

* `Document` a Word‑tartalom konténerje. Egy friss példány létrehozása tiszta vásznat biztosít.
* `DocumentBuilder` egy folyékony API‑t nyújt az elemek beszúrásához; automatikusan nyomon követi a beszúrási pontot.
* `insertForms2OleControl()` egy általános OLE vezérlő helyőrzőt hoz létre. Az Aspose.Words ezt ActiveX tárolónak tekinti.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` azt mondja a Wordnek, hogy a helyőrző Parancsgombként jelenjen meg.
* `setCaption("Click Me")` meghatározza a gombon megjelenő szöveget.
* `setLeft` és `setTop` a gombot a lap margójához viszonyítva helyezi el. Igazítsd ezeket az értékeket a saját elrendezésedhez.
* `setWidth` és `setHeight` opcionális, de javítják a gomb megjelenését, különösen ha az alapértelmezett méret túl kicsi.
* `doc.save` a memóriában lévő struktúrát egy fizikai .docx fájlba írja, amelyet a Word megnyithat.

## 3. lépés: Ellenőrizd a generált dokumentumot

Nyisd meg a `output/ActiveXCommandButton.docx` fájlt a Microsoft Wordben:

1. A dokumentumnak egyetlen oldalt kell mutatnia, amelyen egy **Click Me** feliratú gomb található a bal‑felső sarok közelében.
2. Ha a gomb nem jelenik meg, ellenőrizd, hogy a **ActiveX vezérlők engedélyezve** vannak‑e a Word Bizalmi Központjában (File → Options → Trust Center → Trust Center Settings → ActiveX Settings).
3. A gomb csak a Windows‑os Word‑verziókon működik, amelyek támogatják az ActiveX‑et. macOS‑on vagy web‑alapú Wordben a vezérlő statikus képként jelenik meg.

## 4. lépés: Gyakori edge case‑ek kezelése

| Helyzet | Ok | Ajánlott teendő |
|-----------|--------|--------------------|
| A gomb hiányzik a fájl megnyitása után | A Word biztonsági beállításai blokkolják az ActiveX‑et | Engedélyezd a “Run all controls without restrictions” opciót a megbízható helyekhez. |
| A generált .docx nem nyitható meg | Nem kompatibilis Aspose.Words verzió | Frissíts a legújabb Aspose.Words kiadásra; a régebbi verziók esetleg nem ágyazzák be helyesen a szükséges OLE részeket. |
| A gombnak makrót kell futtatnia | Az ActiveX önmagában nem tartalmaz makrókódot | Kombináld az ActiveX vezérlőt egy VBA makróval, amely kezeli a `Click` eseményt. Használd a `DocumentBuilder.insertOleObject` metódust egy makró‑engedélyezett sablon beágyazásához. |
| Az elrendezés eltérő oldalméreteknél torzul | A koordináták abszolút pontok | Használd a `builder.getPageSetup().setPageWidth` és `setPageHeight` metódusokat a lapméret szabványosításához a vezérlő elhelyezése előtt. |

## 5. lépés: A megoldás kibővítése

Más ActiveX vezérlőket is beszúrhatsz a `ControlType` enum módosításával:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Az Aspose.Words támogatja továbbá **ActiveX szövegdobozok**, **list boxok** és **combo boxok** beszúrását is. Ugyanazok a pozicionálási metódusok (`setLeft`, `setTop`, `setWidth`, `setHeight`) alkalmazandók.

Ha több vezérlőt szeretnél elhelyezni, hívd meg többször a `builder.insertForms2OleControl()`‑t, és minden egyes vezérlő koordinátáit ennek megfelelően állítsd be.

## Teljes forrásfájl

Az alábbiakban megtalálod a teljes `ActiveXDocxCreator.java` fájlt, amelyet egyszerűen másolhatsz‑beilleszthetsz:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

A program futtatása **ActiveX‑et tartalmazó docx** fájlt hoz létre, amelyet továbbadhatsz azoknak a végfelhasználóknak, akik interaktív űrlapokra van szükségük.

## Összegzés

Most már tudod, hogyan **hozz létre ActiveX‑et tartalmazó docx fájlt** Java és az Aspose.Words segítségével, és hogyan **szúrj be ActiveX parancsgombot** programozottan. Az útmutató lefedte a projekt beállítását, a teljes forráskódot, az ellenőrzési lépéseket, valamint a tipikus problémák megoldására szolgáló stratégiákat.

Innen tovább:

* VBA makrók hozzáadása a gombkattintás kezeléséhez.
* Egyéb ActiveX vezérlők, például jelölőnégyzetek vagy combo boxok beágyazása.
* Többoldalas űrlapok dinamikus adatokkal történő automatizálása.

Kísérletezz különböző koordinátákkal, méretekkel és vezérlőtípusokkal, hogy a dokumentumod elrendezéséhez leginkább illeszkedjen. Jó kódolást!


## Mit érdemes még tanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket és lépésről‑lépésre magyarázatot tartalmaz, hogy könnyedén elsajátíthasd az API további funkcióit, és alternatív megvalósítási megközelítéseket is felfedezhess saját projektjeidben.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}