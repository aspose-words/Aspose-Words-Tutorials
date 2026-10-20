---
category: general
date: 2026-10-20
description: Vytvořte prázdný DOCX programově a vložte příkazové tlačítko pomocí Javy.
  Naučte se kompletní kód pro vytvoření Word dokumentu, který uloží Word s tlačítkem
  a nastaví popisek příkazového tlačítka.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: cs
lastmod: 2026-10-20
og_description: Vytvořte prázdný DOCX programově a vložte příkazové tlačítko. Postupujte
  podle tohoto podrobného průvodce v Javě, jak uložit Word s tlačítkem a nastavit
  popisek příkazového tlačítka.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Vytvořte prázdný DOCX programově – přidejte příkazové tlačítko
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
title: Vytvořte prázdný DOCX programově a přidejte příkazové tlačítko
url: /cs/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný DOCX programově a přidejte tlačítko příkazu

Pokud potřebujete **vytvořit prázdný DOCX programově**, tento tutoriál vám ukáže, jak vložit tlačítko příkazu přímo do souboru. Získáte kompletní *create word document code*, který uloží Word dokument s tlačítkem, umožní vám **nastavit popisek tlačítka příkazu** a funguje s nejnovější knihovnou Aspose.Words pro Java.

Vkládání interaktivních ovládacích prvků do souboru DOCX je užitečné, když chcete distribuovat šablony, které spouštějí makra, spouštějí externí programy nebo jednoduše vedou uživatele pomocí klikatelného tlačítka „Click Me“. Níže uvedené kroky pokrývají vše od inicializace prázdného dokumentu po uložení finálního souboru na disk.

## Požadavky

