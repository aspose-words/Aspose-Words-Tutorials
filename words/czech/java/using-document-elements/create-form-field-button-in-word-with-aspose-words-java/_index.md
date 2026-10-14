---
category: general
date: 2026-10-13
description: Vytvořte tlačítko formulářového pole ve Wordu pomocí Aspose.Words pro
  Javu. Naučte se, jak vložit příkazové tlačítko do formulářových polí Wordu a nastavit
  popisek příkazového tlačítka v několika jednoduchých krocích.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: cs
lastmod: 2026-10-13
og_description: Vytvořte tlačítko formulářového pole ve Wordu pomocí Aspose.Words
  pro Java. Tento tutoriál ukazuje, jak rychle vložit pole příkazového tlačítka a
  nastavit popisek tlačítka.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Vytvoření tlačítka formulářového pole ve Wordu – Průvodce Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Vytvořte tlačítko formulářového pole ve Wordu pomocí Aspose.Words Java
url: /cs/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření tlačítka formulářového pole ve Wordu s Aspose.Words Java

Pokud potřebujete **vytvořit tlačítko formulářového pole** ve Word dokumentu, tento průvodce vás provede kompletním procesem pomocí Aspose.Words pro Java. Ať už vytváříte šablonu formuláře k vyplnění nebo přidáváte interaktivní ovládací prvky do zprávy, naučíte se **vložit tlačítko příkazu** formulářová pole a **nastavit popisek tlačítka příkazu** s minimálním množstvím kódu.

Tutoriál pokrývá vše od nastavení Maven až po plně spustitelný příklad, takže můžete kód zkopírovat‑vložit, spustit jej a získat soubor `.docx`, který obsahuje klikatelné tlačítko připravené k dalším úpravám.

## Požadavky

Než začnete, ujistěte se, že máte:

- Java 17 (nebo novější) nainstalovanou a nakonfigurovanou na vašem počítači.
- Maven 3.6+ pro správu závislostí.
- IDE nebo textový editor dle vašeho výběru (např. IntelliJ IDEA, VS Code).
- Platnou licenci Aspose.Words pro Java (zkušební verze funguje pro evaluaci).

## Krok 1: Přidání Aspose.Words do Maven projektu

Vytvořte soubor `pom.xml` (nebo upravte existující) a zahrňte závislost Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Tip:** Udržujte číslo verze aktuální. Nová vydání přidávají podporu pro nejnovější funkce Wordu a zlepšují výkon.

## Krok 2: Inicializace prázdného dokumentu a `DocumentBuilder`

Třída `DocumentBuilder` poskytuje plynulé API pro úpravu Word dokumentu. V tomto kroku vytvoříme prázdný `Document` a připojíme k němu builder.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Vytvoření dokumentu je základem pro **vytvoření tlačítka formulářového pole** později v tutoriálu.

## Krok 3: Vložení tlačítka příkazu jako formulářového pole

