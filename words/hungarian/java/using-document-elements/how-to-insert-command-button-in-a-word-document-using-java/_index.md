---
category: general
date: 2026-08-23
description: Tanulja meg, hogyan szúrjon be parancsgombot egy Word-dokumentumba Java
  és az Aspose.Words segítségével. Ez az útmutató bemutatja, hogyan adjon hozzá űrlapvezérlőt,
  állítsa be a gomb nevét, és ágyazzon be egy ActiveX gombot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: hu
lastmod: 2026-08-23
og_description: Parancsgomb beszúrása Word dokumentumba Java használatával. Kövesse
  ezt az útmutatót a űrlapvezérlő hozzáadásához, a gomb nevének beállításához, és
  egy ActiveX gomb beágyazásához az Aspose.Words segítségével.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Parancsgomb beszúrása a Wordbe Java-val – lépésről‑lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Hogyan szúrjunk be parancsgombot egy Word-dokumentumba Java-val
url: /hu/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan szúrjunk be parancsgombot egy Word dokumentumba Java segítségével

Ha **parancsgombot** kell beillesztenie egy Word fájlba, ez a bemutató egy teljes megoldást mutat be az Aspose.Words for Java segítségével. Megmutatjuk, hogyan adjon hozzá űrlapvezérlőt, állítsa be a feliratát, és állítsa be a gomb nevét anélkül, hogy elhagyná a fejlesztői környezetet.

Az útmutató mindent lefed, amire szüksége van egy `.docx` létrehozásához, amely ActiveX gombot tartalmaz, készen áll a Microsoft Word-ben való használatra. Nem szükséges további eszköz, és a példa Java 8+-on fut.

## Mit fog megtanulni

* Hogyan adjon hozzá **CommandButton** típusú űrlapvezérlőt egy Word dokumentumhoz.  
* A pontos lépések a **button name** beállításához és az **add activex button** tulajdonságokhoz.  
* Hogyan mentse a dokumentumot, hogy a gomb helyesen jelenjen meg a Word-ben megnyitáskor.  

Alapvető Java fejlesztői környezettel és egy Maven vagy Gradle projekttel kell rendelkeznie, amely képes importálni az Aspose.Words könyvtárat.

## Előfeltételek

| Requirement | Reason |
|-------------|--------|
| Java 8 vagy újabb | Az Aspose.Words for Java Java 8+ környezetben fut. |
| Maven vagy Gradle build eszköz | Megkönnyíti az Aspose.Words függőség hozzáadását. |
| Aspose.Words for Java licenc (vagy ingyenes próba) | Szükséges a teljes funkciókhoz; az API értékelő módban működik. |
| IDE, például IntelliJ IDEA vagy Eclipse | Megkönnyíti a példa szerkesztését és futtatását. |

## 1. lépés: Aspose.Words hozzáadása a projekthez

Ha Maven-t használ, adja hozzá a következő függőséget a `pom.xml`-hez:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Gradle esetén helyezze ezt a sort a `build.gradle` fájlba:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Miután a függőség feloldódott, importálhatja a könyvtár osztályait a Java forrásfájlban.

## 2. lépés: Parancsgomb beszúrása – a fő kód

Hozzon létre egy új Java osztályt `InsertCommandButtonDemo` néven. Az alábbi kód elvégzi a **parancsgomb beszúrásához** szükséges négy műveletet:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Miért fontos minden sor

* **Document & DocumentBuilder** – A Word fájl memóriabeli reprezentációját és a tartalom módosításához szükséges API-t biztosítják.  
* **insertForms2OleControl** – Ez a metódus **form control-t ad hozzá** `COMMAND_BUTTON` típusúként. A visszaadott `Forms2OleControl` objektum az ActiveX vezérlőt képviseli.  
* **setName** – Programozott azonosítót (`btnSubmit`) rendel. A Word makrók vagy VBA később hivatkozhatnak erre a névre.  
* **setCaption** – Meghatározza a gombon megjelenő szöveget, amely a felhasználó számára látható, ezzel válaszolva a „hogyan adjunk hozzá gombot” kérdésre.  
* **save** – Kiírja a `.docx` fájlt a lemezre, megőrizve a beágyazott ActiveX gombot.  

