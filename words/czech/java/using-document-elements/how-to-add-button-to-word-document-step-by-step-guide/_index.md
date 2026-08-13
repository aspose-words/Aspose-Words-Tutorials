---
category: general
date: 2026-07-20
description: Jak přidat tlačítko do dokumentu Word pomocí Aspose.Words. Naučte se
  během několika minut vložit tlačítko Forms2OleControl pomocí DocumentBuilderu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: cs
lastmod: 2026-07-20
og_description: Jak přidat tlačítko do dokumentu Word pomocí Aspose.Words. Postupujte
  podle tohoto praktického návodu, jak vložit Forms2OleControl CommandButton pomocí
  Javy.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Jak přidat tlačítko do dokumentu Word – Kompletní tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Jak přidat tlačítko do dokumentu Word – průvodce krok za krokem
url: /cs/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat tlačítko do Word dokumentu – Kompletní tutoriál Aspose.Words

Už jste se někdy zamýšleli **jak přidat tlačítko do Word dokumentu** bez otevírání uživatelského rozhraní a klikání? Nejste v tom sami. Mnoho vývojářů potřebuje programově vložit interaktivní ovládací prvky – například tlačítko „Submit“ v šabloně, které později vyplní koncový uživatel. Dobrá zpráva? S Aspose.Words pro Java to můžete udělat během několika řádků kódu.

V tomto tutoriálu projdeme přesně kroky, jak vložit `Forms2OleControl` typu **CommandButton** pomocí `DocumentBuilder`. Na konci budete mít připravený soubor `.docx`, který zobrazuje klikatelné tlačítko s popiskem „Click Me“. Žádná magie, jen jasný kód a vysvětlení každého řádku.

## Co se naučíte

- Jak vytvořit nový Word dokument od nuly.
- Jak použít **DocumentBuilder** k umístění **Forms2OleControl**.
- Proč nastavovat popisek tlačítka a jeho velikost tak, jak to děláme.
- Jak uložit a ověřit výsledek.
- Běžné úskalí (např. chybějící knihovny, nepodporované typy ovládacích prvků) a jak se jim vyhnout.

**Prerequisites** – Potřebujete Java 8+ (nebo novější) a knihovnu Aspose.Words pro Java (verze 23.12 nebo novější). IDE jako IntelliJ IDEA nebo Eclipse vám práci usnadní, ale funguje i libovolný textový editor.

---

## Krok 1: Nastavte svůj projekt a importujte závislosti

Než se spustí jakýkoli kód, musí Maven (nebo Gradle) vědět, odkud stáhnout Aspose.Words. Přidejte tento úryvek do svého `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Pokud dáváte přednost Gradlu, ekvivalent je:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Používejte nejnovější vydání; starší verze mohou postrádat API `Forms2OleControl`.

Jakmile se závislost vyřeší, můžete psát Java kód.

## Krok 2: Vytvořte nový dokument a získejte DocumentBuilder

Třída `Document` představuje celý balíček `.docx`, zatímco `DocumentBuilder` je štětec, kterým na něj malujete obsah. Představte si `DocumentBuilder` jako „kurzor“, který ví, kam má jít další prvek.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** Inicializace čerstvého `Document` vám poskytne čisté plátno. Builder automaticky ukazuje na první odstavec, takže se nemusíte starat o sekce nebo stránky ručně.

## Krok 3: Vložte Forms2OleControl typu CommandButton

Nyní přichází hvězda představení: `insertForms2OleControl`. Tato metoda vytvoří OLE (Object Linking and Embedding) ovládací prvek, který Word považuje za formulářový element. Předáme tři argumenty:

1. `Forms2OleControlType.COMMANDBUTTON` – říká Wordu, že chceme tlačítko.
2. `100` – šířka v bodech (≈1,39 palce).
3. `30` – výška v bodech (≈0,42 palce).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**How it works:** Pod kapotou Aspose.Words vytvoří odpovídající XML v části `word/document.xml`, odkazující na OLE objekt. Rozměry, které zadáte, jsou respektovány layoutovým enginem Wordu, takže tlačítko se objeví přesně tam, kde je kurzor builderu.

## Krok 4: Nastavte popisek (text) na tlačítku

Tlačítko bez popisku je matoucí – představte si tiché tlačítko výtahu. Metoda `setCaption` nastaví viditelný text:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Popisek můžete změnit na cokoli: „Submit“, „Approve“ nebo dokonce na lokalizovaný řetězec. Popisek je uložen v vlastnostech OLE objektu, takže Word jej vykreslí nativně.

## Krok 5: Uložte dokument a ověřte výsledek

Nakonec zapíšete soubor na disk. Vyberte složku, do které máte právo zapisovat; jinak narazíte na `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Otevřete `button-demo.docx` v Microsoft Word. Měli byste vidět tlačítko s popiskem **Click Me** umístěné v horní části dokumentu. Kliknutí na něj ve Wordu spustí výchozí OLE chování (obvykle placeholder zpráva, pokud nepřipojíte makro).

