---
category: general
date: 2026-10-07
description: ActiveX parancsgomb létrehozása Java-ban, és programozottan parancsgomb
  hozzáadása Word-dokumentumokhoz. Tanulja meg, hogyan állítható be a gomb bal felső
  pozíciója.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: hu
lastmod: 2026-10-07
og_description: Készíts ActiveX parancsgombot Java-ban, hogy interaktív vezérlőket
  ágyazhass be Word dokumentumaidba. Tanuld meg, hogyan adhatod hozzá programozottan
  a parancsgombot, állíthatod be a pozícióját, és testreszabhatod a megjelenését.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: ActiveX parancsgomb létrehozása Java-ban – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Hogyan hozhatunk létre ActiveX parancsgombot Java-ban
url: /hu/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre ActiveX parancsgombot Java-ban

Ha **ActiveX parancsgombot** szeretnél létrehozni egy Word dokumentumban Java segítségével, ez az útmutató pontosan megmutatja, hogyan. Megtekintheted a teljes, futtatható példát, amely **programozottan hozzáad egy parancsgombot**, a `setLeft` és `setTop` metódusokkal pozicionálja, és `.docx` fájlként menti el az eredményt.

Egy interaktív gomb beágyazása lehetővé teszi űrlapok építését, munkafolyamatok automatizálását vagy a felhasználói bemenet közvetlen gyűjtését egy Word fájlban. Az alábbi lépések mindent lefednek a projekt beállításától a végső ellenőrzésig, így a kódot egyszerűen átmásolhatod a saját projektedbe anélkül, hogy bármit kihagynál.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következők telepítve vannak:

- JDK 17 vagy újabb  
- Maven 3.8+ (vagy a kedvenc build eszközöd)  
- Aspose.Words for Java 23.9 vagy újabb – a könyvtár, amely biztosítja a `DocumentBuilder` és az OLE vezérlő támogatást  
- Alapvető ismeretek a Java szintaxisról és az objektum‑orientált koncepciókról  

Ha Maven‑t használsz, add hozzá a függőséget a `pom.xml` fájlodhoz:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Pro tip:** Használd az Aspose.Words legújabb verzióját a hibajavítások és az új OLE funkciók kihasználásához.

## 1. lépés: Új üres dokumentum és DocumentBuilder létrehozása

Az első lépés a **ActiveX parancsgomb létrehozásához** egy üres `Document` és egy `DocumentBuilder` példányosítása. A builder egy folyékony API‑t biztosít a tartalom beszúrásához, beleértve az OLE vezérlőket is.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A `Document` a Word fájlt reprezentálja a memóriában, míg a `DocumentBuilder` egy kurzorként működik, amely lehetővé teszi az elemek pontos elhelyezését.

## 2. lépés: OLE parancsgomb vezérlő beszúrása

Az ActiveX vezérlőket OLE objektumként szúrjuk be. Az Aspose.Words a `Forms2OleControl` osztályt biztosítja erre a célra.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Amikor meghívod a `insertForms2OleControl()` metódust, az Aspose automatikusan létrehoz egy helyőrző alakzatot, amely a ActiveX gombot fogja tartalmazni.

## 3. lépés: A gomb tulajdonságainak beállítása

