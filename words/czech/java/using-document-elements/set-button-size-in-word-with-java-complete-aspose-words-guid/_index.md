---
category: general
date: 2026-07-16
description: Nastavte velikost tlačítka programově v dokumentu Word pomocí Aspose.Words
  pro Java. Naučte se, jak vložit ActiveX tlačítko, nastavit umístění tlačítka a další.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: cs
lastmod: 2026-07-16
og_description: Nastavte velikost tlačítka ve Word dokumentu pomocí Javy. Tento krok‑za‑krokem
  průvodce ukazuje, jak vložit ActiveX tlačítko, nastavit jeho umístění a programově
  přidat tlačítko.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Nastavte velikost tlačítka ve Wordu pomocí Javy – Kompletní tutoriál Aspose.Words
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
title: Nastavte velikost tlačítka ve Wordu pomocí Javy – Kompletní průvodce Aspose.Words
url: /cs/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení velikosti tlačítka ve Wordu pomocí Javy – Kompletní průvodce Aspose.Words

Už jste se někdy zamysleli, jak **set button size** uvnitř souboru Word bez otevření uživatelského rozhraní? Nejste v tom sami. Když potřebujete za běhu vygenerovat dokument s vyplněným formulářem – například uvítací balíček s tlačítkem „Submit“ – provedení toho programově ušetří hodiny ruční práce.

V tomto tutoriálu projdeme přesně kroky k **insert ActiveX button**, úpravě jeho rozměrů, správnému umístění a nakonec uložení souboru. Na konci budete schopni **programmatically add button** ovládací prvky do libovolného dokumentu Word pomocí Aspose.Words pro Java.

## Požadavky – Co potřebujete před začátkem

- **Java Development Kit (JDK) 8+** – kód běží na jakémkoli aktuálním JDK.
- **Aspose.Words for Java** knihovna (stáhněte nejnovější JAR z oficiální stránky).  
- **IDE** dle vašeho výběru – IntelliJ IDEA, Eclipse nebo i jednoduchý textový editor funguje.
- Základní znalost syntaxe Javy; není vyžadována hluboká znalost Word‑automatizace.

> *Tip:* Udržujte Aspose.Words JAR ve classpath vašeho projektu, jinak narazíte na `ClassNotFoundException` ve chvíli, kdy se pokusíte importovat `com.aspose.words.*`.

## Krok 1: Vytvoření nového dokumentu Word

Prvním krokem je vytvořit prázdný dokument a `DocumentBuilder`. Představte si builder jako pero, které nám umožňuje kreslit cokoliv uvnitř souboru.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Proč je to důležité:** Objekt `Document` představuje celý soubor .docx, zatímco `DocumentBuilder` je hlavní nástroj, který nám umožňuje vkládat odstavce, tabulky a — ano — ActiveX ovládací prvky.

## Krok 2: Vložení ActiveX tlačítka – Moment „Insert ActiveX Button“

