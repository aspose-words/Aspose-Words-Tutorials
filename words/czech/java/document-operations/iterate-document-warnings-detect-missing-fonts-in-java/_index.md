---
category: general
date: 2026-04-28
description: Iterujte varování dokumentu ve Word souboru, abyste zjistili chybějící
  písma, získali názvy chybějících písem a vytiskli podrobnosti o chybějících písmenech
  pomocí Aspose.Words pro Javu.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: cs
og_description: Procházejte varování dokumentu, abyste našli chybějící písma, získali
  názvy chybějících písem a vytiskli podrobnosti o chybějících písmech pomocí kompletního
  příkladu v Javě.
og_title: 'Iterovat varování dokumentu: Detekovat chybějící fonty v Javě'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Iterovat varování dokumentu: Detekovat chybějící fonty v Javě'
url: /cs/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Procházení varování dokumentu – Detekce chybějících fontů v Javě

Už jste někdy potřebovali **procházet varování dokumentu** při otevírání souboru Word a přemýšleli, které fonty chybí? Nejste v tom sami. Chybějící fonty mohou narušit vzhled zprávy a bez možnosti je odhalit můžete odeslat dokument, který vůbec nepřipomíná originál.  

V tomto tutoriálu vám ukážeme, jak **detekovat chybějící fonty** načtením Word dokumentu, procházením jeho varování, získáním názvů chybějících fontů a nakonec vytištěním informací o chybějících fontech — vše pomocí Aspose.Words pro Java.  

Probereme vše od úplně první řádky kódu až po očekávaný výstup v konzoli, takže můžete okamžitě zkopírovat a vložit funkční řešení do svého projektu. Žádná další dokumentace není potřeba.

## Požadavky

- Nainstalovaný Java 8 nebo novější.
- Knihovna Aspose.Words pro Java (nejnovější verze k 28. 04. 2026).
- Soubor Word, který může obsahovat fonty nenainstalované ve vašem systému (např. `doc-with-missing-font.docx`).

Pokud je již máte, skvělé — jste připraveni **načíst Word dokument** a začít procházet.

## Krok 1 – Načtení Word dokumentu s výchozími možnostmi

Než budeme moci **procházet varování dokumentu**, musí být soubor načten do paměti. Aspose.Words vám to umožní jedním voláním konstruktoru. Použití výchozího `LoadOptions` je obvykle dostačující, ale pro přehlednost ukážeme i explicitní vytvoření.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Proč je to důležité:**  
> Načtení dokumentu spustí v Aspose.Words skenování souboru na jakékoli zdroje, které nelze vyřešit, například fonty, které nejsou nainstalovány lokálně. Tyto problémy jsou uloženy jako **varování**, která v dalším kroku **projdeme varování dokumentu**.

## Krok 2 – Procházení varování dokumentu pro nalezení problémů s fonty

Nyní přichází jádro řešení: procházíme každé varování, které knihovna během načítání shromáždila. Objekt `WarningInfo` nám říká, co se pokazilo, a můžeme filtrovat na `FontSubstitutionWarning`, abychom **detekovali chybějící fonty**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Tip:** Kontrola `instanceof` zajišťuje, že zpracováváme jen varování související s fonty, a ignorujeme ostatní, například problémy s načítáním obrázků. To činí smyčku efektivní a udržuje výstup zaměřený na fonty, pro které skutečně potřebujete **získat informace o chybějících fontech**.

### Očekávaný výstup v konzoli

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Pokud dokument neobsahuje žádné chybějící fonty, smyčka se jednoduše ukončí tiše — nic k **vytištění chybějících fontů**.

## Krok 3 – Proč ne jen zachytit výjimku?

Možná se ptáte: „Proč neobalit volání `new Document(...)` do try‑catch a hledat výjimku?“ Odpověď má dva body:

1. **Detailní informace:** Výjimky vám pouze řeknou, že něco selhalo. Varování vám poskytnou přesný název fontu a náhradní font, který Aspose.Words zvolil.
2. **Nefatální problémy:** Chybějící fonty jsou obvykle nefatální; dokument se stále načte, ale vizuální věrnost je ohrožena. **Procházením varování dokumentu** si zachováte možnost zpracovat zbytek souboru.

## Krok 4 – Rozšíření příkladu: Shromažďování chybějících fontů do seznamu

Někdy potřebujete chybějící fonty pro další zpracování — například je vložit nebo upozornit uživatele přes UI. Zde je rychlá úprava, která shromažďuje názvy do `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Nyní máte čistý způsob, jak **získat informace o chybějících fontech** programově, které můžete předat do modulu reportování nebo průvodce instalací fontů.

## Krok 5 – Praktické úvahy

- **Více náhrad:** Jeden chybějící font může být nahrazen různými fonty v různých částech dokumentu. Seznam varování bude obsahovat každou výskyt, takže můžete vidět duplicitní položky chybějících fontů.
- **Výkon:** Načítání velmi velkých dokumentů může generovat tisíce varování. Pokud vás zajímají jen fonty, filtrujte brzy, jak je ukázáno, aby smyčka byla rychlá.
- **Fonty napříč platformami:** Na Linuxu je výchozí náhradní font často *Liberation Sans*. Na Windows to může být *Arial*. Znalost náhrady vám pomůže rozhodnout, zda musíte s aplikací distribuovat vlastní fonty.

## Krok 6 – Vizuální pomůcka

Níže je snímek obrazovky výstupu v konzoli (alternativní text obsahuje hlavní klíčové slovo pro SEO).

![Procházení varování dokumentu v konzoli zobrazující chybějící fonty a jejich náhrady](/images/iterate-document-warnings.png)

*Alt text:* *příklad procházení varování dokumentu zobrazující názvy chybějících fontů a podrobnosti o náhradách.*

## Závěr

Právě jste se naučili, jak **procházet varování dokumentu** v Aspose.Words pro Java, **detekovat chybějící fonty**, **bezpečně načíst Word dokument**, **získat informace o chybějících fontech** a **vypsat podrobnosti o chybějících fontech** do konzole. Kompletní úryvek kódu funguje tak, jak je, a můžete jej přizpůsobit pro zápis do souboru, zobrazení UI dialogu nebo dokonce automatické vložení chybějících fontů.

Dále byste se mohli chtít podívat na to, jak **načíst Word dokument** s vlastními zdroji fontů (např. přidáním složky s firemními fonty) nebo jak vložit chybějící fonty přímo do souboru, aby byl vzhled zachován napříč počítači. Obě témata navazují přirozeně na to, co jsme zde probírali.

Šťastné programování a ať vaše PDF vždy vypadají přesně tak, jak jste zamýšleli!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}