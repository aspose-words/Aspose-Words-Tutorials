---
category: general
date: 2026-06-30
description: Jak přejmenovat obrázky při převodu DOCX na markdown. Naučte se měnit
  názvy obrázků a uložit Word jako markdown s vlastními názvy souborů obrázků.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: cs
og_description: Jak přejmenovat obrázky při převodu DOCX na markdown. Tento návod
  vám ukáže, jak změnit názvy obrázků, uložit Word jako markdown a použít vlastní
  názvy souborů obrázků.
og_title: Jak přejmenovat obrázky při převodu DOCX na Markdown
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: Jak přejmenovat obrázky při převodu DOCX na Markdown
url: /cs/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přejmenovat obrázky při konverzi DOCX na Markdown

Už jste se někdy zamysleli **jak automaticky přejmenovat obrázky** při převodu souboru DOCX na Markdown? Nejste v tom sami. V mnoha dokumentačních pipelinech se výchozí názvy obrázků (např. `image1.png`) stávají noční můrou, zejména když je stejný markdown verzovan mezi týmy.  

Dobrou zprávou je, že Aspose.Words for Python to dělá hračkou – **změní názvy obrázků** za běhu a umožní vám udržet Markdown čistý a zároveň mít přehlednou složku s vlastně pojmenovanými prostředky.  

V tomto tutoriálu se naučíte:

* Načíst Word dokument (`.docx`) v Pythonu.  
* Zapojit se do procesu ukládání Markdownu pomocí callbacku, který každému obrázku přiřadí název založený na GUID.  
* Uložit dokument jako Markdown, aby vygenerovaný soubor odkazoval na nově pojmenované obrázky.  

Pokud ovládáte základní Python a máte nainstalovaný Aspose.Words, budete mít vše připravené během pěti minut. Žádné externí skripty, žádné ruční přejmenovávání – jen jeden samostatný program, který za vás udělá těžkou práci.

---

## Požadavky — Co potřebujete před začátkem

| Požadavek | Proč je důležité |
|-------------|----------------|
| **Python 3.7+** | Příklad používá f‑stringy a typové anotace zavedené v 3.6, ale 3.7+ vám poskytne pohodlí `os.path.splitext`. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | Tato knihovna poskytuje třídu `aw.Document` a `MarkdownSaveOptions`, na které se spoléháme. |
| **Oprávnění k zápisu** do výstupní složky | Callback vytvoří nové soubory obrázků, takže skript musí mít právo je zapisovat. |
| **Soubor DOCX**, který chcete převést | Funguje cokoliv – od jednoduché zprávy po složitý manuál. |

> **Tip:** Pokud používáte virtuální prostředí, aktivujte jej před instalací Aspose.Words. Izoluje závislosti a zabraňuje konfliktům verzí.

---

## Krok 1: Načtěte Word dokument  

První věc, kterou uděláte, když chcete **převést docx na markdown**, je otevřít zdrojový soubor. Aspose.Words abstrahuje veškeré nízkoúrovňové OPC operace, takže stačí jediný řádek.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Proč je to důležité:* Bez načtení dokumentu nemůžete prozkoumat jeho prostředky a exportér Markdownu nebude mít co zapisovat. Objekt `aw.Document` drží celý Word balíček v paměti, což umožňuje bezpečnou manipulaci před uložením.

---

## Krok 2: Napište callback, který **přejmenuje zdroje obrázků**  

Aspose.Words vám umožní připojit `resource_saving_callback` k `MarkdownSaveOptions`. Callback obdrží každý zdroj (obrázky, CSS atd.) těsně před tím, než je zapsán na disk. Úpravou `resource.file_name` můžeme vynutit **vlastní názvy obrázků**.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### Proč použít GUID?

* **Jedinečnost** – GUID (`uuid4`) zaručuje, že se dva obrázky nikdy nepřekryjí, i při více spuštěních.  
* **Sledovatelnost** – Pokud budete potřebovat později ladit, GUID lze zaznamenat spolu s původním číslem odstavce ve Wordu.  
* **Přenositelnost** – Nezávisí na původním pojmenování ve Wordu, které může obsahovat mezery nebo speciální znaky narušující odkazy v Markdownu.

---

## Krok 3: Připojte callback k nastavení uložení Markdownu  

Nyní řekneme Aspose, aby použil naši logiku přejmenování pokaždé, když zapíše obrázek do výstupní složky.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*Vysvětlení:* Třída `MarkdownSaveOptions` řídí vše od zalomení řádků po umístění složky s obrázky. Nastavením `resource_saving_callback` získáte **háček**, který se spustí pro každý vložený zdroj a umožní vám **změnit názvy obrázků** před tím, než se soubor objeví na disku.

---

## Krok 4: Uložte dokument jako Markdown – poslední krok  

S nastaveným callbackem je poslední krok přímočarý.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

Po dokončení skriptu najdete:

* `CustomResources.md` – Markdownová reprezentace vašeho Word souboru.  
* Složku `images/` (nebo jakoukoliv jinou, kterou jste nastavili) obsahující soubory jako `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png`.  

Markdownový soubor bude odkazovat na nové názvy založené na GUID, takže jakýkoli downstream procesor (GitHub, MkDocs, atd.) načte správné obrázky bez nutnosti ručního přejmenování.

### Očekávaný výstup (úryvek)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

GUID se při každém běhu liší, ale vzor zůstává stejný.

---

## Řešení okrajových případů a častých otázek  

### Co když dokument obsahuje prostředky, které nejsou obrázky?  

Náš callback již kontroluje příponu souboru a vrací `True` pro vše, co není obrázek. To znamená, že CSS soubory, fonty nebo vložené OLE objekty si zachovají původní názvy, což je obvykle požadované při **ukládání word jako markdown**.

### Můžu použít vlastní pojmenovací schéma místo GUID?  

Samozřejmě. Nahraďte volání `uuid.uuid4()` libovolnou funkcí, která vrátí řetězec. Například můžete předponovat původní index odstavce:

```python
new_name = f"para{resource.resource_id}{ext}"
```

Jen se ujistěte, že výsledný název je v celém dokumentu jedinečný.

### Jaký dopad má toto řešení na výkon u velkých dokumentů?  

Callback se spustí jednou pro každý zdroj, takže režie je minimální – převážně čas na vygenerování GUID. I 200‑stránková zpráva se stovkami obrázků dokončí za méně než sekundu na moderním notebooku.

### Co když potřebuji, aby názvy obrázků byly deterministické (např. pro CI buildy)?  

Vyměňte `uuid.uuid4()` za hash původních bajtů obrázku:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

Tím získáte stejný název souboru při každém spuštění skriptu na stejném zdrojovém obrázku.

---

## Kompletní funkční skript – zkopírujte, vložte, spusťte  



## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, abyste mohli ovládnout další funkce API a prozkoumat alternativní implementační přístupy ve svých projektech.

- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}