Nyní skutečně **insert activex button** do dokumentu. Aspose.Words poskytuje pohodlnou metodu `insertForms2OleControl`, která vrací objekt `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Co se děje pod kapotou?* `Forms2OleControlType.COMMAND_BUTTON` říká Wordu, že chceme klasické CommandButton, stejný typ, jaký byste vložili z karty Developer v UI.

## Krok 3: Nastavení velikosti a umístění tlačítka – Jádro logiky „Set Button Size“

Zde se ukáže hlavní klíčové slovo. **set button size** a také **set button location** nastavíme tak, aby se ovládací prvek objevil přesně tam, kde jej na stránce chceme.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Proč by vás to mělo zajímat:** Body jsou nativní jednotkou měření ve Wordu (1 point = 1/72 palce). Úpravou `setLeft`, `setTop`, `setWidth` a `setHeight` získáte pixel‑dokonalou kontrolu — už žádné „vypadá to dobře na obrazovce, ale ne na tiskárně“.

> *Častý úskalí:* Zapomenutí nastavit šířku nebo výšku ponechá tlačítko ve výchozí velikosti, která může být příliš malá na kliknutí. Vždy specifikujte obojí.

## Krok 4: Uložení dokumentu – „Create Word Document Button“ dokončeno

Nakonec zapíšeme soubor na disk. Název naznačuje, že **creating a Word document button** uvnitř .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Když otevřete `CommandButtonDemo.docx` v Microsoft Word, uvidíte tlačítko **Submit** umístěné 100 pt od levého okraje a 150 pt od horního, o rozměrech 80 × 30 pt. Kliknutí na něj v UI spustí výchozí chování ActiveX (které můžete později propojit s VBA, pokud bude potřeba).

### Očekávaný výstup – Screenshot

![Word dokument zobrazující vložené tlačítko s nastavenou velikostí tlačítka](https://example.com/images/set-button-size.png "Screenshot Word souboru, kde byla velikost tlačítka nastavena pomocí Aspose.Words pro Java")

*Alt text:* nastavení velikosti tlačítka ve Word dokumentu pomocí Javy

## Krok 5 (volitelně): Přidat další ovládací prvky nebo stylovat tlačítko

Pokud potřebujete **programmatically add button** ovládací prvky nad rámec jednoho tlačítka Submit, stačí zopakovat blok vložení s novými názvy a popisky. Můžete také upravit písmo, barvu pozadí nebo později připojit VBA makra.

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

> *Tip:* Udržujte všechny rozměry tlačítek konzistentní pro profesionální vzhled. Rychlý způsob je uložit šířku/výšku do konstant.

## Časté otázky a okrajové případy

### „Mohu nastavit velikost tlačítka pomocí centimetrů místo bodů?“

API Wordu přijímá pouze body, ale můžete převést centimetry na body (`points = cm * 28.3465`). Napište malou pomocnou metodu, pokud dáváte přednost metrickým jednotkám.

### „Co když potřebuji, aby se tlačítko objevilo na konkrétní stránce?“

Po vložení tlačítka můžete přesunout kurzor na konkrétní stránku pomocí `builder.moveToPage(pageNumber)`. Vložte ovládací prvek hned po přesunu a poté nastavte jeho umístění, jak je uvedeno výše.

### „Funguje to s .doc (Word 97‑2003) soubory?“

Ano—Aspose.Words automaticky zpracovává starší formáty. Stačí změnit příponu souboru v `doc.save("Demo.doc")`.

## Kompletní, spustitelný příklad

Níže je celý program, který můžete zkopírovat a vložit do třídy Java a okamžitě spustit (za předpokladu, že Aspose.Words JAR je na classpath).

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

Spusťte program, otevřete vygenerovaný `CommandButtonDemo.docx` a uvidíte dvě pěkně velikostně nastavená tlačítka připravená k interakci.

## Závěr – Ovládáte nastavení velikosti tlačítka ve Wordu

Právě jsme prošli kompletním řešením od začátku do konce pro **set button size** a **set button location** pomocí Aspose.Words pro Java. Dodržením kroků můžete **insert activex button**, **programmatically add button** ovládací prvky a nakonec **create word document button** elementy, které se chovají přesně tak, jak potřebujete.

Co dál? Zkuste vložit tlačítko do buňky tabulky nebo připojit VBA makro, které před odesláním ověří pole formuláře. Stejný vzor funguje i pro jiné ActiveX ovládací prvky, jako jsou zaškrtávací políčka nebo rozbalovací seznamy – stačí vyměnit `Forms2OleControlType.COMMAND_BUTTON` za odpovídající hodnotu výčtu.

Pokud narazíte na nějaké potíže, zanechte komentář níže. Šťastné kódování a užívejte si sílu automatizovaného vytváření Word dokumentů!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak nastavit LoadOptions v Aspose.Words pro Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Jak odstranit zápatí z Word dokumentů pomocí Aspose.Words pro Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java: Kompletní průvodce zpracováním Word dokumentů](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}