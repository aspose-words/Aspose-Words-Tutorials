---
category: general
date: 2026-10-20
description: Programozott módon hozzon létre egy üres DOCX-et, és ágyazzon be egy
  parancsgombot Java-val. Ismerje meg a teljes Word dokumentum létrehozó kódot, amely
  a gombbal menti a Word-öt, és beállítja a parancsgomb feliratát.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: hu
lastmod: 2026-10-20
og_description: Hozzon létre programozottan egy üres DOCX fájlt, és ágyazzon be egy
  parancsgombot. Kövesse ezt a lépésről‑lépésre útmutatót Java nyelven, hogy a Word
  dokumentumot gombbal mentse, és beállítsa a parancsgomb feliratát.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Üres DOCX létrehozása programozott módon – parancsgomb hozzáadása
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Üres DOCX létrehozása programozott módon és parancsgomb hozzáadása
url: /hu/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres DOCX létrehozása programozottan és parancsgomb hozzáadása

Ha **programozottan szeretne üres DOCX-et létrehozni**, ez a bemutató megmutatja, hogyan ágyazhat be egy parancsgombot közvetlenül a fájlba. Megkapja a teljes *create word document code* kódot, amely egy gombbal ellátott Word dokumentumot ment, lehetővé teszi a **set command button caption** beállítását, és a legújabb Aspose.Words for Java könyvtárral működik.

Az interaktív vezérlők DOCX fájlba ágyazása hasznos, ha sablonokat szeretne terjeszteni, amelyek makrókat indítanak, külső programokat indítanak el, vagy egyszerűen egy kattintható „Click Me” gombbal vezérlik a felhasználókat. Az alábbi lépések mindent lefednek az üres dokumentum inicializálásától a végső fájl lemezre mentéséig.

## Előkövetelmények

* Java 17 vagy újabb telepítve.
* Maven (vagy a kedvenc build eszközöd) a függőségek kezeléséhez.
* Aspose.Words for Java 23.9 vagy későbbi. Add hozzá a függőséget a `pom.xml`-hez:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Egy IDE, például IntelliJ IDEA vagy VS Code (bármely Java-t támogató szerkesztő megfelelő).

## Üres DOCX létrehozása programozottan – lépésről‑lépésre

Az alábbi szakaszok a folyamatot világos, számozott lépésekre bontják. Minden lépés elmagyarázza, **miért** szükséges, nem csak **mit** kell beírni.

### 1. lépés: Új üres dokumentum inicializálása

Az üres dokumentum a vászon, amelyre a parancsgombot helyezi. Az Aspose.Words a `Document` osztályt biztosítja erre a célra.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Miért fontos*: Egy üres `Document`-tel kezdve biztosítja, hogy semmilyen rejtett formázás vagy meglévő vezérlő ne zavarja a később hozzáadott gombot.

### 2. lépés: `DocumentBuilder` beállítása

`DocumentBuilder` egy segédeszköz, amely lehetővé teszi tartalom, köztük OLE vezérlők beszúrását anélkül, hogy alacsony szintű csomópontkezeléssel kellene foglalkozni.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Miért fontos*: A builder fenntartja az aktuális kurzorpozíciót, így a gomb pontosan oda kerül, ahová megadja.

### 3. lépés: OLE parancsgomb beszúrása

A Word az interaktív vezérlőket OLE (Object Linking and Embedding) objektumokként kezeli. Az Aspose.Words a `Forms2OleControl` osztályt biztosítja ehhez.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Miért fontos*: A vezérlő beszúrása egy helyőrzőt hoz létre, amelyet később konfigurálhat (típus, felirat, pozíció).

### 4. lépés: A gomb konfigurálása – típus, felirat és hely

Meg kell határozni a vezérlő típusát (`COMMANDBUTTON`), be kell állítani a felhasználó számára látható feliratot, és el kell helyezni az oldalon.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Miért fontos*:  
* **Type** (típus) azt mondja a Wordnek, hogy a vezérlő kattintható gombként viselkedik.  
* **Caption** (felirat) a felhasználó által látható szöveg; ennek módosítása a **set command button caption** beállítása.  
* **Left** és **Top** a pontos elhelyezést szabályozzák, ami elengedhetetlen, amikor **add command button word** dokumentumokat hoz létre, amelyeknek pontos elrendezésre van szükségük.

### 5. lépés: Dokumentum mentése a beágyazott gombbal