A program futtatása létrehozza a `CommandButtonDemo.docx` fájlt a munkakönyvtárban. A fájl megnyitása a Microsoft Word-ben egy **Submit** feliratú gombot mutat, amelyre kattintva (értékelő módban) egy alapértelmezett ActiveX párbeszédablak jelenik meg.

## 3. lépés: A beszúrt gomb ellenőrzése Word-ben

1. Nyissa meg a `CommandButtonDemo.docx` fájlt a Microsoft Word (2016 vagy újabb) programmal.  
2. A **Submit** gomb ott jelenik meg, ahol a kurzor a beszúráskor állt.  
3. Kattintson jobb gombbal a gombra, és válassza a **Properties** (Tulajdonságok) menüpontot, hogy lássa, a **Name** mező `btnSubmit` értéket tartalmaz.  

Ha a gomb nem jelenik meg, ellenőrizze, hogy a **ActiveX controls** engedélyezve legyen a Word Trust Center beállításaiban.

## 4. lépés: A gomb testreszabása (opcionális)

A gombot tovább testreszabhatja a méretének, pozíciójának módosításával vagy VBA makró hozzáadásával. A `Forms2OleControl` osztály további tulajdonságokat tesz elérhetővé, mint például `setWidth`, `setHeight` és `setLeft`. Az alábbi példa a gombot nagyobbra állítja:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Ezek a sorok a `setCaption` hívás után helyezhetők el. Bemutatják a **add activex button** testreszabását az alap beszúráson túl.

## Gyakori hibák és elkerülésük módja

| Symptom | Cause | Fix |
|---------|-------|-----|
| A gomb nem jelenik meg a Word-ben | A dokumentum a vezérlő hozzáadása előtt lett mentve | Győződjön meg róla, hogy az `insertForms2OleControl` a `doc.save` előtt van meghívva. |
| A gomb felirata üres | `setCaption` nincs meghívva vagy üres karakterlánccal van meghívva | Adjon meg egy nem üres karakterláncot, például `"Submit"`. |
| A VBA nem találja a gombot | Néveltérés a VBA kód és a `setName` érték között | Tartsa a nevet konzisztensen; használja a `setName("btnSubmit")`-t és hivatkozzon a `btnSubmit`-re a VBA-ban. |
| Biztonsági figyelmeztetés a fájl megnyitásakor | A Word makróbiztonsága blokkolja az ActiveX vezérlőket | Állítsa be a Trust Center > Macro Settings beállítást, vagy írja alá a dokumentumot egy megbízható tanúsítvánnyal. |

## Teljes, futtatható példa

Az alábbiakban a teljes forrásfájl található, amely készen áll a másolásra és beillesztésre az IDE-be. Tartalmazza az importálásokat, a kivételkezelést és egy megjegyzésblokkot, amely minden fő lépést magyaráz.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Várható eredmény:** A program futtatása után a `CommandButtonDemo.docx` egyetlen **Submit** gombot tartalmaz. A fájl Word-ben való megnyitása pontosan ott mutatja a gombot, ahol a `DocumentBuilder` kurzor állt.

## Következő lépések

* **Add more form controls** – Használja a `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` vagy `TEXT_BOX` típusokat a teljes Word űrlapok építéséhez.  
* **Combine with mail merge** – Szúrjon be gombokat egy levélösszevonásos dokumentumba, hogy személyre szabott interaktív űrlapokat hozzon létre.  
* **Attach VBA macros** – Programozottan ágyazzon be VBA-t, amely a gomb `Click` eseményére reagál a fejlett automatizálás érdekében.  

Ezek a témák természetesen kiterjesztik a **add form control** technikát, amelyet most elsajátított.

---

### Összefoglalás

Most már tudja, hogyan **insert command button** egy Word dokumentumba Java segítségével, hogyan **add form control**, hogyan **set button name**, és hogyan **add activex button** testreszabásokat végezzen. A teljes példa azonnal futtatható, és bármilyen dokumentum‑generálási munkafolyamatba beilleszthető. Boldog kódolást!

## Mit érdemes következőként megtanulni?

A következő bemutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Hogyan hozzunk létre űrlapmezőket és adjunk hozzá tartalmat a DocumentBuilder segítségével az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Combo Box űrlapmező beszúrása Word dokumentumba](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Check Box űrlapmező beszúrása Word dokumentumba](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}