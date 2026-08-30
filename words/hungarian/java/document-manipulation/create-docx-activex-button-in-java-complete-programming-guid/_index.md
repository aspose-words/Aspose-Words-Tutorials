---
category: general
date: 2026-08-14
description: Hozzon létre docx ActiveX gombot Java-ban az Aspose.Words segítségével.
  Tanulja meg, hogyan adhat hozzá űrlapgombot a Word dokumentumhoz programozottan,
  és mentse el a dokumentumot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: hu
lastmod: 2026-08-14
og_description: Docx ActiveX gomb létrehozása Java-ban az Aspose.Words segítségével.
  Ez az útmutató bemutatja, hogyan adhat hozzá űrlapgombot a Word dokumentumhoz, hogyan
  konfigurálja, és hogyan menti a fájlt.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: docx ActiveX gomb létrehozása Java-ban – lépésről‑lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Docx ActiveX gomb létrehozása Java-ban – teljes programozási útmutató
url: /hu/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx ActiveX gomb létrehozása Java-ban – teljes programozási útmutató

Ha Java-ban **create docx ActiveX button** kell létrehoznod, ez az útmutató végigvezet a teljes folyamaton. Megmutatja, hogyan adhatunk hozzá egy űrlapgombot a Word-hez, hogyan konfiguráljuk a tulajdonságait, és hogyan állítsunk elő egy használatra kész .docx fájlt.

Az ActiveX vezérlőkkel való munka gyakori követelmény a régi Word űrlapok automatizálásakor. Ebben az útmutatóban megtanulod, hogyan **add form button word** dokumentumokban használhatod az Aspose.Words for Java könyvtárat, így interaktív vezérlőket ágyazhatsz be manuális szerkesztés nélkül.

## Amire szükséged lesz

* Java 17 vagy újabb (a kód korábbi verziókkal is lefordítható, de a Java 17 ajánlott).
* Aspose.Words for Java 23.10 vagy újabb – töltsd le a JAR-t az Aspose weboldaláról, vagy add hozzá a Maven függőséget.
* IDE (IntelliJ IDEA, Eclipse vagy VS Code) vagy egyszerű szövegszerkesztő és parancssori build eszközök.
* Alapvető ismeretek a Java szintaxisról és az objektum‑orientált programozásról.

## Hogyan hozzunk létre docx ActiveX gombot az Aspose.Words segítségével

A következő lépések mutatják a pontos sorrendet, amely szükséges a **create docx ActiveX button** objektumok létrehozásához és Word dokumentumba ágyazásához.

### 1. lépés: A projekt beállítása és az Aspose.Words importálása

Add hozzá az Aspose.Words függőséget a `pom.xml`-hez, ha Maven-t használsz:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Vagy, ha a Gradle-t részesíted előnyben:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Miután a függőség feloldódott, importáld a szükséges osztályokat a Java forrásfájlodba:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Ezek az importok hozzáférést biztosítanak a `Document`, `DocumentBuilder` és a `Forms2OleControl` API-hoz, amelyet az ActiveX vezérlők beszúrásához használnak.

### 2. lépés: Új üres dokumentum létrehozása

Példányosíts egy `Document` objektumot, amely egy üres Word fájlt képvisel, készen áll a tartalom fogadására.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

A dokumentum előzetes létrehozása biztosítja, hogy a későbbi builder egy tiszta vásznon dolgozzon.

### 3. lépés: DocumentBuilder inicializálása

`DocumentBuilder` folyékony interfészt biztosít szöveg, kép és vezérlők beszúrásához. Kapcsold a most létrehozott dokumentumhoz.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

A builder nyomon követi a dokumentumban lévő aktuális kurzorpozíciót, így a következő beszúrás pontosan oda kerül, ahová szükséges.

### 4. lépés: ActiveX CommandButton vezérlő beszúrása

Használd az `insertForms2OleControl` metódust egy ActiveX `CommandButton` beágyazásához. Ez a metódus egy `Forms2OleControl` példányt ad vissza, amelyet tovább konfigurálhatsz.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

