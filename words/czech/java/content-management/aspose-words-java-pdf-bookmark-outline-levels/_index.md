---
date: '2025-11-27'
description: Naučte se, jak vytvářet záložky, generovat PDF se záložkami a převádět
  Word do PDF v Javě pomocí Aspose.Words. Tento průvodce zahrnuje vnořené záložky
  a úrovně osnov.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: cs
title: Jak vytvořit záložky a nastavit úrovně osnovy v PDF pomocí Aspose.Words Java
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit záložky a nastavit úrovně osnovy v PDF pomocí Aspose.Words Java

## Úvod
Pokud jste někdy měli potíže s **how to create bookmarks**, které zůstávají uspořádané při převodu dokumentu Word do PDF, jste na správném místě. V tomto tutoriálu projdeme kompletní proces generování PDF se záložkami, jejich vnořením a přiřazením úrovní osnovy, aby bylo finální PDF snadno navigovatelné. Na konci budete schopni **convert Word PDF Java**‑styl s čistou hierarchií záložek, která funguje v jakémkoli PDF prohlížeči.

### Co se naučíte
- Nastavte Aspose.Words pro Java ve svém vývojovém prostředí.  
- **How to create bookmarks** programmatically and nest them.  
- Nakonfigurujte úrovně osnovy záložek pro generování PDF se záložkami, které odrážejí strukturu dokumentu.  
- Uložte soubor Word jako PDF při zachování hierarchie záložek.

## Rychlé odpovědi
- **Jaká je hlavní třída pro vytváření dokumentů?** `DocumentBuilder`.  
- **Která možnost řídí hierarchii záložek?** `BookmarksOutlineLevelCollection` uvnitř `PdfSaveOptions`.  
- **Mohu použít Maven nebo Gradle?** Ano – oba jsou zobrazeny níže.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro testování; pro produkci je vyžadována trvalá licence.  
- **Je tento přístup vhodný pro velké dokumenty?** Ano, ale zvažte techniky optimalizace paměti (např. odstranění nepoužívaných zdrojů).

### Předpoklady
- **Knihovny a závislosti** – Aspose.Words pro Java (25.3 nebo novější).  
- **Prostředí** – JDK 8 nebo novější a IDE jako IntelliJ IDEA nebo Eclipse.  
- **Základní znalosti** – Základy programování v Javě a znalost Maven nebo Gradle.

## Nastavení Aspose.Words
Pro začátek zahrňte potřebné závislosti do svého projektu. Zde je návod, jak přidat Aspose.Words pomocí Maven nebo Gradle:

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

### Získání licence
Aspose.Words je komerční knihovna, ale můžete začít s bezplatnou zkušební verzí:

