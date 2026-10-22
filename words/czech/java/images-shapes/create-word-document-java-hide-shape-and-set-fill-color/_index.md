---
category: general
date: 2026-08-07
description: 'Vytvořte Word dokument v Javě pomocí Aspose.Words: vložte elipsu, nastavte
  barvu výplně tvaru a skryjte tvar ve Wordu pomocí stručného příkladu.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document java
- how to hide shape
- how to insert shape
- hide shape in word
- set shape fill color
language: cs
lastmod: 2026-08-07
og_description: Vytvořte Word dokument v Javě pomocí Aspose.Words. Naučte se vložit
  tvar, nastavit jeho barvu výplně a skrýt tvar ve Wordu – vše v jednom spustitelném
  příkladu.
og_image_alt: Screenshot showing a hidden ellipse shape in a Word document created
  with Java
og_title: Vytvořit Word dokument v Javě – skrýt tvar a nastavit barvu výplně
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: 'Create word document java with Aspose.Words: insert an ellipse, set
    shape fill color, and hide shape in Word using a concise example.'
  headline: Create word document java – hide shape and set fill color
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Vytvořit Word dokument v Javě – skrýt tvar a nastavit barvu výplně
url: /cs/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořit Word dokument v Javě – skrýt tvar a nastavit barvu výplně

Pokud potřebujete **vytvořit Word dokument v Javě** s programovým ovládáním tvarů, tento tutoriál vám ukáže, jak na to. Naučíte se vložit tvar, nastavit jeho barvu výplně a skrýt tvar ve Wordu pomocí Aspose.Words pro Java.

Průvodce pokrývá každý krok od inicializace objektu `Document` až po ověření, že je tvar neviditelný při otevření souboru. Kromě knihovny Aspose.Words nejsou potřeba žádné externí zdroje a kompletní zdrojový kód je poskytnut, takže jej můžete okamžitě spustit.

**Požadavky**

- Java 8 nebo novější
- Maven nebo Gradle pro správu závislostí (nebo Aspose.Words JAR na classpath)
- Základní znalost syntaxe Javy
- IDE nebo textový editor pro vývoj v Javě

Tutoriál také vysvětluje **jak skrýt tvar** v souboru Word, **jak vložit tvar** s přesnými rozměry a **nastavit barvu výplně tvaru** pro vizuální stylizaci.

---

![Create word document java – hidden shape preview](image-placeholder.png){.align-center width=600 alt="Vytvořit Word dokument v Javě – náhled skrytého tvaru"}

## Vytvořit Word dokument v Javě – inicializace dokumentu a builderu

Prvním krokem je vytvořit prázdný Word dokument a `DocumentBuilder`, který vám umožní přidávat obsah. Inicializace těchto objektů alokuje interní struktury, které Aspose.Words potřebuje ke sledování stránek, odstavců a tvarů.

```java
import com.aspose.words.*;

public class ShapeVisibilityDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document
        Document doc = new Document();

        // DocumentBuilder provides methods to insert elements
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité:* Bez `DocumentBuilder` nemůžete vkládat tvary, text ani jiné objekty. Builder pracuje s in‑memory instancí `Document`, což zajišťuje, že všechny změny jsou zachyceny před uložením.

## Jak vložit tvar pomocí Aspose.Words

Aspose.Words podporuje mnoho geometrických tvarů. Zde vložíme elipsu o šířce 150 pt a výšce 100 pt. Metoda `insertShape` vrací objekt `Shape`, který můžete dále konfigurovat.

```java
        // Insert an ellipse shape (width: 150pt, height: 100pt)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 150, 100);
```

*Proč je to důležité:* Použití `insertShape` zaručuje, že tvar bude správně ukotven v toku dokumentu. Vrácený `Shape` vám umožní měnit vlastnosti jako barvu výplně, styl čáry a viditelnost.

## Nastavit barvu výplně tvaru ve Wordu

Tvar bez výplně vypadá průhledně. Nastavení barvy výplně způsobí, že tvar bude výraznější, když je viditelný. Příklad používá `java.awt.Color.GREEN` k demonstraci **nastavení barvy výplně tvaru**.

```java
        // Apply a green fill to the ellipse
        ellipse.setFillColor(java.awt.Color.GREEN);
