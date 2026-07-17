---
category: general
date: 2026-07-16
description: Állítsa be a gomb méretét programozott módon egy Word dokumentumban az
  Aspose.Words for Java segítségével. Tanulja meg, hogyan szúrjon be ActiveX gombot,
  állítsa be a gomb helyét és egyebeket.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: hu
lastmod: 2026-07-16
og_description: Állítsa be a gomb méretét egy Word-dokumentumban Java használatával.
  Ez a lépésről‑lépésre útmutató bemutatja, hogyan szúrjon be ActiveX gombot, állítsa
  be a gomb helyét, és programozottan adjon hozzá egy gombot.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Gombméret beállítása Wordben Java-val – Teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Gombméret beállítása Word-ben Java-val – Teljes Aspose.Words útmutató
url: /hu/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be a gomb méretét Word-ben Java-val – Teljes Aspose.Words útmutató

Gondolkodott már azon, hogyan **állíthatja be a gomb méretét** egy Word-fájlban anélkül, hogy megnyitná a felhasználói felületet? Ön nem egyedül van ezzel. Amikor egy űrlappal kitöltött dokumentumot kell gyorsan előállítani – például egy beléptető csomagot egy „Küldés” gombbal – a programozott megoldás órákat takarít meg a kézi munkában.

Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan **szúrhat be ActiveX gombot**, állíthatja be a méreteit, helyezheti el megfelelően, és végül mentheti a fájlt. A végére képes lesz **programozott módon gomb** vezérlőket hozzáadni bármely Word-dokumentumhoz az Aspose.Words for Java használatával.

## Előfeltételek – Amire szüksége van a kezdéshez

- **Java Development Kit (JDK) 8+** – a kód bármely friss JDK-n fut.
- **Aspose.Words for Java** könyvtár (töltse le a legújabb JAR-t a hivatalos oldalról).
- Egy **IDE** a választása szerint – IntelliJ IDEA, Eclipse, vagy akár egy egyszerű szövegszerkesztő is működik.
- Alapvető ismeretek a Java szintaxisról; mély Word‑automatizálási tudás nem szükséges.

> *Pro tipp:* Tartsa az Aspose.Words JAR-t a projekt osztályútvonalán, különben `ClassNotFoundException` hibát kap, amint megpróbálja importálni a `com.aspose.words.*`.

## 1. lépés: Új Word-dokumentum létrehozása

Az első dolog, amit teszünk, egy üres dokumentum és egy `DocumentBuilder` létrehozása. Tekintse a buildert egy tollként, amely lehetővé teszi, hogy bármit megrajzoljunk a fájlban.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Miért fontos:** A `Document` objektum a teljes .docx fájlt képviseli, míg a `DocumentBuilder` a munkagépe, amely lehetővé teszi bekezdések, táblázatok és – igen – ActiveX vezérlők beszúrását.

## 2. lépés: ActiveX gomb beszúrása – A „Insert ActiveX Button” pillanat

Most ténylegesen **beszúrunk egy activex gombot** a dokumentumba. Az Aspose.Words egy kényelmes `insertForms2OleControl` metódust biztosít, amely egy `Forms2OleControl` objektumot ad vissza.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Mi történik a háttérben?* A `Forms2OleControlType.COMMAND_BUTTON` azt mondja a Wordnek, hogy egy klasszikus CommandButton-t szeretnénk, ugyanazt a típust, amelyet a Fejlesztő fülről a felhasználói felületen helyezünk el.

## 3. lépés: Gomb méretének és helyének beállítása – A központi „Set Button Size” logika

Itt jön a fő kulcsszó szerepére. **Beállítjuk a gomb méretét** és **a gomb helyét**, hogy a vezérlő pontosan ott jelenjen meg, ahol a lapon szeretnénk.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Miért érdekelhet:** A pont a Word natív mértékegysége (1 pont = 1/72 hüvelyk). A `setLeft`, `setTop`, `setWidth` és `setHeight` módosításával pixel‑pontos irányítást kap, többé nem lesz „jól néz ki a képernyőn, de nem a nyomtatón”.

> *Gyakori hibaforrás:* Ha elfelejt beállítani a szélességet vagy a magasságot, a gomb az alapértelmezett méretben marad, ami túl kicsi lehet a kattintáshoz. Mindig adja meg mindkettőt.

