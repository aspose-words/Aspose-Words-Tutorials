---
date: '2026-01-14'
description: Naučte se, jak restartovat číslování stránek pomocí Aspose.Words Java
  a použít LayoutCollector k extrakci dat o stránkování, aktualizaci rozvržení stránky
  a renderování stránek jako obrázků.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
title: Restartování číslování stránek s Aspose.Words Java – LayoutCollector a LayoutEnumerator
url: /cs/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Restartování číslování stránek s Aspose.Words pro Java – LayoutCollector & LayoutEnumerator

## Úvod

Máte potíže s **restartováním číslování stránek** ve velkých dokumentech založených na Javě a zároveň potřebujete analyzovat stránkování nebo vykreslovat stránky jako obrázky? S **Aspose.Words pro Java** můžete využít `LayoutCollector` a `LayoutEnumerator`, abyste nejen restartovali číslování stránek, ale také **extrahovali data o stránkování**, **aktualizovali rozvržení stránky** a **vykreslili stránky jako obrázky** pro náhledy nebo PDF. Tento průvodce vás provede každým krokem, od nastavení knihovny až po implementaci zpětných volání, která vám poskytne plnou kontrolu nad vykreslováním dokumentu.

**Co se naučíte**
- Jak použít `LayoutCollector` k extrahování dat o stránkování a určení rozsahu stránek.
- Procházení rozvržení dokumentu pomocí `LayoutEnumerator`.
- Implementace zpětných volání rozvržení stránky pro **vykreslení stránek jako obrázky**.
- **Restartování číslování stránek** v kontinuálních sekcích pomocí možností rozvržení.
- Tipy pro **efektivní aktualizaci rozvržení stránky**.

## Rychlé odpovědi
- **Jak restartuji číslování stránek v dokumentu Java?** Použijte `doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(...)` a zavolejte `doc.updatePageLayout()`.
- **Která třída extrahuje data o stránkování?** `LayoutCollector` poskytuje počáteční/koncové indexy stránek pro libovolný uzel.
- **Mohu vykreslit každou stránku jako obrázek?** Ano—implementujte `IPageLayoutCallback` a použijte `ImageSaveOptions`.
- **Musím ručně zavolat aktualizaci rozvržení stránky?** Po změně možností rozvržení vždy zavolejte `doc.updatePageLayout()`.
- **Jaká verze Aspose.Words je vyžadována?** Příklady fungují s Aspose.Words pro Java 25.3 (nebo novější).

## Co je restartování číslování stránek?

Restartování číslování stránek vám umožňuje zahájit novou sekvenci číslování v konkrétní sekci dokumentu, což je nezbytné pro zprávy, knihy nebo smlouvy, které vyžadují samostatné číslování kapitol nebo příloh. Aspose.Words poskytuje možnost rozvržení, která vám umožní tuto funkci řídit bez ručních triků s zalomením stránky.

## Proč používat LayoutCollector a LayoutEnumerator?

- **LayoutCollector** vám poskytuje programový přístup k detailům stránkování, což vám umožňuje **extrahovat data o stránkování**, jako je první a poslední stránka libovolného uzlu.
- **LayoutEnumerator** vám umožňuje procházet vizuální strom rozvržení, což usnadňuje vyhledávání stránek, odstavců nebo řádků pro vlastní vykreslování nebo analýzu.
- Společně zjednodušují složité úlohy rozvržení, které by jinak vyžadovaly nákladné konverze do PDF nebo ruční výpočty.

## Předpoklady

### Požadované knihovny a verze
Ujistěte se, že máte nainstalovanou Aspose.Words pro Java verze 25.3 (nebo novější).

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Požadavky na nastavení prostředí
- Nainstalovaný Java Development Kit (JDK).
- IntelliJ IDEA, Eclipse nebo jakékoli jiné Java IDE dle vašeho výběru.
- Platná licence Aspose.Words (bezplatná zkušební verze funguje pro hodnocení).

### Předpoklady znalostí
Základní znalost programování v Javě stačí.

## Nastavení Aspose.Words

