---
category: general
date: 2026-07-03
description: Nastavte režim obnovy pro opravu poškozených souborů Word v Javě a po
  načtení zobrazte počet stránek. Naučte se krok po kroku s Aspose.Words.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: cs
og_description: Nastavte režim obnovy v Aspose.Words pro Java, abyste obnovili poškozené
  soubory Word a zobrazili počet stránek. Sledujte kompletní příklad nyní.
og_title: Nastavte režim obnovy v Aspose.Words pro Javu – kompletní tutoriál
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: Nastavení režimu obnovy v Aspose.Words pro Java – kompletní průvodce
url: /cs/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení režimu obnovy v Aspose.Words pro Java – Kompletní průvodce

Už jste se někdy zamýšleli, jak **nastavit režim obnovy** při načítání poškozeného souboru `.docx` pomocí Aspose.Words? Nejste jediní, kdo se trápí s poškozenými dokumenty Word, které se odmítají otevřít. V tomto tutoriálu vás provedeme právě tím – jak nakonfigurovat knihovnu tak, aby **obnovila poškozené Word** soubory a následně **zobrazila počet stránek** úspěšně načteného obsahu.

Probereme vše od drobného nastavení `LoadOptions` až po závěrečný `System.out.println`, který vám řekne, kolik stránek přežilo záchrannou operaci. Žádné zbytečnosti, jen praktické řešení připravené ke kopírování a vložení, které funguje s nejnovějším vydáním Aspose.Words 23.12.

## Co se naučíte

- Proč je režim obnovy důležitý a jaké možnosti Aspose.Words nabízí.  
- Jak programově pomocí Javy **nastavit režim obnovy**.  
- Jak **zobrazit počet stránek** po načtení dokumentu, čímž potvrdíte úspěšnost obnovy.  
- Běžné úskalí při práci s poškozenými soubory Word a jak se jim vyhnout.  

Než se ponoříme dál, ujistěte se, že máte:

1. Platnou licenci Aspose.Words pro Java (nebo dočasný evaluační klíč).  
2. Java 17 nebo novější nainstalovanou na vašem počítači.  
3. Poškozený soubor `Corrupted.docx`, který chcete otestovat.  

Máte je? Skvělé—pustíme se do toho.

> **Tip:** I když používáte zkušební verzi, funkce obnovy fungují přesně stejně jako v licencované verzi.

---

## ## Jak nastavit režim obnovy pomocí Aspose.Words pro Java

Jádro řešení spočívá ve třídě `LoadOptions`. Ve výchozím nastavení se Aspose.Words snaží načíst dokument co nejlépe, ale když je soubor vážně poškozený, musíte mu říct, *jak* se má chovat. Právě zde vstupuje do hry **nastavení režimu obnovy**.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### Proč `RecoveryMode.PARSE`?

- **PARSE** – Aspose.Words parsuje všechny fragmenty, které dokáže pochopit, a spojí je do částečně funkčního dokumentu. Ideální, když potřebujete *jakýkoli* obsah z poškozeného souboru.  
- **SKIP** – Knihovna přeskočí poškozené sekce úplně, což může být rychlejší, ale může zahodit více dat.  

Ve většině reálných scénářů je **PARSE** bezpečnější volbou, protože maximalizuje množství obnovitelného textu, obrázků a formátování.

---

## ## Zobrazení počtu stránek po obnově

Jakmile je dokument načten, dalším logickým krokem je ověření úspěšnosti operace. Nejjednodušší, ale zároveň nejinformativnější metrika, je počet stránek. Metoda `Document.getPageCount()` právě to provádí.

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

Pokud byl soubor zcela nečitelné, Aspose.Words vyhodí výjimku *před* tím, než se dostanete k tomuto řádku. Když vidíte počet stránek `0` nebo velmi nízké číslo, obvykle to znamená, že režim obnovy musel odhodit velké části původního souboru.

**Očekávaný výstup (příklad):**

```
Document loaded, page count = 12
```

To vám říká, že knihovna dokázala rekonstruovat dvanáct stránek z poškozeného zdroje – docela solidní výsledek pro poškozený `.docx`.

---

## ## Okrajové případy a běžné úskalí

### 1️⃣ Poškozené sekce hlavičky/patky
Někdy se parsuje pouze hlavní tělo, zatímco hlavičky a patky jsou ztraceny. Pokud na nich závisíte pro branding, možná je budete muset po obnově znovu vložit.

