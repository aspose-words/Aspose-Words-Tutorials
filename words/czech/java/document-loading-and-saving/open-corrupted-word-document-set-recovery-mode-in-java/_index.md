---
category: general
date: 2026-05-26
description: Otevřete poškozený dokument Word v Javě pomocí Aspose.Words. Naučte se
  nastavit režim obnovy a spolehlivě obnovit poškozené soubory Word.
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: cs
og_description: Otevřete poškozený dokument Word v Javě pomocí Aspose.Words. Tento
  průvodce ukazuje, jak nastavit režim obnovy a efektivně obnovit poškozené soubory
  Word.
og_title: Otevřít poškozený dokument Word – nastavit režim obnovy v Javě
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: Otevřít poškozený dokument Word – nastavit režim obnovy v Javě
url: /cs/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Otevření poškozeného dokumentu Word – Nastavení režimu obnovy v Javě

Už jste někdy zkoušeli otevřít poškozený dokument Word a sledovali, jak se program zadrhne na výjimce? Nejste sami – tyto poškozené soubory .docx mohou být skutečnou hlavolam. Dobrou zprávou je, že Aspose.Words for Java vám poskytuje detailní kontrolu, takže můžete **otevřít poškozený dokument Word** bez zhroucení aplikace a dokonce si můžete zvolit, zda chcete varování, tichou obnovu nebo tvrdé odmítnutí.

V tomto tutoriálu projdeme kompletním procesem: od vytvoření správných `LoadOptions`, přes výběr vhodné hodnoty **set recovery mode**, až po potvrzení, že dokument byl skutečně načten. Na konci budete vědět **jak programově obnovit poškozený soubor Word**, bez nutnosti ručního kopírování a vkládání.

> **Co budete potřebovat**  
> * Java 8 nebo novější (API funguje také s Java 11)  
> * Aspose.Words for Java 23.9 (nebo nejnovější verze)  
> * Ukázkový poškozený .docx soubor – stačí přejmenovat libovolný platný soubor, aby se simulovalo poškození, pokud žádný po ruce nemáte  

Pojďme na to.

## Otevření poškozeného dokumentu Word – Přehled krok za krokem

Níže je vysokou úrovní tok, který implementujeme:

1. **Vytvořte `LoadOptions`** – tento objekt říká Aspose.Words, jak se má chovat, když narazí na potíže.  
2. **Nastavte režim obnovy** – vyberte `RECOVER_WITH_WARNINGS`, `RECOVER_WITHOUT_WARNINGS` nebo `REJECT_CORRUPTED`.  
3. **Načtěte dokument** pomocí nakonfigurovaných možností.  
4. **Ověřte**, že načtení bylo úspěšné (např. vytiskněte počet stránek).  

Každý krok je podrobně vysvětlen, s úryvky kódu, které můžete zkopírovat přímo do svého IDE.

## Nastavení režimu obnovy pro různé scénáře

Aspose.Words definuje tři strategie obnovy uvnitř `LoadOptions.RecoveryMode`:

| Mode | Chování | Kdy použít |
|------|-----------|-------------|
| `RECOVER_WITH_WARNINGS` | Pokusí se načíst dokument, ale všechny problémy zobrazí jako varování v konzoli. | Chcete vidět *co* se pokazilo, aniž byste přerušili proces. |
| `RECOVER_WITHOUT_WARNINGS` | Tichým způsobem opraví, co může, a potlačí varování. | Produkční prostředí, kde musí být logy čisté. |
| `REJECT_CORRUPTED` | Vyhodí výjimku okamžitě po zjištění poškození. | Přísné validační řetězce, které musí selhat co nejdříve. |

Výběr správného režimu je podstatou správného **set recovery mode**. Ve většině ladicích sezení je `RECOVER_WITH_WARNINGS` ideální, protože vám přesně řekne, které části byly opraveny.

## Jak obnovit poškozený soubor Word pomocí Aspose.Words

Níže je **kompletní, spustitelný Java program**, který demonstruje celý proces. Klidně jej vložte do souboru `RecoveryModeDemo.java`, upravte cestu a spusťte.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### Proč je každý řádek důležitý

* **`LoadOptions loadOptions = new LoadOptions();`** – bez tohoto objektu Aspose.Words používá výchozí obnovu, která *odmítá* poškozené soubory. Vytvořením získáte háček pro změnu tohoto chování.  
* **`setRecoveryMode(...)`** – toto je volání **set recovery mode**, které rozhoduje, zda se zobrazí varování, zůstanou skrytá, nebo vyvolá výjimku.  
* **`new Document(path, loadOptions);`** – konstruktor přijímá `LoadOptions`, které jsme právě nakonfigurovali, takže knihovna ví, jak má od začátku zacházet s poškozeným souborem.  
* **`doc.getPageCount()`** – rychlá kontrola. Pokud se dokument načte a vrátí počet stránek, úspěšně jste **jak obnovit poškozený soubor Word**.  
* **`doc.save(...)`** – volitelné, ale užitečné; můžete zapsat opravenou verzi zpět na disk pro pozdější použití.  

## Řešení běžných okrajových případů

### 1. Soubor nenalezen

Pokud je cesta špatná, `Document` vyhodí `FileNotFoundException`. Zabalte načítání do bloku try‑catch a zaznamenejte přátelskou zprávu:

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. Neobnovitelné poškození

I při `RECOVER_WITH_WARNINGS` jsou některé struktury neobnovitelné. V takovém případě Aspose.Words načte, co může, ale uvidíte varování jako „Cannot read paragraph properties“. Věnujte pozornost výstupu v konzoli; tato varování často ukazují na chybějící sekce, které možná budete muset ručně rekonstruovat.

### 3. Velké soubory a výkon

Obnova přidává malé zatížení, protože knihovna soubor parsuje dvakrát – jednou pro detekci problémů, podruhé pro opravu. U dokumentů o velikosti několika gigabajtů zvažte streamování souboru nebo zvýšení haldy JVM (`-Xmx2g`), aby nedošlo k `OutOfMemoryError`.

## Profesionální tipy – Jak učinit obnovu robustní

* **Zaznamenávejte varování do souboru** – přesměrujte `System.err` do loggeru, abyste měli auditní stopu toho, co bylo opraveno.  
* **Validujte po obnově** – spusťte `doc.updatePageLayout();` a poté znovu zkontrolujte počet stránek; někdy se rozložení změní po opravě poškozených sekcí.  
* **Automatizujte hromadnou obnovu** – obalte demo do smyčky, která zpracuje složku poškozených souborů, přičemž pokaždé použije stejné `LoadOptions`.  

## Závěr

Nyní přesně víte **jak obnovit poškozený soubor Word** pomocí Aspose.Words pro Java. Vytvořením instance `LoadOptions`, nastavením **set recovery mode** na strategii, která vyhovuje vašemu scénáři, a načtením dokumentu s těmito možnostmi můžete bezpečně **otevřít poškozený dokument Word** bez zhroucení aplikace. Ukázkový kód výše je kompletní, připravené řešení, které vytiskne počet stránek a dokonce uloží vyčištěnou kopii.

Co dál? Zkuste přepnout režim obnovy na `RECOVER_WITHOUT_WARNINGS` a porovnat výstup v konzoli, nebo experimentujte s načítáním šifrovaných dokumentů (budete muset zadat heslo přes

## Související tutoriály

- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [How to Compare Two Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}