```

*Proč je to důležité:* Barva výplně je uložena v XML definici tvaru. Změna během běhu umožňuje generovat dokumenty s barvami specifickými pro značku nebo zvýraznit důležité oblasti.

## Jak skrýt tvar ve Wordu

Někdy potřebujete tvar, který určuje rozvržení nebo slouží jako zástupný prvek, ale neměl by být viditelný pro koncového uživatele. Volání `setHidden(true)` implementuje **jak skrýt tvar** a splňuje požadavek **skrýt tvar ve Wordu**.

```java
        // Hide the shape so it will not be visible when the document is opened
        ellipse.setHidden(true);
```

*Proč je to důležité:* Skryté tvary jsou stále součástí objektového modelu dokumentu, což znamená, že je lze později odkazovat (např. pro záložky nebo programovou manipulaci) aniž by zaplňovaly vizuální rozvržení.

## Uložit dokument a ověřit výsledek

Po nastavení tvaru soubor uložte na disk. Uložený `.docx` lze otevřít v Microsoft Word; elipsa bude neviditelná, ale její přítomnost lze potvrdit kontrolou XML dokumentu nebo pomocí Aspose.Words k enumeraci tvarů.

```java
        // Save the document to the desired location
        doc.save("YOUR_DIRECTORY/ShapeVisibilityDemo.docx");
    }
}
```

*Očekávaný výsledek:* Otevření `ShapeVisibilityDemo.docx` zobrazí normální stránku bez viditelných grafických prvků. Pokud soubor rozbalíte pomocí ZIP prohlížeče a otevřete `word/document.xml`, najdete element `<w:shape>` s atributem `hidden="true"` a `<v:fillcolor>` nastaveným na `#00FF00`.

---

## Běžné varianty a okrajové případy

- **Různé typy tvarů:** Nahraďte `ShapeType.ELLIPSE` hodnotou `ShapeType.RECTANGLE`, `ShapeType.CLOUD` nebo jinou podporovanou enum hodnotou pro požadovanou geometrii.
- **Podmíněná viditelnost:** Můžete přepínat `ellipse.setHidden(false)` na základě logiky za běhu, což umožňuje dynamické generování dokumentů.
- **Komplexní výplně:** Místo plné barvy použijte `ellipse.getFill().setTextureImage(...)` pro vzorové výplně. Metoda `setHidden` stále řídí viditelnost.
- **Více tvarů:** Vytvořte pole nebo seznam objektů `Shape`, nakonfigurujte každý samostatně a skryjte jen ty, které splňují konkrétní kritéria.

*Tip:* Při generování velkých dokumentů opakovaně používejte jedinou instanci `DocumentBuilder` místo vytváření nové pro každý tvar. Tím snížíte paměťovou zátěž a zlepšíte výkon.

---

## Závěr

Nyní víte, jak **vytvořit Word dokument v Javě**, který vloží elipsu, **nastavit barvu výplně tvaru** a **skrýt tvar ve Wordu** pomocí Aspose.Words. Kompletní, spustitelný příklad demonstruje každé volání API, vysvětluje, proč je každý krok potřebný, a ukazuje očekávaný výsledek.

Dále prozkoumejte související témata, jako je **jak vložit tvar** s obtékáním textu, přidání hypertextových odkazů do tvarů a export dokumentu do PDF při zachování skrytých prvků. Experimentujte s různými barvami, velikostmi a příznaky viditelnosti, abyste přizpůsobili automatizaci Wordu potřebám vašeho projektu.

Chcete automatizovat další funkce Wordu? Podívejte se na dokumentaci Aspose.Words pro Java o [práci s tvary](https://docs.aspose.com/words/java/working-with-shapes/) a začněte dnes vytvářet bohatší, programově generované dokumenty.

## Co se naučíte dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}