1. **Free Trial** – Stáhněte z [Aspose release page](https://releases.aspose.com/words/java/).  
2. **Temporary License** – Požádejte na [temporary‑license page](https://purchase.aspose.com/temporary-license/), pokud potřebujete krátkodobý klíč.  
3. **Full License** – Zakupte přes [Aspose purchasing portal](https://purchase.aspose.com/buy) pro produkční použití.

Po získání souboru licence jej načtěte při spuštění aplikace, aby se odemkly všechny funkce.

## Jak vytvořit záložky v PDF pomocí Aspose.Words Java
Níže rozdělíme implementaci do přehledných číslovaných kroků. Každý krok obsahuje krátké vysvětlení následované původním blokem kódu (beze změny).

### Krok 1: Inicializace Document a DocumentBuilder
Začínáme s čerstvou instancí `Document` a `DocumentBuilder`, který nám umožňuje vkládat obsah a záložky.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Krok 2: Vložení první (rodičovské) záložky
Vytvořte záložku nejvyšší úrovně, která později bude obsahovat podřízenou záložku.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Krok 3: Vnoření podřízené záložky do rodičovské
Nyní přidáme druhou záložku, která se nachází uvnitř první, což demonstruje vnoření.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Krok 4: Uzavření rodičovské záložky
Dokončete vnější záložku po vnořeném obsahu.

```java
builder.endBookmark("Bookmark 1");
```

### Krok 5: Přidání samostatné třetí záložky
Vždy můžete přidat další záložky, které nejsou vnořeny.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Konfigurace úrovní osnovy záložek
Po vytvoření záložek řekneme Aspose.Words, jak by měly tyto záložky vypadat v osnově PDF (levý navigační panel).

### Krok 6: Příprava PdfSaveOptions
`PdfSaveOptions` nám poskytuje přístup k nastavením osnovy.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Krok 7: Přiřazení úrovní hierarchie
Každá záložka dostane celočíselnou úroveň; nižší čísla jsou výše v hierarchii.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Krok 8: Uložení dokumentu jako PDF
Konečně exportujte dokument Word do PDF při zachování osnovy záložek.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Proč použít tento přístup k generování PDF se záložkami?
- **Professional Navigation** – Čtenáři mohou přejít přímo na sekce, což zlepšuje použitelnost velkých zpráv nebo právních smluv.  
- **Full Control** – Hierarchii rozhodujete vy, ne PDF prohlížeč.  
- **Cross‑Platform** – Funguje stejně na Windows, Linuxu i macOS, protože je čistě Java.

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Řešení |
|---|---|---|
| Chybějící záložky v PDF | `startBookmark` bez odpovídajícího `endBookmark` | Ověřte, že každý `startBookmark` má odpovídající `endBookmark`. |
| Nesprávná hierarchie | Úrovně osnovy přiřazeny v nesprávném pořadí | Zajistěte, aby rodičovské záložky měly nižší čísla úrovní než jejich podřízené. |
| Licence nebyla použita | Soubor licence nebyl načten před vytvořením dokumentu | Load the license at the very start of your application (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## Praktické aplikace
1. **Legal Documents** – Rychle navigujte v klauzulech, přílohách a dodatcích.  
2. **Financial Reports** – Přepínejte mezi sekcemi jako Výkaz zisku a ztráty, Rozvaha a Poznámky.  
3. **E‑Learning Materials** – Poskytněte obsah, který odráží osnovu PDF.

## Úvahy o výkonu
- **Memory Management** – Pro velmi velké soubory Word zvažte volání `doc.cleanup()` před uložením.  
- **Resource Optimization** – Odstraňte nepoužívané obrázky nebo styly, aby byl PDF soubor malý.

## Často kladené otázky

**Q: Jak nainstaluji Aspose.Words pro Java?**  
A: Přidejte Maven nebo Gradle závislost uvedenou výše, poté umístěte soubor licence do classpath a načtěte jej za běhu.

**Q: Můžu vytvořit záložky bez nastavení úrovní osnovy?**  
A: Ano, ale PDF prohlížeč je zobrazí jako plochý seznam, což může být obtížné navigovat v komplexních dokumentech.

**Q: Existuje limit, jak hluboko mohou být záložky vnořeny?**  
A: Technicky ne, ale většina PDF prohlížečů pohodlně podporuje až 9 úrovní. Udržujte hierarchii logickou pro čtenáře.

**Q: Jak Aspose zachází s velmi velkými soubory Word?**  
A: Knihovna streamuje obsah a poskytuje metody jako `Document.optimizeResources()` ke snížení paměťové náročnosti.

**Q: Můžu upravit záložky po vygenerování PDF?**  
A: Určitě – můžete použít Aspose.PDF pro Java k přidání, odebrání nebo přejmenování záložek v existujícím PDF.

## Zdroje
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)  
- [Download Latest Releases](https://releases.aspose.com/words/java/)  
- [Purchase a License](https://purchase.aspose.com/buy)  
- [Free Trial](https://releases.aspose.com/words/java/)  
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)  
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Poslední aktualizace:** 2025-11-27  
**Testováno s:** Aspose.Words 25.3 for Java  
**Autor:** Aspose