---
category: general
date: 2026-09-30
description: Povolte režim obnovy pro otevření poškozeného dokumentu Word pomocí Aspose.Words.
  Naučte se, jak bezpečně a spolehlivě obnovit poškozené soubory docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- open corrupted word document
- recover corrupted docx
- how to open corrupted docx
- load document with recovery
language: cs
lastmod: 2026-09-30
og_description: Povolte režim obnovy pro otevření poškozeného dokumentu Word pomocí
  Aspose.Words. Tento průvodce ukazuje krok za krokem, jak obnovit poškozené soubory
  docx a udržet stabilní pracovní postup.
og_image_alt: Code snippet showing Aspose.Words recovery mode enabled for a corrupted
  DOCX
og_title: Povolit režim obnovy pro otevření poškozených dokumentů Word
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Enable recovery mode to open a corrupted Word document using Aspose.Words.
    Learn how to recover corrupted docx files safely and reliably.
  headline: Enable recovery mode to open a corrupted Word document
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
title: Povolit režim obnovení pro otevření poškozeného dokumentu Word
url: /cs/python/document-options-and-settings/enable-recovery-mode-to-open-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Povolit režim obnovy pro otevření poškozeného dokumentu Word

Pokud potřebujete **povolit režim obnovy** při otevírání poškozeného dokumentu Word, tento tutoriál vám přesně ukáže, jak to provést pomocí Aspose.Words pro Python. Ať už byl soubor poškozen během přenosu nebo upraven nekompatibilním programem, povolení režimu obnovy umožní knihovně pokusit se dokument opravit místo vyhození výjimky.

V tomto průvodci se naučíte, jak **otevřít poškozené soubory Word**, **obnovit poškozený obsah docx** a pochopit možnosti, které řídí proces **načtení dokumentu s obnovou**. Kroky fungují s Aspose.Words 23.10 (nejnovější vydání v době psaní) a vyžadují pouze standardní prostředí Python.

## Požadavky

* Nainstalovaný Python 3.9 nebo novější.
* Nainstalovaný Aspose.Words pro Python přes .NET (`aspose-words`) (`pip install aspose-words`).
* Soubor DOCX, o kterém je známo, že je poškozený (pro testování můžete přejmenovat platný `.docx` na `.zip` a ručně poškodit XML).

> **Tip:** Uchovejte zálohu originálního souboru. Režim obnovy upravuje dokument v paměti, ale nikdy neukládá zpět do zdroje, pokud jej výslovně neuložíte.

## Krok 1: Naimportujte knihovnu a vytvořte možnosti načtení

Prvním krokem, který musíte provést, je importovat `aspose.words` a vytvořit objekt `LoadOptions`. Tento objekt obsahuje všechna nastavení, která ovlivňují, jak je soubor čten.

```python
import aspose.words as aw

# Create load options – this is where we will enable recovery mode
load_options = aw.loading.LoadOptions()
```

*Proč je to důležité:* `LoadOptions` je vstupní bránou pro jemné ladění parseru. Bez něj Aspose.Words používá výchozí přísný režim, který při jakékoli strukturální chybě ukončí zpracování.

## Krok 2: Povolit režim obnovy

Nastavte vlastnost `recovery_mode` na `RecoveryMode.RECOVER`. Tím řeknete načítači, aby se pokusil o automatickou opravu poškozených částí, jako jsou chybějící XML uzly, poškozené vztahy nebo zkrácené proudy.

```python
# Enable recovery mode – the core of “enable recovery mode” for this tutorial
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

Povolení režimu obnovy **ne**zaručuje dokonalý dokument, ale výrazně zvyšuje šanci, že stále můžete extrahovat text, obrázky nebo tabulky.

## Krok 3: Načíst potenciálně poškozený DOCX s nakonfigurovanými možnostmi

Nyní použijte konstruktor `Document`, který přijímá jak cestu k souboru, tak instanci `LoadOptions`.

```python
# Path to the corrupted file – replace with your actual location
corrupted_path = "YOUR_DIRECTORY/corrupted.docx"

try:
    # Load the document using the recovery‑enabled options
    document = aw.Document(corrupted_path, load_options)
    print("Document loaded successfully with recovery mode.")
except aw.core.exceptions.InvalidOperationException as ex:
    # If recovery fails, the library throws an exception
    print(f"Failed to load document even with recovery mode: {ex}")
```

*Proč je to důležité:* Blok `try/except` ukazuje **jak bezpečně otevřít poškozený docx**. Bez režimu obnovy by stejný volání okamžitě vyvolalo výjimku a zastavilo váš program.

## Krok 4: Ověřit obnovený obsah (volitelné, ale doporučené)

Po načtení byste měli zkontrolovat, zda dokument obsahuje smysluplný obsah. Rychlý způsob je extrahovat prostý text a vypsat prvních několik znaků.

```python
# Extract plain text to verify recovery
text = document.get_text()
if text.strip():
    print("Recovered text preview (first 200 chars):")
    print(text[:200])