## 4. lépés: Dokumentum mentése – A „Create Word Document Button” befejezve

Végül a fájlt leírjuk a lemezre. A név arra utal, hogy **Word-dokumentum gombot hozunk létre** egy .docx-ben.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Amikor megnyitja a `CommandButtonDemo.docx` fájlt a Microsoft Wordben, egy **Submit** gombot fog látni, amely 100 pt-re van a bal szegélytől és 150 pt-re a tetejétől, mérete 80 × 30 pt. A felhasználói felületen való kattintás az alapértelmezett ActiveX viselkedést indítja el (amelyet később VBA-val is összekapcsolhat, ha szükséges).

### Várt kimenet képernyőképe

![Word-dokumentum, amely a beszúrt gombot mutatja a beállított gombmérettel](https://example.com/images/set-button-size.png "Word-fájl képernyőképe, ahol a gomb méretét az Aspose.Words for Java használatával állították be")

*Alt szöveg:* gomb méretének beállítása Word-dokumentumban Java használatával

## 5. lépés (Opcionális): További vezérlők hozzáadása vagy a gomb stílusának módosítása

Ha egyetlen Submit gombon túl további **programozott módon hozzáadott gomb** vezérlőkre van szüksége, egyszerűen ismételje meg a beszúrási blokkot új nevekkel és feliratokkal. A betűtípust, háttérszínt is módosíthatja, vagy később VBA makrókat is hozzákapcsolhat.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tipp:* Tartsa a gombok méreteit konzisztensen a professzionális megjelenés érdekében. Egy gyors módszer, ha a szélességet/magasságot állandóként tárolja.

## Gyakori kérdések és szélhelyzetek

### „Beállíthatom a gomb méretét centiméterben a pontok helyett?”

A Word API csak pontokat fogad el, de átalakíthatja a centimétert pontokra (`points = cm * 28.3465`). Írjon egy kis segédfüggvényt, ha a metrikus egységeket részesíti előnyben.

### „Mi van, ha a gombnak egy adott oldalon kell megjelennie?”

A gomb beszúrása után a kurzort egy adott oldalra mozgathatja a `builder.moveToPage(pageNumber)` használatával. A mozgatás után azonnal szúrja be a vezérlőt, majd állítsa be a helyét, ahogy fentebb látható.

### „Működik ez .doc (Word 97‑2003) fájlokkal is?”

Igen – az Aspose.Words automatikusan kezeli a régebbi formátumokat. Csak módosítsa a fájl kiterjesztését a `doc.save("Demo.doc")`‑ben.

## Teljes, futtatható példa

Az alábbiakban a teljes programot láthatja, amelyet bemásolhat egy Java osztályba, és azonnal futtathat (feltéve, hogy az Aspose.Words JAR a classpath-on van).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Futtassa a programot, nyissa meg a generált `CommandButtonDemo.docx` fájlt, és két szép méretű gombot fog látni, amelyek készen állnak a használatra.

## Összegzés – Megtanulta a gomb méretének beállítását Word-ben

Most végigvezettük a teljes, vég‑a‑végig megoldást a **gomb méretének beállítására** és a **gomb helyének beállítására** az Aspose.Words for Java használatával. A lépések követésével **beszúrhat activex gombot**, **programozott módon hozzáadhat gomb** vezérlőket, és végül **Word-dokumentum gomb** elemeket hozhat létre, amelyek pontosan úgy viselkednek, ahogy szükséges.

Mi a következő? Próbálja meg a gombot egy táblázatcellába ágyazni, vagy csatoljon egy VBA makrót, amely a beküldés előtt ellenőrzi az űrlapmezőket. Ugyanez a minta működik más ActiveX vezérlőkkel, például jelölőnégyzetekkel vagy kombinált listákkal – csak cserélje le a `Forms2OleControlType.COMMAND_BUTTON`-t a megfelelő enum értékre.

Ha bármilyen problémába ütközik, hagyjon megjegyzést alább. Boldog kódolást, és élvezze az automatizált Word-dokumentumkészítés erejét!

## Mit érdemes legközelebb megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to remove footers from Word documents using Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}