---
date: '2025-11-12'
description: Naučte se, jak používat LayoutCollector a LayoutEnumerator v Aspose.Words
  pro Javu k určení rozsahů stránek, procházení entit rozvržení a restartování číslování
  stránek v souvislých sekcích.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- determine page span
- analyze document pagination
- restart page numbering
language: cs
title: 'Aspose.Words Java: Průvodce LayoutCollector a LayoutEnumerator'
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: Průvodce LayoutCollector a LayoutEnumerator

## Úvod  

Máte potíže s **určením rozsahu stránky**, analýzou stránkování nebo restartováním číslování stránek v složitých Java dokumentech? S **Aspose.Words for Java** můžete tyto problémy rychle vyřešit pomocí `LayoutCollector` a `LayoutEnumerator`. V tomto průvodci vám ukážeme **jak použít LayoutCollector**, **jak procházet LayoutEnumerator** a jak řídit číslování stránek v kontinuálních sekcích — vše s přehledným, krok‑za‑krokem kódem, který můžete spustit ještě dnes.

Dozvíte se, jak:

1. Použít `LayoutCollector` k **určení rozsahu stránky** libovolného uzlu.  
2. **Procházet layoutové entity** pomocí `LayoutEnumerator`.  
3. Implementovat layoutové callbacky pro dynamické vykreslování.  
4. **Restartovat číslování stránek** v kontinuálních sekcích.  

Začneme tím, že se ujistíme, že je vaše prostředí připravené.

## Požadavky  

### Potřebné knihovny  

> **Poznámka:** Kód funguje s nejnovější verzí Aspose.Words for Java (není potřeba uvádět číslo verze).  

**Maven**

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>latest</version>
</dependency>
```

**Gradle**

```gradle
implementation 'com.aspose:aspose-words:latest'
```

### Prostředí  

- JDK 17 nebo novější.  
- IntelliJ IDEA, Eclipse nebo jakékoli jiné Java IDE, které preferujete.  

### Znalosti  

Základní povědomí o syntaxi Javy a objektově orientovaných konceptech vám usnadní sledování příkladů.

## Nastavení Aspose.Words  

Nejprve přidejte knihovnu Aspose.Words do svého projektu a aplikujte licenci (nebo použijte zkušební verzi). Následující úryvek ukazuje, jak načíst licenci a potvrdit, že je knihovna připravena:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file (skip this line for a trial)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

> **Tip:** Uložte soubor s licencí mimo verzovací systém, abyste ochránili své přihlašovací údaje.

Nyní se můžeme ponořit do dvou hlavních funkcí.

## 1. Jak použít LayoutCollector pro analýzu rozsahu stránky  

`LayoutCollector` vám umožní **určit rozsah stránky** pro libovolný uzel v dokumentu, což je nezbytné pro analýzu stránkování.

### Krok‑za‑krokem implementace  

1. **Vytvořte nový Document a instanci LayoutCollector.**  
2. **Přidejte obsah, který zabírá více stránek.**  
3. **Obnovte layout a dotazujte metriky rozsahu stránky.**  

```java
// 1. Initialize Document and LayoutCollector
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);

// 2. Populate the Document with multi‑page content
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);

// 3. Update layout and retrieve page‑span information
layoutCollector.clear();          // Reset any previous state
doc.updatePageLayout();           // Force layout calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected number of pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Vysvětlení**

- `DocumentBuilder` vkládá text a zalomení, čímž vytvoří dokument, který přirozeně zabírá několik stránek.  
- `updatePageLayout()` vynutí výpočet layoutu v Aspose.Words, což zajišťuje přesná čísla stránek.  
- `getNumPagesSpanned()` vrací celkový počet stránek, které pokrývá zadaný uzel (zde celý dokument).

## 2. Jak procházet LayoutEnumerator  

`LayoutEnumerator` poskytuje **strukturální pohled na layoutové entity** (stránky, odstavce, běhy atd.) a umožňuje se pohybovat dopředu i dozadu.

### Krok‑za‑krokem implementace  

1. Načtěte existující dokument, který obsahuje layoutové entity.  
2. Vytvořte instanci `LayoutEnumerator`.  
3. Přesuňte se na úroveň stránky a poté procházejte dopředu i dozadu pomocí pomocných metod.

