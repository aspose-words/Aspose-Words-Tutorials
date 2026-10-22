---
category: general
date: 2026-10-04
description: Naučte se, jak skrýt tvar ve Wordu pomocí Javy. Tento krok‑za‑krokem
  průvodce vám ukáže, jak skrýt tvar ve Wordu, jak učinit tvar neviditelným ve Wordu
  a jak programově skrýt tvar v Microsoft Wordu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible word
- hide shape microsoft word
language: cs
lastmod: 2026-10-04
og_description: Jak skrýt tvar ve Wordu pomocí Javy. Postupujte podle tohoto návodu,
  jak skrýt tvar ve Wordu, učinit tvar neviditelným ve Wordu a skrýt tvar v Microsoft
  Wordu pomocí několika řádků kódu.
og_image_alt: Screenshot showing a Word document with a hidden shape after applying
  the how to hide shape code
og_title: Jak skrýt tvar v dokumentu Word pomocí Javy – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to hide shape in Word with Java. This step‑by‑step guide
    shows you how to hide shape in Word, make shape invisible Word, and hide shape
    Microsoft Word programmatically.
  headline: How to hide shape in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Microsoft Word
- Document Automation
title: Jak skrýt tvar v dokumentu Word pomocí Javy
url: /cs/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak skrýt tvar v dokumentu Word pomocí Javy

Pokud potřebujete v souboru Word skrýt tvar, tento průvodce vám přesně ukáže **jak skrýt tvar** programově. Ať už generujete zprávy, čistíte šablony nebo připravujete dokumenty pro soulad, můžete tvar učinit neviditelným, aniž byste jej odstranili ze struktury souboru.

V následujících sekcích se naučíte, jak skrýt tvar ve Wordu, učinit tvar neviditelným ve Wordu a skrýt tvar v Microsoft Word pomocí knihovny Aspose.Words pro Javu. Tutoriál předpokládá, že máte základní znalosti Javy a funkční vývojové prostředí pro Javu.

## Požadavky

* Java Development Kit (JDK) 8 nebo novější  
* Maven nebo Gradle pro správu závislostí  
* Aspose.Words pro Javu (verze 23.9 nebo novější) – přidejte Maven koordinátu `com.aspose:aspose-words:23.9`  
* Dokument Word (`input.docx`) obsahující alespoň jeden tvar (např. obrázek, textové pole nebo SmartArt)

## Krok 1: Nastavte projekt a importujte Aspose.Words

Vytvořte nový Maven projekt nebo přidejte závislost Aspose.Words do existujícího projektu.

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier> <!-- adjust classifier for your JDK -->
</dependency>
```

Knihovna poskytuje třídy `Document`, `NodeType` a `Shape`, které jsou použity v následujících krocích. Importujte je na začátek vašeho Java zdrojového souboru:

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;
```

## Krok 2: Načtěte dokument Word

Načtení dokumentu je prvním krokem v jakémkoli workflow zpracování Wordu. Konstruktor `Document` načte soubor do paměti a zachová všechny uzly, včetně skrytých tvarů.

```java
// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Proč je to důležité*: Načtení souboru vytvoří DOM (Document Object Model), který vám umožní procházet, dotazovat se a upravovat jednotlivé uzly, jako jsou tvary, odstavce nebo tabulky.

## Krok 3: Získejte cílový tvar

Pokud dokument obsahuje více tvarů, můžete určitý tvar najít podle indexu, názvu nebo jiných kritérií. Pro rychlou ukázku příklad získá první tvar v hierarchii dokumentu, včetně tvarů vložených do tabulek nebo skupin.

```java
// Retrieve the first shape (including descendants)
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*Proč je to důležité*: Metoda `getChild` s hodnotou `true` pro příznak `isDeep` prochází celý strom uzlů a zajišťuje, že zachytíte tvary, které nejsou přímými potomky těla dokumentu.

## Krok 4: Skryjte tvar

Nastavení vlastnosti `Hidden` na `true` říká Microsoft Wordu, aby tvar vyloučil z vykreslování rozvržení, přičemž jej ponechá ve struktuře dokumentu. Tvar nebude viditelný při otevření souboru ve Wordu, ale zůstane přístupný pro pozdější zpracování.

```java
// Hide the shape so it does not appear in the layout
shape.setHidden(true);
```

*Proč je to důležité*: Skrytí tvaru je užitečné, když potřebujete tvar zachovat pro pozdější aktivaci (např. podmíněný obsah, verzování) aniž by byl zobrazen koncovému uživateli.

## Krok 5: Uložte upravený dokument

