---
category: general
date: 2026-10-16
description: Vytvořte prázdný dokument Word, vložte do Wordu tvar, přidejte vnější
  stín a uložte jej jako PDF pomocí Pythonu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: cs
lastmod: 2026-10-16
og_description: Vytvořte prázdný dokument Word s tvarem s vnějším stínem pomocí Aspose.Words
  pro Python. Tento návod ukazuje, jak vložit tvar, aplikovat stín a uložit soubor
  jako PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Vytvořte prázdný dokument Word se stínem tvaru – průvodce v Pythonu
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Vytvořte prázdný dokument Word se stínovaným tvarem v Pythonu
url: /cs/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word s tvarem se stínem v Pythonu

Pokud potřebujete **vytvořit prázdný dokument Word** a přidat vlastní grafiku, tento průvodce vám pomůže. Provedeme vás tím, jak **vložit tvar do Wordu**, aplikovat **vnější stín tvaru** a nakonec **uložit jako PDF pomocí Pythonu**.

Naučíte se, jak nastavit Aspose.Words pro Python, vytvořit obdélník, nastavit jeho stín a vygenerovat PDF, které zachová vizuální efekt. Předchozí zkušenost s Aspose API není vyžadována, ale měli byste mít základní znalosti Pythonu a funkční instalaci Python 3.10 nebo novější.

## Požadavky

* Nainstalovaný Python 3.10 nebo novější.
* Aktivní licence Aspose.Words pro Python (pro hodnocení stačí bezplatná zkušební verze).
* Přístup k `pip` pro instalaci balíčku `aspose-words`.
* Oprávnění k zápisu do adresáře, kam bude PDF uloženo.

You can install the library with a single command:

```bash
pip install aspose-words
```

## Vytvoření prázdného dokumentu Word – nastavení prostředí

Prvním krokem je vytvořit prázdný soubor Word, který bude sloužit jako plátno pro tvar.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` represents a completely blank Word file. By using `DocumentBuilder` you gain access to methods like `insert_shape`, which we’ll use in the next step.

## Vložení tvaru do Wordu a nastavení rozměrů

Nyní přidáme obdélník, který později získá vnější stín. Velikost je vyjádřena v bodech (1 pt ≈ 1/72 palce).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

Volání `insert_shape` vrací objekt `Shape`, který můžete dále přizpůsobovat. V tomto okamžiku dokument již obsahuje viditelný obdélník po otevření v Microsoft Wordu.

## Přidání vnějšího stínu tvaru – úprava efektu

Aspose.Words poskytuje třídu `ShadowEffect` pro definování vlastností stínu, jako jsou styl, rozostření, vzdálenost a barva.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Nastavení `style` na `OUTER` zajistí, že se stín objeví mimo okraj obdélníku, čímž vytvoří jemný 3‑D vzhled. Můžete experimentovat s `blur` a `distance`, abyste dosáhli těsnějšího nebo rozptýlenějšího stínu.

## Uložení jako PDF v Pythonu – dokončení dokumentu

Po úpravě tvaru lze dokument uložit přímo jako PDF. Aspose.Words provádí konverzi interně a zachovává efekt stínu.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Když otevřete `shape_with_shadow.pdf` v libovolném prohlížeči PDF, uvidíte obdélník s vnějším stínem přesně tak, jak se zobrazil ve Wordu.

## Kompletní funkční příklad

Níže je kompletní skript, který kombinuje všechny kroky. Zkopírujte jej do souboru s názvem `create_word_with_shadow.py` a spusťte.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Očekávaný výstup**

Spuštění skriptu vypíše potvrzovací řádek, např.:

```
PDF generated at: output/shape_with_shadow.pdf
```

Otevření výsledného PDF zobrazí jedinou stránku obsahující obdélník 200 pt × 100 pt s jemným černým vnějším stínem.

## Běžné varianty a okrajové případy

* **Změna barvy stínu** – Nahraďte `aw.Color.black` libovolnou jinou hodnotou `aw.Color`, například `aw.Color.red` nebo `aw.Color.from_argb(255, 0, 120, 215)`.
* **Použití jiného tvaru** – Změňte `aw.drawing.ShapeType.RECTANGLE` na `OVAL`, `DIAMOND` nebo jakoukoli podporovanou hodnotu enumu.
* **Uložení jako DOCX místo PDF** – Zavolejte `doc.save("output/shape.docx")`, abyste zachovali formát Word.
* **Více tvarů** – Vytvořte další tvary voláním `builder.insert_shape` znovu; každý tvar může mít svůj vlastní `ShadowEffect`.

**Pro tip:** Pokud potřebujete umístit tvar na konkrétní místo, nastavte po vložení `rectangle.left` a `rectangle.top`. To vám poskytne pixel‑dokonalou kontrolu nad umístěním.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **vložit tvar do Wordu**, **přidat vnější stín tvaru** a **uložit jako PDF pomocí Pythonu**. Kompletní ukázkový kód demonstruje celý workflow a vysvětlení objasňují, proč je každé volání API nutné.

Odtud můžete zkoumat pokročilejší možnosti stylování, přidat text uvnitř tvaru nebo kombinovat více tvarů pro tvorbu složitých diagramů. Experimentujte s různými parametry stínu, aby odpovídaly vizuálnímu stylu vaší značky, a integrujte tento přístup do větších pipeline pro generování dokumentů.

Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořte obdélníkový tvar, přidejte stín a uložte PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Vytvořte PDF z Wordu – Kompletní průvodce Pythonem s Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Přidejte stín k tvaru ve Wordu s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}