* Java 17 nebo novější nainstalováno.
* Maven (nebo váš preferovaný nástroj pro sestavení) pro správu závislostí.
* Aspose.Words pro Java 23.9 nebo novější. Přidejte závislost do vašeho `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* IDE jako IntelliJ IDEA nebo VS Code (jakýkoli editor, který podporuje Javu, funguje).

## Vytvoření prázdného DOCX programově – krok za krokem

Následující sekce rozdělují proces do přehledných, číslovaných kroků. Každý krok vysvětluje **proč** je potřeba, ne jen **co** napsat.

### Krok 1: Inicializace nového prázdného dokumentu

Prázdný dokument je plátno, na které umístíte tlačítko příkazu. Aspose.Words poskytuje třídu `Document` pro tento účel.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Proč je to důležité*: Začátek s prázdným `Document` zajišťuje, že žádné skryté formátování nebo existující ovládací prvky nebudou rušit tlačítko, které později přidáte.

### Krok 2: Nastavení `DocumentBuilder`

`DocumentBuilder` je pomocník, který vám umožní vkládat obsah, včetně OLE ovládacích prvků, aniž byste museli manipulovat s nízkoúrovňovými uzly.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Proč je to důležité*: Builder udržuje aktuální pozici kurzoru, takže tlačítko bude umístěno přesně tam, kde určíte.

### Krok 3: Vložení OLE tlačítka příkazu

Word zachází s interaktivními ovládacími prvky jako s OLE (Object Linking and Embedding) objekty. Aspose.Words pro to poskytuje `Forms2OleControl`.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Proč je to důležité*: Vložení ovládacího prvku vytvoří zástupný objekt, který můžete později konfigurovat (typ, popisek, umístění).

### Krok 4: Konfigurace tlačítka – typ, popisek a umístění

Musíte definovat typ ovládacího prvku (`COMMANDBUTTON`), nastavit popisek viditelný pro uživatele a umístit jej na stránku.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Proč je to důležité*:  
* **Type** říká Wordu, že ovládací prvek se chová jako klikatelné tlačítko.  
* **Caption** je text, který uživatel vidí; jeho změna je způsob, jak **nastavit popisek tlačítka příkazu**.  
* **Left** a **Top** řídí přesné umístění, což je zásadní, když **add command button word** dokumenty, které potřebují přesné rozložení.

### Krok 5: Uložení dokumentu s vloženým tlačítkem

Nakonec zapíšete soubor na disk. Výsledný soubor lze otevřít v Microsoft Wordu, kde bude tlačítko plně funkční.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Proč je to důležité*: Tento krok **saves Word with button** takže ovládací prvek přetrvává napříč počítači. Soubor může být distribuován jako šablona nebo použit v automatizovaných pipelinech pro generování reportů.

## Kompletní funkční příklad

Zkopírujte celou třídu níže do souboru pojmenovaného `CommandButtonDemo.java`, upravte `YOUR_DIRECTORY` na skutečnou cestu a spusťte ji pomocí `mvn compile exec:java`.

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

### Očekávaný výsledek

Když otevřete `CommandButton.docx` v Microsoft Wordu:

* Dokument je zcela prázdný kromě tlačítka označeného **Click Me**.
* Kliknutí na tlačítko zobrazí výchozí chování Wordu (nedělá nic, pokud není připojeno makro), což potvrzuje, že OLE ovládací prvek byl správně vložen.

## Časté otázky a okrajové případy

| Question | Answer |
|----------|--------|
| **Mohu změnit velikost tlačítka?** | Ano. Použijte `commandButton.setWidth(double)` a `commandButton.setHeight(double)` pro úpravu rozměrů v bodech. |
| **Co když potřebuji k tlačítku připojit makro?** | Tlačítko samo o sobě je jen OLE ovládací prvek. Musíte do dokumentu přidat VBA makro ručně nebo pomocí utilit `addMacro` API `Document` v Aspose.Words. |
| **Bude tlačítko fungovat v LibreOffice?** | LibreOffice podporuje omezené OLE ovládací prvky. Tlačítko se zobrazí, ale jeho chování při kliknutí se může lišit. |
| **Jak přidat více tlačítek?** | Opakujte kroky 3‑4 s novou instancí `Forms2OleControl`. Upravte `setLeft`/`setTop` pro každé tlačítko, aby nedocházelo k překrytí. |
| **Je kód kompatibilní s .NET?** | Stejná logika platí, ale použijete třídy `Aspose.Words` pro .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Tipy z praxe

* **Pro tip:** Použijte `builder.moveToDocumentEnd()` před vložením tlačítka, pokud jej chcete mít úplně na konci dokumentu, bez ohledu na předchozí obsah.
* **Dejte si pozor na:** Velmi malé hodnoty `Left`/`Top` mohou umístit tlačítko mimo tisknutelnou oblast, což jej učiní neviditelným v náhledu rozložení ve Wordu.
* **Poznámka k výkonu:** Vkládání mnoha OLE ovládacích prvků může zvětšit velikost souboru. Pokud potřebujete jen vizuální indikaci, zvažte použití obyčejného `Shape` s hypertextovým odkazem.

## Závěr

Nyní víte, jak **vytvořit prázdný DOCX programově** a vložit plně funkční tlačítko příkazu pomocí Javy. Tutoriál pokryl celý workflow *create word document code*, ukázal, jak **save Word with button**, předvedl správný způsob **add command button word** prvků a vysvětlil, jak **set command button caption**.

Odtud můžete:

* Přidat více OLE ovládacích prvků (zaškrtávací políčka, rozbalovací seznamy) pro bohatší formuláře.
* Připojit VBA makra, aby tlačítko provádělo vlastní akce.
* Kombinovat tuto techniku s hromadnou korespondencí dokumentů pro dynamické, interaktivní šablony.

Neváhejte experimentovat se styly tlačítek, pozicemi a dalšími ovládacími prvky, aby odpovídaly vašim konkrétním obchodním požadavkům. Šťastné programování

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořte prázdný Word dokument s tlačítkem příkazu – krok za krokem průvodce](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Jak vložit ActiveX tlačítko do Wordu – nastavit popisek tlačítka](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Vytvořte prázdný Word dokument pomocí Javy – kompletní průvodce Aspose.Words](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}