Po změně viditelnosti tvaru zapište dokument zpět na disk. Můžete přepsat původní soubor nebo vytvořit nový; příklad zapisuje do `HiddenShape.docx`.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx");
```

Když otevřete `HiddenShape.docx` v Microsoft Wordu, tvar bude neviditelný, ale rozvržení dokumentu bude odrážet jeho skrytý stav (žádné další prázdné místo).

## Kompletní spustitelný příklad

Spojením všech kroků získáte samostatný program, který můžete přímo zkompilovat a spustit.

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

/**
 * Demonstrates how to hide shape in a Word document using Aspose.Words for Java.
 */
public class HideShapeExample {
    public static void main(String[] args) {
        // Verify that the input path is provided
        if (args.length != 1) {
            System.out.println("Usage: java HideShapeExample <input-docx-path>");
            return;
        }

        String inputPath = args[0];
        String outputPath = "HiddenShape.docx";

        try {
            // Step 1: Load the Word document
            Document doc = new Document(inputPath);

            // Step 2: Retrieve the first shape (including descendants)
            Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
            if (shape == null) {
                System.out.println("No shape found in the document.");
                return;
            }

            // Step 3: Hide the shape
            shape.setHidden(true);

            // Step 4: Save the modified document
            doc.save(outputPath);
            System.out.println("Shape hidden successfully. Output saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error processing document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Očekávaný výsledek**  
Spuštěním programu se vytvoří `HiddenShape.docx`. Otevřením tohoto souboru v Microsoft Wordu se zobrazí původní obsah, ale tvar, který byl v `input.docx`, již není viditelný. Struktura dokumentu stále obsahuje uzel tvaru, který lze později znovu zobrazit nastavením `shape.setHidden(false)`.

## Proč skrýt tvar místo jeho smazání?

* **Zachovat metadata** – Tvary často obsahují alternativní text, hypertextové odkazy nebo vlastní data, která můžete později potřebovat.  
* **Podmíněné zobrazení** – V scénářích hromadné korespondence nebo generování zpráv můžete tvar zobrazit jen pro konkrétní příjemce.  
* **Správa verzí** – Udržení tvaru skrytého vám umožní mít jedinou šablonu a programově přepínat jeho viditelnost.

## Běžné varianty a okrajové případy

| Situace | Doporučené úpravy |
|-----------|------------------------|
| Více tvarů, potřeba konkrétního | Použijte `doc.getChild(NodeType.SHAPE, index, true)` s odpovídajícím indexem, nebo iterujte přes `doc.getChildNodes(NodeType.SHAPE, true)` a porovnávejte `shape.getName()` nebo `shape.getAlternativeText()`. |
| Tvar je uvnitř GroupShape | Hluboké hledání (`true`) již dosáhne do skupin, ale může být potřeba nejprve přetypovat na `GroupShape`, pokud chcete skrýt jen člena skupiny. |
| Chcete skrýt všechny tvary | Projděte všechny uzly tvarů a v cyklu zavolejte `setHidden(true)`. |
| Kompatibilita se staršími verzemi Wordu | `Hidden` příznak je podporován od Wordu 2000. Starší formáty (`.doc`) jej také respektují, ale otestujte na cílové verzi, pokud narazíte na neočekávané změny rozvržení. |

**Tip:** Po skrytí tvaru můžete zavolat `doc.updatePageLayout()`, pokud potřebujete, aby se před uložením přepočítalo rozvržení stránky. To je zřídka potřeba, protože Word automaticky při otevření přetéká obsah, ale může být užitečné pro generování náhledů na serveru.

## Testování výsledku programově

Pokud chcete potvrdit, že je tvar skrytý, aniž byste otevírali Word, můžete po uložení dotázat se na vlastnost:

```java
Document checkDoc = new Document(outputPath);
Shape hiddenShape = (Shape) checkDoc.getChild(NodeType.SHAPE, 0, true);
System.out.println("Shape hidden flag: " + hiddenShape.isHidden()); // prints true
```

## Další kroky

Nyní, když víte, jak skrýt tvar ve Wordu, zvažte tato související témata:

* **Skrýt tvar ve Wordu na základě vlastních podmínek** – Kombinujte příznak `Hidden` s poli hromadné korespondence pro přepínání viditelnosti podle příjemce.  
* **Učinit tvar neviditelným ve Wordu pomocí VBA** – Pro automatizaci na zařízení lze stejnou vlastnost nastavit pomocí VBA (`Shape.Visible = msoFalse`).  
* **Hromadně skrýt tvar v Microsoft Word** – Zpracujte složku dokumentů pomocí smyčky, která aplikuje stejný kód na každý soubor.  

Prozkoumání těchto rozšíření prohloubí vaši kontrolu nad automatizací dokumentů Word a udrží vaše generované soubory čisté a profesionální.

--- 

*Tento tutoriál následuje Google Developer Documentation Style Guide, používá aktivní hlas, druhou osobu a poskytuje kompletní, citovatelný řešení jak pro vyhledávače, tak pro AI asistenty.*

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit obdélníkový tvar ve Wordu pomocí Javy – Kompletní průvodce](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Přidat stín k tvaru ve Wordu – Kompletní průvodce Aspose.Words](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Vytvořit Word dokument v Javě – Přidat obdélníkový tvar se stínovým efektem](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}