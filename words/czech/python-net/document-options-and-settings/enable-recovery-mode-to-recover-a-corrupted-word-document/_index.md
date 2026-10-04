---
category: general
date: 2026-10-04
description: Povolte režim obnovy v Aspose.Words, abyste bezpečně obnovili poškozený
  dokument Word. Postupujte podle podrobného návodu s kompletním Python kódem a vysvětleními.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: cs
lastmod: 2026-10-04
og_description: Povolte režim obnovy pro opravu poškozeného dokumentu Word pomocí
  Aspose.Words. Tento tutoriál ukazuje přesný kód v Pythonu, proč funguje, a jak zacházet
  s okrajovými případy.
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: Povolit režim obnovy pro obnovení poškozeného dokumentu Word – kompletní
  průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: Povolit režim obnovy k obnovení poškozeného dokumentu Word
url: /cs/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Povolení režimu obnovy pro obnovení poškozeného dokumentu Word

Pokud potřebujete **povolit režim obnovy** při načítání souboru Word, tento návod vám přesně ukáže, jak to provést pomocí Aspose.Words pro Python. Zapnutím režimu obnovy můžete **obnovit poškozený dokument Word**, který by jinak vyvolal výjimku.

V následujících sekcích se dozvíte:

* Které třídy a vlastnosti řídí chování obnovy.  
* Jak načíst potenciálně poškozený soubor `.docx` bez zhroucení aplikace.  
* Tipy pro řešení běžných problémů s načítáním a přizpůsobení strategie obnovy.

> **Požadavek** – Máte nainstalované Aspose.Words pro Python (`pip install aspose-words`) a základní znalosti práce se soubory v Pythonu.

## Co dělá režim obnovy a proč byste jej měli povolit

Aspose.Words analyzuje vnitřní strukturu souboru Word, než ji vystaví jako objekt `Document`. Když je soubor poškozený — chybějící části, poškozené XML nebo neplatné vztahy — parser může buď:

| Režim | Chování |
|------|------------|
| `STRICT` | Vyvolá výjimku při první známce poškození. |
| `IGNORE_ERRORS` | Přeskočí nečitelné části, ale může tiše ztratit obsah. |
| `RECOVER` (the **enable recovery mode** option) | Pokusí se dokument znovu sestavit, zachovat co nejvíce obsahu a zpřístupní zvolený režim přes `load_options.recovery_mode`. |

`RECOVER` je doporučená volba, když musíte **obnovit poškozené dokumenty Word** pro následné zpracování, například extrakci textu nebo konverzi do PDF.

## Krok 1: Vytvořte LoadOptions a povolte režim obnovy

Prvním krokem je vytvořit instanci `LoadOptions` a nastavit vlastnost `recovery_mode` na `RecoveryMode.RECOVER`. Tím se knihovně řekne, aby během parsování vstoupila do cesty obnovy.

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**Proč je to důležité:**  
Pokud tento krok přeskočíte a dokument je poškozený, konstruktor `aw.Document(...)` vyvolá `InvalidOperationException`. Povolení režimu obnovy zabrání pádu a poskytne vám částečně opravený objekt `Document`, se kterým můžete nadále pracovat.

## Krok 2: Načtěte potenciálně poškozený dokument pomocí zadaných možností

Předávejte instanci `load_options` konstruktoru `Document`. Načítací mechanismus nyní automaticky použije algoritmus obnovy.

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**Tip:** Nahraďte `YOUR_DIRECTORY` absolutní nebo relativní cestou, ke které má vaše runtime přístup. Pokud soubor neexistuje, Aspose.Words vyvolá `FileNotFoundError`, ještě předtím, než se dostane k logice obnovy.

## Krok 3: Ověřte, že byl režim obnovy použit

Aktivní režim můžete potvrdit kontrolou `load_options.recovery_mode`. To je užitečné pro logování nebo podmíněné zpracování později v pipeline.

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**Očekávaný výstup**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

Pokud výstup ukazuje `RECOVER`, úspěšně jste **povolili režim obnovy** a dokument je nyní připraven pro další zpracování (např. extrakci textu, konverzi do PDF nebo uložení opravené kopie).

## Krok 4 (volitelně): Uložte opravenou kopii pro budoucí použití

Po načtení můžete chtít uložit obnovený dokument, abyste nemuseli opakovat krok obnovy.

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Uložení vytvoří nový soubor `.docx`, který Aspose.Words považuje za platný a lze jej otevřít v Microsoft Word bez varování.

## Časté otázky a řešení okrajových případů

| Otázka | Odpověď |
|----------|--------|
| **Co když je dokument zcela nečitelný?** | I v režimu `RECOVER` jsou některé soubory mimo opravu. Objekt `Document` bude vytvořen, ale může obsahovat jen jedinou prázdnou stránku. Zkontrolujte `doc.get_page_count()`, abyste ověřili obsah. |
| **Mohu po načtení přepnout na `IGNORE_ERRORS`?** | Ne. Režim obnovy musí být nastaven **před** spuštěním konstruktoru `Document`. Vytvořte novou instanci `LoadOptions`, pokud potřebujete jinou strategii. |
| **Ovlivňuje režim obnovy výkon?** | Ano, přidává malou režii, protože knihovna se snaží rekonstruovat poškozené části. Dopad je zanedbatelný pro většinu souborů (< 2 MB). |
| **Je tento přístup jazykově nezávislý?** | Stejný koncept existuje v .NET, Java a Node.js API (`LoadOptions.RecoveryMode`). Syntaxe kódu se mění, ale logika je identická. |

## Profesionální tip: Logujte podrobné informace o obnově

Aspose.Words poskytuje `LoadOptions.recovery_callback`, který přijímá podrobné zprávy o každém kroku obnovy. Připojení tohoto callbacku vám může pomoci diagnostikovat, proč konkrétní dokument selhal.

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

Nyní bude každá interní oprava (např. „Removed duplicate relationship“) vytištěna do konzole.

## Kompletní, spustitelný příklad

Spojením všech částí dohromady získáte samostatný skript, který můžete zkopírovat a okamžitě spustit:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

Spuštěním skriptu se vypíše režim obnovy, počet stránek a seznam slov extrahovaných z opraveného dokumentu. Pokud nastavíte `save_repaired=True`, objeví se nový čistý soubor vedle originálu.

## Závěr

Nyní víte, jak **povolit režim obnovy** v Aspose.Words pro Python a spolehlivě **obnovit poškozené dokumenty Word**. Klíčové kroky jsou:

1. Vytvořte `LoadOptions` a nastavte `recovery_mode` na `RECOVER`.  
2. Načtěte soubor `.docx` pomocí těchto možností.  
3. Ověřte režim a případně uložte opravenou kopii.

Odtud můžete zkoumat další témata, jako je **extrakce textu z obnoveného dokumentu**, **konverze do PDF**, nebo **automatizace hromadné obnovy** pro velké knihovny dokumentů.

---

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Recover Corrupted DOCX – Complete Guide to Enable Recovery Mode & Get Page](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}