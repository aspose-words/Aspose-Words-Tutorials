---
category: general
date: 2026-08-07
description: Az Aspose.Words ActiveX útmutató bemutatja, hogyan lehet CommandButton
  vezérlőt hozzáadni egy Word dokumentumhoz Java használatával. Ismerje meg a teljes
  kódot, a konfigurációt és a mentési lépéseket.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: hu
lastmod: 2026-08-07
og_description: Az Aspose.Words ActiveX útmutató bemutatja, hogyan lehet egy CommandButton
  ActiveX vezérlőt beágyazni egy Word dokumentumba Java használatával. Kövesse a teljes
  példát a dokumentum létrehozásához, konfigurálásához és mentéséhez.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX oktatóanyag – Java lépésről‑lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX útmutató – CommandButton beszúrása Java-val
url: /hu/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX oktató – CommandButton beszúrása Java-val

Ha ActiveX vezérlőt kell beágyazni egy Word fájlba, ez a **Aspose.Words ActiveX oktató** végigvezet a teljes folyamaton. Megmutatja, hogyan hozhatsz létre egy üres dokumentumot, szúrj be egy CommandButton‑t, állítsd be a tulajdonságait, és mentsd el az eredményt – mindezt egyszerű Java kóddal.

A példa az Aspose.Words for Java API‑t használja, amelynek köszönhetően nincs szükség Microsoft Office‑ra a build szerveren. A útmutató végére képes leszel .docx fájlokat generálni, amelyek teljesen működőképes CommandButton vezérlőket tartalmaznak, készen állva a Windows környezetben való használatra.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következőkkel rendelkezel:

- Java Development Kit (JDK) 8 vagy újabb telepítve.
- Maven vagy más build eszköz a függőségek kezeléséhez.
- Aspose.Words for Java licenc (vagy ideiglenes értékelő kulcs) a vízjelek elkerüléséhez.
- Alapvető ismeretek a Java szintaxisról és az objektum‑orientált programozásról.

> **Pro tipp:** Add hozzá az Aspose.Words Maven függőséget a `pom.xml`‑hez, hogy az IDE automatikusan feloldja az osztályokat:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## 1. lépés: Új üres dokumentum és egy `DocumentBuilder` létrehozása

A `Document` osztály a Word fájlt reprezentálja a memóriában, míg a `DocumentBuilder` egy folyékony API‑t biztosít a dokumentum szerkesztéséhez. Mindkét objektum inicializálása felkészíti a dokumentumot a további módosításokra.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Miért fontos ez:**  
A `DocumentBuilder` nyomon követi az aktuális kurzorpozíciót, így minden későbbi beszúrási művelet – például egy vezérlő hozzáadása – pontosan ott jelenik meg, ahol szeretnéd.

## 2. lépés: CommandButton ActiveX vezérlő beszúrása

Az Aspose.Words a `Forms2OleControl`‑t teszi elérhetővé ActiveX objektumokhoz. Az `insertForms2OleControl` metódus megköveteli a vezérlő típusát, amelyet a `Forms2OleControlType` felsorolás segítségével adsz meg.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Magyarázat:**  
A beszúrt vezérlő egy COM‑alapú objektum, amelyet a Word kattintható gombként jelenít meg, amikor a dokumentumot Windows környezetben nyitják meg.

## 3. lépés: A gomb tulajdonságainak beállítása

A beszúrás után módosíthatod a gomb nevét, feliratát, méretét és pozícióját. Ezek a tulajdonságok befolyásolják, hogyan néz ki és viselkedik a vezérlő a Wordben.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Miért fontosak ezek a beállítások:**  