Most **programozottan hozzáadod a parancsgomb** részleteit, például a ProgID‑t, a feliratot és a méretet. A leggyakoribb ProgID egy parancsgombhoz a `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Hogyan állítsuk be a gomb bal‑felső koordinátáit

A gomb pozicionálása az a pont, ahol a **how to set button left top** kulcsszó releváns lesz. A `setLeft` és `setTop` metódusok pontban (1 pont = 1/72  hüvelyk) megadott értékeket várnak.

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Ezeket a számokat a saját elrendezésedhez igazíthatod. Például, ha a gombot egy táblázatcellához szeretnéd igazítani, számold ki a cella koordinátáit, és add át őket a `setLeft`/`setTop` metódusoknak.

## 4. lépés: Dokumentum mentése

Végül írd a dokumentumot a lemezre. A fájl tartalmazni fogja a ActiveX gombot, amely a Microsoft Word‑ben megnyitáskor interaktív lesz.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

A `main` metódus futtatása `CommandButton.docx` fájlt hoz létre. Nyisd meg a fájlt Word‑ben, engedélyezd a tartalmat, ha a program kéri, és egy **Click Me** feliratú kattintható gombot látsz a megadott koordinátákon.

![ActiveX parancsgomb létrehozása Java-ban](/images/activex-button-screenshot.png){.center width=600 alt="ActiveX parancsgomb létrehozása Java-ban képernyőkép, amely a gombot mutatja a Word dokumentumban"}

## Gyakori variációk és szélhelyzetek

### Több gomb hozzáadása

Ha több gombra van szükséged, ismételd meg a **2. lépést** és a **3. lépést** minden egyes vezérlőnél. Ne felejtsd el módosítani a `setLeft` és `setTop` értékeket, hogy a gombok ne fedjék egymást.

### A gomb viselkedésének módosítása

Az ActiveX gombok VBA makrókat futtathatnak kattintáskor. Makró csatolásához állítsd be a `setOnAction` tulajdonságot a makró nevével:

```java
commandButton.setOnAction("MyMacro");
```

Győződj meg róla, hogy a cél dokumentum tartalmazza a megfelelő VBA modult; ellenkező esetben a Word hibát jelez.

### Kompatibilitási megjegyzések

- A gomb csak asztali Word‑verziókban működik, amelyek támogatják az ActiveX‑et (pl. Word Windows‑ra). Mac‑os vagy online szerkesztőkben statikus képként jelenik meg.  
- Ha vegyes környezetet célozol, fontold meg egy **tartalomvezérlő** (`RichTextContentControl`) használatát az ActiveX helyett.

## Teljes forráskód referenciaként

Az alábbiakban a komplett, önálló példa látható, amelyet egyszerűen bemásolhatsz egy új Maven projektbe, és azonnal futtathatsz.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Várt kimenet:** A futtatás után a projekt munkakönyvtárában megtalálod a `CommandButton.docx` fájlt. A Microsoft Word‑ben megnyitva a gomb a megadott helyen jelenik meg a „Click Me” felirattal.

## Összegzés

Most már tudod, hogyan **hozz létre ActiveX parancsgombot** Java‑ban, **programozottan adj hozzá parancsgombot** egy Word dokumentumhoz, és pontosan szabályozd a elhelyezését a **how to set button left top** módszerekkel. Ez a technika lehetővé teszi gazdag, interaktív Word űrlapok készítését, amelyek makrókat indíthatnak, külső alkalmazásokat indíthatnak el, vagy közvetlenül a dokumentumban gyűjthetik a felhasználói adatokat.

### Következő lépések

- Fedezd fel a többi ActiveX vezérlőt, például a `Forms.TextBox.1` vagy a `Forms.CheckBox.1` elemeket.  
- Kombináld több vezérlővel egy VBA modult, hogy teljes funkcionalitású űrlapokat hozz létre.  
- Cseréld le az ActiveX‑et tartalomvezérlőkre, ha platformközi kompatibilitásra van szükséged.  

Kísérletezz a mérettel, felirattal és pozicionálással, hogy a UI‑d tervezésének megfeleljen. Ha problémába ütközöl, ellenőrizd, hogy az általad használt Aspose.Words verzió támogatja-e az OLE vezérlőket, és hogy a Word biztonsági beállításai engedélyezik-e az ActiveX végrehajtását. Boldog kódolást!

## Mit tanulj meg legközelebb?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljesen működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek az API további funkcióinak elsajátításában és alternatív megvalósítási megközelítések felfedezésében a saját projektjeidben.

- [OLE objektumok és ActiveX vezérlők beágyazása Word dokumentumokba](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Űrlapmezők létrehozása és tartalom hozzáadása DocumentBuilderrel az Aspose.Words for Java‑ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Téglalap alakzat létrehozása Word‑ben Java‑val – Teljes útmutató](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}