## Běžné okrajové případy a jak je řešit

| Situation | Why It Happens | Fix |
|-----------|----------------|-----|
| **Missing `Forms2OleControl` type** | Older Aspose.Words versions didn’t expose this enum. | Upgrade to 23.12+ or later. |
| **Button appears as a picture** | Word’s security settings block OLE controls. | Enable “Trust access to the VBA project object model” in Trust Center, or use a macro‑enabled `.docm`. |
| **Incorrect size** | Points vs. pixels confusion. | Remember 1 point = 1/72 inch. Adjust numbers accordingly. |
| **Saving throws `FileNotFoundException`** | Path does not exist. | Ensure the directory (`output/`) is created before `doc.save`. Use `new File("output").mkdirs();`. |

## Rozšíření příkladu: Přidání více tlačítek nebo jiných ovládacích prvků

Pokud potřebujete více než jedno tlačítko, jednoduše přesuňte kurzor builderu pomocí `builder.moveTo` nebo `builder.writeln()` před dalším voláním `insertForms2OleControl`.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Můžete také vložit **CheckBox**, **ComboBox** nebo **ListBox** výměnou `Forms2OleControlType.COMMANDBUTTON` za odpovídající enum hodnotu (`CHECKBOX`, `COMBOBOX`, atd.). Stejné parametry šířky/výšky platí.

## Jak to zapadá do větších pracovních postupů automatizace Wordu

- **Template Generation:** Build a contract template that includes a “Approve” button for downstream sign‑off.
- **Reporting:** Generate a daily report with a “Refresh Data” button that triggers a macro.
- **Form Distribution:** Ship a questionnaire with interactive controls pre‑populated.

Všechny tyto scénáře těží z přístupu **Word automation**, který jsme demonstrovali. Vkládáním ovládacích prvků programově eliminujete ruční úpravy a snižujete lidské chyby.

## Kompletní zdrojový kód (připravený ke kopírování)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Expected output:** When you open `output/button-demo.docx` in Microsoft Word, you’ll see two buttons—“Click Me” and “Submit”—stacked vertically at the top of the file.

## Závěr

Odpověděli jsme **jak přidat tlačítko do Word dokumentu** pomocí Aspose.Words pro Java, krok za krokem. Začali jsme s prázdným `Document`, využili **DocumentBuilder** k vložení `Forms2OleControl` typu **CommandButton**, nastavili přátelský popisek a uložili výsledek. Přístup škáluje na více ovládacích prvků a čistě se integruje do širších **Word automation** pipeline.

Jste připraveni na další výzvu? Zkuste nahradit tlačítko za **CheckBox**, nebo připojte makro, které reaguje, když uživatel klikne na tlačítko v souboru `.docm`. Stejný vzor platí – stačí změnit enum a upravit popisek.

Pokud narazíte na potíže, dvakrát zkontrolujte verzi knihovny a oprávnění výstupní složky. Neváhejte zanechat komentář níže s otázkami nebo sdílet svůj vlastní případ použití. Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}