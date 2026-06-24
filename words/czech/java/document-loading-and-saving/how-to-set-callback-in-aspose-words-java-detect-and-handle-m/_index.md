---
category: general
date: 2026-06-20
description: Jak nastavit zpětné volání v Aspose.Words Java pro detekci chybějících
  fontů a přizpůsobení načítání dokumentu. Naučte se krok za krokem, jak zacházet
  s varováními o náhradě fontů.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: cs
og_description: Jak nastavit zpětné volání v Aspose.Words Java pro detekci chybějících
  fontů, zpracování substitucí a přizpůsobení načítání dokumentu. Kompletní průvodce
  s kódem.
og_title: jak nastavit zpětné volání – Detekce chybějících fontů v Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Jak nastavit zpětné volání v Aspose.Words Java – Detekce a řešení chybějících
  fontů
url: /cs/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak nastavit callback v Aspose.Words Java – Detekce a zpracování chybějících fontů

Už jste se někdy zamysleli **jak nastavit callback** v Aspose.Words Java, abyste mohli odhalit chybějící fonty dříve, než zničí váš PDF nebo DOCX? Nejste jediní. Varování o chybějících fontech mohou tiše narušit rozvržení a bez správného callbacku pro varování si toho možná vůbec neuvědomíte, dokud finální dokument nevypadá špatně.  

V tomto tutoriálu projdeme kompletním, připraveným k spuštění příkladem, který **detekuje chybějící fonty**, **elegantně zpracovává chybějící fonty** a ukazuje, jak **přizpůsobit načítání dokumentu** pomocí callbacku pro varování. Na konci budete mít samostatnou třídu Java, kterou můžete vložit do libovolného projektu — žádné další hledání v dokumentaci není potřeba.

## Co budete potřebovat

- Java 8 nebo novější (kód funguje také s Java 11+)  
- Knihovna Aspose.Words pro Java (verze 23.9 nebo novější)  
- Soubor DOCX, který odkazuje na font, který nemáte nainstalovaný (např. vlastní firemní font)  

Pokud jste ještě nepřidali Aspose.Words do svého Maven projektu, stačí zahrnout:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

A to je vše — žádné extra pluginy, žádné nativní závislosti.

---

## Krok 1: Pochopit mechanismus WarningCallback

**warning callback** je způsob, jakým Aspose.Words na vás „křičí“, když se během načítání nebo ukládání dokumentu objeví něco neočekávaného. Implementací `IWarningCallback` získáte plnou kontrolu nad tím, co se zaznamená, co se ignoruje nebo co se dokonce promění na výjimku.

> **Why this matters:**  
> Když chybí font, Aspose nahradí fontem záložním. Výsledek může být dramaticky odlišný, zejména u PDF s silnou značkovou identitou. Zachycením `WarningType.FONT_SUBSTITUTION` můžete zaznamenat přesný název fontu, rozhodnout, zda proces ukončit, nebo programově nahradit vlastní font.

---

## Krok 2: Vytvořit instanci LoadOptions

`LoadOptions` je vstupní bod pro přizpůsobení načítání dokumentu. Callback připojíte k tomuto objektu ještě před samotným načtením souboru.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

V tomto okamžiku je `loadOptions` jen obyčejný kontejner — zatím se nic neděje. Skutečná magie začne, až do něj zapojíme callback.

---

## Krok 3: Implementovat a připojit callback

Níže je kompaktní anonymní třída, která implementuje `IWarningCallback`. Vypisuje přátelskou zprávu do konzole vždy, když dojde k náhradě fontu.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Pro tip:** Pokud chcete **zpracovat chybějící fonty** tím, že poskytnete náhradu, můžete také nastavit `FontSettings` na `LoadOptions` a mapovat chybějící fonty na známý záložní font.

---

## Krok 4: Načíst dokument s vlastními možnostmi

