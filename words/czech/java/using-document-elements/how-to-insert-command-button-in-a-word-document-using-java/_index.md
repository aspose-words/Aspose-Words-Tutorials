---
category: general
date: 2026-08-23
description: Naučte se, jak vložit příkazové tlačítko do dokumentu Word pomocí Javy
  a Aspose.Words. Tento průvodce ukazuje, jak přidat ovládací prvek formuláře, nastavit
  název tlačítka a vložit ActiveX tlačítko.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: cs
lastmod: 2026-08-23
og_description: Vložte příkazové tlačítko do dokumentu Word pomocí Javy. Postupujte
  podle tohoto návodu, abyste přidali ovládací prvek formuláře, nastavili název tlačítka
  a vložili ActiveX tlačítko pomocí Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Vložení příkazového tlačítka do Wordu pomocí Javy – krok za krokem
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
title: Jak vložit tlačítko příkazu do dokumentu Word pomocí Javy
url: /cs/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit command button do dokumentu Word pomocí Java

Pokud potřebujete **vložit command button** do souboru Word, tento tutoriál vám ukáže kompletní řešení s Aspose.Words for Java. Uvidíte, jak přidat form control, nakonfigurovat jeho popisek a nastavit název tlačítka, aniž byste opustili své IDE.

Průvodce pokrývá vše, co potřebujete k vytvoření souboru `.docx`, který obsahuje ActiveX tlačítko připravené k použití v Microsoft Word. Žádné další nástroje nejsou potřeba a příklad běží na Java 8+.

## Co se naučíte

* Jak přidat form control typu **CommandButton** do dokumentu Word.  
* Přesné kroky k **nastavení názvu tlačítka** a **přidání vlastností activex button**.  
* Jak uložit dokument, aby se tlačítko po otevření ve Wordu zobrazilo správně.  

Měli byste mít základní vývojové prostředí Java a projekt Maven nebo Gradle, který může importovat knihovnu Aspose.Words.

## Požadavky

| Požadavek | Důvod |
|-------------|--------|
| Java 8 or newer | Aspose.Words for Java běží na Java 8+. |
| Maven or Gradle build tool | Zjednodušuje přidání závislosti Aspose.Words. |
| Aspose.Words for Java license (or free trial) | Vyžadováno pro plnou sadu funkcí; API funguje v režimu hodnocení. |
| An IDE such as IntelliJ IDEA or Eclipse | Usnadňuje úpravy a spuštění příkladu. |

## Krok 1: Přidejte Aspose.Words do svého projektu

Pokud používáte Maven, přidejte následující závislost do `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Pro Gradle umístěte tento řádek do `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Po vyřešení závislosti můžete importovat třídy knihovny ve svém Java zdrojovém souboru.

## Krok 2: Vložení command button – jádro kódu

Vytvořte novou třídu Java s názvem `InsertCommandButtonDemo`. Níže uvedený kód provádí všechny čtyři akce potřebné k **vložit command button**:

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

### Proč je každý řádek důležitý

* **Document & DocumentBuilder** – Poskytují in‑memory reprezentaci souboru Word a API pro úpravu jeho obsahu.  
* **insertForms2OleControl** – Tato metoda **přidává form control** typu `COMMAND_BUTTON`. Vrácený objekt `Forms2OleControl` představuje ActiveX kontrolu.  
* **setName** – Přiřadí programový identifikátor (`btnSubmit`). Makra Wordu nebo VBA mohou tento název později odkazovat.  
* **setCaption** – Definuje text, který uživatel vidí na tlačítku, odpovídá na otázku „jak přidat tlačítko“.  
* **save** – Zapíše `.docx` na disk, zachovává vložené ActiveX tlačítko.

Spuštěním programu se vytvoří `CommandButtonDemo.docx` v pracovním adresáři. Otevřením souboru v Microsoft Word se zobrazí tlačítko označené **Submit**, na které můžete kliknout (zobrazí se výchozí ActiveX dialog v režimu hodnocení).

## Krok 3: Ověřte vložené tlačítko ve Wordu

1. Otevřete `CommandButtonDemo.docx` pomocí Microsoft Word (2016 nebo novější).  
2. Tlačítko **Submit** se objeví tam, kde byl během vkládání umístěn kurzor.  
3. Klikněte pravým tlačítkem na tlačítko a vyberte **Properties**, abyste viděli, že pole **Name** obsahuje `btnSubmit`.  

Pokud se tlačítko neobjeví, ujistěte se, že jsou v nastavení Trust Center ve Wordu povoleny **ActiveX controls**.

## Krok 4: Přizpůsobení tlačítka (volitelné)

Můžete tlačítko dále přizpůsobit úpravou jeho velikosti, pozice nebo přidáním VBA makra. Třída `Forms2OleControl` odhaluje další vlastnosti jako `setWidth`, `setHeight` a `setLeft`. Níže je příklad, který zvětší tlačítko:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Tyto řádky lze umístit po volání `setCaption`. Ukazují přizpůsobení **add activex button** nad rámec základního vložení.

## Časté úskalí a jak se jim vyhnout

| Projev | Příčina | Řešení |
|---------|-------|-----|
| Button does not appear in Word | Dokument byl uložen před přidáním kontroly | Zajistěte, aby `insertForms2OleControl` byl zavolán před `doc.save`. |
| Button caption is empty | `setCaption` nebyl zavolán nebo byl zavolán s prázdným řetězcem | Poskytněte neprázdný řetězec, např. `"Submit"`. |
| VBA cannot find the button | Nesoulad názvu mezi VBA kódem a hodnotou `setName` | Udržujte název konzistentní; použijte `setName("btnSubmit")` a odkazujte na `btnSubmit` ve VBA. |
| Security warning on opening the file | Bezpečnostní nastavení maker ve Wordu blokuje ActiveX controls | Upravte Trust Center > Macro Settings, nebo podepište dokument důvěryhodným certifikátem. |

## Kompletní, spustitelný příklad

Níže je kompletní zdrojový soubor, připravený ke zkopírování a vložení do vašeho IDE. Obsahuje importy, ošetření výjimek a blok komentářů, který vysvětluje každý hlavní krok.

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

**Očekávaný výsledek:** Po spuštění programu `CommandButtonDemo.docx` obsahuje jedno tlačítko **Submit**. Otevřením souboru ve Wordu se tlačítko zobrazí přesně tam, kde byl kurzor `DocumentBuilder`.

## Další kroky

* **Přidat více form controls** – Použijte `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` nebo `TEXT_BOX` k vytvoření kompletních formulářů ve Wordu.  
* **Kombinovat s hromadnou korespondencí** – Vkládejte tlačítka do dokumentu vytvořeného hromadnou korespondencí pro vytvoření personalizovaných interaktivních formulářů.  
* **Připojit VBA makra** – Programově vložte VBA, které reaguje na událost `Click` tlačítka pro pokročilou automatizaci.  

Tyto témata přirozeně rozšiřují techniku **add form control**, kterou jste právě zvládli.

---

### Shrnutí

Nyní víte, jak **vložit command button** do dokumentu Word pomocí Javy, jak **přidat form control**, jak **nastavit název tlačítka** a jak **přidat přizpůsobení activex button**. Kompletní příklad funguje ihned po spuštění a můžete jej přizpůsobit libovolnému workflow generování dokumentů. Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Vložit Combo Box formulářové pole do dokumentu Word](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Vložit Check Box formulářové pole do dokumentu Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}