Nejprve integrujte knihovnu Aspose.Words do svého projektu. Bezplatnou zkušební licenci můžete získat [zde](https://releases.aspose.com/words/java/) nebo použít dočasnou licenci pro testování.

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

S připravenou knihovnou můžeme přejít k hlavním funkcím.

## Průvodce implementací

### Funkce 1: Použití LayoutCollector pro analýzu rozsahu stránek

Funkce `LayoutCollector` vám umožňuje určit, jak uzly zasahují do stránek, což je základ pro **extrahování dat o stránkování**.

#### Přehled
Využitím `LayoutCollector` můžete získat počáteční a koncové indexy stránek libovolného uzlu a vypočítat celkový počet stránek, které zabírá.

#### Kroky implementace

**1. Inicializace dokumentu a LayoutCollector**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. Naplnění dokumentu**
Zde přidáme obsah, který zasahuje do více stránek:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. Aktualizace rozvržení a získání metrik**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### Vysvětlení
- **`DocumentBuilder`** vkládá text a zalomení stránky/sekce.
- **`updatePageLayout()`** přepočítá informace o rozvržení, aby data o stránkování byla přesná.

### Funkce 2: Procházení pomocí LayoutEnumerator

`LayoutEnumerator` umožňuje efektivní navigaci vizuálním stromem rozvržení.

#### Přehled
Můžete procházet stránky, odstavce, řádky a další entity rozvržení, což je užitečné pro vlastní vykreslování nebo diagnostiku.

#### Kroky implementace

**1. Inicializace dokumentu a LayoutEnumerator**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. Procházení dopředu a dozadu**
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### Vysvětlení
- **`moveParent()`** přesune enumerátor na nadřazený entitu (v tomto případě na úroveň stránky).
- Rekurzivní metody procházení vám umožní prozkoumat celou hierarchii rozvržení.

### Funkce 3: Zpětná volání rozvržení stránky

Implementujte zpětná volání pro sledování událostí rozvržení a **vykreslení stránek jako obrázky**, když je to potřeba.

#### Přehled
Rozhraní `IPageLayoutCallback` vás upozorní, když část dokumentu dokončí přetékání nebo když se dokončí konverze.

#### Kroky implementace

**1. Nastavení zpětného volání**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. Implementace metod zpětného volání**
```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### Vysvětlení
- **`notify()`** reaguje na události rozvržení.
- **`ImageSaveOptions`** spolu s `PageSet` vám umožní **vykreslit stránky jako obrázky** (PNG v tomto příkladu).

### Funkce 4: Restartování číslování stránek v kontinuálních sekcích

Řízení číslování stránek, když máte více sekcí, které plynule pokračují.

#### Přehled
Nastavením možnosti `ContinuousSectionRestart` můžete rozhodnout, zda se číslování stránek restartuje na nové stránce nebo pokračuje plynule.

#### Kroky implementace

**1. Načtení dokumentu**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. Konfigurace možností číslování stránek**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### Vysvětlení
- **`setContinuousSectionPageNumberingRestart()`** říká Aspose.Words, jak zacházet s číslováním v kontinuálních sekcích.
- Po změně možnosti **aktualizujte rozvržení stránky**, aby se změny projevily.

## Praktické aplikace
1. **Analýza stránkování dokumentu** – Použijte `LayoutCollector` k auditu, jak se obsah rozprostírá po stránkách, a podle toho upravte okraje nebo zalomení.
2. **Vykreslování PDF** – Kombinujte `LayoutEnumerator` se zpětným voláním k vytvoření vysoce kvalitních obrázků stránek před konverzí do PDF.
3. **Dynamické aktualizace dokumentu** – Reagujte na události rozvržení (např. po rozšíření tabulky) a automaticky znovu vykreslete ovlivněné stránky.
4. **Vícesekční zprávy** – Použijte **restartování číslování stránek**, aby každá kapitola měla vlastní schéma číslování při zachování kontinuálního toku.

## Úvahy o výkonu
- Odstraňte nepoužité sekce nebo skrytý obsah před voláním `updatePageLayout()`, aby zpracování bylo rychlé.
- Používejte streamingové API pro velké dokumenty, aby se předešlo načítání celého souboru do paměti.
- Omezte hloubku rekurzivního procházení v `LayoutEnumerator`, pokud potřebujete jen informace na úrovni stránky.

## Časté problémy a řešení

| Problém | Příčina | Řešení |
|-------|-------|-----|
| `layoutCollector.getNumPagesSpanned()` vrací 0 | Rozvržení nebylo aktualizováno | Zavolejte `doc.updatePageLayout()` před dotazem |
| Obrázky nejsou v callbacku generovány | Chybí konfigurace `ImageSaveOptions` | Ujistěte se, že je nastaveno `saveOptions.setPageSet(new PageSet(pageIndex))` |
| Čísla stránek se nerestartují | Špatná hodnota `ContinuousSectionRestart` | Použijte `ContinuousSectionRestart.FROM_NEW_PAGE_ONLY` pro skutečný restart |

## Často kladené otázky

**Q: Můžu extrahovat přesné číslo stránky konkrétního odstavce?**  
A: Ano—použijte `LayoutCollector` k získání počáteční stránky uzlu odstavce a poté zavolejte `doc.updatePageLayout()`, aby byla data aktuální.

**Q: Ovlivňuje `update page layout` obsah dokumentu?**  
A: Ne. Pouze přepočítá informace o rozvržení; skutečný text a formátování zůstávají nezměněny.

**Q: Jak efektivně vykreslit všechny stránky velkého dokumentu jako obrázky?**  
A: Implementujte `IPageLayoutCallback` a zpracovávejte každou stránku sekvenčně, případně použijte vícevláknové zpracování pro I/O‑vázané ukládání.

**Q: Je možné restartovat číslování jen pro určité sekce?**  
A: Ano—použijte `setContinuousSectionPageNumberingRestart` na možnosti rozvržení konkrétní sekce před zavoláním `updatePageLayout()`.

**Q: Která verze Aspose.Words zavedla `LayoutCollector`?**  
A: `LayoutCollector` je k dispozici od počátku vydání v roce 2020; příklady používají verzi 25.3.

## Závěr
Osvojením **restartování číslování stránek**, `LayoutCollector` a `LayoutEnumerator` nyní máte výkonný nástroj pro pokročilé zpracování textu v Aspose.Words pro Java. Ať už potřebujete **extrahovat data o stránkování**, **vykreslit stránky jako obrázky**, nebo jednoduše řídit číslování stránek napříč sekcemi, tyto API vám poskytují přesnou programovou kontrolu při zachování vysokého výkonu.

---

**Poslední aktualizace:** 2026-01-14  
**Testováno s:** Aspose.Words pro Java 25.3  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}