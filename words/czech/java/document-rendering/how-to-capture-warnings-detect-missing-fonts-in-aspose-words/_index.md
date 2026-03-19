---
category: general
date: 2026-03-19
description: Naučte se zachytávat varování v Aspose.Words pro Javu a detekovat chybějící
  písma. Tento průvodce krok za krokem také ukazuje, jak s chybějícími písmy zacházet
  elegantně.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: cs
og_description: Jak zachytit varování v Aspose.Words pro Javu, detekovat chybějící
  písma a zpracovat chybějící písma s kompletním příkladem kódu.
og_title: Jak zachytit varování – detekovat chybějící písma v Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Jak zachytit varování – detekovat chybějící písma v Aspose.Words
url: /cs/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak zachytit varování – Detekce chybějících fontů v Aspose.Words

Už jste se někdy zamysleli **jak zachytit varování**, když se načítá dokument Word a některé fonty nejsou na počítači k dispozici? Nejste v tom sami. V mnoha reálných projektech způsobují chybějící fonty tiché posuny rozvržení a jediný způsob, jak zjistit, co se stalo, je poslouchat stream varování, který Aspose.Words vydává.  

V tomto tutoriálu projdeme kompletním, připraveným příkladem, který **detekuje chybějící fonty**, ukáže vám **jak programově detekovat chybějící fonty** a dokonce poskytne rychlou radu o **zpracování chybějících fontů**, aby váš výstup zůstal předvídatelný.

> **Rychlá poznámka:** Kód funguje s Aspose.Words 23.9 (nebo novějším) a vyžaduje Java 8+.

---

## Co budete potřebovat

- **Aspose.Words for Java** (Maven/Gradle závislost nebo JAR na classpath)  
- Word soubor (`input.docx`), který odkazuje na font, který není nainstalován ve vašem systému (např. „Comic Sans MS“)  
- Java IDE nebo jednoduché nastavení příkazové řádky `javac`/`java`  

Žádné další knihovny nejsou vyžadovány—vše ostatní je součástí balíčku Aspose.Words.

## Krok 1 – Nastavení LoadOptions pro zachycení varování  

Chcete‑li začít poslouchat varování, musíte vytvořit instanci `LoadOptions`. Tento objekt říká načítači, aby sledoval všechny problémy, na které narazí, například chybějící fonty.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Proč je to důležité:** Bez `LoadOptions` načítač tiše nahrazuje chybějící fonty výchozím systémovým fontem a nikdy byste se nedozvěděli, že k nahrazení došlo. Povolení varování vám poskytne úplnou přehlednost.

## Krok 2 – Načtení dokumentu pomocí LoadOptions  

Nyní skutečně načteme dokument. `LoadOptions`, které jsme právě vytvořili, jsou předány konstruktoru, takže všechna varování vzniklá během parsování jsou zachycena.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Tip:** Pokud zpracováváte mnoho souborů najednou, znovu použijte stejnou instanci `LoadOptions`, abyste se vyhnuli zbytečnému vytváření objektů.

## Krok 3 – Procházení zachycených varování  

Aspose.Words ukládá každé varování jako objekt `WarningInfo`. Zajímáme se jen o varování související s fonty, takže filtrujeme podle `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Vysvětlení:**  
- `document.getWarnings()` vrací seznam všech varování, která nastala během načítání.  
- `FontSubstitutionWarningInfo` obsahuje dva klíčové údaje: **požadovaný font** (ten, který DOCX požaduje) a **skutečný font**, na který Aspose.Words přepnul.  
- Vytištěním obou okamžitě uvidíte, které fonty chybí a jaká náhrada proběhla.

## Krok 4 – (Volitelné) Programové zpracování chybějících fontů  

Zachycení varování je jen polovina příběhu. Jakmile zjistíte, že font chybí, můžete **zpracovat chybějící fonty** poskytnutím vlastní náhrady nebo zaznamenáním problému pro pozdější revizi.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Proč to dělat?**  
- Zajišťuje konzistentní vykreslování napříč počítači.  
- Zabraňuje neočekávaným změnám rozvržení v PDF nebo obrázcích generovaných později.  

Můžete také uložit podrobnosti varování do databáze, poslat e‑mail obsahovému týmu nebo dokonce proces přerušit, pokud chybí kritický font.

## Kompletní funkční příklad  

Níže je kompletní spustitelný program. Stačí nahradit `YOUR_DIRECTORY/input.docx` cestou k vašemu testovacímu souboru, přidat Aspose.Words JAR do classpath a spustit.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Očekávaný výstup** (když chybí „Comic Sans MS“):

```
Requested: Comic Sans MS → Substituted: Arial
```

Po spuštění volitelného kódu pro náhradu bude uložený `output.docx` vykreslován pomocí **Arial**, kdekoliv bylo původně odkazováno na „Comic Sans MS“.

## Časté otázky a okrajové případy  

| Question | Answer |
|----------|--------|
| *Co když dokument obsahuje více chybějících fontů?* | Smyčka vygeneruje varování pro každý z nich. Můžete je shromáždit do `Map<String, String>` pro hromadné zpracování. |
| *Funguje to pro PDF generovaná z dokumentu?* | Rozhodně. Náhrada fontů probíhá během fáze načítání, takže jakýkoli pozdější export (PDF, HTML, obrázek) používá vyřešené fonty. |
| *Mohu varování potlačit místo jejich zachycení?* | Ano—nastavte `loadOptions.setWarningCallback(null);`, ale ztratíte přehled o chybějících fontech. |
| *Je seznam varování po uložení vymazán?* | Sbírka varování patří k instanci `Document`. Po zavolání `document.save()` zůstane seznam nezměněn, pokud nevytvoříte nový `Document`. |
| *Co s vlastními fonty vloženými v DOCX?* | Vložené fonty jsou považovány za dostupné; Aspose.Words je použije i když nejsou nainstalovány v hostitelském systému. |

## Profesionální tipy pro produkční použití  

- **Cache FontSettings:** Pokud zpracováváte stovky souborů, vytvořte jediný `FontSettings` s preferovanými náhradami a znovu jej použijte, abyste se vyhnuli režii.  
- **Log Structured Data:** Místo prostého `System.out` zapisujte varování do JSON logu—tím se zjednoduší následná analytika (např. „nejčastěji chybějící fonty“).  
- **Validate Early:** Proveďte rychlé „dry‑load“ s `LoadOptions` před náročným zpracováním; včas přerušte, pokud chybí kritické fonty.  
- **Thread Safety:** Objekt `Document` není thread‑safe. Zpracovávejte každý soubor ve vlastním vlákně nebo použijte thread‑local `LoadOptions`.  

## Závěr  

Nyní víte **jak zachytit varování** v Aspose.Words pro Java, **detekovat chybějící fonty** a **zpracovat chybějící fonty** pomocí čisté strategie náhrady. Využitím `LoadOptions` a procházením `document.getWarnings()` získáte úplný přehled o událostech náhrady fontů, což zajišťuje, že vaše generované dokumenty vypadají přesně podle očekávání ve všech prostředích.

Jste připraveni na další krok? Zkuste rozšířit tento vzor na **detekci chybějících obrázků**, **sledování nepodporovaných funkcí** nebo dokonce **automatické vložení chybějících fontů** do výstupního souboru. Stejný přístup k zachycení varování funguje pro mnoho dalších scénářů zpracování dokumentů, což činí váš kód robustním a připraveným na budoucnost.

Šťastné programování a ať se vaše dokumenty vždy krásně vykreslují!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}