Aspose.Words vystavuje třídu `Forms2OleControl` pro OLE formulářové ovládací prvky. Pro **vložit tlačítko příkazu** formulářová pole zavolejte `insertForms2OleControl` s hodnotou výčtu `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Metoda vrací instanci `Forms2OleControl`, kterou můžeme před uložením nakonfigurovat.

## Krok 4: Definování velikosti a umístění tlačítka

Tlačítko příkazu potřebuje explicitní rozměry a umístění na stránce. Upravit šířku, výšku a souřadnice tak, aby odpovídaly vašemu rozvržení.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Doladění těchto hodnot zajistí, že se tlačítko objeví přesně tam, kde jej chcete mít v konečném dokumentu.

## Krok 5: **Nastavit popisek tlačítka příkazu**

Viditelný text na tlačítku řídí metoda `setCaption`. Zde **nastavíme popisek tlačítka příkazu**, aby uživatele navedl.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Můžete nahradit `"Click Me"` libovolným popiskem, který odpovídá záměru vašeho formuláře, např. `"Submit"` nebo `"Approve"`.

## Krok 6: Uložení dokumentu

Nakonec zapíšeme dokument na disk. Výsledný soubor obsahuje interaktivní tlačítko a lze jej otevřít v Microsoft Word nebo LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Po spuštění programu vznikne soubor `CommandButtonDemo.docx`. Otevření v Wordu zobrazí tlačítko s popiskem **Click Me** umístěné 50 pt od levého okraje a 100 pt od horního okraje stránky.

### Očekávaný výstup

- Soubor `.docx` pojmenovaný `CommandButtonDemo.docx`.
- Dokument obsahuje jedinou stránku s formulářovým polem tlačítka příkazu.
- Tlačítko zobrazuje popisek, který jste nastavili (např. **Click Me**).

## Běžné varianty a okrajové případy

| Situace | Jak přizpůsobit |
|-----------|--------------|
| **Více tlačítek** | Opakovaně zavolejte `insertForms2OleControl`, přičemž pro každé nové tlačítko upravte `setLeft`/`setTop`. |
| **Různý popisek pro každé tlačítko** | Použijte `setCaption` s unikátním řetězcem po každém vložení. |
| **Tlačítko uvnitř buňky tabulky** | Přesuňte kurzor do požadované buňky pomocí `builder.moveTo(cell.getFirstParagraph())` před vložením ovládacího prvku. |
| **Starší formáty Wordu (.doc)** | Uložte pomocí `doc.save("Demo.doc", SaveFormat.DOC);` – tlačítko příkazu bude zachováno. |
| **Formuláře jen pro čtení** | Po vložení nastavte `commandButton.setEnabled(false);`, aby se zabránilo interakci uživatele. |

## Tipy pro robustní implementaci

- **Ověřte rozměry**: Extrémně velké šířky mohou způsobit, že tlačítko přesáhne okraj stránky.
- **Vynucení licence**: Bez platné licence přidá Aspose.Words vodoznak do vygenerovaného dokumentu. Licenci aplikujte co nejdříve pomocí `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Testování**: Otevřete vygenerovaný soubor ve Wordu a zapněte **Design Mode** (Developer → Design Mode), abyste viděli vlastnosti tlačítka.

## Kompletní přehled zdrojového kódu

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Zkopírujte kód do souboru pojmenovaného `InsertCommandButtonDemo.java`, zkompilujte pomocí Maven (`mvn compile`) a spusťte (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Vygenerovaný dokument se objeví v kořenovém adresáři vašeho projektu.

## Závěr

Nyní víte, jak **vytvořit tlačítko formulářového pole** ve Wordu pomocí Aspose.Words pro Java, jak **vložit tlačítko příkazu** formulářová pole a jak **nastavit popisek tlačítka příkazu** programově. Tento end‑to‑end příklad vám poskytuje pevný základ pro tvorbu bohatších, interaktivních Word dokumentů – ať už potřebujete jediný odesílací button nebo kompletní sadu formulářových ovládacích prvků.

### Co dál?

- Prozkoumejte další formulářové ovládací prvky, jako jsou zaškrtávací políčka (`Forms2OleControlType.CHECKBOX`) a textová pole (`Forms2OleControlType.TEXTBOX`).
- Kombinujte formulářová pole s hromadnou korespondencí pro generování personalizovaných dotazníků.
- Použijte Aspose.Words `FormField` API k načtení dat zadaných uživatelem po vyplnění dokumentu.

Neváhejte experimentovat s různými velikostmi, popisky a umístěním. Jakmile zvládnete tlačítka příkazu, přidání plnohodnotných formulářů do vašich Word automatizačních pipeline se stane jednoduchým úkolem. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným krok‑za‑krokem vysvětlením, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Přidání Combo Box formulářového pole do Word dokumentu s Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Přidání Check Box formulářového pole do Word dokumentu s Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}