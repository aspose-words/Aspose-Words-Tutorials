---
category: general
date: 2026-10-04
description: Ismerje meg, hogyan inicializálja a DocumentBuilder‑t egy új dokumentumhoz,
  és hogyan adjon hozzá egy ActiveX gombot az Aspose.Words Java‑ban. Lépésről‑lépésre
  útmutató teljes kóddal.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: hu
lastmod: 2026-10-04
og_description: Inicializálja a DocumentBuilder-t egy új dokumentumhoz, és ágyazzon
  be egy ActiveX parancsgombot az Aspose.Words Java API használatával. Kövesse ezt
  a tömör útmutatót.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: DocumentBuilder inicializálása új dokumentumhoz – teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Hogyan inicializáljuk a DocumentBuilder-t új dokumentumhoz az Aspose.Words
  használatával
url: /hu/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan inicializáljuk a DocumentBuilder-t új dokumentumhoz az Aspose.Words használatával

Ha **DocumentBuilder-t szeretnél inicializálni új dokumentumhoz** egy Java projektben, ez a bemutató pontos lépéseket mutat. Megmutatjuk, hogyan hozhatsz létre egy üres Word‑fájlt, hogyan csatolj egy ActiveX parancsgombot, és hogyan mentheted el az eredményt – mindezt egyetlen, önálló kódrészlettel.

A Word‑dokumentumok programozott kezelése gyakran magában foglal alacsony szintű részleteket, például űrlapvezérlőket. A leírás végére képes leszel egy ActiveX gombot beágyazni anélkül, hogy elhagynád az IDE‑det, ami hasznos sablonok, automatizált jelentések vagy interaktív űrlapok generálásához.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következők telepítve vannak:

* Java 17 vagy újabb  
* Maven 3.8+ (vagy Gradle, ha azt részesíted előnyben)  
* Aspose.Words for Java licenc (a ingyenes próba verzió teszteléshez elegendő)  
* Alapvető ismeretek a Java szintaxisáról  

Ha újonc vagy az Aspose.Words‑ben, a könyvtár egy magas szintű API‑t biztosít Word‑dokumentumok létrehozásához, szerkesztéséhez és mentéséhez. A `DocumentBuilder` osztály a fő belépési pont a dokumentumtartalom felépítéséhez.

## 1. lépés: Maven projekt beállítása

Hozz létre egy új Maven projektet (vagy adj hozzá egy meglévőhöz) és add hozzá az Aspose.Words függőséget:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Tartsd naprakészen a könyvtár verzióját; az újabb kiadások további űrlapvezérlőket támogatnak és javítják a teljesítményt.

## 2. lépés: `DocumentBuilder` inicializálása új dokumentumhoz

A bemutató központi eleme a **DocumentBuilder inicializálása új dokumentumhoz** művelet. Először egy üres `Document` példányt hozol létre, majd átadod azt a `DocumentBuilder` konstruktorának.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Miért fontos:* A `DocumentBuilder` inicializálása egy konkrét `Document` objektumhoz köti a builder‑t, lehetővé téve bekezdések, táblázatok vagy űrlapvezérlők közvetlen hozzáadását a dokumentumhoz. Enélkül a buildernek nincs célobjektuma, amire dolgozhatna.

## 3. lépés: ActiveX parancsgomb vezérlő beszúrása

Az Aspose.Words a `Forms2OleControl` osztályt biztosítja a régi ActiveX vezérlők beágyazásához. Az alábbi kód egy **Forms2OleControl parancsgombot** szúr be az aktuális kurzorpozícióba.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Mi az az ActiveX parancsgomb?

Az ActiveX parancsgomb egy régi UI elem, amely makrókat futtathat vagy eseményeket indíthat el, amikor a felhasználó rákattint egy Word‑dokumentumban. Bár a modern Office verziók a Content Controls‑t részesítik előnyben, sok vállalati sablon még mindig az ActiveX‑et használja a visszafelé kompatibilitás miatt.

## 4. lépés: Dokumentum mentése