Nyní, když je callback připojen, načtěte dokument. Pokud soubor odkazuje na font, který nemáte, uvidíte vytištěné varování.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Po spuštění programu se v konzoli může objevit:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Tento řádek dokazuje, že jste úspěšně **detekovali chybějící fonty** a nyní můžete **zpracovat chybějící fonty** podle libosti.

---

## Krok 5: Volitelné – Nahradit chybějící fonty známým fontem

Pokud chcete automaticky nahradit jakýkoli chybějící font, například `Times New Roman`, můžete přidat objekt `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Nyní se dokument načte a jakýkoli odkaz na `MyCustomFont` je tiše nahrazen za `Times New Roman`. Konzole vám i nadále sdělí, co bylo nahrazeno, takže budete v obraze.

---

## Kompletní funkční příklad

Níže je jediná třída Java, která zahrnuje všechny výše uvedené kroky. Zkopírujte ji do svého IDE, upravte `docPath` a spusťte.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Očekávaný výstup**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Nyní máte reprodukovatelný způsob, jak **detekovat chybějící fonty**, **zpracovat chybějící fonty** a **přizpůsobit načítání dokumentu** — vše tím, že se naučíte **jak nastavit callback** správně.

---

## Často kladené otázky

### Co když chci, aby program přestal načítat, když chybí font?

Vyhoďte výjimku uvnitř metody `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Blok `catch` na konci ji zachytí a můžete si rozhodnout, jak ji zaznamenat nebo upozornit uživatele.

### Funguje to i pro PDF generované z DOCX?

Rozhodně. Callback se spustí během **loading** fáze, která je stejná pro všechny výstupní formáty (`save` do PDF, DOCX, HTML atd.). Dokud načítáte zdrojový dokument se stejnými `LoadOptions`, zachytíte chybějící fonty dříve, než ovlivní finální PDF.

### Mohu zachytit i jiné typy varování (např. konverze obrázku)?

Ano — `WarningInfo.getWarningType()` lze porovnat s jinými enumy, jako je `WarningType.IMAGE_CONVERSION`. Stačí přidat další `if` větve do callbacku.

### Má to dopad na výkon?

Nevýznamný. Callback běží synchronně během načítání a dodatečné kontroly jsou lehké. Pokud načítáte tisíce dokumentů, můžete varování v produkci vypnout nastavením `loadOptions.setWarningCallback(null);`.

---

## Vizuální přehled

![příklad nastavení callbacku v Aspose.Words Java](https://example.com/images/callback-diagram.png "nastavení callbacku")

*Diagram ilustruje tok: `LoadOptions` → `IWarningCallback` → Načítání dokumentu → Zpracování náhrady fontu.*

---

## Závěr

Probrali jsme **jak nastavit callback** v Aspose.Words Java, demonstrovali **detekci chybějících fontů**, ukázali praktické způsoby **zpracování chybějících fontů** a vysvětlili, jak **přizpůsobit načítání dokumentu** pomocí `LoadOptions`.  

S těmito znalostmi můžete nyní chránit své dokumentové pipeline před tichými výměnami fontů, udržet značku neporušenou a poskytnout uživatelům jasnou zpětnou vazbu, když se něco pokazí.

### Co dál?

- Prozkoumejte **font substitution tables** pro hromadné mapování mnoha chybějících fontů.  
- Kombinujte tento callback s **document validation** pro vynucení stylových směrnic.  
- Vyzkoušejte **custom warning callbacks**, které zapisují do souboru logu nebo monitorovacího systému místo `System.out`.  

Klidně experimentujte a dejte nám vědět, jak jste si přizpůsobili callback pro své vlastní projekty. Šťastné kódování!

---

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětlením, aby vám pomohl ovládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [Jak nastavit LoadOptions v Aspose.Words pro Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Jak detekovat fonty v Aspose.Words – Zpracovat varování a nastavení](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Jak zachytit fonty v Aspose.Words – Kompletní průvodce](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}