Ekkor a .docx fájl tartalmaz egy helyőrzőt a gomb számára, de még nincs vizuális felirata vagy mérete.

### 5. lépés: A gomb tulajdonságainak beállítása

Állítsd be a vezérlő nevét, feliratát és elrendezési attribútumait. Ezek az értékek határozzák meg, hogyan jelenik meg a gomb a Word-ben, és hogyan hivatkozhatsz rá később VBA vagy automatizálási szkriptek segítségével.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Pro tip:** A Word a pozíciókat pontban méri (1 pt ≈ 1/72 in). Állítsd be a `setTop` és `setLeft` értékeket, hogy a gombot a környező tartalommal igazítsd.

### 6. lépés: Dokumentum mentése

Végül írd a dokumentumot a lemezre. Használd a `.docx` kiterjesztést, hogy a fájl a modern Office Open XML formátumban maradjon.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Amikor megnyitod a keletkezett fájlt a Microsoft Wordben, egy **Submit** gombot látsz a megadott koordinátákon. A gomb kattintása a Wordben nem vált ki semmilyen műveletet, hacsak nem csatolsz VBA kódot, de a vezérlő teljesen működőképes űrlap‑alapú munkafolyamatokhoz.

## Gyakori kérdések és szélhelyzetek

| Question | Answer |
|----------|--------|
| **Szükségem van speciális Word verzióra?** | Az ActiveX vezérlők a Windows-on futó Microsoft Word asztali verziójában támogatottak. Nem érhetők el a Mac-re vagy a Word Online-ra. |
| **Használhatom ezt `.doc` fájlokkal?** | Igen. Mentsd a dokumentumot `.doc` kiterjesztéssel (`document.save("ActiveXButton.doc")`). Ugyanaz az API működik a régebbi bináris formátummal is. |
| **Mi van, ha a gomb nem jelenik meg?** | Győződj meg arról, hogy a **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** engedélyezi az ActiveX vezérlőket. Ellenőrizd továbbá, hogy a dokumentum nincs‑e „Protected View” módban megnyitva. |
| **Hozzáadhatok más ActiveX vezérlőket?** | Természetesen. Cseréld le a `Forms2OleControlType.COMMAND_BUTTON`-t `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` stb. értékekre. |
| **Van méretkorlát?** | A vezérlő mérete csak a lapelrendezés által korlátozott. Nagyon nagy méretek esetén előfordulhat, hogy a layout túlcsordul. |

## Teljes, futtatható példa

Az alábbiakban egy teljes Java osztály található, amelyet másolhatsz, lefordíthatsz és futtathatsz. Tartalmazza az összes importot, a main metódust és a beágyazott megjegyzéseket a tisztaság kedvéért.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Várható eredmény:** A program futtatása után a `ActiveXButton.docx` megjelenik a munkakönyvtárban. A Microsoft Wordben megnyitva egy kattintható **Submit** gombot látsz, amely az első oldal bal‑felső közelében helyezkedik el.

## Következtetés

Most már tudod, hogyan **create docx ActiveX button** objektumokat hozhatsz létre Java-ban az Aspose.Words segítségével, és láttad, hogyan **add form button word** dokumentumokba programozottan illesztheted be őket. A lépések – a projekt beállítása, dokumentum létrehozása, a vezérlő beszúrása, tulajdonságainak konfigurálása és mentése – lefedik a teljes munkafolyamatot az elejétől a végéig.

Ezután érdemes lehet:

* VBA makrók hozzáadása, amelyek reagálnak a gombkattintásra.
* Más ActiveX vezérlők beágyazása, például jelölőnégyzetek vagy listamezők.
* Többoldalas űrlapok generálásának automatizálása több interaktív elemmel.

Nyugodtan kísérletezz a méretekkel, pozíciókkal és feliratokkal, hogy megfeleljenek a konkrét űrlaptervezési igényeidnek. Boldog kódolást!

## Mit érdemes következőként megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}