A vezérlő beszúrása után egyszerűen meghívod a `save` metódust. A fájl tartalmazni fogja az ActiveX gombot, és megnyitható a Microsoft Word‑ben.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Amikor megnyitod a `ActiveXButton.docx` fájlt Word‑ben, egy **Click Me** feliratú gombot látsz. A gombra kattintás önmagában nem csinál semmit, hacsak nem csatolsz hozzá makrót, de a vezérlő maga teljesen működőképes.

## Teljes, futtatható példa

Az alábbi program a teljes kód, amelyet beilleszthetsz a `src/main/java/com/example/ActiveXButtonDemo.java` fájlba. Tartalmazza az összes importot és a gyors teszthez szükséges hibakezelést.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Várható kimenet**

```
Document saved to output/ActiveXButton.docx
```

Nyisd meg a generált fájlt Microsoft Word 2016 vagy újabb verzióban; a első oldal tetején egy *Click Me* feliratú gombot kell látnod.

## Gyakori variációk és szélhelyzetek

| Szenárió | Módosítás |
|----------|------------|
| **A gomb hozzáadása egy adott bekezdéshez** | A builder kurzorát mozdítsd a `builder.moveToParagraph(index, NodeType.PARAGRAPH);` hívással, mielőtt meghívod az `insertForms2OleControl`‑t. |
| **Gomb méretének beállítása** | Használd a `commandButton.setWidth(100);` és `commandButton.setHeight(30);` metódusokat a pontban megadott méretekhez. |
| **Makró hozzáadása a gombhoz** | A dokumentum mentése után nyisd meg Word‑ben, engedélyezd a Fejlesztő lapot, és manuálisan csatolj egy VBA makrót a gombhoz (az ActiveX vezérlőket nem lehet közvetlenül scriptelni az Aspose.Words‑ből). |
| **.doc (bináris) formátum célozása** | Módosítsd a `doc.save(outputPath, SaveFormat.DOC);` sort, hogy egy régi Word 97‑2003 fájlt hozzon létre. |
| **Androidon való futtatás** | Használd az Aspose.Words for Android‑t a Java API‑jával; ugyanaz a kód működik, amíg a könyvtár be van építve az APK‑ba. |

## Hibaelhárítási tippek

* **`java.lang.NoClassDefFoundError`** – Győződj meg róla, hogy az Aspose.Words JAR a classpath‑on van. A Maven automatikusan hozzáadja; kézi build esetén helyezd a JAR‑t a `libs/` könyvtárba, és add hozzá az IDE‑d könyvtáraihoz.  
* **A gomb nem jelenik meg Word‑ben** – Ellenőrizd, hogy a *Show legacy forms* opció be van-e kapcsolva a Word Trust Center‑ben (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **Licenc kivétel** – Ha a kódot érvényes licenc nélkül futtatod, az Aspose.Words vízjelet helyez el. Regisztrálj egy ingyenes próbaverziót vagy vásárolj licencet a vízjel eltávolításához.

## Összegzés

Most már tudod, hogyan **initializáld a DocumentBuilder‑t új dokumentumhoz**, hogyan szúrj be egy ActiveX parancsgombot, és hogyan mentsd el az eredményt az Aspose.Words for Java‑val. Ez a minta lehetővé teszi interaktív Word‑sablonok programozott generálását, ami különösen hasznos automatizált jelentések vagy űrlap‑alapú munkafolyamatok esetén.

Innen tovább felfedezheted a további űrlapvezérlőket (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, stb.), kombinálhatod a gombot egyedi VBA makrókkal, vagy teljesen felszerelt dokumentumokat hozhatsz létre táblázatokkal, képekkel és stílusokkal – mindezt ugyanazzal a `DocumentBuilder` munkafolyamattal.

---

*Készen állsz összetettebb Word‑automatizálásra? Nézd meg útmutatóinkat a **insert table with DocumentBuilder**, **apply styles programmatically**, és **export to PDF with Aspose.Words** témakörökben.*

## Mit tanulj meg legközelebb?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy könnyedén elsajátíthasd az API további funkcióit, és alternatív megvalósítási megközelítéseket is felfedezhess a saját projektjeidben.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Add a watermark to a document using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}