---
category: general
date: 2026-08-17
description: Jak uložit PNG pomocí Aspose.Words pro Python. Naučte se přidat stín
  k tvaru, uložit dokument jako PDF a exportovat Word do PNG v jednom průvodci.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: cs
lastmod: 2026-08-17
og_description: Jak uložit PNG pomocí Aspose.Words. Tento tutoriál ukazuje přidání
  stínu k tvaru, uložení dokumentu jako PDF a export Wordu do PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Jak uložit PNG a přidat stín k tvaru pomocí Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Jak uložit PNG a přidat stín k tvaru pomocí Aspose.Words
url: /cs/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak uložit PNG a přidat stín k tvaru pomocí Aspose.Words

Pokud potřebujete **jak uložit PNG** ze souboru Word, tento průvodce vám poskytne kompletní, spustitelné řešení. Také uvidíte, jak **přidat stín k tvaru**, **uložit dokument jako PDF** a **exportovat Word do PNG** aniž byste opustili prostředí Aspose.Words.

Tutoriál pokrývá vše potřebné k převodu prázdného dokumentu Word na PDF a PNG obrázek, přičemž na obdélníkový tvar aplikuje jednoduchý efekt stínu. Žádné externí nástroje nejsou vyžadovány a kód funguje s Aspose.Words for Python via .NET 7 nebo novějším.

## Co dosáhnete

Na konci tohoto článku budete schopni:

* Programově vytvořit nový dokument Word.  
* Vložit obdélníkový tvar a nastavit efekt stínu.  
* Uložit stejný dokument jako PDF soubor.  
* Exportovat dokument jako PNG obrázek.  

Tyto kroky odpovídají častému dotazu **jak uložit PNG** a zároveň řeší **přidat stín k tvaru** a **uložit dokument jako PDF** v jednom pracovním postupu.

## Požadavky

* Python 3.9 nebo novější.  
* Aspose.Words for Python via .NET nainstalovaný (`pip install aspose-words`).  
* Oprávnění k zápisu do výstupního adresáře, který specifikujete.  

Pokud jste ještě neinstalovali Aspose.Words, spusťte:

```bash
pip install aspose-words
```

## Jak uložit PNG s Aspose.Words

Prvním hlavním krokem je vytvořit dokument a `DocumentBuilder`. Builder vám poskytuje plynulé API pro vkládání obsahu, jako jsou tvary, tabulky nebo text.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` představuje celý soubor Word v paměti. `aw.DocumentBuilder` ukazuje na aktuální místo vkládání, které je zpočátku na začátku první (a jediné) sekce.

## Přidat stín k tvaru před exportem

Tvar může být jakýkoli kreslicí objekt – obdélník, elipsa nebo vlastní polygon. Zde vytvoříme obdélník o rozměrech 100 × 100 point a použijeme měkký stín.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Proč nastavit stín před uložením? Aspose.Words vykresluje stín během fází exportu do PDF a PNG, takže vizuální efekt je zachován v obou výstupních formátech.

### Pro tip
Pokud potřebujete ostřejší stín, snižte `blur`. Pro výraznější posun zvýšte `distance`. Třída `Shadow` také umožňuje nastavit `angle` a `transparency` pro jemné doladění.

## Uložit dokument jako PDF

Uložení dokumentu Word jako PDF je jednorázový příkaz, jakmile je obsah připraven. Konstantní `SaveFormat.PDF` říká Aspose.Words, aby provedl konverzi.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

Výsledné PDF obsahuje obdélník s přesně definovaným stínem. Aspose.Words pracuje s vektorovou grafikou, takže velikost PDF zůstává skromná.

## Exportovat Word do PNG

Export do PNG vytvoří rastrový obrázek každé stránky. Ve výchozím nastavení používá Aspose.Words 96 DPI; tuto hodnotu můžete zvýšit pro výstup s vyšším rozlišením pomocí objektu `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Když **exportujete Word do PNG**, každá stránka se uloží jako samostatný PNG soubor. Protože náš ukázkový dokument má jen jednu stránku, objeví se jen jeden PNG soubor.

### Volitelné: PNG s vyšším rozlišením

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Vyšší DPI je užitečné, když bude PNG použito v tisku nebo když potřebujete ostrý náhled.

## Kompletní skript – zkopírujte, vložte a spusťte

Níže je kompletní, samostatný skript, který implementuje každý krok popsaný výše. Uložte jej jako `generate_assets.py` a spusťte z příkazové řádky.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Očekávaný výstup

Spuštěním skriptu vzniknou tři soubory:

* `output/output.pdf` – PDF s obdélníkem, který vrhá černý stín.  
* `output/output.png` – PNG s rozlišením 96 DPI zobrazující stejnou stránku.  
* `output/high_res_output.png` – PNG s rozlišením 300 DPI pro vyšší kvalitu.

Otevřete kterýkoli ze souborů ve svém oblíbeném prohlížeči a ověřte, že se stín zobrazuje přesně tak, jak byl definován.

## Časté otázky a okrajové případy

**Co když výstupní adresář neexistuje?**  
Skript volá `os.makedirs(output_dir, exist_ok=True)`, který složku vytvoří automaticky. Tím se zabrání `FileNotFoundError` během operací ukládání.

**Mohu přidat více tvarů s různými stíny?**  
Ano. Vytvořte další objekty `Shape`, nezávisle nastavte každou vlastnost `shadow` a vložte je pomocí `builder.insert_node(shape)` před uložením.

**Zůstane stín zachován při konverzi do jiných rastrových formátů (např. JPEG)?**  
Aspose.Words vykresluje stín pro všechny rastrové formáty podporované `SaveFormat`. Můžete nahradit `aw.SaveFormat.PNG` za `aw.SaveFormat.JPEG` a stín se stále zobrazí.

**Jak se to liší od „convert word to pdf“?**  
`convert word to pdf` je v podstatě stejná operace provedená v kroku 4. Stejné volání `doc.save` s `SaveFormat.PDF` provádí konverzi interně, zachovává rozvržení, písma i grafiku, jako jsou stíny.

**Existuje limit na velikost tvaru?**  
Tvary jsou měřeny v bodech (1 pt ≈ 1/72 palce). Velmi velké rozměry mohou zvýšit výslednou velikost souboru, ale Aspose.Words neklade žádný pevný limit. Přizpůsobte argumenty `width` a `height` při konstrukci `aw.Shape` podle svého rozvržení.

## Závěr

Nyní víte **jak uložit PNG** z dokumentu Word a zároveň jste se naučili **přidat stín k tvaru**, **uložit dokument jako PDF** a **exportovat Word do PNG** pomocí Aspose.Words for Python. Kompletní skript ukazuje čistý, opakovatelný vzor, který můžete přizpůsobit pro větší dokumenty, více stránek nebo složitější grafické efekty.

Další kroky mohou zahrnovat:

* Experimentování s dalšími hodnotami `ShapeType` (elipsa, mrak atd.).  
* Použití `

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}