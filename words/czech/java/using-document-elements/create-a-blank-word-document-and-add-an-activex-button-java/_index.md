---
category: general
date: 2026-10-16
description: Vytvořte prázdný dokument Word v Javě a naučte se, jak přidat tlačítko
  ActiveX, nastavit jeho popisek a upravit jeho rozměry pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: cs
lastmod: 2026-10-16
og_description: Vytvořte prázdný dokument Word pomocí Javy, poté přidejte tlačítko
  ActiveX, nastavte jeho popisek a definujte jeho rozměry pomocí Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Vytvořte prázdný dokument Word a vložte tlačítko ActiveX – Java průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Vytvořte prázdný dokument Word a přidejte tlačítko ActiveX (Java)
url: /cs/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word a přidejte ActiveX tlačítko (Java)

Pokud potřebujete **vytvořit prázdný dokument Word** programově, tento návod vám ukáže, jak to provést pomocí Javy a Aspose.Words. Také se naučíte, jak **přidat ActiveX tlačítko**, **nastavit popisek tlačítka** a **nastavit rozměry tlačítka**, aby ovládací prvek vypadal přesně tak, jak očekáváte.

Tento tutoriál pokrývá:

* Inicializaci prázdného souboru Word pomocí Aspose.Words pro Javu.  
* Vložení ActiveX `CommandButton` ovládacího prvku.  
* Konfiguraci popisku a velikosti tlačítka.  
* Uložení finálního souboru `.docx`.

Měli byste mít základní znalosti Javy a aktuální verzi knihovny Aspose.Words pro Javu (kód funguje s verzí 23.9 a novější). Žádné další závislosti nejsou vyžadovány.

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="Vytvořte prázdný dokument Word s ActiveX tlačítkem"}

## Vytvořte prázdný dokument Word pomocí Aspose.Words

Prvním krokem je vytvořit prázdný objekt `Document`. Tento objekt představuje celý soubor Word v paměti a poskytuje třídu `DocumentBuilder` pro úpravy.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Proč je to důležité:**  
Vytvoření prázdného dokumentu vám poskytne čisté plátno, čímž se vyhnete skrytým stylům nebo sekcím, které by mohly později narušovat výpočty rozvržení.

## Přidejte ActiveX tlačítko do dokumentu

Aspose.Words vám umožňuje vkládat starší ActiveX ovládací prvky pomocí třídy `Forms2OleControl`. Následující kód vloží ovládací prvek `CommandButton` na aktuální pozici kurzoru.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Tip:** Hodnota `setOleClassName` `"Forms.CommandButton.1"` je ProgID pro standardní tlačítko Microsoft Forms. Použití jiného ProgID (např. `"Forms.CheckBox.1"`) by vložilo jiný typ ovládacího prvku.

## Nastavte popisek tlačítka

Popisek je text, který se zobrazuje na povrchu tlačítka. Můžete jej změnit kdykoli před uložením dokumentu.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Proč to potřebujete:** Uživatelé rozumí ovládacímu prvku jen tehdy, když je jeho účel jasný. Nastavení smysluplného popisku zlepšuje použitelnost, zejména když je dokument otevřen ve Wordu na Windows.

## Nastavte rozměry tlačítka

Pozice a velikost jsou zadány v bodech (1 bod = 1/72 palce). Upravit hodnoty tak, aby vyhovovaly vašemu rozvržení.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Běžné varianty:**

| Scénář | Úprava |
|----------|------------|
| Větší tlačítko pro dotykové obrazovky | Zvětšete `setWidth` a `setHeight` úměrně |
| Tlačítko vycentrované na stránce | Vypočítejte `left = (pageWidth - width) / 2` |
| Více tlačítek ve sloupci | Zvyšte `setTop` pro každé nové tlačítko |

## Uložte dokument obsahující ActiveX tlačítko

Nakonec zapište dokument na disk. Formát `.docx` zachovává ActiveX ovládací prvek pro Windows verze Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Očekávaný výsledek:** Otevření `ActiveXCommandButton.docx` ve Wordu (Windows) zobrazí prázdnou stránku s klikacím tlačítkem označeným **Click Me**, umístěným 100 pt od levého okraje a 200 pt od horního okraje.

## Kompletní, spustitelný příklad

Zkopírujte celou třídu níže do svého IDE, přidejte Aspose.Words pro Java JAR do classpath projektu a spusťte ji.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Spuštěním programu vznikne `ActiveXCommandButton.docx` v pracovním adresáři. Otevřete jej v Microsoft Word (Windows), abyste ověřili, že se tlačítko zobrazí přesně tak, jak bylo nakonfigurováno.

## Proč je tento přístup doporučen

* **Jednoduchost:** Používá se pouze jádro API Aspose.Words; není potřeba COM interop ani další knihovny.  
* **Přenositelnost:** Kód běží na jakékoli platformě podporující Javu, i když samotný ActiveX ovládací prvek funguje jen ve Windows verzích Wordu.  
* **Udržovatelnost:** Všechny vlastnosti (popisek, rozměry, pozice) jsou nastaveny pomocí jasných, samodokumentujících metod, což usnadňuje budoucí úpravy.

## Časté úskalí a jak se jim vyhnout

| Úskalí | Řešení |
|---------|------------|
| Tlačítko se nezobrazuje ve Wordu na macOS nebo Linuxu | ActiveX ovládací prvky jsou pouze pro Windows. Použijte jiný ovládací prvek (např. obsahový ovládací prvek) pro multiplatformní dokumenty. |
| Popisek je oříznutý | Ujistěte se, že šířka tlačítka je dostatečná pro text; zvětšete `setWidth` nebo použijte kratší popisek. |
| Tlačítko překrývá jiný obsah | Upravte hodnoty `setTop` a `setLeft`, nebo vložte nový odstavec před ovládací prvek, aby měl svůj vlastní prostor. |

## Další kroky

Nyní, když můžete **vytvořit prázdný dokument Word**, **přidat ActiveX tlačítko**, **nastavit popisek tlačítka** a **nastavit rozměry tlačítka**, můžete zkoumat:

* Přidání kódu pro zpracování událostí pomocí VBA maker (vyžaduje vložení modulu makra).  
* Vkládání více ovládacích prvků do tabulkového rozvržení pro formulářové dokumenty.  
* Použití **FormField** API Aspose.Words pro multiplatformní řešení formulářů.

Experimentujte s různými velikostmi, pozicemi a popisky, aby vyhovovaly vašemu konkrétnímu návrhu dokumentu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vlastních projektech.

- [Vytvořte Word dokument v Javě – Přidejte obdélníkový tvar se stínovým efektem](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Přidejte vodoznak do dokumentu pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}