Végül írja a fájlt a lemezre. A kapott fájl megnyitható a Microsoft Wordben, ahol a gomb teljesen működőképes lesz.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Miért fontos*: Ez a lépés **saves Word with button**, így a vezérlő gépek között is megmarad. A fájl sablonként terjeszthető vagy automatizált jelentésgenerálási folyamatokban használható.

## Teljes működő példa

Másolja az alábbi teljes osztályt egy `CommandButtonDemo.java` nevű fájlba, állítsa be a `YOUR_DIRECTORY`-t egy valós útvonalra, és futtassa a `mvn compile exec:java` paranccsal.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Várt eredmény

Amikor megnyitja a `CommandButton.docx` fájlt a Microsoft Wordben:

* A dokumentum teljesen üres, kivéve egy **Click Me** feliratú gombot.
* A gombra kattintva a Word alapértelmezett viselkedése jelenik meg (semmit sem csinál, hacsak nincs makró csatolva), ami megerősíti, hogy az OLE vezérlő helyesen lett beágyazva.

## Gyakori kérdések és szélhelyzetek

| Question | Answer |
|----------|--------|
| **Módosíthatom a gomb méretét?** | Igen. Használja a `commandButton.setWidth(double)` és `commandButton.setHeight(double)` metódusokat a méretek pontban történő beállításához. |
| **Mi van, ha a gombhoz makrót kell csatolni?** | A gomb önmagában csak egy OLE vezérlő. VBA makrót kell manuálisan vagy az Aspose.Words `Document` API `addMacro` segédeszközeivel hozzáadni a dokumentumhoz. |
| **Működik a gomb a LibreOffice-ban?** | A LibreOffice korlátozott OLE vezérlőket támogat. A gomb megjelenik, de a kattintási viselkedése eltérhet. |
| **Hogyan adhatok hozzá több gombot?** | Ismételje meg a 3‑4. lépéseket egy új `Forms2OleControl` példánnyal. Állítsa be a `setLeft`/`setTop` értékeket minden gombnál, hogy elkerülje az átfedést. |
| **Kompatibilis a kód .NET‑tel?** | Ugyanez a logika érvényes, de a .NET osztályokhoz (`Document`, `DocumentBuilder`, `Forms2OleControl`) a `Aspose.Words` for .NET-et kell használni. |

## Tippek a gyakorlatból

* **Pro tip:** Használja a `builder.moveToDocumentEnd()`-et a gomb beszúrása előtt, ha azt a dokumentum teljes végére szeretné helyezni, függetlenül az előző tartalomtól.
* **Figyeljen:** Nagyon kis `Left`/`Top` értékek a gombot a nyomtatható területen kívülre helyezhetik, így az láthatatlan lesz a Word elrendezés nézetében.
* **Teljesítményjegyzet:** Sok OLE vezérlő beszúrása növelheti a fájlméretet. Ha csak vizuális jelzésre van szükség, fontolja meg egy egyszerű `Shape` használatát hiperhivatkozással.

## Következtetés

Most már tudja, hogyan **create a blank DOCX programmatically**, és hogyan ágyazhat be egy teljesen működő parancsgombot Java használatával. A bemutató lefedte a teljes *create word document code* munkafolyamatot, bemutatta, hogyan **save Word with button**, megmutatta a helyes módját a **add command button word** elemek hozzáadásának, és elmagyarázta, hogyan **set command button caption**.

Innen tovább:

* További OLE vezérlők (jelölőnégyzetek, kombinált listák) hozzáadása a gazdagabb űrlapokhoz.
* VBA makrók csatolása, hogy a gomb egyedi műveleteket hajtson végre.
* Ennek a technikának a kombinálása dokumentum levél-összevonással (mail‑merge) dinamikus, interaktív sablonokhoz.

Nyugodtan kísérletezzen a gomb stílusaival, pozícióival és további vezérlőkkel, hogy megfeleljenek az Ön konkrét üzleti igényeinek. Boldog kódolást


## Mit érdemes legközelebb megtanulni?

Az alábbi bemutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Üres Word dokumentum létrehozása parancsgombbal – lépésről‑lépésre útmutató](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Hogyan szúrjon be ActiveX gombot a Wordben – Gombfelirat beállítása](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Üres Word dokumentum létrehozása Java-val – Teljes Aspose.Words útmutató](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}