- **Name** – Lehetővé teszi, hogy a VBA makrók hivatkozzanak a vezérlőre (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Meghatározza a felhasználók által kattintott látható feliratot.
- **Left / Top** – A pozíciót a lap margójához viszonyítva szabályozza.
- **Width / Height** – Biztosítja a konzisztens vizuális méretet különböző képernyőfelbontásokon.

## 4. lépés: Dokumentum mentése

A `save` hívás a memóriában lévő ábrázolást egy fizikai fájlba írja. Bármely támogatott formátumot választhatsz (`.docx`, `.doc`, `.pdf`, stb.). Ebben az oktatóban a natív Word formátumot használjuk.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Eredmény:**  
A `ActiveXDemo.docx` megnyitása a Microsoft Word‑ben egy **Submit** feliratú CommandButton‑t jelenít meg a megadott koordinátákon. A gombra kattintva az alapértelmezett viselkedés lép életbe (alapértelmezés szerint nincs VBA kód csatolva).

## Teljes forráskód

Az egyes részek összeillesztésével a teljes, futtatható program a következő:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Várható kimenet

- Egy **ActiveXDemo.docx** nevű fájl az `output` mappában.
- Amikor Microsoft Word‑ben (Windows) megnyitod, a dokumentum egy kattintható **Submit** gombot mutat a megadott helyen.
- A gomb kiválasztható, áthelyezhető, vagy a Word UI‑ból (Fejlesztő → Tulajdonságok) VBA kódhoz kapcsolható.

## Gyakori változatok kezelése

| Forgatókönyv | Módosítás |
|--------------|-----------|
| **Save as .doc** (legacy format) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Add an event handler** | A Word nem teszi elérhetővé az ActiveX eseményeket az Aspose.Words‑on keresztül. VBA kódot manuálisan kell hozzáadni a dokumentum generálása után. |
| **Multiple controls** | Ismételd meg a beszúrási/konfigurációs blokkot különböző `setName` és `setCaption` értékekkel. |
| **Different control type (e.g., CheckBox)** | Használd a `Forms2OleControlType.CHECKBOX` értéket az `insertForms2OleControl` hívásban. |
| **Non‑Windows platforms** | Az ActiveX vezérlők csak Windows Word‑ben jelennek meg. Keresztplatformos megoldásokhoz fontold meg a tartalomvezérlőket (`StructuredDocumentTag`). |

## Legjobb gyakorlatok és buktatók

- **License early** – Regisztráld az Aspose.Words licencet a `Document` létrehozása előtt, hogy elkerüld az értékelő figyelmeztetéseket.
- **Coordinate system** – A pozíciók pontban (1 pt = 1/72 in) vannak megadva. Konvertálj pixelből vagy centiméterből, ha a UI‑d más egységeket használ.
- **File paths** – Használj abszolút útvonalakat vagy a Java `Paths` API‑t, hogy elkerüld a `FileNotFoundException`‑t, ha a kimeneti könyvtár nem létezik.
- **Thread safety** – A `Document` és a `DocumentBuilder` nem szálbiztos. Hozz létre különálló példányokat szálanként, ha párhuzamosan generálsz dokumentumokat.
- **Testing** – Ellenőrizd a generált dokumentumot a cél Word‑verzión (pl. Word 2016, Word 365), mivel a régebbi verziók másként jeleníthetik meg az ActiveX vezérlőket.

## Összegzés

Ez a **Aspose.Words ActiveX oktató** bemutatja, hogyan adhatunk programozottan CommandButton vezérlőt egy Word dokumentumhoz Java használatával. Megtanultad, hogyan:

1. Inicializáld a `Document` és `DocumentBuilder` objektumokat.
2. Szúrd be a `Forms2OleControl`‑t `COMMAND_BUTTON` típusban.
3. Állítsd be a gomb nevét, feliratát, méretét és pozícióját.
4. Mentsd el a dokumentumot .docx formátumban, amely tartalmazza az ActiveX vezérlőt.

Innen tovább felfedezheted a különböző vezérlőtípusokat, automatizálhatod a VBA makrók beillesztését, vagy kombinálhatod az ActiveX vezérlőket más Aspose.Words funkciókkal, például levélösszevonással és tartalomvezérlőkkel. Kísérletezz különböző elrendezésekkel, és integráld a generált dokumentumokat a nagyobb Java‑alapú jelentéskészítő folyamatodba.

---


## Mi legyen a következő tanulnivaló?

Az alábbi oktatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convert Word to RTF with Aspose.Words for Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}