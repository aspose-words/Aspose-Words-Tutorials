---
category: general
date: 2026-11-25
description: Přidejte stín k tvaru v dokumentu Word pomocí Pythonu. Naučte se, jak
  vložit obdélníkový tvar do Wordu a aplikovat průhledný stín pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: cs
lastmod: 2026-11-25
og_description: Přidejte stín k tvaru v dokumentu Word pomocí Pythonu. Tento tutoriál
  ukazuje, jak vložit obdélníkový tvar do Wordu a nastavit 30 % průhledný stín pomocí
  Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Přidejte stín k tvaru v dokumentu Word pomocí Pythonu – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Jak přidat stín k tvaru ve Word dokumentu pomocí Pythonu
url: /cs/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat stín k tvaru ve Word dokumentu pomocí Pythonu

Pokud potřebujete **přidat stín k tvaru** ve Word dokumentu, tento průvodce vám ukáže kompletní, spustitelný řešení. Uvidíte, jak vytvořit soubor Word, vložit obdélníkový tvar a aplikovat 30 % průhledný stín – vše pomocí knihovny Aspose.Words pro Python.

Práce s Word dokumenty programově vás ušetří ručního formátování a umožní vám generovat zprávy, smlouvy nebo marketingové letáky ve velkém měřítku. Na konci tohoto tutoriálu budete schopni odpovědět na otázku “**how to create Word document python**” s připraveným spustitelným ukázkovým kódem.

## Požadavky

* Python 3.8 nebo novější nainstalovaný.
* Aktivní licence Aspose.Words pro Python (bezplatná zkušební verze funguje pro hodnocení).
* balíček `aspose-words` nainstalovaný pomocí `pip install aspose-words`.
* Složka, do které lze zapsat výstupní soubor (nahraďte `YOUR_DIRECTORY` v kódu).

Žádné další závislosti nejsou vyžadovány.

## Krok 1: Vytvořte nový Word dokument

Prvním krokem je vytvořit instanci objektu `Document`. Tento objekt představuje celý .docx soubor v paměti.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` funguje jako virtuální kurzor. Když voláte jeho metody, knihovna vloží odpovídající prvky na aktuální pozici kurzoru.

## Krok 2: Vložte obdélníkový tvar

Dále **vložíte obdélníkový tvar** pomocí metody `insert_shape` builderu. Metoda vyžaduje typ tvaru a jeho velikost v bodech (1 bod = 1/72 palce).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Můžete změnit rozměry tak, aby odpovídaly vašemu návrhu. Obdélník se stane součástí kreslicí vrstvy dokumentu, což znamená, že jej můžete později upravit – výplň, obrys nebo stín.

## Krok 3: Přístup k formátu stínu tvaru

Každý kreslicí objekt má vlastnost `shadow_format`, která řídí vzhled stínu. Získejte ji, abyste mohli upravit průhlednost, posun, rozostření a barvu.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

V tomto okamžiku má tvar výchozí stín (žádný stín). Objekt `ShadowFormat` obsahuje všechny parametry potřebné k vytvoření realistického efektu.

## Krok 4: Nastavte stín na 30 % průhlednost

Průhlednost se vyjadřuje hodnotou mezi `0` (zcela neprůhledný) a `1` (zcela průhledný). Nastavením na `0.3` získáte 30 % průhledný stín, což je často dostatečné pro přidání hloubky, aniž by text přehlušil.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Tyto další vlastnosti nejsou povinné, ale ukazují, jak můžete efekt jemně doladit. Příznak `visible` je nezbytný; pokud jej zapomenete, stín se nezobrazí, i když jsou ostatní nastavení nakonfigurována.

## Krok 5: Uložte dokument a zobrazte výsledek

Nakonec zapište dokument na disk. Otevření výsledného souboru `.docx` v Microsoft Word nebo jakémkoli kompatibilním prohlížeči zobrazí obdélník s aplikovaným průhledným stínem.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Když otevřete `output.docx`, uvidíte jednoduchý obdélník s jemným šedým stínem posunutým dolů a doprava. 30 % průhlednost stínu způsobí, že se tvar jeví jako nadzvednutý od stránky.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Příklad přidání stínu k tvaru ve Word dokumentu vytvořeném pomocí Pythonu"}

## Kompletní, spustitelný skript

Spojením všech částí získáte samostatný skript, který můžete okamžitě zkopírovat, vložit a spustit.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Očekávaný výstup:** Otevřením vygenerovaného `output.docx` se zobrazí jedna stránka s obdélníkem, který vrhá lehký, poloprůhledný stín. Žádné další formátování není potřeba.

## Běžné varianty a okrajové případy

| Situace | Jak přizpůsobit kód |
|-----------|-----------------------|
| **Jiný typ tvaru** (např. elipsa) | Změňte `aw.drawing.ShapeType.RECTANGLE` na `aw.drawing.ShapeType.ELLIPSE`. |
| **Vlastní barva stínu** | Nastavte `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` pro červený stín. |
| **Více tvarů** | Opakovaně volajte `builder.insert_shape`; každý volání vrátí samostatný objekt `Shape`, který můžete stylovat nezávisle. |
| **Ukládání jako PDF** | Nahraďte `doc.save(output_path)` výrazem `doc.save(output_path.replace('.docx', '.pdf'))` a použijte příponu `.pdf`. |
| **Spouštění bez licence** | Bezplatná zkušební verze přidává vodoznak na první stránku. Získejte licenci, abyste jej odstranili pro produkční použití. |

Tyto varianty ukazují, že stejný vzor – vytvořit dokument, vložit tvar, upravit `shadow_format`, uložit – pokrývá většinu automatizačních scénářů.

## Tipy a osvědčené postupy

* **Znovu použijte builder**: Uchovávejte jedinou instanci `DocumentBuilder` pro celý dokument, abyste se vyhnuli zbytečnému vytváření objektů.
* **Uvolněte zdroje**: V dlouho běžících službách zavolejte po uložení `doc.dispose()`, aby se uvolnila nativní paměť.
* **Ověřte výstup**: Použijte `doc.validate(aw.ValidationType.FULL_VALIDATION)` před uložením, pokud potřebujete zajistit soulad s Open XML standardem.
* **Kompatibilita verzí**: Kód funguje s Aspose.Words pro Python ≥ 22.9. Ujistěte se, že máte balíček aktuální pomocí `pip install --upgrade aspose-words`.

## Závěr

Nyní víte, jak **přidat stín k tvaru** ve Word dokumentu pomocí Pythonu. Dodržením pěti kroků – vytvořit dokument, **vložit obdélníkový tvar**, nastavit stín a uložit – můžete automatizovat tvorbu profesionálních dokumentů pro zprávy, faktury nebo marketingové materiály.  

Odtud můžete zkoumat další možnosti formátování, jako jsou gradientní výplně, obtékání textu nebo převod dokumentu do PDF. Každé z těchto témat staví na stejných konceptech `DocumentBuilder` a formátování tvarů, které byly představeny v tomto tutoriálu.

Šťastné programování a užijte si vizuální hloubku, kterou jednoduchý stín může přinést vašim automatizovaným Word dokumentům!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit obdélníkový tvar ve Word dokumentu pomocí Pythonu](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Přidat stín k tvaru v Pythonu – Kompletní tutoriál Aspose.Words](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Vytvořit prázdný Word dokument a přidat stín k tvaru – Kompletní průvodce pro Python](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}