### 2️⃣ Obrázky, které se nenačtou
Vložené obrázky jsou často odstraněny, když je poškozena zipová kontejnér (základní formát `.docx`). Toto můžete zachytit iterací přes `doc.getSections()` a kontrolou `Section.getBody().getParagraphs()` na objekty `Shape`.

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

Pokud smyčka nic nevytiskne, pravděpodobně režim obnovy obrázky přeskočil.

### 3️⃣ Velké dokumenty a paměť
Obnova 200‑stránkového poškozeného souboru může být náročná na paměť. Zvažte zvýšení velikosti haldy JVM (`-Xmx2g`), pokud očekáváte obrovské dokumenty.

### 4️⃣ Omezení licence
Evaluační verze omezuje některé funkce, ale **obnova** je plně funkční. Nicméně vytištěný počet stránek může být v trial verzi omezen na několik stránek. Vždy testujte s licencovanou verzí pro produkci.

---

## ## Kompletní end‑to‑end příklad (spustitelný)

Níže je samostatný program, který můžete vložit do libovolného Maven nebo Gradle projektu. Obsahuje potřebné deklarace závislostí pro Aspose.Words 23.12.

### Maven `pom.xml` úryvek

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Java zdrojový soubor `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Co to dělá:**

1. **Nastaví režim obnovy** – jádro našeho tutoriálu.  
2. Načte poškozený soubor pomocí nakonfigurovaných `LoadOptions`.  
3. **Zobrazí počet stránek**, což vám poskytne okamžitou zpětnou vazbu.  
4. Uloží vyčištěnou verzi (`Recovered.docx`), kterou můžete později otevřít ve Wordu.

Spusťte program pomocí:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

Měli byste vidět vytištěný počet stránek v konzoli, což potvrzuje úspěšnou obnovu.

---

## ## Vizuální přehled (obrázek)

![diagram toku nastavení režimu obnovy](https://example.com/images/recovery-mode-flow.png "Diagram ukazující, jak funguje nastavení režimu obnovy v Aspose.Words pro Java")

*Alt text obsahuje primární klíčové slovo **set recovery mode** pro SEO.*

---

## ## Často kladené otázky

**Q: Co když `RecoveryMode.PARSE` stále vyhodí výjimku?**  
A: To obvykle znamená, že soubor je nevyprobatelný – možná je zipová kontejnér úplně poškozena. V takových případech můžete potřebovat nástroj třetí strany na opravu před předáním Aspose.Words.

**Q: Můžu kombinovat `RecoveryMode.PARSE` s vlastními zpětnými voláními při načítání dokumentu?**  
A: Rozhodně. Implementujte `IWarningCallback`, abyste zachytili všechna varování, která Aspose.Words během procesu parsování generuje. To vám poskytne přehled o tom, které části byly přeskočeny.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**Q: Ovlivní změna režimu obnovy původní soubor?**  
A: Ne. Aspose.Words pracuje s kopií v paměti; zdrojový soubor zůstane nedotčen, pokud výslovně nevoláte `doc.save()`.

---

## ## Závěr

Přehledně jsme probrali, jak **nastavit režim obnovy** v Aspose.Words pro Java, proč je `PARSE` obecně nejlepší volbou pro záchranu poškozeného dokumentu, a jak **zobrazit počet stránek** pro ověření výsledku. Podle kompletního příkladu máte nyní připravené řešení, které může **obnovit poškozené Word** soubory a poskytnout okamžitou zpětnou vazbu o úspěšnosti operace.

Další kroky? Vyzkoušejte výměnu `RecoveryMode.SKIP` a podívejte se na rozdíl, experimentujte s velkými soubory s více sekcemi, nebo integrujte logiku do webové služby, která automaticky opravuje nahrané dokumenty uživatelů. Stejný vzor funguje i pro PDF (pomocí Aspose.PDF) a dokonce i pro obnovu prostého textu s jinými knihovnami – stačí si zapamatovat základní myšlenku: nakonfigurujte načítač, pokuste se o obnovu a následně ověřte pomocí jednoduché metriky, jako je počet stránek.

Šťastné kódování a ať vaše dokumenty zůstávají neporušené!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Combine Multiple Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}