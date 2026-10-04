---
category: general
date: 2026-10-04
description: Naučte se, jak inicializovat DocumentBuilder pro nový dokument a přidat
  tlačítko ActiveX pomocí Aspose.Words v Javě. Podrobný návod krok za krokem s kompletním
  kódem.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: cs
lastmod: 2026-10-04
og_description: Inicializujte DocumentBuilder pro nový dokument a vložte tlačítko
  ActiveX pomocí Aspose.Words Java API. Postupujte podle tohoto stručného tutoriálu.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Inicializace DocumentBuilderu pro nový dokument – kompletní průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Jak inicializovat DocumentBuilder pro nový dokument pomocí Aspose.Words
url: /cs/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak inicializovat DocumentBuilder pro nový dokument pomocí Aspose.Words

Pokud potřebujete **initialize DocumentBuilder for new document** v Java projektu, tento tutoriál vám ukáže přesné kroky. Uvidíte, jak vytvořit prázdný soubor Word, připojit ActiveX tlačítko příkazu a uložit výsledek — vše v jediném, samostatném ukázkovém kódu.

Práce s dokumenty Word programově často znamená řešení nízkoúrovňových detailů, jako jsou ovládací prvky formulářů. Na konci tohoto průvodce budete schopni vložit ActiveX tlačítko, aniž byste opustili své IDE, což je užitečné pro generování šablon, automatizovaných reportů nebo interaktivních formulářů.

## Předpoklady

Předtím, než začnete, ujistěte se, že máte:

* Java 17 nebo novější nainstalována  
* Maven 3.8+ (nebo Gradle, pokud dáváte přednost)  
* Licence Aspose.Words pro Java (bezplatná zkušební verze funguje pro testování)  
* Základní znalost syntaxe Javy  

Pokud jste v Aspose.Words noví, knihovna poskytuje high‑level API pro vytváření, úpravu a ukládání Word dokumentů. Třída `DocumentBuilder` je hlavním vstupním bodem pro konstrukci obsahu dokumentu.

## Krok 1: Nastavení Maven projektu

Vytvořte nový Maven projekt (nebo jej přidejte k existujícímu) a zahrňte závislost Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Udržujte verzi knihovny aktuální; novější vydání přidávají podporu pro další ovládací prvky formulářů a zlepšují výkon.

## Krok 2: Inicializovat `DocumentBuilder` pro nový dokument

Jádrem tutoriálu je operace **initialize DocumentBuilder for new document**. Nejprve vytvoříte prázdnou instanci `Document`, poté ji předáte konstruktoru `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité:* Inicializace `DocumentBuilder` spojuje builder s konkrétním objektem `Document`, což vám umožní přidávat odstavce, tabulky nebo ovládací prvky formulářů přímo do tohoto dokumentu. Bez tohoto kroku by builder neměl žádný cíl, na kterém by mohl pracovat.

## Krok 3: Vložit ovládací prvek ActiveX tlačítko příkazu

Aspose.Words vystavuje třídu `Forms2OleControl` pro vložení starších ActiveX ovládacích prvků. Následující kód přidá **Forms2OleControl command button** na aktuální pozici kurzoru.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Co je ActiveX tlačítko příkazu?

ActiveX tlačítko příkazu je starší UI prvek, který může spouštět makra nebo vyvolávat události, když na něj uživatel klikne uvnitř Word dokumentu. Přestože moderní verze Office upřednostňují Content Controls, mnoho podnikových šablon stále spoléhá na ActiveX pro zpětnou kompatibilitu.

## Krok 4: Uložit dokument

Po vložení ovládacího prvku jednoduše zavoláte `save`. Soubor bude obsahovat ActiveX tlačítko a může být otevřen v Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Když otevřete `ActiveXButton.docx` ve Wordu, uvidíte tlačítko označené **Click Me**. Kliknutí na tlačítko nic neudělá, pokud k němu nepřipojíte makro, ale samotný ovládací prvek je plně funkční.

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat a vložit do `src/main/java/com/example/ActiveXButtonDemo.java`. Obsahuje všechny importy a ošetření chyb potřebné pro rychlý test.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Očekávaný výstup**

```
Document saved to output/ActiveXButton.docx
```

Otevřete vygenerovaný soubor v Microsoft Word 2016 nebo novějším; měli byste vidět tlačítko označené *Click Me* umístěné v horní části první stránky.

## Běžné varianty a okrajové případy

| Scénář | Úprava |
|----------|------------|
| **Přidat tlačítko do konkrétního odstavce** | Přesuňte kurzor builderu pomocí `builder.moveToParagraph(index, NodeType.PARAGRAPH);` před voláním `insertForms2OleControl`. |
| **Nastavit velikost tlačítka** | Použijte `commandButton.setWidth(100);` a `commandButton.setHeight(30);` pro definování rozměrů v bodech. |
| **Přidat makro k tlačítku** | Po uložení dokumentu jej otevřete ve Wordu, povolte kartu Vývojář a ručně připojte VBA makro k tlačítku (ActiveX ovládací prvky nelze skriptovat přímo z Aspose.Words). |
| **Cílový formát .doc (binární)** | Změňte `doc.save(outputPath, SaveFormat.DOC);` pro vytvoření staršího souboru Word 97‑2003. |
| **Spustit na Androidu** | Použijte Aspose.Words pro Android přes jeho Java API; stejný kód funguje, pokud je knihovna zahrnuta v APK. |

## Tipy pro řešení problémů

* **`java.lang.NoClassDefFoundError`** – Ujistěte se, že Aspose.Words JAR je na classpath. Maven jej přidá automaticky; pro ruční sestavení umístěte JAR do `libs/` a přidejte jej do knihoven vašeho IDE.  
* **Button does not appear in Word** – Ověřte, že je v Trust Centeru Wordu povolena možnost *Show legacy forms* (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **License exception** – Pokud spustíte kód bez platné licence, Aspose.Words vloží vodoznak. Zaregistrujte si bezplatnou zkušební verzi nebo zakupte licenci, abyste jej odstranili.

## Závěr

Nyní víte, jak **initialize DocumentBuilder for new document**, vložit ActiveX tlačítko příkazu a uložit výsledek pomocí Aspose.Words pro Java. Tento vzor vám umožní programově generovat interaktivní Word šablony, což je zvláště užitečné pro automatizované reportování nebo workflow založené na formulářích.

Odtud můžete zkoumat další ovládací prvky formulářů (`Forms2OleControlType.CHECKBOX`, `COMBOBOX` atd.), kombinovat tlačítko s vlastními VBA makry nebo generovat plnohodnotné dokumenty, které zahrnují tabulky, obrázky a stylování — vše pomocí stejného workflow `DocumentBuilder`.

---

*Připraveni vytvářet složitější automatizaci Wordu? Podívejte se na naše průvodce o **vložení tabulky pomocí DocumentBuilder**, **aplikaci stylů programově** a **exportu do PDF s Aspose.Words**.*

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak uložit dokument jako PDF s Aspose.Words pro Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Přidat vodoznak do dokumentu pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}