else:
    print("Document appears empty after recovery – further inspection may be needed.")
```

Pokud výstup ukazuje rozumný náhled, můžete pokračovat ve zpracování dokumentu (např. převést na PDF, extrahovat tabulky atd.). Pokud je text prázdný, soubor může být neodstranitelně poškozený a budete muset požádat o čerstvou kopii.

## Krok 5: Uložit opravený dokument (pokud chcete čistou kopii)

Když jste spokojeni s obnoveným obsahem, můžete uložit nový, čistý DOCX. Tento krok je volitelný, ale často užitečný pro následné pracovní postupy.

```python
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Uložení vytvoří nový soubor, který již neobsahuje poškození, které spustilo režim obnovy.

## Okrajové případy a další tipy

| Situace | Doporučený přístup |
|----------------------------------------|----------------------|
| **Soubor není DOCX** (např. `.doc`) | Použijte `aw.loading.LoadOptions.file_format = aw.LoadFormat.DOC` před načtením. |
| **Částečná obnova pouze** | Po načtení zkontrolujte `document.get_text()` a `document.get_page_count()`. Pokud je počet stránek 0, dokument může být neobnovitelný. |
| **Velké dokumenty** | Povolte `load_options.memory_optimization = aw.loading.MemoryOptimizationMode.OPTIMIZE` pro snížení využití RAM během obnovy. |
| **Potřeba zaznamenat, co bylo opraveno** | Nastavte `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER` a poté přečtěte `document.get_last_save_options().recovery_log` (pokud je k dispozici) pro podrobnosti. |

> **Pozor:** Režim obnovy může tiše odstranit nepodporované prvky (např. chybějící písma). Pokud je vizuální věrnost kritická, porovnejte opravený soubor s verzi, o které víte, že je v pořádku.

## Kompletní funkční příklad

Spojením všeho dohromady je zde samostatný skript, který můžete spustit okamžitě:

```python
import aspose.words as aw

def open_corrupted_docx(path: str, output_path: str = None):
    """Load a corrupted DOCX with recovery mode and optionally save a repaired copy."""
    # 1. Configure load options
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # 2. Attempt to load the document
    try:
        doc = aw.Document(path, load_options)
        print("✅ Document loaded with recovery mode.")
    except aw.core.exceptions.InvalidOperationException as err:
        print(f"❌ Unable to recover document: {err}")
        return None

    # 3. Verify recovered content
    txt = doc.get_text()
    if txt.strip():
        print("📄 Text preview (first 200 chars):")
        print(txt[:200])
    else:
        print("⚠️ Document appears empty after recovery.")

    # 4. Save a clean copy if requested
    if output_path:
        doc.save(output_path)
        print(f"💾 Repaired file saved to {output_path}")

    return doc

if __name__ == "__main__":
    corrupted_file = "YOUR_DIRECTORY/corrupted.docx"
    repaired_file = "YOUR_DIRECTORY/repaired.docx"
    open_corrupted_docx(corrupted_file, repaired_file)
```

Spuštění skriptu vypíše zprávu o úspěchu, krátký úryvek textu a vytvoří `repaired.docx` ve stejné složce.

## Závěr

Nyní víte, jak **povolit režim obnovy** pro **otevření poškozených souborů Word**, **obnovit poškozený obsah docx** a bezpečně **načíst dokument s obnovou** pomocí Aspose.Words pro Python. Hlavní kroky — vytvoření `LoadOptions`, zapnutí `RecoveryMode.RECOVER` a zpracování výjimek — tvoří spolehlivý vzor, který můžete znovu použít v jakémkoli automatizačním pipeline.

Dále zvažte prozkoumání souvisejících témat, jako je **převod obnoveného dokumentu na PDF**, **extrakce tabulek pomocí `DocumentVisitor`** nebo **dávkové zpracování složky poškozených souborů**. Všechny tyto stavby vycházejí ze stejného základu režimu obnovy, který byl zde předveden.

Šťastné kódování a ať vaše dokumenty zůstávají zdravé!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [jak obnovit docx – nastavit režim obnovy a otevřít poškozené soubory Word](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [obnovit poškozený docx pomocí Aspose.Words – nastavit režim obnovy a možnosti načtení](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Obnovit poškozený DOCX pomocí Aspose.Words LoadOptions – Kompletní průvodce pro C#](/words/english/net/programming-with-loadoptions/recover-corrupted-docx-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}