```java
// 1. Load the document containing layout entities
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");

// 2. Initialize LayoutEnumerator
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);

// 3. Position the enumerator at the page level
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Forward traversal
traverseLayoutForward(layoutEnumerator, 1);

// Backward traversal
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Poznámka:** Metody `traverseLayoutForward` a `traverseLayoutBackward` jsou rekurzivní pomocníci, kteří procházejí strom layoutu. Můžete je upravit tak, aby sbíraly informace jako ohraničující rámečky, detaily fontů nebo vlastní metadata.

## 3. Jak implementovat callbacky pro layout stránky  

Někdy potřebujete reagovat na události layoutu — např. když sekce dokončí přetékání nebo když konverze do jiného formátu skončí. Implementujte rozhraní `IPageLayoutCallback`, abyste získali tato oznámení.

### Krok‑za‑krokem implementace  

1. Nastavte instanci callbacku v možnostech layoutu dokumentu.  
2. Definujte logiku callbacku pro zpracování událostí `PART_REFLOW_FINISHED` a `CONVERSION_FINISHED`.  

```java
// 1. Register the callback
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();   // Triggers the callback during layout processing

// 2. Callback implementation
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs args) throws Exception {
        if (args.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            renderPage(args, args.getPageIndex());
        } else if (args.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            System.out.println("Document conversion finished.");
        }
    }

    private void renderPage(PageLayoutCallbackArgs args, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            args.getDocument().save(stream, saveOptions);
        }
    }
}
```

**Vysvětlení**

- `notify()` přijímá každou událost layoutu. Filtrujeme jen ty, které nás zajímají.  
- Když část dokončí přetékání, `renderPage()` uloží tuto stránku jako PNG obrázek.

## 4. Jak restartovat číslování stránek v kontinuálních sekcích  

Když dokument obsahuje kontinuální sekce, můžete chtít, aby se číslování stránek restartovalo pouze na nové stránce. Aspose.Words vám to umožní pomocí `ContinuousSectionRestart`.

### Krok‑za‑krokem implementace  

1. Načtěte cílový dokument.  
2. Nastavte možnost `ContinuousSectionPageNumberingRestart`.  
3. Obnovte layout, aby se změna projevila.

```java
// 1. Load the multi‑section document
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");

// 2. Configure page‑numbering restart behavior
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);

// 3. Update layout to reflect the new numbering scheme
doc.updatePageLayout();
System.out.println("Page numbering restart configured for continuous sections.");
```

**Vysvětlení**

- `FROM_NEW_PAGE_ONLY` říká Aspose.Words, aby restartovalo číslování pouze tehdy, když se objeví nová fyzická stránka, čímž zachová plynulý tok napříč kontinuálními sekcemi.

## Praktické aplikace  

| Scénář | Která funkce pomáhá? | Přínos |
|----------|----------------------|---------|
| **Auditovat stránkování dokumentu** | `LayoutCollector` | Rychle najdete sekce, které přesahují stránky. |
| **Vytvářet PDF s naprostou vizuální věrností** | `LayoutEnumerator` + callbacky | Přístup k detailům layoutu pro přesné vykreslení. |
| **Automaticky vkládat vodoznak po každém layoutu stránky** | Callbacky pro layout stránky | Okamžitě reagujete, když je stránka vytvořena. |
| **Generovat vícesekční zprávy s vlastním číslováním** | Restart číslování kontinuální sekce | Udržujete profesionální číslování bez ručních úprav. |

## Tipy pro výkon  

- **Odstraňte nepoužívané uzly** před voláním `updatePageLayout()`, aby se snížila spotřeba paměti.  
- **Znovu použijte jediný LayoutCollector** pro více dotazů místo jeho opakovaného vytváření.  
- **Omezte hloubku rekurze** v pomocných metodách procházení, aby nedošlo k přetečení zásobníku u velmi velkých dokumentů.  

## Závěr  

Ovládnutím **používání LayoutCollector**, **procházení LayoutEnumerator** a **restartování číslování stránek** máte nyní výkonnou sadu nástrojů pro pokročilé zpracování textu s Aspose.Words for Java. Tyto techniky vám umožní **určovat rozsah stránky**, **analyzovat stránkování dokumentu** a **kontrolovat chování layoutu** s jistotou. Použijte je v reportech, e‑knihách nebo jakémkoli automatizovaném workflow dokumentů a zaznamenáte výrazné zlepšení jak v přesnosti, tak v produktivitě.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}